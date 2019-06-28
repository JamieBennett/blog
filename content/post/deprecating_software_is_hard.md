+++
Description = "Deprecating software is hard; why the move to ROS 2 is causing heated debate"
Tags = ["Development", "Software", "ROS", "Robotics", "Ubuntu"]
Categories = ["Development", "Robotics"]
menu = "main"
title = "Deprecating software is hard; why the move to ROS 2 is causing heated debate"
date = "2018-10-17T10:37:08+01:00"
image = "/media/robot.jpg"

+++

<div align="center"><img src="/media/robot.jpg" alt="photo credit: https://flic.kr/p/4KEF4F"><small></div>

## Software never stays the same

Inevitably, all software is destined to die. Whether that is through becoming end of life (EOL), obsolete, or unused, or through the code being rewritten and replaced, software is not static and nor should it be. Bug fixes, security updates, and new functionality ensure that code churn, or the number of lines being modified, keeps developers busy and projects healthy. But, what happens when software completely changes? When one version of software is replaced by another, incompatible version especially when people and businesses rely on that software? Well of course, debates get heated and people get upset. There are always reasons for seismic change in a project and usually everyone agrees that there are advantages, but making that change and bridging the gap can be a painful process. This exact scenario is playing out today with ROS, the Robot Operating System.

## What is ROS, the Robot Operating System?

According to the <a href="http://www.ros.org">ROS Website</a>:
 
 >*"The Robot Operating System (ROS) is a flexible framework for writing robot software. It is a collection of tools, libraries, and conventions that aim to simplify the task of creating complex and robust robot behaviour across a wide variety of robotic platforms."*
 
With roots back to 2007, ROS was originally a coalesce of several robotic ideas and projects from Stanford University which was spun out into a separate entity and taken over by the research lab, Willow Garage. With a mission to provide an open source alternative to proprietary robotics software as well as foster innovation and creativity, Willow Garage worked on the project until it's first major release in 2010. But despite the name, ROS is not an Operating System (OS). Instead it is a framework that is built on top of an OS, and in most cases that is Ubuntu. Doing this allows ROS to provide support by leveraging the existing nature of Ubuntu's Long Term Support (LTS) releases which promise 5 years of updates and fixes for the OS.
 
ROS has rapidly grown since to be widely used by both business and research institutions but it's growth was not without problems. It is fair to say that the project has grown organically over the last 10 years and despite the best efforts of Willow Garage, and later the OSRF (Open Source Robotics Foundation) and now Open Robotics, some of the original design decisions that applied back then have led to challenges in certain robotic domains. Security, real-time capabilities, support for QoS (Quality of Service), and a more layered architecture are quoted as being blockers for some domains such as self-driving cars and aerospace, but ROS is more than capable for several other verticals. We have seen communities form around the <a href="https://rosindustrial.org/">industrial</a> space and <a href="http://rosagriculture.org/">agriculture</a> to name but two and a range of products from <a href="http://www.pal-robotics.com/en/home/">humanoid robots</a> to <a href="https://www.dji.com/">drones</a> but currently, the project is undergoing a major upheaval in the form of ROS 2.
 
## A New Beginning

ROS 2 is a ground-up rewrite of the whole software stack to address some of the shortcoming mentioned earlier. All new APIs and tools are being designed which in effect means ROS 2 is not backwards compatible with ROS 1. This major change has lead to <a href="https://discourse.ros.org/t/discussion-on-ros-to-ros2-transition-plan/6155">heated debate</a> in the community sparked, most recently by <a href="https://discourse.ros.org/t/ros-2-tsc-meeting-minutes-september-6th-2018/6157">comments</a> made at the <a href="https://discourse.ros.org/t/introducing-the-ros-2-technical-steering-committee/6132">ROS2 Technical Steering Committee</a> level. September 6th saw the committee discuss the end of life (EoL) of ROS 1 which has prompted deeper discussion on what it means to transition a community from one software stack to another.
 
>*"The longer people can use ROS1 the less motivated they will be to move to ROS2. There will be pushback, but it will at least get the conversation going."* (<a href="https://discourse.ros.org/t/ros-2-tsc-meeting-minutes-september-6th-2018/6157">source</a>).
 
ROS is experiencing a rich growth spurt at the moment as the topic of robotics in general is becoming more popular. All of the <a href="http://wiki.ros.org/Metrics">metrics</a> collected by the ROS project, such as website hits and package downloads are showing sizable increases with users of the public ROS discourse forum, the place where the community talk about ROS, showing a 250% increase since last year. This growth is in tandem with companies and start-up's joining the robotics space but one dilemma they face is, do they adopt ROS 1 knowing full well that it will become end of life shortly, move to ROS 2 knowing that it is missing key features, or avoid ROS altogether? Today, there is no clear answer.

## The move to ROS 2 is inevitable

Maintaining ROS 1 and making new releases is the responsibility of <a href="https://www.openrobotics.org/">Open Robotics</a> but in conjunction with this effort, they are also the ones responsible for creating ROS 2. With limited resources and an estimate of <a href="https://discourse.ros.org/t/discussion-on-ros-to-ros2-transition-plan/6155/24">8-9 person months of effort</a> needed for every release, the investment needed for ROS 1 is not insignificant. Add to this the need for post-release bug fixing, security fixes, and updates, and the fact that some releases are 'supported' for 5 years, a decision to divert resources to ROS 2 means that some ROS 1 users are getting nervous. Companies that have built their business on the use of ROS 1 are facing a future that includes either migrating their products to ROS 2 or sticking to an unsupported, unmaintained software stack. Worst case is that they move away from ROS completely by either picking a commercial solution or creating their own from scratch, all of the options have their pitfalls.

## What is the answer?

Unfortunately there is no clear-cut *'right'* way. From Open Robotics point of view, ROS 2 is a <a href="https://design.ros2.org/articles/why_ros2.html">better, more appropriate framework for modern robotics</a> and they have taken the decision to forge ahead with the hope of making it feature complete over the next couple of years. In tandem, they are rightly exploring if and when they should depricate ROS 1 and direct those resources to ROS 2 instead. There has been talk of technical solutions that could ease the transition from ROS 1 to ROS 2, with shims and translation layers able to merge old with new but of course that is extra development effort that could be spent elsewhere. In the end, as with most open source projects, this is not just a problem that Open Robotics has to solve alone, it should be one that the community gets behind. It is great to see new investment in the project by <a href="https://blogs.windows.com/windowsexperience/2018/09/28/bringing-the-power-of-windows-10-to-the-robot-operating-system/">large institutions</a> who bring with them both expertise and funding and this problem could instead be an opportunity for others to step up.