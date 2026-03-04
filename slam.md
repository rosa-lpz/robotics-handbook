Simultaneous Localization and Mapping (SLAM) is the "chicken-and-egg" problem of robotics: a robot needs a map to know where it is, but it needs to know where it is to build a map. In 2026, the industry has largely converged on a few high-performance, open-source frameworks integrated with the Robot Operating System (ROS 2).

The most used SLAM algorithms are generally categorized by the primary sensor they use: LiDAR, Vision (Cameras), or Multi-sensor Fusion.


1. LiDAR-Based SLAM (Laser-Based)
LiDAR SLAM remains the gold standard for industrial Autonomous Mobile Robots (AMRs) and self-driving cars due to its high precision and long-range sensing.

Google Cartographer: Currently the most widely used graph-based SLAM system for 2D and 3D mapping. It provides real-time loop closure, which corrects the "drift" that accumulates over time as the robot moves. It is highly optimized for low-compute platforms and is a staple in ROS 2 navigation stacks (Macario Barros et al., 2022).

Gmapping: A classic algorithm based on Rao-Blackwellized Particle Filters. While older and primarily used for 2D indoor environments, it is still frequently used for educational purposes and simple warehouse robots because of its reliability and low setup complexity.

LOAM (LiDAR Odometry and Mapping) & Derivatives: For high-speed 3D mapping, LOAM and its successors like LeGO-LOAM or LIO-SAM (which integrates IMU data) are industry favorites. They achieve low-drift odometry by separating the problem into high-frequency motion estimation and low-frequency mapping (Wu et al., 2023).
