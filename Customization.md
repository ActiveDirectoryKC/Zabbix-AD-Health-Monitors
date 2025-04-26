# Tunable Items to Customize the Monitoring in the AD Health Monitor Template
__More details will be added in the future__
Most items are alterable and customizable for your environment. Nothing fancy has been done, there are no scripts being processed, this is all out-of-the-box Zabbix. 

## MACROS (Variables)
Under All Tempates, locate the "Active Directory Health Monitor" template and click on it. You may need to click on the name again at the top to get the template settings window open.
Click the Macros tab to alter the Macros. 

- **{$ADDS.DRA.MAX_PENDING_REPL_OPS}**
  - Value: 50
  - Description: Specify the number of Replication (DRA) pending replication events before triggering an alert. Default is 50.
  - Notes: This may need to be adjusted to reflect the amount of replication latency/queuing your environment experiences. 
- **{$ADDS.DRA.MAX_PENDING_REPL_SYNC}**
  - Value: 50
  - Description: Specify the warning threshold for ATQ Outstanding Queue Requests. Ideally this is as low as possible. Default is 5.
  - Notes: This may need to be adjusted to reflect the amount of replication latency/queuing your environment experiences. 
- **{$ADDS.LDAP.ATQ_OUTSTANDING_REQS_WARN_THRESHOLD}**
  - Value: 10
  - Description: Specify the warning threshold for ATQ Estimated Queue Delay. Ideally this is as low as possible. Default is 5.
  - Notes: 
- **{$ADDS.LDAP.ATQ_QUEUE_DELAY_WARN_THRESHOLD}**
  - Value: 5
  - Description: Specify the warning threshold for ATQ Estimated Queue Delay.Ideally this is as low as possible.  Ideally this is as low as possible. Default is 5.
  - Notes: 
- **{$ADDS.LDAP.ATQ_REQ_LATENCY_WARN_THRESHOLD}**
  - Value: 5
  - Description: Specify the warning threshold for ATQ Request Latency. Ideally this is as low as possible. Default is 5.
  - Notes: 
- **{$ADDS.LDAP.ATQ_USE_WARN_THRESHOLD}**
  - Value: 0.65
  - Description: Specify the warning threshold for ATQ thread usage. If all the threads are consumed AD cannot process authentications on that server. Defaults to 0.65 (65%).
  - Notes: Adjust this to meet your organization's needs. This value can show a trend upward but in busy or smaller environments this can deplete fast.
- **{$ADDS.LDAP.MAXPOOLTHREADS}**
  - Value: 4
  - Description: Manual entry for the LDAP Query for MaxPoolThreads. This value is used to determine the maximum ATQ threads ($MaxPoolThreads * $CPU_Cores). Default in Windows is 4. 
  - Notes: Unfortunately there isn't an easy way to detect these as they are stored in a way that is difficult to query without using scripts, which I've avoided to reduce risks and dependencies. 
- **{$ADDS.NTDS.DB_PATH}**
  - Value: ```registry.data["HKLM\SYSTEM\CurrentControlSet\Services\NTDS\Parameters","DSA Database file"]```
  - Description: NTDS Database path. The volume is specified on AD DS installation, found in the registry. 
  - Notes: __NOT WORKING__ This is not quite working yet. Still needs some work. 
- **{$ADDS.NTDS.LOG_NAME}**
  - Value: edb.log
  - Description: Name of the NTDS log. Combines with NTDS Log Path value. This value is standard in all AD installs. Do not ever delete thsi file!
- **{$ADDS.NTLM.MAXCONCURRENTAPI}**
  - Value: 15
  - Description: Manual entry for MaxConcurrentAPI used for NTLM Authentication. Server 2012+ is 15. If you change this in the registry, it needs changed here.
  - Notes: Once I get the registry lookup stuff working, this will probably evolve into a registry check. 
