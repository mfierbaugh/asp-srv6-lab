# Features 

This project has been modified from it's original form and is meant to be run in dcloud on ContainerLabs hosts. 
Authors: Marty Fierbaugh (mfierbau@cisco.com), Chris Olson (christoo@cisco.com)

Features in this playbook:
 - Segment Routing v6 uSID using ISIS
 - Transport Independant Loop Free Alternate (TI-LFA)
 - Flexable Algorithm
 - Core [QOS](Qos.md)
 - Model-Driven Telemetry
 - Segment Routing Performance Measurement (SR-PM)
 - BGP with PIC Edge/Core

# Usage

This project is a full CI/CD pipline for configuration management. All configuration changes should be made by logging an issue then merging the changes to the Development branch then Test branch.

WARNING - this is a full commit replace and will restore the Converged SDN Transport configuration.

# Setup

Start by updating the host field to mach your enviroment.
.
..
...

# Run playbooks directly

To run the playbook without committing changes:

    ansible-playbook -i hosts.yml lab_master_playbook.yml -e "commit_changes=0"

To run the playbook committing the changes:

    ansible-playbook -i hosts.yml clab_master_playbook.yml -e "commit_changes=1"

The following script just simply execute the second example and commits changes

./config_lab




# Start T-REX 

# Start the interactive trex console which will make a local connection to the running interactive daemon
./trex-console

# Start generating some traffic
start -f stl/imix.py

# To interact with and view statistics for the current stream launch the text-based user interface (tui)
tui

# Attempt to increase per interface traffic rate to 200mbps (400mbps rx/tx total). Throughput achievable in the Docker environment is dependent primarily on single core\thread CPU performance.
update -m 200mbps
