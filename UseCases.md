# ROS-Industrial Consortium Roadmapping

# Use Case Document
*note items in _italics_ are suggested specifications for review.

## Purpose
This document is an interim result of a "customer" requirements elicitation process.  It documents end-user needs and application requirements at a high-level for further analysis and breakdown into technical specifications and gap analysis.

## Scope
The scope has been limited to potential ROS-Industrial end-user needs and does not directly address developer, integrator or other stakeholders needs.  It is prioritized based on feedback from current ROS-Industrial Consortium members, but may be revised as additional members join the consortium and additional user needs are identified.

## Use Cases

### 1. CMM-Accelerated Path Planning

__Stakeholder:__ Any user with need to generate accurate path programming from an existing workpiece

__Scope:__ Path based processes such as dispensing, painting, sanding, machining, routing

__Description:__ The operator uses a device such as a portable CMM or motion tracking wand to outline a Cartesian path on a part or tool.  Generally, 6 degree of freedom (DOF) pose information is require to be extracted from the teaching device.  The system then extracts this data and automatically generates robot programming that meets the process constraints and is guaranteed to be executable and collision free.  The proposed path plan is shown in simulation for the operator to approve and then executed.

__Success Criteria:__

* Rapid programming: < 20 minutes 
* Collision free paths: < 0 collisions
* High success rate planning: > _95% successful plans generated_
* Follows existing process specifications (speeds, normalcy etc.)
  
__Technology Areas:__

* CMM Driver to extract high resolution pose data
* Cartesian path filtering
* Constraint-obeying path planning (inverse kinematics)
* Collision checking integrated into IK solution
* Visual (kinematic) simulation
* Operator friendly GUI or wizard interface

![MindMap](pics/CMMAccelerated.png)
	
### 2. Mobile Material Handling

__Stakeholder:__ Any manufacturer or warehouser with significant and repetitive material handling needs between machines or operations

__Scope:__ Material Handling

__Description:__ A manufacturer has material transport needs over distances greater than a few meters.  Examples include machine tending, work-in-progress (WIP) transport, warehousing, order fulfillment etc.  The robot manipulator is on a mobile base and is able to navigate between predefined stations in a dynamic environment.  Other robots, people, or equipment may be in the nominal path, requiring replanning or, minimally, waiting for a clear path.  Once at a destination, the robot is capable of roughly localizing with the machine, shelf, bin etc.  A perception system is capable of recognizing the object(s) of interest in an unstructured presentation such as a bin, shelf, or machine.  Automated path planning and grasp planning permits the robot to pick the object and transport it to the drop-off location (or store onboard for multiple items).  The robot should be capable of reacting automatically to machine or inventory states.

__Success Criteria:__

* Highly reliable: _< 1 human intervention per hour_
* Cost effective: _capital costs < $100k per system_
* Efficient: _< 2X time required for manual process_
* Flexible: able to handle a variety of parts with minimal programming and configuration
  
__Technology Areas:__

* Mobile localization (3DOF: X-Y-Yaw)
* Mobile planning in a known map with obstacles
* Machine/shelf/structure localization (6DOF)
* Cluttered scene 3D mapping
* Object recognition/pose estimation in clutter
* Manipulator planning in cluttered environment
* Grasp planning with clutter/uncertainty
* Adaptable grippers
* Omni directional bases
* Low cost, high dexterity manipulators
* Human safe designs, considering ISO 10218 | RIA R15.06

![MindMap](pics/MobileMaterialHandling.png)

### 3. Heavy Helper

__Stakeholder:__ Manufacturers with large/heavy objects to be transported or fixtured

__Scope:__ Material Handling

__Description:__ A manufacturer has material transport needs or part fixturing needs that are too large for safe manual operation, i.e. > 50 pounds or awkward to handle.  The operator instead uses a (potentially mobile) robotic manipulator under guided operation to pick and position the part.  The part may be immediately dropped off or positioned for further operation such as welding, painting, or inspection.  The robot is flexible enough to pick a range of parts of similar class.  The user interface may be a direct guided operation or perhaps via a non-contact method such as a gesture command. Due to the fact that large/heavy objects may introduce significant dynamics into the system, force feedback could be beneficial when performing remote guided operation.

__Success Criteria:__

* Flexible: able to handle a variety of parts with minimal programming and configuration
* Easy to command: only non-programming interfaces required
* Cost efficient: minimal capital investment beyond robot cost
* Minimal setup: no cages or other safety equipment, minimal or no calibration
  
__Technology Areas:__

* Gesture or command recognition (optional)
* Remote guidance interface incorporating force feedback
* Guidance sensor (force etc.)
* Gravity compensation
* Adaptable grippers
* Omni directional bases (optional)
* Human safe designs, considering ISO 10218 | RIA R15.06

![MindMap](pics/HeavyHelper.png)

### 4. Scan 'n' Weld

__Stakeholder:__ Large Weldment Manufacturers

__Scope:__ Welding

__Description:__ Large article welding often requires multiple passes to adequately fill a weld joint and often the large parts have significant geometric distortions either from fabrication tolerances or from thermal deformation.  Current practice for seam tracking can only accomodate small dimensional variations and generally can not adapt to the as-welded condition.  Future systems will sense the condition of the base and weld materials, and they will automatically adjust for both minor deviations such as seam/weld tracking, but also large deviations that might require extra weld passes.  A fully adaptive system could fill an unknown gap or joint without prescribed path plans, only rough joint geometry and the required end conditions.

__Success Criteria:__

* Flexible: No significant programming for new welds other than specifying joint to weld and the desired end conditions
* High Quality: Joint quality equivalent or better than traditionally programmed welds
* Minimal setup: Minimal or no part registration
  
__Technology Areas:__

* Weld process controller
* Automated part registration
* Weld joint sensing
* Constraint-obeying path planning (inverse kinematics)
* Collision checking integrated into IK solution
* Cluttered environment path planning

![MindMap](pics/ScanNWeld.png)

### 5. Human Collaborative Assembly

__Stakeholder:__ High Volume Assembled Goods Manufacturers

__Scope:__ Assembly

__Description:__ Traditional high volume assembly such as consumer electronics and automotive final assembly are mostly manual operations due to the complex environments, many varied tasks, and high-dexterity operations.  Future robotic assembly capabilities will enable collaborative or shared-space operations where humans would perform high value tasks such as quality control and robots would do repetitive and ergonomically difficult tasks.  The robots would be required to safely and productively work in the same space as the human workers.  The robots would perform multiple assembly operations using adaptable tooling.  Perception capabilities would eliminate issues with work piece registration and cell calibration.  Initial systems would manage light-weight, slow-speed tasks, while future systems would safely handle larger payloads at higher speeds.  The robots will require flexible and intuitive programming so that they can be easily moved and retasked.

__Success Criteria:__

* Flexible: Robots are able to perform a variety of force-guided assembly tasks with a single hardware configuration
* Minimal setup: Minimal or no part registration
* Simple Tooling Design: _Tooling design and fabricated in hours for < $1000_
* Simple Programming: Line operator able to retask
* Cost Effective: Return on investment < 18 months
  
__Technology Areas:__

* Human safe designs, considering ISO 10218 | RIA R15.06 and future standards
* Automated part registation
* Collision checking
* Cluttered environment path planning
* Human pose tracking
* High fidelity force/impedance control

![MindMap](pics/Collaborative.png)

### 6. Machine Tool Blending

__Stakeholder:__ Machined Part Manufacturers

__Scope:__ Material Removal

__Description:__ Machined parts leave small tooling marks that are often undesirable for to aesthetic or surface quality reasons.  Current practice is to manually blend the tool marks with sanding, grinding, or other processes.  A robotic system is needed that has the flexibility to deal with a wide variety of parts and surface conditions.  Due to the presence of contact with a surface whose characteristics are not well known, force control could be considered to complement position control. Fixturing must be simple and flexible between parts.  Robot programming should be intuitive such that the operator only selects the regions to be blended.  Ideally,  the programming interface should be such that machine tool experts can program the robot without requiring additional knowledge about robotics. CAM packages such as MasterCAM or Catia's advanced machining module could be used as a starting point and adapted for robot programming. The system will have the ability to automatically inspect the result and modulate the process based on the surface state feedback.

__Success Criteria:__

* Flexible: Tooling and robot programming need to be able to handle a wide variety of parts
* Minimal setup: Minimal or no part registration
* Simple Programming: Line operator should be able to "program" a new part
* Coverage: Needs to be able to process _80% of a typical CNC output_
  
__Technology Areas:__

* Automated part registation
* Collision checking
* Cluttered environment path planning
* Constraint obeying path planning
* Robot program generation from CAM output file (APTsource, G-code...)
* Machined surfaces sensing/characterization
* Actual to ideal(CAD) part comparison to extract process parameters
* Force control 
* GUI interface for selecting surfaces
* Point cloud processing to extract surfaces

### 7. Speed Optimized Path Planner

__Stakeholder:__ Manufacturer/Product Developers with High Speed Material Handling Needs

__Scope:__ Material Handling

__Description:__ A generalized path planner is envisioned for speed-optimized path planning that obeys Cartesian constraints.  A robotic system is needed that provides optimal or near optimal path plans for high DOF systems (6/7 axis articulated arms) that perform material handling tasks.  For example, a fluid container handing robot may need to obey Cartesian constraints to keep the container near vertical while moving in free-space.  More sophisticated constraint models are envisioned, for example that would take into account the dynamics of the fluid in the container to achieve greater accelerations/speeds.  The planning needs to be real-time to account for dynamic replanning. In addition to kinematic considerations, speed optimized trajectories need to take into account robot dynamics (masses, inertias, joint elasticity...) in order to ensure proper tracking. The planner should be able to rely on an accurate dynamic model of the robot and payload.  

__Success Criteria:__

* High Performance: plans that are near the theoretical speed (acceleration) of the machine while obeying the constraints
* Fast Planning: _< 1 second plan time_
* Flexible: Able to accomodate multiple serial kinematic configurations including redundant ones 
  
__Technology Areas:__

* Collision checking
* Cluttered environment path planning
* Optimal path planning with constraints
* Redundancy resolution
* Dynamic modeling and simulation

### 8. Robotic 3D Printing

__Stakeholder:__ Manufacturers and Product Designers who Need Large Scale "Printed" Structures

__Scope:__ Additive Manufacturing

__Description:__ There exist many applications of high-accuracy and small scale additive manufacturing processes such as 3D Printing (FDM) and Selective Laser Sintering (SLS).  However, there are relatively few examples of large (robot scale) processes which may have lower accuracy requirements (mm instead of microns).  Envisioned is a capability to 3D "print" materials using robotic technologies that scale in size to civil engineering products.  CNC machining path planning is needed for high-accuracy paths (square corners etc.) and potentially very large applications may use mobile navigation technologies.  Process feedback may be used to adjust the process and path plan in real-time based on the as-built structure.

__Success Criteria:__

* Accuracy: Planning and process control that achieves part accuracy on the order of the robot kinematic accuracy
    * May require robot localization techniques using intrinsic or extrinsic sensing
* Flexibility: Planning must be executed from CAD in an offline environment (no online teaching)
* Process Planning: Certain additive processes may have unique demands in planning and feedback control that need to be accommodated
  
__Technology Areas:__

* CAM/CNC (CAD to path) Planning
* Robot Localization
* Real-time path correction based on sensor feedback

### 9. Robot Cell Layout and Optimization

__Stakeholder:__ Any Robot User with Needs to Optimize Reach and Speed of a Robot Manipulator

__Scope:__ Any Robot User

__Description:__ One fundamental challenge with robotic manipulation is the placement of the robot with respect to the workpiece.  This is a non-trivial problem because of high dimensionally (6DOF position and orientation), and complexity of motion profiles.  Traditional methods use off-line CAD tools to perform reach studies that are typically limited to a few test cases.  One can also look at manipulability through a robot's workspace, but this is independent of the true motion profiles.  There is a need for a tool to optimize (based on cycle time, floor space, reach, flexibility etc.) the layout of a robot workspace in a robust and automated way.

__Success Criteria:__

* Flexible: Arbitrary kinematic models and workspaces need to be accommodated
* Complete: Representative path plans need to be provided by another tool (off line programmer) or automatically generated
* Fast: New simulations should be created and executed in less than a day for typical workcells and motion profiles
  
__Technology Areas:__

* Automated (approximate) path planning from CAD or heuristic
* Optimization/simulation tool
* Workspace visualization

### 10. Robot CNC Machining for High Accuracy and Large Scale

__Stakeholder:__ Aerospace, Heavy Industry, Civil and other Large Product Producers 

__Scope:__ Machining

__Description:__ Traditional large scale machining is accomplished by dedicated 3 or 5 axis machining centers.  For very large parts, common in fields such as aerospace, bridge or gantry style machining centers are used.  These tools are very expensive and require significant facility infrastructure including floorspace and foundations.  Envisioned is a mobile robot capability that would address medium-accuracy and large-scale machining of low to medium strength materials such as sheet metal, aluminum, and carbon fiber.  The robot would need to be mobile to achieve large scale, flexibility, and low cost.  An external metrology system would be required to generate high accuracy tool paths.

__Success Criteria:__

* Flexible: Arbitrary workpiece forms and sizes should be easily accommodated
* Accuracy: Machined part accuracy of 0.25mm/meter
* Large Scale: Demonstrated work volume of 2 x 2 x 1.5 meter
  
__Technology Areas:__

* CNC Path Planning
* Workspace visualization
* High accuracy external localization
* Robot mobility platform
* Automated part registration
