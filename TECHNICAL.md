# EchoQuest Technical Documentation 🛠️

## 📜 Script Architecture

### Core Systems

#### Player Controller (`PlayerController.cs`)
```csharp
public class PlayerController : MonoBehaviour
{
    // Movement
    private Vector2 movement;
    private Rigidbody2D rb;
    private float moveSpeed = 5f;
    
    // Dash
    private float dashForce = 20f;
    private float dashCooldown = 1f;
    private bool canDash = true;
    
    // State Management
    private PlayerState currentState;
    private Animator animator;
}
```

#### Emotion System (`EmotionManager.cs`)
```csharp
public class EmotionManager : MonoBehaviour
{
    // Emotion States
    private Dictionary<string, float> emotionLevels;
    private float maxEmotionLevel = 100f;
    
    // Mind Shard Collection
    private int collectedShards = 0;
    private int totalShards = 10;
}
```

### Zone Management

#### Zone Controller (`ZoneController.cs`)
```csharp
public class ZoneController : MonoBehaviour
{
    // Zone Properties
    public string zoneName;
    public EmotionType primaryEmotion;
    public float zoneInfluence;
    
    // Environmental Effects
    public ParticleSystem ambientParticles;
    public AudioSource zoneMusic;
}
```

## 🎮 Game Mechanics

### Movement System
- **WASD Movement**: Smooth 4-directional movement with acceleration/deceleration
- **Click-to-Move**: Pathfinding with A* algorithm
- **Dash Ability**: 
  - Cooldown: 1 second
  - Distance: 5 units
  - Invincibility frames: 0.2 seconds

### Combat System
- **Attack Types**:
  - Light Attack: Quick, low damage
  - Heavy Attack: Slow, high damage
  - Special Attack: Emotion-based abilities
- **Combo System**:
  - 3-hit combo chain
  - Timing window: 0.5 seconds between hits
  - Combo multiplier: 1.2x per successful hit

### Emotion Mechanics
- **Mind Shard Collection**:
  - Required for zone progression
  - Affects world state
  - Unlocks new abilities
- **Emotional Resonance**:
  - Player's emotional state affects NPC interactions
  - Influences puzzle solutions
  - Changes environmental effects

## 🎵 Rhythm & Audio System

### Music System
```csharp
public class MusicManager : MonoBehaviour
{
    // Dynamic Music
    private AudioSource[] musicLayers;
    private float[] layerVolumes;
    
    // Emotion-based Transitions
    public void TransitionToEmotion(EmotionType emotion)
    {
        // Smoothly crossfade between emotional states
    }
}
```

### Sound Design
- **Ambient Sounds**:
  - Dynamic mixing based on player location
  - Environmental awareness system
  - Spatial audio implementation
- **Emotional Audio**:
  - Music layers respond to player's emotional state
  - Sound effects reflect current zone theme
  - Voice acting for key emotional moments

## 🧩 Puzzle Systems

### Interaction System
```csharp
public class Interactable : MonoBehaviour
{
    // Interaction Properties
    public float interactionRange = 2f;
    public string interactionPrompt;
    
    // Puzzle Elements
    public PuzzleType puzzleType;
    public bool isSolved;
}
```

### Puzzle Types
1. **Emotional Puzzles**:
   - Match emotions to solve
   - Use collected Mind Shards
   - Time-based challenges

2. **Environmental Puzzles**:
   - Manipulate the environment
   - Use emotional states to affect surroundings
   - Combine multiple elements

3. **NPC Interaction Puzzles**:
   - Dialogue-based solutions
   - Emotional response matching
   - Trust-building mechanics

## 🎨 Visual Effects

### Particle Systems
- **Emotional Auras**:
  - Color-coded by emotion type
  - Intensity based on emotional level
  - Dynamic scaling with player movement

### Animation System
```csharp
public class AnimationController : MonoBehaviour
{
    // Animation States
    private Dictionary<EmotionType, AnimationClip> emotionAnimations;
    private float blendSpeed = 0.5f;
    
    // Transition Management
    public void BlendToEmotion(EmotionType emotion)
    {
        // Smooth transition between emotional states
    }
}
```

## 🔄 Save System

### Save Data Structure
```csharp
[System.Serializable]
public class SaveData
{
    // Player Progress
    public Vector3 playerPosition;
    public int collectedShards;
    public Dictionary<string, float> emotionLevels;
    
    // Zone Progress
    public List<string> unlockedZones;
    public Dictionary<string, bool> completedPuzzles;
    
    // Settings
    public float musicVolume;
    public float sfxVolume;
    public int languageIndex;
}
```

## 📱 Mobile Optimization

### Touch Controls
- **Virtual Joystick**:
  - Customizable position
  - Adjustable sensitivity
  - Haptic feedback
- **Touch Gestures**:
  - Swipe for dash
  - Tap for interaction
  - Pinch for zoom

### Performance Optimization
- **Asset Bundling**:
  - Zone-based loading
  - Dynamic quality settings
  - Memory management
- **Battery Optimization**:
  - Frame rate limiting
  - Background process management
  - Power-saving modes

## 🔍 Debug Tools

### Development Console
```csharp
public class DebugConsole : MonoBehaviour
{
    // Debug Commands
    private Dictionary<string, System.Action> commands;
    
    // Performance Monitoring
    public void MonitorPerformance()
    {
        // Track FPS, memory usage, etc.
    }
}
```

### Testing Tools
- **Emotion Simulator**:
  - Test emotional states
  - Trigger events
  - Monitor responses
- **Zone Editor**:
  - Place puzzle elements
  - Set emotional influences
  - Test interactions

---

*This technical documentation is a living document and will be updated as the project evolves.* 