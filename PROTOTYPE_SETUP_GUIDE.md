# Harbinger - Prototype Setup Guide (No Pixel Art)

**Goal:** Create a playable flight prototype with placeholder graphics in 1-2 weeks
**Focus:** Core mechanics first, visuals later
**Approach:** Colored rectangles for UI, simple 3D shapes for debris

---

## Phase 1: Unity Project Setup (Day 1)

### Install Unity

1. **Download Unity Hub**
   - Visit: https://unity.com/download
   - Install Unity Hub (free)

2. **Install Unity 2022.3 LTS** (Recommended)
   - Open Unity Hub
   - Go to: Installs → Install Editor → 2022.3 LTS
   - Select modules:
     - ✅ iOS Build Support
     - ✅ Android Build Support (optional, for testing)
     - ✅ Documentation
     - ✅ Visual Studio (if on Windows) or VS Code

3. **Create New Project**
   ```
   Template: 3D (URP) - Universal Render Pipeline
   Project Name: Harbinger
   Location: Choose folder (NOT inside git repo yet)
   Unity Version: 2022.3 LTS
   ```

### Initial Unity Configuration

After project opens:

1. **Project Settings** (Edit → Project Settings)
   ```
   Player → Other Settings:
   - Company Name: [Your Name]
   - Product Name: Harbinger
   - Default Orientation: Landscape Left
   - Target Platform: iOS
   - Minimum iOS Version: 13.0

   Quality → Default:
   - V Sync Count: Every V Blank
   - Anti Aliasing: Disabled (retro style)

   Input System:
   - Switch to "Both" (old + new input system)
   ```

2. **Install Required Packages** (Window → Package Manager)
   ```
   ✅ Input System (com.unity.inputsystem)
   ✅ Cinemachine (com.unity.cinemachine) - Optional for camera
   ✅ TextMeshPro (com.unity.textmeshpro) - For UI text
   ```

---

## Phase 2: Project Structure Setup (Day 1)

### Create Folder Structure

In Project window, create these folders:

```
Assets/
├── _Scenes/
│   ├── MainMenu.unity          (Create scene)
│   ├── Phase1_Orbital.unity    (Create scene)
│   └── TestScene.unity          (Create scene - start here)
├── Scripts/
│   ├── Flight/
│   ├── UI/
│   ├── Debris/
│   └── GameManagement/
├── Prefabs/
│   ├── Ship/
│   ├── Debris/
│   └── UI/
├── Materials/
│   ├── UI/
│   └── Debris/
├── Audio/
│   ├── Music/
│   ├── SFX/
│   └── Ambience/
└── Settings/
    └── InputActions/
```

**Quick Create Tip:** Right-click in Project window → Create → Folder

---

## Phase 3: Placeholder UI Setup (Day 2)

### Create Placeholder Cockpit Canvas

1. **Create UI Canvas** (Hierarchy → Right-click → UI → Canvas)
   ```
   Name: CockpitCanvas
   Canvas → Render Mode: Screen Space - Overlay
   Canvas Scaler:
   - UI Scale Mode: Scale With Screen Size
   - Reference Resolution: 1920 x 1080
   - Match: 0.5 (width/height blend)
   ```

2. **Create UI Structure** (Right-click CockpitCanvas)

   **Left Panel (Gauges):**
   ```
   Create: UI → Panel
   Name: LeftPanel
   Rect Transform:
   - Anchor: Left-stretch
   - Pos X: 150, Pos Y: 0
   - Width: 300, Height: 100% (stretch)
   - Color: Dark gray (30, 30, 30, 200)
   ```

   **Right Panel (Radar/Systems):**
   ```
   Create: UI → Panel
   Name: RightPanel
   Rect Transform:
   - Anchor: Right-stretch
   - Pos X: -150, Pos Y: 0
   - Width: 300, Height: 100% (stretch)
   - Color: Dark gray (30, 30, 30, 200)
   ```

   **Bottom Panel (Console):**
   ```
   Create: UI → Panel
   Name: BottomPanel
   Rect Transform:
   - Anchor: Bottom-stretch
   - Pos X: 0, Pos Y: 75
   - Width: 100% (stretch), Height: 150
   - Color: Dark gray (40, 40, 40, 220)
   ```

   **Top Bar (Ship Name):**
   ```
   Create: UI → Panel
   Name: TopBar
   Rect Transform:
   - Anchor: Top-stretch
   - Pos X: 0, Pos Y: -20
   - Width: 100% (stretch), Height: 40
   - Color: Medium gray (70, 70, 70, 255)
   ```

3. **Add Text Labels** (Right-click panels → UI → Text - TextMeshPro)

   **Top Bar Text:**
   ```
   Name: ShipNameText
   Text: "USCSS HARBINGER - PROSPECTOR CLASS"
   Font: LiberationSans SDF
   Font Size: 24
   Alignment: Center + Middle
   Color: White (255, 255, 255, 255)
   ```

   **Gauge Labels (Left Panel):**
   ```
   Create 3 TextMeshPro objects:
   - FuelLabel: "FUEL: 100%"
   - VelocityLabel: "VEL: 0.0"
   - TemperatureLabel: "TEMP: NORMAL"

   Font Size: 20
   Color: Green (0, 255, 0, 255)
   Alignment: Left + Top
   Arrange vertically with 40px spacing
   ```

   **System Status (Right Panel):**
   ```
   Create 5 TextMeshPro objects:
   - EngineStatus: "ENG: OK"
   - ShieldStatus: "SHD: OK"
   - RCSStatus: "RCS: OK"
   - SensorStatus: "SNR: OK"
   - LandingGearStatus: "LND: RETRACTED"

   Font Size: 18
   Color: Green (0, 255, 0, 255)
   Arrange vertically
   ```

4. **Add Placeholder Gauges** (UI → Image)

   **Fuel Gauge (Left Panel):**
   ```
   Create: UI → Image
   Name: FuelGaugeBackground
   Color: Dark gray (20, 20, 20, 255)
   Width: 100, Height: 100
   Position: Top-left of LeftPanel

   Child object: FuelGaugeFill (UI → Image)
   - Image Type: Filled
   - Fill Method: Radial 360
   - Fill Origin: Top
   - Fill Amount: 1.0 (100%)
   - Color: Green (0, 255, 0, 255)
   ```

   **Radar Scope (Right Panel):**
   ```
   Create: UI → Image
   Name: RadarBackground
   Color: Very dark green (0, 50, 0, 255)
   Width: 200, Height: 200
   Shape: Circle (use sprite or RawImage with circle texture)
   Position: Top-right of RightPanel

   Add crosshair: UI → Image
   - Sprite: Use built-in "Knob" sprite
   - Color: Bright green (0, 255, 0, 255)
   - Width: 20, Height: 20
   - Center of RadarBackground
   ```

5. **Add Thrust Indicator (Bottom Panel):**
   ```
   Create 5 UI Images (arrows):
   - ThrustUp, ThrustDown, ThrustLeft, ThrustRight, ThrustForward
   - Use built-in arrow sprites or create with triangles
   - Arrange in cross pattern (+)
   - Default color: Dark gray (50, 50, 50, 255)
   - Active color: Cyan (0, 200, 255, 255) - will change via script
   ```

6. **Save Canvas as Prefab**
   ```
   Drag CockpitCanvas to Assets/Prefabs/UI/
   Now you can reuse across scenes
   ```

---

## Phase 4: Create Simple Ship (Day 2-3)

### Player Ship GameObject

1. **Create Ship Object** (Hierarchy → Create Empty)
   ```
   Name: PlayerShip
   Transform:
   - Position: (0, 0, 0)
   - Rotation: (0, 0, 0)
   - Scale: (1, 1, 1)
   ```

2. **Add Visual Mesh** (Right-click PlayerShip → 3D Object → Cube)
   ```
   Name: ShipMesh
   Transform:
   - Scale: (1, 0.5, 2) - Make it ship-shaped
   - Position: (0, 0, 0) relative to parent

   Material:
   - Create: Assets/Materials/ → New Material → ShipMaterial
   - Color: Light gray (180, 180, 180)
   - Shader: URP/Lit
   ```

3. **Add Thruster Visual** (Right-click PlayerShip → 3D Object → Cube)
   ```
   Name: ThrusterGlow
   Transform:
   - Position: (0, 0, -1.2) - Behind ship
   - Scale: (0.3, 0.3, 0.5)

   Material:
   - Create: ThrusterMaterial
   - Color: Cyan (0, 200, 255)
   - Emission: Enabled, Color: Cyan (0, 200, 255)
   - Intensity: 2
   ```

4. **Add Components to PlayerShip:**
   ```
   Add Component → Physics → Rigidbody
   - Mass: 1000
   - Drag: 0 (space has no drag)
   - Angular Drag: 0.5
   - Use Gravity: UNCHECKED (we're in space!)
   - Constraints: Freeze Rotation Z (prevent rolling if desired)

   Add Component → Physics → Box Collider
   - Size: (1, 0.5, 2) - Match ship mesh
   - Is Trigger: Unchecked
   ```

---

## Phase 5: Create Flight Control Script (Day 3-4)

### Create ShipController.cs

1. **Create Script** (Assets/Scripts/Flight → Right-click → Create → C# Script)
   ```
   Name: ShipController.cs
   ```

2. **Copy this starter code:**

```csharp
using UnityEngine;

public class ShipController : MonoBehaviour
{
    [Header("Flight Settings")]
    [SerializeField] private float mainThrustForce = 50f;
    [SerializeField] private float rcsThrustForce = 20f;
    [SerializeField] private float rotationSpeed = 100f;
    [SerializeField] private float maxVelocity = 50f;

    [Header("Components")]
    [SerializeField] private Rigidbody rb;
    [SerializeField] private GameObject thrusterGlow;

    [Header("UI References")]
    [SerializeField] private TMPro.TextMeshProUGUI velocityLabel;
    [SerializeField] private TMPro.TextMeshProUGUI fuelLabel;

    // Private variables
    private float currentFuel = 100f;
    private float fuelConsumptionRate = 1f; // Per second when thrusting
    private Vector3 thrustInput;
    private Vector2 rotationInput;

    void Start()
    {
        // Get rigidbody if not assigned
        if (rb == null)
            rb = GetComponent<Rigidbody>();

        // Find thruster glow if not assigned
        if (thrusterGlow == null)
            thrusterGlow = transform.Find("ThrusterGlow")?.gameObject;

        // Set thruster glow to inactive initially
        if (thrusterGlow != null)
            thrusterGlow.SetActive(false);
    }

    void Update()
    {
        // Get input
        GetInput();

        // Update UI
        UpdateUI();

        // Visual feedback
        UpdateThrusterVisual();
    }

    void FixedUpdate()
    {
        // Apply physics
        ApplyThrust();
        ApplyRotation();

        // Limit velocity
        LimitVelocity();
    }

    void GetInput()
    {
        // Thrust input (WASD + Space/Shift for up/down)
        thrustInput = Vector3.zero;

        // Forward/Backward
        if (Input.GetKey(KeyCode.W))
            thrustInput.z = 1f;
        if (Input.GetKey(KeyCode.S))
            thrustInput.z = -1f;

        // Strafe Left/Right
        if (Input.GetKey(KeyCode.A))
            thrustInput.x = -1f;
        if (Input.GetKey(KeyCode.D))
            thrustInput.x = 1f;

        // Up/Down
        if (Input.GetKey(KeyCode.Space))
            thrustInput.y = 1f;
        if (Input.GetKey(KeyCode.LeftShift))
            thrustInput.y = -1f;

        // Rotation input (Arrow keys)
        rotationInput = Vector2.zero;

        if (Input.GetKey(KeyCode.UpArrow))
            rotationInput.x = 1f;
        if (Input.GetKey(KeyCode.DownArrow))
            rotationInput.x = -1f;
        if (Input.GetKey(KeyCode.LeftArrow))
            rotationInput.y = -1f;
        if (Input.GetKey(KeyCode.RightArrow))
            rotationInput.y = 1f;
    }

    void ApplyThrust()
    {
        if (currentFuel <= 0)
            return; // No fuel, no thrust

        // Calculate thrust direction in world space
        Vector3 thrust = transform.TransformDirection(thrustInput) * mainThrustForce;

        // Apply force
        rb.AddForce(thrust, ForceMode.Force);

        // Consume fuel if thrusting
        if (thrustInput.magnitude > 0.1f)
        {
            currentFuel -= fuelConsumptionRate * Time.fixedDeltaTime;
            currentFuel = Mathf.Max(currentFuel, 0); // Don't go below 0
        }
    }

    void ApplyRotation()
    {
        // Pitch (up/down rotation)
        if (Mathf.Abs(rotationInput.x) > 0.1f)
        {
            float pitch = rotationInput.x * rotationSpeed * Time.fixedDeltaTime;
            rb.AddTorque(transform.right * pitch, ForceMode.Acceleration);
        }

        // Yaw (left/right rotation)
        if (Mathf.Abs(rotationInput.y) > 0.1f)
        {
            float yaw = rotationInput.y * rotationSpeed * Time.fixedDeltaTime;
            rb.AddTorque(transform.up * yaw, ForceMode.Acceleration);
        }
    }

    void LimitVelocity()
    {
        // Cap maximum velocity
        if (rb.velocity.magnitude > maxVelocity)
        {
            rb.velocity = rb.velocity.normalized * maxVelocity;
        }
    }

    void UpdateUI()
    {
        // Update velocity display
        if (velocityLabel != null)
        {
            float speed = rb.velocity.magnitude;
            velocityLabel.text = $"VEL: {speed:F1} M/S";
        }

        // Update fuel display
        if (fuelLabel != null)
        {
            fuelLabel.text = $"FUEL: {currentFuel:F0}%";

            // Change color based on fuel level
            if (currentFuel > 50)
                fuelLabel.color = Color.green;
            else if (currentFuel > 25)
                fuelLabel.color = new Color(1f, 0.65f, 0f); // Orange
            else
                fuelLabel.color = Color.red;
        }
    }

    void UpdateThrusterVisual()
    {
        // Show thruster glow when thrusting forward
        if (thrusterGlow != null)
        {
            bool isThrusting = thrustInput.z > 0.1f;
            thrusterGlow.SetActive(isThrusting && currentFuel > 0);
        }
    }

    // Public methods for external systems
    public float GetSpeed()
    {
        return rb.velocity.magnitude;
    }

    public float GetFuel()
    {
        return currentFuel;
    }

    public void AddFuel(float amount)
    {
        currentFuel = Mathf.Min(currentFuel + amount, 100f);
    }
}
```

3. **Attach Script to PlayerShip**
   ```
   Select PlayerShip in Hierarchy
   Add Component → Scripts → ShipController

   Assign references in Inspector:
   - Rigidbody: Drag PlayerShip's Rigidbody
   - Thruster Glow: Drag ThrusterGlow child object
   - Velocity Label: Drag VelocityLabel UI text
   - Fuel Label: Drag FuelLabel UI text
   ```

---

## Phase 6: Create Simple Debris Field (Day 4-5)

### Debris Prefab

1. **Create Debris Object** (Hierarchy → 3D Object → Cube)
   ```
   Name: DebrisBlock
   Transform:
   - Scale: (2, 1, 3) - Irregular shape
   - Rotation: (15, 30, 10) - Angled

   Material:
   - Create: Assets/Materials/DebrisMaterial
   - Color: Dark gray (50, 50, 50)
   - Metallic: 0.7
   - Smoothness: 0.3

   Add Component: Box Collider
   - Is Trigger: Unchecked (solid collision)
   ```

2. **Make it a Prefab**
   ```
   Drag DebrisBlock to Assets/Prefabs/Debris/
   Delete from scene (we'll spawn procedurally)
   ```

3. **Create Debris Spawner Script** (Assets/Scripts/Debris/DebrisSpawner.cs)

```csharp
using UnityEngine;

public class DebrisSpawner : MonoBehaviour
{
    [Header("Spawn Settings")]
    [SerializeField] private GameObject debrisPrefab;
    [SerializeField] private int debrisCount = 20;
    [SerializeField] private float spawnRadius = 50f;
    [SerializeField] private float minScale = 0.5f;
    [SerializeField] private float maxScale = 3f;

    void Start()
    {
        SpawnDebrisField();
    }

    void SpawnDebrisField()
    {
        for (int i = 0; i < debrisCount; i++)
        {
            // Random position within sphere
            Vector3 randomPos = Random.insideUnitSphere * spawnRadius;

            // Random rotation
            Quaternion randomRot = Random.rotation;

            // Spawn debris
            GameObject debris = Instantiate(debrisPrefab, randomPos, randomRot, transform);

            // Random scale
            float randomScale = Random.Range(minScale, maxScale);
            debris.transform.localScale *= randomScale;

            // Optional: Add slow rotation
            Rigidbody rb = debris.AddComponent<Rigidbody>();
            rb.useGravity = false;
            rb.angularVelocity = Random.insideUnitSphere * 0.5f;
        }
    }
}
```

4. **Create Debris Manager** (Hierarchy → Create Empty)
   ```
   Name: DebrisManager
   Add Component → DebrisSpawner
   Assign:
   - Debris Prefab: Drag DebrisBlock prefab
   - Debris Count: 20
   - Spawn Radius: 50
   ```

---

## Phase 7: Setup Camera (Day 5)

### First-Person Camera

1. **Create Camera** (Already exists as "Main Camera")
   ```
   Position Camera as child of PlayerShip:
   - Parent: Drag Main Camera onto PlayerShip in Hierarchy
   - Local Position: (0, 0.3, 0.5) - Inside cockpit position
   - Local Rotation: (0, 0, 0)

   Camera Settings:
   - Field of View: 70 (wider for cockpit feel)
   - Clipping Planes: Near 0.1, Far 1000
   - Clear Flags: Skybox
   ```

2. **Add Skybox** (for space background)
   ```
   Window → Rendering → Lighting
   Environment tab:
   - Skybox Material: Default-Skybox (or black for space)

   Alternative for pure black space:
   Camera → Clear Flags → Solid Color
   Background: Black (0, 0, 0)
   ```

---

## Phase 8: Collision Detection (Day 5)

### Create CollisionHandler.cs

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class CollisionHandler : MonoBehaviour
{
    [Header("UI References")]
    [SerializeField] private TMPro.TextMeshProUGUI warningText;

    private bool isDead = false;

    void OnCollisionEnter(Collision collision)
    {
        if (isDead)
            return;

        // Check if we hit debris
        if (collision.gameObject.CompareTag("Debris"))
        {
            HandleCrash();
        }
    }

    void HandleCrash()
    {
        isDead = true;

        // Show warning
        if (warningText != null)
        {
            warningText.text = "COLLISION DETECTED - HULL BREACH";
            warningText.color = Color.red;
            warningText.fontSize = 48;
        }

        // Stop ship movement
        Rigidbody rb = GetComponent<Rigidbody>();
        if (rb != null)
        {
            rb.velocity = Vector3.zero;
            rb.angularVelocity = Vector3.zero;
        }

        // Restart scene after delay
        Invoke(nameof(RestartScene), 3f);
    }

    void RestartScene()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().name);
    }
}
```

**Attach to PlayerShip and tag debris:**
```
1. Select PlayerShip → Add Component → CollisionHandler
2. Create UI warning text (center screen, large font)
3. Assign warning text reference
4. Select all debris → Inspector → Tag → Add Tag → "Debris"
5. Tag all debris objects with "Debris" tag
```

---

## Phase 9: Testing & Controls (Day 6)

### Control Scheme Summary

**Flight Controls (WASD + Space/Shift):**
```
W = Forward thrust
S = Reverse thrust
A = Strafe left
D = Strafe right
Space = Thrust up
Shift = Thrust down
```

**Rotation (Arrow Keys):**
```
Up Arrow = Pitch up
Down Arrow = Pitch down
Left Arrow = Yaw left
Right Arrow = Yaw right
```

**Debug Controls (Add to ShipController.cs Update()):**
```csharp
// Add to Update() method for testing
if (Input.GetKeyDown(KeyCode.R))
{
    // Reset ship position
    transform.position = Vector3.zero;
    rb.velocity = Vector3.zero;
    rb.angularVelocity = Vector3.zero;
}

if (Input.GetKeyDown(KeyCode.F))
{
    // Refuel
    currentFuel = 100f;
    Debug.Log("Refueled!");
}
```

### Testing Checklist

**Test Scene Setup:**
- [ ] PlayerShip spawns at (0, 0, 0)
- [ ] Camera follows ship (child of PlayerShip)
- [ ] UI panels visible on all corners
- [ ] Debris field spawned around origin
- [ ] Thruster glow activates when pressing W

**Test Flight Physics:**
- [ ] W key accelerates ship forward
- [ ] Velocity increases gradually (momentum)
- [ ] Ship continues moving when releasing W (space physics)
- [ ] Arrow keys rotate ship
- [ ] Collision with debris triggers crash

**Test UI:**
- [ ] Velocity updates in real-time
- [ ] Fuel decreases when thrusting
- [ ] Fuel color changes (green → orange → red)
- [ ] UI visible at all times

---

## Phase 10: Build for iOS (Day 7)

### iOS Test Build

1. **Switch Platform**
   ```
   File → Build Settings
   Select: iOS
   Click: Switch Platform (wait for reimport)
   ```

2. **Player Settings**
   ```
   Click: Player Settings button

   iOS tab:
   - Bundle Identifier: com.[yourname].harbinger
   - Version: 0.1.0
   - Target iOS Version: 13.0 or higher
   - Architecture: ARM64
   - Camera Usage Description: "Not used" (required by Apple)
   ```

3. **Build Project**
   ```
   Click: Build
   Choose folder: iOS_Build
   Wait for Xcode project generation
   ```

4. **Open in Xcode** (Mac only)
   ```
   Open generated .xcodeproj file
   Connect iPhone via USB
   Select device in Xcode
   Click: Run (▶️ button)
   ```

**Note:** iOS builds require Mac + Xcode. For testing on Windows, use Android build instead.

---

## Phase 11: Next Steps After Prototype

### You Now Have:
✅ Working flight controls (6DOF)
✅ Collision detection
✅ Simple debris field
✅ Placeholder UI
✅ Playable prototype

### Iterate and Improve:

**Week 2:**
- [ ] Add more debris variety (different shapes/sizes)
- [ ] Implement scanning mechanic (raycast from ship)
- [ ] Add detection meter (increases when scanning)
- [ ] Create simple objective ("Scan 5 objects")
- [ ] Add sound effects (engine, collision)

**Week 3:**
- [ ] Create Phase 2 scene (atmospheric flight)
- [ ] Implement simple aerodynamic drag
- [ ] Add weather particles (rain = white dots)
- [ ] Create landing zone marker
- [ ] Test landing precision mechanics

**Week 4:**
- [ ] Replace placeholder UI with pixel art (from earlier docs)
- [ ] Add retro post-processing (scanlines, CRT effect)
- [ ] Implement proper color palette shader
- [ ] Polish animations and transitions

---

## Troubleshooting Common Issues

### Ship Won't Move
- Check Rigidbody "Use Gravity" is UNCHECKED
- Verify ShipController script attached
- Check thrustInput is not zero (add Debug.Log)
- Increase mainThrustForce value

### UI Not Visible
- Check Canvas render mode is "Screen Space - Overlay"
- Verify Canvas Scaler reference resolution
- Check text color is not black on black
- Ensure UI is not behind camera

### Collision Not Working
- Verify debris has "Debris" tag
- Check both ship and debris have colliders
- Rigidbody on ship must NOT be kinematic
- Collision Handler script attached to PlayerShip

### Performance Issues
- Reduce debris count (debrisCount = 10)
- Lower debris rigidbody count (make static)
- Disable shadows on debris materials
- Reduce camera far clipping plane

---

## Quick Start Commands

**Create all folders:**
```
Right-click Project window repeatedly, or use this structure as guide
```

**Import TextMeshPro:**
```
First time creating UI text, Unity will prompt to import
Click "Import TMP Essentials"
```

**Test Play:**
```
Press Play button (Ctrl+P)
Use WASD + Arrow keys
Press R to reset, F to refuel
Avoid debris blocks
```

---

## Development Timeline

### Week 1 (Current):
- ✅ Unity setup
- ✅ Placeholder UI
- ✅ Basic flight controls
- ✅ Debris field
- ✅ Collision detection

### Week 2:
- Scanning mechanics
- Detection system
- Objectives
- Audio

### Week 3:
- Phase 2 prototype
- Atmospheric flight
- Landing mechanics
- Weather system

### Week 4:
- Pixel art integration
- Retro shaders
- Polish and juice
- Playtesting

---

## Resources

**Unity Learn:**
- https://learn.unity.com/project/3d-game-kit-lite
- https://learn.unity.com/tutorial/working-with-rigidbodies

**URP Documentation:**
- https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@latest

**C# Scripting:**
- https://docs.unity3d.com/ScriptReference/

---

**Ready to start? Follow Phase 1 and you'll be flying in an hour!**

*"Prototype first, polish later."*
