Session8
Assignment 3
Architecture of APACHE HADOOP YARN:
The fundamental idea of YARN is to split up the functionalities of resource management and job scheduling/monitoring into separate daemons. The architecture of YARN has a global ResourceManager (RM) and per-application ApplicationMaster (AM). The ResourceManager and the NodeManager form the data-computation framework. 
1)	ResourceManager:
•	The ResourceManager is the ultimate authority that arbitrates resources among all the applications in the system. 
•	The NodeManager is the per-machine framework agent who is responsible for containers, monitoring their resource usage (CPU, memory, disk, and network) and reporting the same to the ResourceManager/Scheduler.
The ResourceManager has two main components: Scheduler and ApplicationsManager.
1.	Scheduler:
•	The Scheduler is responsible for allocating resources to the various running applications subject to familiar constraints of capacities, queues etc. 
•	The Scheduler is pure, that is it performs no monitoring or tracking of status for the application and also offers no guarantees about restarting failed tasks either due to application failure or hardware failures. 
•	The Scheduler performs its scheduling function based the resource requirements of the applications.
•	The Scheduler has a pluggable policy which is responsible for partitioning the cluster resources among the various queues, applications etc. 
•	The current schedulers such as the Capacity Scheduler and the Fair Scheduler would be some examples of plug-ins.
There are different schedulers 1) FIFO Scheduler 2) Capacity Scheduler 3) Fair Scheduler.
i.	Fair Scheduler - Fair scheduling is a method of assigning resources to applications such that all apps get, on average, an equal share of resources over time.
ii.	FIFO Scheduler – Scheduling is done according to the sequence of the request.
iii.	Capacity Scheduler - The Capacity Scheduler is designed to allow sharing a large cluster while giving each organization a minimum capacity guarantee. 
2.	ApplicationsManager
•	The ApplicationsManager is responsible for accepting job-submissions, negotiating the first container for executing the application specific ApplicationMaster and provides the service for restarting the ApplicationMaster container on failure. 
•	This means that all MapReduce jobs should still run unchanged on top of YARN with just a recompile.
2)	ApplicationMaster:
•	The per-application ApplicationMaster is a framework specific library and is tasked with negotiating resources from the ResourceManager and working with the NodeManager(s) to execute and monitor the tasks.
•	The per-application ApplicationMaster has the responsibility of negotiating appropriate resource containers from the Scheduler, tracking their status and monitoring for progress.
