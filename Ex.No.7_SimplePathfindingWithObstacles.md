# Ex.No: 7  Implementation of Simple Pathfinding with Obstacles
### DATE: 01.11.1026                                                                    
### REGISTER NUMBER : 212225240079
### AIM: 
To write a program to pathfinding using AI navigation 
### Algorithm:
```
1. Create a New Unity Project by Open the  Unity Hub and create a new 3D Project,Name the project (e.g., Pathfinding).
2. Set Up the Scene by Create the Ground (Plane or Terrain)
  Go to: GameObject → 3D Object → Plane and Rename: "Ground"  Scale it: (10, 1, 10) (or adjust as needed)
3. Add Obstacles (Cubes or Walls)
  Go to: GameObject → 3D Object → Cube  Scale it: (3, 3, 1) (for a wall-like structure)
  Position it: Place it anywhere to block AI movement Rename it: "Obstacle"  Duplicate: Ctrl + D to create multiple obstacles ,tag the obstacke with same name.
4.Bake the NavMesh
Go to: Window → AI → Navigation , Select Ground: Click on your Ground object ,
In Navigation Window: Check ✅ "Navigation Static"  or Add component Navigation surface and Bake
5.Create the AI Character and Attach navMesh Agent
Go to: GameObject → 3D Object → Capsule ,  Rename: "AICharacter" , Scale: (1, 2, 1)
Go to: Inspector → Add Component → NavMeshAgent Adjust Settings: Speed: 3.5 Stopping Distance: 1  Obstacle Avoidance: High
6.Create the Script "AIPathFinder" (Go to: Assets → Right Click → Create → C# Script and  Rename it: "AIPathfinder"
7.Attach the Script"AIPathFinder" code by Drag & Drop the AIPathfinder.cs onto the AICharacter 
8.Assign the Target:Create a Target: GameObject → 3D Object → Sphere, Rename it: "Target",
 In AICharacter Inspector → AIPathfinder → Drag the Target Sphere into the "target" field.
9.Add NavMeshObstacle
Select an Obstacle (Cube)
Go to: Inspector → Add Component → NavMeshObstacle and Check: ✅ "Carve"
10.Move the Obstacle with Code ( attach it with Obstacle) 
11. Run the program
```  
### Program:
```

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;

public class AIPathfinder : MonoBehaviour
{
    public Transform target;
    private NavMeshAgent agent;

    void Start()
    {
        agent = GetComponent<NavMeshAgent>();
    }

    void Update()
    {
        agent.SetDestination(target.position);
    }
}

```
```

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Moving : MonoBehaviour
{
    public float moveDistance = 3f;
    public float moveSpeed = 2f;
    private Vector3 startPos;

    void Start()
    {
        startPos = transform.position;
    }

    void Update()
    {
        float movement = Mathf.PingPong(Time.time * moveSpeed, moveDistance) - moveDistance / 2;
        transform.position = startPos + new Vector3(movement, 0, 0);
    }
}

```
For smooth movement(optional)  -> use  
float movement = Mathf.PingPong(Time.time * moveSpeed, moveDistance) - moveDistance / 2;
transform.position = startPos + new Vector3(movement, 0, 0);
### Output:

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/bfd61486-a324-4714-b179-9404ecff4e87" />


<img width="760" height="1078" alt="image" src="https://github.com/user-attachments/assets/6854dd8a-bd09-4955-9345-dc81280aea32" />

<img width="735" height="1035" alt="image" src="https://github.com/user-attachments/assets/61d7846a-5451-4989-b325-9a733ad867fa" />



### Result:
Thus the simple path finding  behavior was implemented using AI navigation successfully.
