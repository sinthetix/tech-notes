# Docker
## What is it?
_(Notes are from John Willis's Docker Workshop from Velocity NYC 2015)._

Docker is a platform for developing, shipping, and running applications using container technology

Docker has multiple products/tools:
* Docker Engine: actually drives the containers. Kind of like a hypervisor (but it’s not a hypervisor).
* Docker Hub: Store/retrieve images.
* Docker Trusted Registry: Enterprise/self-hosted version of Docker Hub.
* Docker Machine: Tool to create Docker hosts. (Docker hosts are where you run your Docker engines). Command line interface. 
* Docker Swarm: Orchestration tool (Similar to Kubernetes and Mesos). Can work with Kub. Works well with Mesos. Handles policies, multiple machines, affinities, etc. Abstraction on how to operate docker.
* Docker Compose: Composition language for managing docker runs/building containers. Docker file.
* Kitematic: GUI for installing/running containers.
* Docker Toolbox: Helpful for people running Docker on Windows or Mac.

Docker CONTAINERS run as PROCESSES instead of fully emulated OS.

#### Bare Metal (Application > OS > Physical Server):
* Slow deployment times
* Huge costs
* Wasted Resources
* Difficult to scale
* Difficult to migrate
* Vendor lock in

#### Hypervisor-based Virtualization ((multiple VMS which contain Application > Guest OS) > Hypervisor > Host OS > Physical Server):
* Hypervisor is broker between VMs and physical. 
* Each VM is full-blown image of OS.

#### Benefits of VMs:
* better resource pooling (one machine is multiple VMs)
* Easier to scale
* VMs in the CLOOD (pay as you go, elastic)

#### Limitations of VMs:
* Each VM still requires CPU allocation, storage, RAM, and an entire guest OS.
* More VMS = more resources
* Guest OS = wasted resources
* Application portability not guaranteed

#### Containers ((Application (Container)) > OS Kernel (Host OS) > Physical server):
* Uses the kernel on host OS to run multiple root file systems
* Each root file system is a container
* Each container has its own processes, memory, devices, and network stack

_Smaller footprint, higher density._

#### Why is docker so popular?
* Speed of instantiation (400-500ms to fire up, vs VM which takes a minute)
* Convergence: containers use service registry to converge

#### Containers VS VMs:
* Containers more lightweight
* No need to install guest OS
* Less CPU, RAM, storage space req’d
* More containers per machine than VMs
* Speed of instantiation
* Greater portability

#### Docker:
* Isolation
* Lightweight
* Simplicity
* Workflow
* Community

Docker made running linux containers easier. 5-6 namespaces, network namespace, c groups, network plumbing.

#### Benefits of Docker:
* Separation of concerns (devs focus on apps, sys admins focus on deployment)
* Fast development cycle
* Application portability (build in one env, ship to another)
* Scalability (easily spin up containers if needed)
* Run more apps on one host machine
