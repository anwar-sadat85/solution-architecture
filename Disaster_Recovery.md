#Disaster Recovery
Resiliency - high availability and DR
Availability = Mean Time Between Failures (MTBF) / Mean Time Between Failures (MTBF) + Mean Time to Recover (MTTR)
HA is not DR
RTO - Recovery time objective - Time taken to recover from failure
RPO - Recovery point objective - Amount of data loss
Aurora Global tables - RTO less than one min. RPO less than one second.
Immutable pieces of application - Eg: Infrastructure, Code
Mutable pieces of application - Eg: data in DB or EBS
RDS backup - AWS Backup - RPO of less than 5 minutes

##DR strategies

-Backup and restore
-Pilot light
-Warm standby
-Multisite active / active
