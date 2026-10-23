# Ex.No: 3  Basic movements in Unity 
### DATE:   23.10.2026                                                                         
### REGISTER NUMBER : 212225240079
### AIM: 
 To learn the basic movements translation,scaling and rotation of game objects through code.
### Procedure:
1. Setup the Scene
2. Open Unity and create a 3D Scene.
3. Add three objects:Cube → Rename to Object1 (for movement),Sphere → Rename to Object2 (for rotation).Capsule → Rename to Object3 (for scaling).
4. Add the Script,Create a C# Script → Name it TransformOperations.cs.
5. Write the code for translation,scaling and rotation,save and close the script
6. Save the script
7. Select any empty GameObject (or create one: GameObject → Create Empty).
8. Attach the TransformOperations script to it.
9. In the Inspector, assign Object1 → Drag the Cube,Object2 → Drag the Sphere.Object3 → Drag the Capsule.
10. Run the Scene Press Play ▶️ in Unity
11. Stop the program.
### Program 
```
using UnityEngine;
public class TransformOperations : MonoBehaviour
{
    public Transform object1; // Object for translation
    public Transform object2; // Object for rotation
    public Transform object3; // Object for scaling

    public float moveSpeed = 2f;  // Speed of translation
    public float rotateSpeed = 50f; // Speed of rotation
    public float scaleSpeed = 0.5f; // Speed of scaling

    void Update()
    {
        // Translate (Move) object1 along the X-axis- Time.deltaTime to make movement smooth across all frame rates
        if (object1 != null)
        {
           // object1.position += Vector3.right * moveSpeed;
               object1.Translate(0.02f,0,0);

        }

        // Rotate object2 around the Y-axis
        if (object2 != null)
        {
            //object2.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
            //object2.Rotate(0,0.02f.0);
        }

        // Scale object3 up and down
        if (object3 != null)
        {
           // float scaleChange = Mathf.PingPong(Time.time * scaleSpeed, 1f) + 0.5f; // generates a value that moves back and forth between 0 and length
           // object3.localScale = new Vector3(scaleChange, scaleChange, scaleChange);
            object3.localScale+=new Vector3(0.02f.0.02f,0);

        }
    }
}
```
### Output:

<img width="1917" height="1075" alt="Screenshot 2026-10-22 223951" src="https://github.com/user-attachments/assets/12a06914-ed7d-4fba-a3b6-b7cde6d9bc93" />


<img width="1917" height="1078" alt="Screenshot 2026-10-22 224006" src="https://github.com/user-attachments/assets/c8aa2899-33eb-4530-a5f5-12e6abf9246e" />


<img width="1627" height="1008" alt="Screenshot 2026-10-22 224216" src="https://github.com/user-attachments/assets/d13757fb-06af-4930-9368-9b6fa714f0a7" />



### Result:
Thus the basic movement is learned through scripting


