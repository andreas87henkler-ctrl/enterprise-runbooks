\# WI-002 – Ceph OSD Management



\*\*Work Instruction ID:\*\* WI-002

\*\*Version:\*\* 1.0

\*\*Status:\*\* Approved

\*\*Category:\*\* Storage

\*\*Platform:\*\* Ceph

\*\*Related Runbooks:\*\* RB-003, RB-004, RB-005, RB-006

\*\*Owner:\*\* Storage Operations

\*\*Reviewer:\*\* \*To be assigned\*

\*\*Last Updated:\*\* 2026-08-06

\*\*Next Review:\*\* 2027-08-06

\*\*Classification:\*\* Public



\---



\# 1. Purpose



This Work Instruction describes the technical procedures for managing Ceph Object Storage Daemons (OSDs), including adding, removing, replacing, and validating OSDs.



\---



\# 2. Scope



This instruction applies to Ceph clusters managed using supported deployment methods (e.g. cephadm).



Platform-specific deployment methods shall follow the organization's approved standards.



\---



\# 3. Prerequisites



Before starting:



\* Administrative access to the Ceph cluster

\* Administrative access to the target host

\* Cluster health verified

\* Approved maintenance window

\* Replacement hardware available (if applicable)



\---



\# 4. Safety Notes



⚠ Verify cluster health before modifying any OSD.



⚠ Ensure sufficient redundancy remains during maintenance.



⚠ Never remove multiple OSDs simultaneously unless explicitly approved.



⚠ Confirm the correct OSD identifier before executing destructive actions.



\---



\# 5. Related Documents



\* RB-003 – Replace Ceph OSD

\* RB-004 – Add New Ceph OSD

\* RB-005 – Remove Ceph OSD

\* RB-006 – Ceph Cluster Expansion

\* TS-002 – Ceph Troubleshooting



\---



\# 6. Procedure



\---



\## Step 1 – Verify Cluster Health



\### Objective



Ensure the cluster is healthy before performing maintenance.



\### Actions



Check cluster status.



```bash

ceph -s

```



Review detailed health information.



```bash

ceph health detail

```



\### Expected Result



\* HEALTH\_OK (preferred)

\* No unexpected warnings affecting storage maintenance



\### Verification



Confirm cluster health before continuing.



\---



\## Step 2 – Identify the Target OSD



\### Objective



Locate the correct OSD.



\### Actions



List OSDs.



```bash

ceph osd tree

```



Display OSD status.



```bash

ceph osd status

```



\### Expected Result



The correct OSD has been identified.



\### Verification



Confirm the OSD ID matches the maintenance plan.



\---



\## Step 3 – Execute OSD Maintenance



\### Objective



Perform the required OSD operation.



\### Actions



Execute the approved maintenance procedure.



Examples include:



\* Add new OSD

\* Replace failed OSD

\* Remove OSD

\* Reintegrate replacement storage



Follow the organization's approved deployment procedure.



\### Expected Result



The requested maintenance operation completes successfully.



\### Verification



Confirm that the OSD reaches the expected operational state.



\---



\## Step 4 – Monitor Recovery



\### Objective



Observe cluster recovery.



\### Actions



Monitor recovery status.



```bash

ceph -s

```



Review placement group status.



```bash

ceph pg stat

```



\### Expected Result



Placement groups recover successfully.



\### Verification



Confirm recovery progresses without unexpected warnings.



\---



\## Step 5 – Final Validation



\### Objective



Validate normal cluster operation.



\### Actions



Review cluster status.



```bash

ceph -s

```



Review OSD status.



```bash

ceph osd status

```



\### Expected Result



\* All expected OSDs available

\* Cluster healthy

\* Recovery completed



\### Verification



Confirm that the cluster reports normal operational status.



\---



\# 7. Rollback



If maintenance cannot be completed:



\* Stop further storage modifications.

\* Stabilize the cluster.

\* Restore the previous configuration where possible.

\* Escalate according to organizational procedures.



\---



\# 8. Troubleshooting



If issues occur during maintenance, refer to:



\* TS-002 – Ceph Troubleshooting



\---



\# 9. Documentation



Record:



\* Maintenance date

\* Host

\* OSD ID

\* Maintenance performed

\* Validation results

\* Related Change Request

\* Observed issues



\---



\# 10. References



\* RB-003 – Replace Ceph OSD

\* RB-004 – Add New Ceph OSD

\* RB-005 – Remove Ceph OSD

\* RB-006 – Ceph Cluster Expansion

\* TS-002 – Ceph Troubleshooting

\* Ceph Documentation



