# ros2-timescaledb-bridge

A ROS 2 node that writes robot telemetry directly to TimescaleDB. Built in public, documented as it gets made.

**Status: early exploration. No working code yet. Come watch it get built.**

---

## What this is

rosbag2 is good at recording and replay. It's not built for fleet-level analytics — for answering "what did sensor X do across 200 test runs" without loading every bag file into memory. There's [an open feature request](https://github.com/ros2/rosbag2/issues/1739) in the rosbag2 repo naming TimescaleDB and InfluxDB as candidate options for exactly this problem. It's been open since July 2024. Zero comments.

This repo is an attempt to fill that gap, or at least figure out what filling it actually looks like.

## What's being built

A ROS 2 node that subscribes to topics and writes to TimescaleDB in real time. Starting with `/joint_states` and `/cmd_vel` — the two most universal topics in any ROS 2 setup. Eventually: schema decisions, compression, continuous aggregates for fleet-level queries, a Grafana dashboard over live telemetry.

The person building this (me) is a database person who has never written a ROS node before. That's deliberate. The interesting question isn't "how do you use TimescaleDB" — it's "what does a database person actually hit when they try to wire this up."

## Follow along

This is part of a learning-in-public series on dev.to:

- [Post 1: Why I'm Learning ROS 2 as a Database Person](https://dev.to/mattstratton/why-im-learning-ros-2-as-a-database-person) *(you are here)*
- Post 2: What's in a bag file (and why the format question matters) — coming soon
- Post 3: Here's what broke when I tried to store ROS 2 topics in Postgres — coming soon
- The full tutorial — coming once I've learned enough to actually teach it

## Environment

- ROS 2 Jazzy
- TurtleBot3 sim / Gazebo
- TimescaleDB (PostgreSQL extension)
- Python

## Questions, issues, opinions

If you've thought about this problem — rosbag2 at scale, time-series storage for robot data, what fleet analytics actually looks like in production — open an issue or find me on [dev.to](https://dev.to/mattstratton). Especially interested in hearing from people who've hit the wall this repo is trying to address.

