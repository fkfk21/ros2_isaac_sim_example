# ros2_isaac_sim_example

## Note

** for Isaac Sim ver.2022.2.0 **
### enable ros2_bridge not ros_bridge

local workstation: ~/.local/share/ov/pkg/isaac_sim-2022.2.0/apps/omni.isaac.sim.base.kit

[dependencies."filter:platform"."linux-x86_64"]
"omni.isaac.ros2_bridge-humble" = {}

### [ROS2 Bridge prep](https://docs.omniverse.nvidia.com/app_isaacsim/app_isaacsim/install_ros.html#enabling-the-ros-ros-2-bridge-extension)

1. Create a file named fastdds.xml under ~/.ros/, paste the following snippet link into the file.
```
<?xml version="1.0" encoding="UTF-8" ?>

<license>Copyright (c) 2022, NVIDIA CORPORATION.  All rights reserved.
NVIDIA CORPORATION and its licensors retain all intellectual property
and proprietary rights in and to this software, related documentation
and any modifications thereto.  Any use, reproduction, disclosure or
distribution of this software and related documentation without an express
license agreement from NVIDIA CORPORATION is strictly prohibited.</license>


<profiles xmlns="http://www.eprosima.com/XMLSchemas/fastRTPS_Profiles" >
    <transport_descriptors>
        <transport_descriptor>
            <transport_id>UdpTransport</transport_id>
            <type>UDPv4</type>
        </transport_descriptor>
    </transport_descriptors>

    <participant profile_name="udp_transport_profile" is_default_profile="true">
        <rtps>
            <userTransports>
                <transport_id>UdpTransport</transport_id>
            </userTransports>
            <useBuiltinTransports>false</useBuiltinTransports>
        </rtps>
    </participant>
</profiles>
```

1. Run unset LD_LIBRARY_PATH in the terminal.

1. Run export FASTRTPS_DEFAULT_PROFILES_FILE=~/.ros/fastdds.xml

1. (Optional) Run export ROS_DOMAIN_ID=(id_number) before launching Isaac Sim. You will have a chance later to decide whether to use this ROS_DOMAIN_ID inside your environment, or explictly use a different id number for any given topic.

1. Launch Isaac Sim.

## [ROS2 Execution](https://docs.omniverse.nvidia.com/app_isaacsim/app_isaacsim/install_ros.html#included-ros-2-packages)
