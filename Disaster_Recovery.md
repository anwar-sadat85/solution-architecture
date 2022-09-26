# Disaster Recovery
Resiliency - high availability and DR

Availability = Mean Time Between Failures (MTBF) / Mean Time Between Failures (MTBF) + Mean Time to Recover (MTTR)

## HA is not DR
RTO - Recovery time objective - Time taken to recover from failure

RPO - Recovery point objective - Amount of data loss

## Aurora global tables for DR
Aurora Global tables - RTO less than one min. RPO less than one second.

## Mutable and immutable components

Immutable pieces of application - Eg: Infrastructure, Code
Mutable pieces of application - Eg: data in DB or EBS

## AWS Backup
RDS backup - AWS Backup - RPO of less than 5 minutes

## DR strategies

### Backup and restore 
- High RTO and RPO
- Get notified by an event
- Use a mix of automation and manual intervention to restore services from backups
- Use AWS Backup (<b>Cross region back up</b>)
  - RDS
  - EBS
  - Dynamo DB tables
  - S3
- Low cost
### Pilot light
- Active / Passive
- Services inactive (immutable)
- Traffic not active
- Data replicated to another region anticipating a disaster
- When disaster strikes, 
  - services are made actice
  - Traffic is switched
### Warm standby
- Active / Passive
- Services active (immutable)
- Traffic not active
- Data replicated to another region anticipating a disaster
- When disaster strikes, 
 - Traffic is switched
### Multisite active / active 
- Lowest (0) RTO and RPO 
- High cost
- Active / Active
- Services active (immutable)
- Traffic active
- Data replicated to another region anticipating a disaster

## RTO & RPO
Backup and restore (hours) > Pilot light (10s of minutes) > Warm standby (within a minute) > Multisite active / active (zero)

## RPO RDS recovery
AWS RDS Backup > Aurora Global Database
