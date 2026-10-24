# Ex.No: 5  Implementation of Steering behaviour-Pursue and Evade in Unity
### DATE: 24.10.2026                                                                           
### REGISTER NUMBER : 212225240079
### AIM: 
To write a program to simulate the process of Pursue and Evade behavior in Unity using NavigationMeshAgent. 
### Algorithm:

1. Create a New Unity Project by Open the  Unity Hub and create a new 3D Project.
2. Name the project "SteeringBehaviors" and select a location. Click Create.
3.Open Unity Scene (default is SampleScene).
  In the Hierarchy, create a Plane:
  Right-click → 3D Object → Plane (this will be the ground).
  Set its Scale to (10, 1, 10) for a larger surface.
  Create three Capsule for the Player, Pursuer, and Evader:
  Rename them to "Player", "Pursuer", and "Evader".
  Set their Y Position to 0.5 (so they sit on the ground).
  Change their Material for better distinction (optional).
3. Check AI navigation in window.
 Window → AI → Navigation (opens the Navigation tab).  If it is not available then add package by name "com.unity.ai.navigation"
4. Select the Plane, go to the Navigation tab, and mark it as Navigation Static.
   Go to the Bake tab and click Bake.
   or
   Add navMeshSurface to plane and bake 
4. Add NavMeshAgent Component 
    Select Pursuer, and Evader.
    Click Add Component → Search for NavMeshAgent and add it.
    Adjust NavMeshAgent Settings:
    Player: Set Speed = 5.
    Pursuer: Set Speed = 4.
    Evader: Set Speed = 6.
5. Write a script for  Player_movement behavior and save it

**Player script**
```

using UnityEngine;

public class Player_movement : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        float x = Input.GetAxis("Horizontal") * speed * Time.deltaTime;
        float z = Input.GetAxis("Vertical") * speed * Time.deltaTime;

        transform.Translate(x, 0, z);
    }
}

```

**Evader script**
```
using UnityEngine;
using UnityEngine.AI;

public class Evader : MonoBehaviour
{
    public NavMeshAgent agent;
    public Transform target;
    public float evadespeed = 5f;

    void Start()
    {
        agent = GetComponent<NavMeshAgent>();
    }

    void Update()
    {
        Vector3 dir = transform.position - target.position;
        Vector3 destination = transform.position
                            + dir.normalized * evadespeed;

        agent.SetDestination(destination);
    }
}
```

**Pursuer script**
```
using UnityEngine;
using UnityEngine.AI;

public class Pursuer : MonoBehaviour
{
    public NavMeshAgent agent;
    public Transform target;
    public float speed = 4f;

    void Start()
    {
        agent = GetComponent<NavMeshAgent>();
    }

    void Update()
    {
        Vector3 dir = target.position - transform.position;
        Vector3 destination = target.position;

        agent.speed = speed;
        agent.SetDestination(destination);
    }
}
```
7. Attach the Script to each player,pursuer and Evader.
   Drag & Drop the Target from the Hierarchy into the "Target" field in the script component ( For pursuer and Evader).
12. Run the game 
13. Stop the program
    
```
### Output:

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/b16b4664-c39a-4467-8683-a49703d7b01e" />


<img width="905" height="1063" alt="image" src="https://github.com/user-attachments/assets/6c959273-3389-4fd0-990a-78deb831b4a6" />


<img width="907" height="908" alt="image" src="https://github.com/user-attachments/assets/f6bc7a69-5238-4436-b586-ecf11dbb8d75" />




### Result:
Thus the simple pursue and evade behavior was implemented successfully.
