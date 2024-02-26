# CollisionTest
scenario test for collision

We are Creating a project in unreal engine 5.3.2 and  we were trying to detect hit on the Vehicle door.
But found weird behaviour in the engine collision events.

Link to Doc with images :  https://docs.google.com/document/d/1PUG-XD0vYrI8sd7jHEd_WYB7Npznx0WdFEnL9MAf1OI/edit?usp=sharing

Link to project in git : https://github.com/KanzariyaJayraj300mind/CollisionTest

Overview : 
- We have an Vehicle actor which has a Body(staticmesh) as main component which has Simulate physics true and generate hit events true.
- We have a StaticMeshComponent’s Child DoorComponent which has 
Simulate physics false and generate hit event true.

- We are testing the hit event received from Vehicle’s body component and Door Component
On hit event(of body, leftdoor,rightdoor) we are printing string like below

[Component’s name on which event is triggered] hit by [ Other component from hit result ]

 Here we have colored objects as follow to better identify the objects
VehicleA body Orange
VehicleB body Blue
Right Doors DarkBlue
Left Doors green


Here are the Scenarios we are testing and expected and current result.
We have put the pairs of ActorA and ActorB  which are instance of same class.

Case 1:

Expected Output: 
TestActor5.Body Cube hit by: TestActor6.Body Cube (A’s Body  => B’s Body)
TestActor6.Body Cube hit by: TestActor5.Body Cube (B’s Body  => A’s Body)

Current Output:
TestActor5.Body Cube hit by: TestActor6.Body Cube (A’s Body  => B’s Body)
TestActor6.Body Cube hit by: TestActor5.Body Cube (B’s Body  => A’s Body)


Case 2:

Expected Output: 
TestActor2.Door_L Cube hit by: TestActor1.Door_L Cube (B’s LeftDoor => A’s LeftDoor)
TestActor1.Door_L Cube hit by: TestActor2.Door_L Cube (A’s LeftDoor => B’s LeftDoor)

Current Output:
TestActor2.Door_L Cube hit by: TestActor1.Door_L Cube (B’s LeftDoor=> A’s LeftDoor)
TestActor1.Door_L Cube hit by: TestActor2.Door_L Cube (A’s LeftDoor=> B’s LeftDoor)


Case 3:

Expected Output: 
TestActor3.Door_L Cube hit by: TestActor4.Door_R Cube (A’s LeftDoor => B’s RightDoor)
TestActor4.Door_R Cube hit by: TestActor3.Door_L Cube (B’s RightDoor => A’s LeftDoor)

Current Output:
TestActor3.Door_R Cube hit by: TestActor4.Door_L Cube (A’s RightDoor => B’s LeftDoor)
TestActor4.Door_R Cube hit by: TestActor3.Door_L Cube (B’s RightDoor => A’s LeftDoor)
























Case 4:



Expected Output: 
TestActor7.Door_L Cube hit by: TestActor8.Body Cube (A’s LeftDoor => B’s Body)
TestActor8.Body Cube hit by: TestActor7.Door_L Cube (B’s Body => A’s LeftDoor)

Current Output:
TestActor7.Body Cube hit by: TestActor8.Door_L Cube (A’s Body => B’s LeftDoor)
TestActor8.Body Cube hit by: TestActor7.Door_L Cube (B’s Body => A’s LeftDoor)

