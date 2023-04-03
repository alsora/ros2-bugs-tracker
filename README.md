# ROS 2 Bugs Tracker

This document tracks currently known critical bugs affecting the ROS 2 core libraries and functionalities.

## Guidelines

We consider a critical bug everything that results in the application to crash or fail.
Common examples are segmentation faults and deadlocks, but we also include other critical bugs that violate the ROS 2 communication assumptions, e.g. data-races that can result in entities never receiving data.

We only list bugs up to the ROS 2 client libraries.
Some bugs may be due to the RMW implementation used by the application; here we only list bugs related to the Tier 1 RMW implementations (as of today Fast-DDS and CycloneDDS).


### Description of the fields

The bugs tracker contains the following fields:

 - `Description`: a short description of the bug (this may be the title of the ticket/PR).
 - `Report`: a link to the Github issue where the bug was reported, if available.
 Some bugs are fixed without first being reported and in this case the PR with the fix should be written in this field.
 - `Fix`: a link to the Github PR that fixes the bug in the most recent distribution.
 Eventual backports should be indicated at this link.
 - `First Affected Distro`: the name of the oldest ROS 2 distribution that is affected by the bug.
 - `Currently Affected Distros`: the name(s) of the ROS 2 distribution(s) where the bug is still present.

Each issue should go in a new line in this markdown file.

### Releasing new distributions

When a new ROS 2 distribution is going to be released, the tracker should be updated.
Assuming that the new distribution is `I`, all the bugs currently affecting `H` and without a "fix" indicated should be tested again.
If the bug is still present in the new distribution, the `Currently Affected Distros` column should be updated to reflect that.

## rclcpp

| Description | Report | Fix | First Affected Distro | Currently Affected Distros |
| --- | --- | --- | --- | --- |
| Deadlock when calling `async_get_result` and receiving a result simultaneously | [rclcpp #2130](https://github.com/ros2/rclcpp/issues/2130) | [rclcpp #2132](https://github.com/ros2/rclcpp/pull/2132) | Foxy | Foxy, Galactic |
| Service list not refreshed | [rclcpp #2138](https://github.com/ros2/rclcpp/issues/2138) | N/A | Humble | Humble |
| `rclcpp_lifecycle::LifecycleNode::get_current_state` is not thread safe | [rclcpp #1746](https://github.com/ros2/rclcpp/issues/1746) | [rclcpp #1756](https://github.com/ros2/rclcpp/issues/1756) | Foxy | Foxy, Galactic, Humble |

## rcl

## fast-dds

| Description | Report | Fix | First Affected Distro | Currently Affected Distros |
| --- | --- | --- | --- | --- |
| SharedFuture from `async_send_request` never becomes valid | [rclcpp #2039](https://github.com/ros2/rclcpp/issues/2039) | [fast-dds #3087](https://github.com/eProsima/Fast-DDS/pull/3087) | Humble | N/A |

## cyclonedds
