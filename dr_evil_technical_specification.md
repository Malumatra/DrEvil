# Dr. Evil - Technical Specification Document

## Document Information
**Version:** 1.0  
**Date:** November 14, 2025  
**Purpose:** Technical implementation guide for developers  
**Related Documents:** Game Design Document v1.0

---

## Table of Contents
1. [System Architecture](#system-architecture)
2. [Technology Stack](#technology-stack)
3. [Data Models](#data-models)
4. [Core Systems](#core-systems)
5. [API Specifications](#api-specifications)
6. [Performance Requirements](#performance-requirements)
7. [Security Considerations](#security-considerations)
8. [Testing Strategy](#testing-strategy)

---

## System Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Presentation Layer                       │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Dashboard  │  │  Chat System │  │  Glossary    │      │
│  │   Component  │  │  Component   │  │  Component   │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                      Business Logic Layer                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Task Manager │  │   Minion AI  │  │   Education  │      │
│  │   Service    │  │   Service    │  │   Service    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                        Data Layer                            │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  Game State  │  │  Terminology │  │  User Data   │      │
│  │   Storage    │  │   Database   │  │   Storage    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

### Component Architecture

#### Frontend Components
- **App Container**: Root application component
- **Dashboard**: Main game interface manager
- **Minion Gallery**: Portrait and status display
- **Chat System**: Message rendering and management
- **Task Queue**: Task list and assignment interface
- **Stats Panel**: Metrics and progress display
- **Input Controller**: Command parsing and execution
- **Glossary**: Term database and learning tracker
- **Virtual Computer**: File system and tool simulation

#### Backend Services (if applicable)
- **Save/Load Service**: Game state persistence
- **Analytics Service**: Player behavior tracking
- **Content Service**: Dynamic content delivery
- **Achievement Service**: Progress and unlock tracking

---

## Technology Stack

### Recommended Stack (Web Version)

#### Frontend
```javascript
{
  "framework": "React 18+",
  "stateManagement": "Redux Toolkit or Zustand",
  "styling": "Tailwind CSS + CSS Modules",
  "animations": "Framer Motion",
  "typeChecking": "TypeScript 5+",
  "buildTool": "Vite",
  "testing": "Vitest + React Testing Library"
}
```

#### Backend (Optional - for multiplayer/cloud saves)
```javascript
{
  "runtime": "Node.js 18+",
  "framework": "Express.js or Fastify",
  "database": "PostgreSQL or MongoDB",
  "caching": "Redis",
  "authentication": "JWT tokens"
}
```

#### Development Tools
```javascript
{
  "versionControl": "Git",
  "linting": "ESLint + Prettier",
  "cicd": "GitHub Actions",
  "deployment": "Vercel or Netlify (frontend)",
  "monitoring": "Sentry (error tracking)"
}
```

### Alternative Stack (Desktop Version)

```javascript
{
  "framework": "Electron",
  "frontend": "Same as web version",
  "storage": "SQLite (local)",
  "updates": "electron-updater"
}
```

---

## Data Models

### Core Data Structures

#### Game State
```typescript
interface GameState {
  version: string;
  player: PlayerData;
  minions: Minion[];
  tasks: Task[];
  glossary: GlossaryProgress;
  timeline: GameTimeline;
  settings: GameSettings;
  lastSaved: timestamp;
}
```

#### Player Data
```typescript
interface PlayerData {
  id: string;
  name: string;
  level: number;
  experience: number;
  evilEmpirePoints: number;
  statistics: {
    totalTasksCompleted: number;
    termsLearned: number;
    playTime: number;
    currentStreak: number;
  };
  unlocks: {
    minions: string[];
    features: string[];
    taskTypes: string[];
  };
  achievements: Achievement[];
}
```

#### Minion Model
```typescript
interface Minion {
  id: string;
  name: string;
  type: MinionType;
  portrait: string;
  level: number;
  experience: number;
  
  // Attributes
  attributes: {
    energy: number;          // 0-100
    maxEnergy: number;       // 100 base
    morale: number;          // 0-100
    skillLevel: number;      // 1-10
  };
  
  // Skills
  skills: {
    [skillName: string]: number;  // 1-10 rating
  };
  
  // Specialization
  specialty: Specialty;
  subSpecialties: string[];
  
  // Personality
  personality: {
    traits: string[];
    communicationStyle: string;
    workPreference: string;
  };
  
  // Relationships
  relationships: {
    [minionId: string]: number;  // -10 to 10
  };
  
  // Current status
  status: MinionStatus;
  currentTask: string | null;
  busyUntil: timestamp | null;
}

enum MinionType {
  INFILTRATOR = 'infiltrator',
  CODEBREAKER = 'codebreaker',
  ARCHITECT = 'architect',
  ANALYST = 'analyst',
  COORDINATOR = 'coordinator',
  FORGER = 'forger'
}

enum MinionStatus {
  AVAILABLE = 'available',
  BUSY = 'busy',
  COLLABORATING = 'collaborating',
  RESTING = 'resting',
  COMPLETED = 'completed'
}
```

#### Task Model
```typescript
interface Task {
  id: string;
  title: string;
  description: string;
  category: TaskCategory;
  complexity: TaskComplexity;
  
  // Requirements
  requiredSkills: {
    [skillName: string]: number;  // minimum level
  };
  requiredMinions: number;
  estimatedDuration: number;  // minutes
  
  // Assignment
  assignedMinions: string[];
  startedAt: timestamp | null;
  completedAt: timestamp | null;
  
  // Progress
  status: TaskStatus;
  progress: number;  // 0-100
  quality: number;   // 0-100 (determined at completion)
  
  // Educational content
  terminologyUsed: string[];
  learningObjectives: string[];
  
  // Rewards
  rewards: {
    eep: number;
    experience: number;
    unlocks: string[];
  };
  
  // Output
  deliverables: Deliverable[];
  chatLog: ChatMessage[];
}

enum TaskCategory {
  RESEARCH = 'research',
  DEVELOPMENT = 'development',
  DATA_OPS = 'data_ops',
  DOCUMENTATION = 'documentation',
  STRATEGIC = 'strategic',
  CREATIVE = 'creative'
}

enum TaskComplexity {
  SIMPLE = 'simple',      // 1 minion, 1-5 min
  STANDARD = 'standard',  // 1-2 minions, 5-15 min
  COMPLEX = 'complex',    // 2-4 minions, 15-30 min
  EPIC = 'epic'          // 3-6 minions, 30+ min
}

enum TaskStatus {
  QUEUED = 'queued',
  IN_PROGRESS = 'in_progress',
  REVIEW = 'review',
  COMPLETED = 'completed',
  FAILED = 'failed'
}
```

#### Chat System
```typescript
interface ChatMessage {
  id: string;
  taskId: string;
  senderId: string;  // minion ID
  timestamp: number;
  content: string;
  messageType: MessageType;
  
  // Educational markers
  highlightedTerms: TermReference[];
  
  // Context
  isCollaboration: boolean;
  respondingTo: string | null;  // message ID
  
  // Display
  mood: string;  // affects portrait expression
}

enum MessageType {
  STATUS_UPDATE = 'status_update',
  QUESTION = 'question',
  ANSWER = 'answer',
  COLLABORATION = 'collaboration',
  REVIEW = 'review',
  COMPLETION = 'completion'
}

interface TermReference {
  term: string;
  termId: string;
  startIndex: number;
  endIndex: number;
  isNew: boolean;  // first encounter for player
}
```

#### Terminology/Glossary
```typescript
interface Term {
  id: string;
  term: string;
  definition: string;
  category: TermCategory;
  difficulty: TermDifficulty;
  
  // Examples
  exampleUsage: string[];
  relatedTerms: string[];
  
  // Educational
  fullExplanation: string;
  resources: string[];  // links or references
  
  // Metadata
  addedVersion: string;
  tags: string[];
}

interface GlossaryProgress {
  termsEncountered: {
    [termId: string]: {
      firstSeen: timestamp;
      encounterCount: number;
      mastered: boolean;
      lastReviewed: timestamp;
    }
  };
  
  // Statistics
  totalTermsEncountered: number;
  termsMastered: number;
  currentStreak: number;
  
  // Categories
  categoriesProgress: {
    [category: string]: {
      total: number;
      learned: number;
    }
  };
}

enum TermCategory {
  TECHNICAL = 'technical',
  BUSINESS = 'business',
  PROJECT_MGMT = 'project_management',
  COLLABORATION = 'collaboration',
  PROFESSIONAL = 'professional'
}

enum TermDifficulty {
  BEGINNER = 'beginner',
  INTERMEDIATE = 'intermediate',
  ADVANCED = 'advanced',
  EXPERT = 'expert'
}
```

#### Virtual Computer
```typescript
interface VirtualComputer {
  fileSystem: FileNode;
  openApplications: Application[];
  clipboard: string;
  commandHistory: string[];
}

interface FileNode {
  name: string;
  type: 'file' | 'directory';
  path: string;
  content?: string | BinaryData;
  mimeType?: string;
  children?: FileNode[];
  metadata: {
    created: timestamp;
    modified: timestamp;
    size: number;
    permissions: string;
  };
}

interface Application {
  id: string;
  type: ApplicationType;
  name: string;
  isActive: boolean;
  state: any;  // application-specific state
}

enum ApplicationType {
  TEXT_EDITOR = 'text_editor',
  CODE_EDITOR = 'code_editor',
  SPREADSHEET = 'spreadsheet',
  TERMINAL = 'terminal',
  BROWSER = 'browser',
  DATABASE = 'database'
}
```

---

## Core Systems

### 1. Task Management System

#### Task Generation
```typescript
class TaskGenerator {
  /**
   * Generates a task based on player level and available minions
   */
  generateTask(
    playerLevel: number,
    availableMinions: Minion[],
    category?: TaskCategory
  ): Task {
    // Algorithm:
    // 1. Determine appropriate complexity
    // 2. Select task template from pool
    // 3. Customize requirements based on available minions
    // 4. Add appropriate terminology for player level
    // 5. Calculate rewards
    
    const complexity = this.determineComplexity(playerLevel);
    const template = this.selectTemplate(category, complexity);
    const task = this.customizeTask(template, availableMinions);
    
    return task;
  }
  
  private determineComplexity(playerLevel: number): TaskComplexity {
    if (playerLevel < 5) return TaskComplexity.SIMPLE;
    if (playerLevel < 10) return TaskComplexity.STANDARD;
    if (playerLevel < 15) return TaskComplexity.COMPLEX;
    return TaskComplexity.EPIC;
  }
}
```

#### Task Assignment
```typescript
class TaskAssigner {
  /**
   * Assigns minions to a task based on requirements and availability
   */
  assignMinions(task: Task, minions: Minion[]): Assignment {
    // Algorithm:
    // 1. Filter available minions (energy > 20, status = available)
    // 2. Score each minion for this task
    // 3. Select optimal combination
    // 4. Consider relationships for collaboration
    
    const available = this.filterAvailable(minions);
    const scored = this.scoreMinions(available, task);
    const selected = this.selectOptimal(scored, task.requiredMinions);
    
    return {
      minions: selected,
      estimatedQuality: this.estimateQuality(selected, task),
      estimatedDuration: this.estimateDuration(selected, task)
    };
  }
  
  private scoreMinions(minions: Minion[], task: Task): ScoredMinion[] {
    return minions.map(minion => ({
      minion,
      score: this.calculateScore(minion, task)
    }));
  }
  
  private calculateScore(minion: Minion, task: Task): number {
    let score = 0;
    
    // Skill match
    for (const [skill, required] of Object.entries(task.requiredSkills)) {
      const minionSkill = minion.skills[skill] || 0;
      score += Math.max(0, minionSkill - required) * 10;
    }
    
    // Energy level
    score += minion.attributes.energy / 10;
    
    // Morale
    score += minion.attributes.morale / 10;
    
    return score;
  }
}
```

### 2. Minion AI System

#### Dialogue Generation
```typescript
class DialogueGenerator {
  private templates: DialogueTemplate[];
  private terminology: Term[];
  
  /**
   * Generates contextual dialogue for minions
   */
  generateDialogue(
    context: DialogueContext,
    minion: Minion,
    task: Task
  ): ChatMessage {
    // Algorithm:
    // 1. Select appropriate template based on context
    // 2. Inject personality traits
    // 3. Add relevant terminology
    // 4. Ensure educational value
    
    const template = this.selectTemplate(context, minion.type);
    const personalized = this.applyPersonality(template, minion);
    const withTerms = this.injectTerminology(personalized, task, context);
    
    return {
      id: generateId(),
      taskId: task.id,
      senderId: minion.id,
      timestamp: Date.now(),
      content: withTerms.text,
      messageType: context.type,
      highlightedTerms: withTerms.terms,
      isCollaboration: context.isCollaboration,
      respondingTo: context.respondingTo,
      mood: this.selectMood(minion, context)
    };
  }
  
  private injectTerminology(
    text: string,
    task: Task,
    context: DialogueContext
  ): { text: string; terms: TermReference[] } {
    // Select 1-3 terms appropriate for this context
    const relevantTerms = this.selectRelevantTerms(task, context);
    const injected = this.insertTermsNaturally(text, relevantTerms);
    
    return injected;
  }
}
```

#### Collaboration Simulation
```typescript
class CollaborationEngine {
  /**
   * Simulates minion collaboration on a task
   */
  async simulateCollaboration(
    task: Task,
    minions: Minion[]
  ): Promise<ChatMessage[]> {
    const messages: ChatMessage[] = [];
    const phases = this.getCollaborationPhases(task);
    
    for (const phase of phases) {
      const phaseMessages = await this.simulatePhase(
        phase,
        task,
        minions,
        messages
      );
      messages.push(...phaseMessages);
      
      // Add delays for realism
      await this.delay(phase.duration);
    }
    
    return messages;
  }
  
  private getCollaborationPhases(task: Task): CollaborationPhase[] {
    // Phases: Planning → Execution → Review → Completion
    return [
      {
        name: 'planning',
        duration: task.estimatedDuration * 0.2,
        messageCount: 3-5,
        focus: 'approach_discussion'
      },
      {
        name: 'execution',
        duration: task.estimatedDuration * 0.6,
        messageCount: 5-10,
        focus: 'work_updates'
      },
      {
        name: 'review',
        duration: task.estimatedDuration * 0.15,
        messageCount: 2-4,
        focus: 'quality_check'
      },
      {
        name: 'completion',
        duration: task.estimatedDuration * 0.05,
        messageCount: 1-2,
        focus: 'wrap_up'
      }
    ];
  }
}
```

### 3. Education System

#### Learning Tracker
```typescript
class LearningTracker {
  /**
   * Tracks player's learning progress
   */
  recordTermEncounter(
    playerId: string,
    termId: string,
    context: string
  ): void {
    const progress = this.getGlossaryProgress(playerId);
    
    if (!progress.termsEncountered[termId]) {
      // First encounter
      progress.termsEncountered[termId] = {
        firstSeen: Date.now(),
        encounterCount: 1,
        mastered: false,
        lastReviewed: Date.now()
      };
      progress.totalTermsEncountered++;
      
      this.showNewTermNotification(termId);
    } else {
      // Repeat encounter
      const termProgress = progress.termsEncountered[termId];
      termProgress.encounterCount++;
      termProgress.lastReviewed = Date.now();
      
      // Check for mastery
      if (this.checkMastery(termProgress)) {
        termProgress.mastered = true;
        progress.termsMastered++;
        this.showMasteryNotification(termId);
      }
    }
    
    this.saveProgress(playerId, progress);
  }
  
  private checkMastery(termProgress: TermProgress): boolean {
    // Mastery criteria:
    // - Encountered at least 5 times
    // - Seen in at least 3 different contexts
    // - Correctly identified in quiz (if taken)
    
    return termProgress.encounterCount >= 5;
  }
}
```

#### Adaptive Learning
```typescript
class AdaptiveLearning {
  /**
   * Adjusts terminology difficulty based on player progress
   */
  selectTerminologyForTask(
    task: Task,
    playerProgress: GlossaryProgress
  ): Term[] {
    const targetCount = this.getTermCountForTask(task);
    const difficulty = this.getCurrentDifficulty(playerProgress);
    
    // Mix of review and new terms
    const reviewTerms = this.selectReviewTerms(playerProgress, targetCount * 0.3);
    const newTerms = this.selectNewTerms(difficulty, targetCount * 0.7);
    
    return [...reviewTerms, ...newTerms];
  }
  
  private getCurrentDifficulty(progress: GlossaryProgress): TermDifficulty {
    const masteryRate = progress.termsMastered / progress.totalTermsEncountered;
    
    if (masteryRate > 0.8) return TermDifficulty.ADVANCED;
    if (masteryRate > 0.6) return TermDifficulty.INTERMEDIATE;
    return TermDifficulty.BEGINNER;
  }
}
```

### 4. Save/Load System

#### Save State Manager
```typescript
class SaveStateManager {
  /**
   * Saves complete game state
   */
  async saveGame(gameState: GameState): Promise<void> {
    // Prepare state
    const serialized = this.serializeState(gameState);
    const compressed = await this.compress(serialized);
    const encrypted = this.encrypt(compressed); // optional
    
    // Save to storage
    await this.writeToStorage('gameState', encrypted);
    
    // Backup to cloud (if enabled)
    if (this.cloudSaveEnabled()) {
      await this.uploadToCloud(encrypted);
    }
  }
  
  /**
   * Loads game state
   */
  async loadGame(): Promise<GameState> {
    try {
      // Try local storage first
      const encrypted = await this.readFromStorage('gameState');
      const compressed = this.decrypt(encrypted);
      const serialized = await this.decompress(compressed);
      const gameState = this.deserializeState(serialized);
      
      return this.validateState(gameState);
    } catch (error) {
      // Fallback to cloud save
      if (this.cloudSaveEnabled()) {
        return await this.loadFromCloud();
      }
      throw new Error('Failed to load game state');
    }
  }
  
  /**
   * Auto-save implementation
   */
  enableAutoSave(interval: number = 30000): void {
    setInterval(() => {
      const gameState = this.getCurrentGameState();
      this.saveGame(gameState).catch(error => {
        console.error('Auto-save failed:', error);
      });
    }, interval);
  }
}
```

---

## API Specifications

### Internal API (Frontend ↔ Game Logic)

#### Task API
```typescript
interface TaskAPI {
  // Create new task
  createTask(params: TaskCreationParams): Task;
  
  // Assign minions to task
  assignTask(taskId: string, minionIds: string[]): Assignment;
  
  // Start task execution
  startTask(taskId: string): void;
  
  // Get task progress
  getTaskProgress(taskId: string): TaskProgress;
  
  // Complete task
  completeTask(taskId: string): TaskResult;
  
  // Cancel task
  cancelTask(taskId: string): void;
}
```

#### Minion API
```typescript
interface MinionAPI {
  // Get minion details
  getMinion(minionId: string): Minion;
  
  // Update minion state
  updateMinion(minionId: string, updates: Partial<Minion>): Minion;
  
  // Level up minion
  levelUpMinion(minionId: string): Minion;
  
  // Rest minion (restore energy)
  restMinion(minionId: string): void;
  
  // Get minion availability
  getMinionAvailability(minionId: string): AvailabilityStatus;
}
```

#### Chat API
```typescript
interface ChatAPI {
  // Get messages for task
  getTaskMessages(taskId: string): ChatMessage[];
  
  // Subscribe to new messages
  subscribeToMessages(taskId: string, callback: (msg: ChatMessage) => void): Unsubscribe;
  
  // Mark messages as read
  markAsRead(messageIds: string[]): void;
  
  // Get term definition
  getTermDefinition(termId: string): Term;
}
```

### External API (if Backend exists)

#### RESTful Endpoints
```
POST   /api/auth/login
POST   /api/auth/register
GET    /api/auth/logout

GET    /api/player/profile
PUT    /api/player/profile
GET    /api/player/progress

POST   /api/game/save
GET    /api/game/load
GET    /api/game/state

GET    /api/content/tasks
GET    /api/content/terminology
GET    /api/content/minions

POST   /api/analytics/event
GET    /api/analytics/stats

GET    /api/leaderboard
POST   /api/achievements/unlock
```

---

## Performance Requirements

### Target Metrics

#### Load Times
- **Initial Load**: < 3 seconds
- **Save Game**: < 500ms
- **Load Game**: < 1 second
- **Task Start**: < 200ms
- **Chat Message Render**: < 16ms (60fps)

#### Resource Usage
- **Memory**: < 200MB RAM
- **Storage**: < 50MB for base game
- **CPU**: < 5% idle, < 20% during active simulation
- **Network**: < 100KB initial load (if online)

### Optimization Strategies

#### 1. Code Splitting
```typescript
// Lazy load heavy components
const VirtualComputer = lazy(() => import('./VirtualComputer'));
const GlossaryPanel = lazy(() => import('./GlossaryPanel'));
```

#### 2. Message Virtualization
```typescript
// Only render visible messages in chat
<VirtualList
  height={600}
  itemCount={messages.length}
  itemSize={80}
  renderItem={({index}) => <ChatMessage message={messages[index]} />}
/>
```

#### 3. State Management Optimization
```typescript
// Use selectors to prevent unnecessary re-renders
const activeTasks = useSelector(selectActiveTasks, shallowEqual);
const availableMinions = useSelector(selectAvailableMinions, shallowEqual);
```

#### 4. Asset Optimization
- Compress images (WebP format)
- Use CSS sprites for minion portraits
- Lazy load terminology database
- Cache static assets

---

## Security Considerations

### Client-Side Security

#### Save File Protection
```typescript
// Encrypt sensitive data
class SaveEncryption {
  private key: CryptoKey;
  
  async encrypt(data: string): Promise<string> {
    const encoder = new TextEncoder();
    const dataBuffer = encoder.encode(data);
    const encrypted = await crypto.subtle.encrypt(
      { name: 'AES-GCM', iv: this.generateIV() },
      this.key,
      dataBuffer
    );
    return this.arrayBufferToBase64(encrypted);
  }
}
```

#### Input Validation
```typescript
// Validate all user input
class InputValidator {
  validateTaskCommand(input: string): ValidationResult {
    // Prevent script injection
    const sanitized = this.sanitize(input);
    
    // Check length
    if (sanitized.length > 500) {
      return { valid: false, error: 'Input too long' };
    }
    
    // Check for malicious patterns
    if (this.containsMaliciousPattern(sanitized)) {
      return { valid: false, error: 'Invalid input' };
    }
    
    return { valid: true, sanitized };
  }
  
  private sanitize(input: string): string {
    return input
      .replace(/<script>/gi, '')
      .replace(/javascript:/gi, '')
      .trim();
  }
}
```

### Backend Security (if applicable)

#### Authentication
```typescript
// JWT-based authentication
class AuthService {
  async login(credentials: Credentials): Promise<AuthToken> {
    const user = await this.validateCredentials(credentials);
    
    const token = jwt.sign(
      { userId: user.id, role: user.role },
      process.env.JWT_SECRET,
      { expiresIn: '7d' }
    );
    
    return { token, user };
  }
  
  verifyToken(token: string): TokenPayload {
    return jwt.verify(token, process.env.JWT_SECRET);
  }
}
```

#### Rate Limiting
```typescript
// Prevent abuse
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // limit each IP to 100 requests per windowMs
  message: 'Too many requests from this IP'
});

app.use('/api/', limiter);
```

---

## Testing Strategy

### Unit Tests

#### Example: Task Generator Tests
```typescript
describe('TaskGenerator', () => {
  let generator: TaskGenerator;
  
  beforeEach(() => {
    generator = new TaskGenerator();
  });
  
  it('should generate simple tasks for low-level players', () => {
    const task = generator.generateTask(2, mockMinions);
    expect(task.complexity).toBe(TaskComplexity.SIMPLE);
    expect(task.requiredMinions).toBeLessThanOrEqual(1);
  });
  
  it('should include appropriate terminology for player level', () => {
    const task = generator.generateTask(5, mockMinions);
    const terms = task.terminologyUsed;
    
    const difficulties = terms.map(t => 
      terminology.find(term => term.id === t).difficulty
    );
    
    expect(difficulties).not.toContain(TermDifficulty.EXPERT);
  });
  
  it('should match task requirements to available minions', () => {
    const minions = [createMockMinion(MinionType.ANALYST)];
    const task = generator.generateTask(5, minions, TaskCategory.DATA_OPS);
    
    expect(task.category).toBe(TaskCategory.DATA_OPS);
    expect(task.requiredSkills).toHaveProperty('data_analysis');
  });
});
```

### Integration Tests

#### Example: Task Execution Flow
```typescript
describe('Task Execution Flow', () => {
  it('should complete full task lifecycle', async () => {
    const game = new GameEngine();
    await game.initialize();
    
    // Create task
    const task = game.createTask({
      category: TaskCategory.RESEARCH,
      complexity: TaskComplexity.SIMPLE
    });
    
    // Assign minions
    const assignment = game.assignTask(task.id, [minion1.id]);
    expect(assignment.minions).toHaveLength(1);
    
    // Start task
    game.startTask(task.id);
    expect(task.status).toBe(TaskStatus.IN_PROGRESS);
    
    // Fast-forward time
    await game.advanceTime(task.estimatedDuration);
    
    // Check completion
    expect(task.status).toBe(TaskStatus.COMPLETED);
    expect(task.deliverables).toHaveLength(1);
    expect(task.chatLog.length).toBeGreaterThan(0);
  });
});
```

### End-to-End Tests

#### Example: Player Journey
```typescript
describe('New Player Experience', () => {
  it('should guide player through tutorial', async () => {
    const app = await launchApp();
    
    // Start new game
    await app.click('[data-testid="new-game"]');
    
    // Verify tutorial starts
    expect(await app.getText('.tutorial-message')).toContain('Welcome');
    
    // Complete first task
    await app.type('[data-testid="input"]', 'Create a to-do list');
    await app.click('[data-testid="submit"]');
    
    // Wait for task completion
    await app.waitFor('[data-testid="task-complete"]');
    
    // Verify learning
    const glossary = await app.click('[data-testid="glossary"]');
    expect(await app.count('.term-entry')).toBeGreaterThan(0);
  });
});
```

### Performance Tests

```typescript
describe('Performance Benchmarks', () => {
  it('should handle 100 concurrent messages', async () => {
    const startTime = performance.now();
    
    const messages = Array(100).fill(null).map(() => 
      createMockMessage()
    );
    
    render(<ChatWindow messages={messages} />);
    
    const endTime = performance.now();
    expect(endTime - startTime).toBeLessThan(100); // 100ms
  });
  
  it('should save game state in under 500ms', async () => {
    const gameState = createLargeGameState();
    const saveManager = new SaveStateManager();
    
    const startTime = performance.now();
    await saveManager.saveGame(gameState);
    const endTime = performance.now();
    
    expect(endTime - startTime).toBeLessThan(500);
  });
});
```

---

## Deployment

### Build Process

```bash
# Development build
npm run dev

# Production build
npm run build

# Preview production build
npm run preview

# Run tests
npm run test

# Run linter
npm run lint

# Type check
npm run type-check
```

### Environment Variables

```env
# App Configuration
VITE_APP_NAME=Dr. Evil
VITE_APP_VERSION=1.0.0
VITE_ENVIRONMENT=production

# API Configuration (if backend exists)
VITE_API_URL=https://api.drevil.game
VITE_API_TIMEOUT=10000

# Feature Flags
VITE_ENABLE_CLOUD_SAVE=true
VITE_ENABLE_ANALYTICS=true
VITE_ENABLE_ACHIEVEMENTS=true

# Analytics
VITE_ANALYTICS_ID=UA-XXXXXXXXX-X

# Error Tracking
VITE_SENTRY_DSN=https://xxx@sentry.io/xxx
```

### Deployment Platforms

#### Vercel (Recommended for Web)
```json
{
  "buildCommand": "npm run build",
  "outputDirectory": "dist",
  "devCommand": "npm run dev",
  "framework": "vite"
}
```

#### Electron (Desktop)
```javascript
// electron-builder configuration
{
  "appId": "com.drevil.game",
  "productName": "Dr. Evil",
  "directories": {
    "output": "release"
  },
  "files": [
    "dist/**/*",
    "electron/**/*"
  ],
  "mac": {
    "category": "public.app-category.games",
    "target": ["dmg", "zip"]
  },
  "win": {
    "target": ["nsis", "portable"]
  },
  "linux": {
    "target": ["AppImage", "deb"]
  }
}
```

---

## Monitoring & Analytics

### Metrics to Track

#### Player Engagement
- Sessions per day
- Average session length
- Task completion rate
- Return rate (1-day, 7-day, 30-day)
- Churn rate

#### Educational Effectiveness
- Terms learned per session
- Mastery rate
- Time to mastery per term
- Quiz scores (if implemented)

#### Game Balance
- Minion usage distribution
- Task category preferences
- Average task completion time vs. estimated
- Player progression speed

#### Technical Performance
- Page load time
- Error rate
- API response times
- Client-side performance metrics

### Analytics Implementation

```typescript
class AnalyticsService {
  trackEvent(event: AnalyticsEvent): void {
    // Send to analytics service
    if (window.gtag) {
      window.gtag('event', event.name, {
        event_category: event.category,
        event_label: event.label,
        value: event.value
      });
    }
    
    // Log locally for development
    if (import.meta.env.DEV) {
      console.log('Analytics Event:', event);
    }
  }
  
  trackPageView(page: string): void {
    this.trackEvent({
      name: 'page_view',
      category: 'navigation',
      label: page
    });
  }
  
  trackTaskCompletion(task: Task, duration: number): void {
    this.trackEvent({
      name: 'task_completed',
      category: 'gameplay',
      label: task.category,
      value: duration
    });
  }
}
```

---

## Appendix

### Code Style Guide

```typescript
// Use TypeScript for type safety
// Use functional components with hooks
// Use meaningful variable names
// Add JSDoc comments for complex functions

/**
 * Calculates the optimal minion assignment for a task
 * @param task - The task to assign
 * @param availableMinions - Pool of available minions
 * @returns Optimal assignment with quality estimate
 */
function calculateOptimalAssignment(
  task: Task,
  availableMinions: Minion[]
): Assignment {
  // Implementation
}
```

### Naming Conventions

- **Components**: PascalCase (TaskCard, MinionPortrait)
- **Functions**: camelCase (calculateScore, generateDialogue)
- **Constants**: UPPER_SNAKE_CASE (MAX_MINIONS, DEFAULT_ENERGY)
- **Interfaces**: PascalCase with 'I' prefix optional (Task, IGameState)
- **Enums**: PascalCase for enum, UPPER_SNAKE_CASE for values

### File Structure

```
src/
├── components/           # React components
│   ├── Dashboard/
│   ├── MinionGallery/
│   ├── ChatSystem/
│   └── shared/
├── services/            # Business logic
│   ├── TaskService.ts
│   ├── MinionAI.ts
│   └── EducationService.ts
├── stores/              # State management
│   ├── gameStore.ts
│   ├── playerStore.ts
│   └── uiStore.ts
├── models/              # TypeScript interfaces
│   ├── Task.ts
│   ├── Minion.ts
│   └── Player.ts
├── utils/               # Utility functions
│   ├── calculations.ts
│   ├── formatters.ts
│   └── validators.ts
├── data/                # Static game data
│   ├── terminology.json
│   ├── taskTemplates.json
│   └── minionData.json
├── assets/              # Images, fonts, etc.
│   ├── images/
│   ├── portraits/
│   └── icons/
└── App.tsx              # Root component
```

---

## Version History

**v1.0 - November 14, 2025**
- Initial technical specification
- Complete system architecture
- Data models defined
- Core systems documented

---

*End of Technical Specification*
