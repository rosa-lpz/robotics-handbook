# Gazebo
Gazebo is a physics-based, high fidelity 3D simulator for robotics. Gazebo provides the ability to accurately simulate one or more robots in complex indoor and outdoor environments filled with static and dynamic objects, realistic lighting, and programmable interactions.

Gazebo facilitates robotic design, rapid prototyping, testing, and simulation of real-life scenarios. While Gazebo is platform agnostic and runs on Windows, Mac, and Linux, it is mostly used in conjunction with the Robotics Operating System (ROS) running on Linux systems. You will learn how to use ROS in the upcoming lessons. Simply put, Gazebo is an essential tool for every roboticist.

# Gazebo Features
Gazebo has eight features that you can take advantage of:

* Dynamics Simulation: Model a robot's dynamics with a high-performance physics engine.
* Advanced 3D Graphics: Render your environment with high-fidelity graphics, including lighting, shadows, and textures.
* Sensors: Add sensors to your robot, generate data, and simulate noise.
* Plugins: Write a plugin to interact with your world, robot, or sensor.
* Model Database: Download a robot or environment from Gazebo library or build your own through their engine.
Socket-Based Communication: Interact with Gazebo running on a remote server through socket-based(opens in a new tab) communication.
* Cloud Simulation: Run Gazebo on a server and interact with it through a browser.
* Command Line Tools: Control your simulated environment through the command line tools.


# Gazebo Workspace

We canlaunch Gazebo from the terminal by typing:
```bash
$ gazebo
```
Be advised that occasionally Gazebo gets stuck in a loading loop. If Gazebo does not fully load after about one minute, try closing it by pressing Ctrl+C while the Gazebo terminal is active. Then, try running the command again to restart Gazebo.


# Gazebo components
There are six components involved in running an instance of a Gazebo simulation:

Gazebo Server
Gazebo Client
World Files
Model Files
Environment Variables
Plugins

## 1- Gazebo Server
The first main component involved in running an instance of a Gazebo simulation is the Gazebo Server or also known by gzserver.

gzserver performs most of the heavy-lifting for Gazebo. It is responsible for parsing the description files related to the scene we are trying to simulate, as well as the objects within. It then simulates the complete scene using a physics and sensor engine.

While the server can be launched independently by using the following command in a terminal:
```bash
$ gzserver
```

It does not have any GUI component. Running gzserver in a so-called headless mode can come in handy in certain situations, but we will talk more about that in future lessons.


## 2- Gazebo Client
The second main component involved in running an instance of a Gazebo simulation is the Gazebo Client or also known by gzclient.

gzclient on the other hand provides the very essential Graphical Client that connects to the gzserver and renders the simulation scene along with useful interactive tools. While you can technically run gzclient by itself using the following command:
```bash
$ gzclient
```
it does nothing at all (except consume your compute resources), since it does not have a gzserver to connect to and receive instructions from.

### Combining Gazebo Server and Gazebo Client
It is a common practice to run gzserver first, followed by gzclient, allowing some time to initialize the simulation scene, objects within, and associated parameters before rendering it. To make our lives easier, there is a single intuitive command that necessarily launches both the components sequentially:
```bash
$ gazebo
```
## 3- World Files
A world file in Gazebo contains all the elements in the simulated environment. These elements are your robot model, its environment, lighting, sensors, and other objects. You have the ability to save your simulation to a world file that usually has a .world extension.

Gazebo can also read the content of a world file from your disk to generate the simulation. To launch the simulation from a world file, type:
```bash
$ gazebo <yourworld>.world
```

The world file is formatted using the Simulation Description Format or SDF(opens in a new tab) for short. Here’s the basic format of an SDF world file:

```html
<?xml version="1.0" ?>
<sdf version="1.5">
  <world name="default">
    <physics type="ode">
      ...
    </physics>
    
    <scene>
      ...
    </scene>

    <model name="box">
      ...
    </model>

    <model name="sphere">
      ...
    </model>

    <light name="spotlight">
      ...
    </light>

  </world>
</sdf>

```

## 4- Model Files
For simplification, you must create a separate SDF file of your robot with exactly the same format as your world file. This model file should only represent a single model (ex: a robot) and can be imported by your world file. The reason why you need to keep your model in a separate file is to use it in other projects. To include a model file of a robot or any other model inside your world file, you can add the following code to the world’s SDF file:
```html
<include>
  <uri>model://model_file_name</uri>
</include>
```

## 5- Environment Variables
There are many environment variables that Gazebo uses, primarily to locate files (world, model, …) and set up communications between gzserver and gzclient. While working on a robotic project, you’ll leave these variables as default. Here’s an example of a variable that Gazebo uses:

```bash
GAZEBO_MODEL_PATH: List of directories where Gazebo looks to populate a model file.
```

## 6- Plugins
To interact with a world, model, or sensor in Gazebo, you can write plugins. These plugins can be either loaded from the command line or added to your SDF world file. You’ll learn about World Plugins later in the lesson.


# References
* [Udacity - Robotics Software Engineer Nanodegree](https://github.com/rosa-lpz/udacity_robotics-software-engineer-nanodegree)