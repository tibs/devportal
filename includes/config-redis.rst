
``additional_backup_regions``
-----------------------------
*array*

**Additional Cloud Regions for Backup Replication** 



``ip_filter``
-------------
*array*

**IP filter** Allow incoming connections from CIDR address block, e.g. '10.20.0.0/16'



``service_log``
---------------
*['boolean', 'null']*

**Service logging** Store logs for the service so that they are available in the HTTP API and console.



``static_ips``
--------------
*boolean*

**Static IP addresses** Use static public IP addresses



``migration``
-------------
*['object', 'null']*

**Migrate data from existing server** 



``private_access``
------------------
*object*

**Allow access to selected service ports from private networks** 

``prometheus``
~~~~~~~~~~~~~~
*boolean*

**Allow clients to connect to prometheus with a DNS name that always resolves to the service's private IP addresses. Only available in certain network locations** 

``redis``
~~~~~~~~~
*boolean*

**Allow clients to connect to redis with a DNS name that always resolves to the service's private IP addresses. Only available in certain network locations** 



``privatelink_access``
----------------------
*object*

**Allow access to selected service components through Privatelink** 

``prometheus``
~~~~~~~~~~~~~~
*boolean*

**Enable prometheus** 

``redis``
~~~~~~~~~
*boolean*

**Enable redis** 



``public_access``
-----------------
*object*

**Allow access to selected service ports from the public Internet** 

``prometheus``
~~~~~~~~~~~~~~
*boolean*

**Allow clients to connect to prometheus from the public internet for service nodes that are in a project VPC or another type of private network** 

``redis``
~~~~~~~~~
*boolean*

**Allow clients to connect to redis from the public internet for service nodes that are in a project VPC or another type of private network** 



``recovery_basebackup_name``
----------------------------
*string*

**Name of the basebackup to restore in forked service** 



``redis_maxmemory_policy``
--------------------------
*['string', 'null']*

**Redis maxmemory-policy** 



``redis_pubsub_client_output_buffer_limit``
-------------------------------------------
*integer*

**Pub/sub client output buffer hard limit in MB** Set output buffer limit for pub / sub clients in MB. The value is the hard limit, the soft limit is 1/4 of the hard limit. When setting the limit, be mindful of the available memory in the selected service plan.



``redis_number_of_databases``
-----------------------------
*integer*

**Number of Redis databases** Set number of Redis databases. Changing this will cause a restart of the Redis service.



``redis_io_threads``
--------------------
*integer*

**Redis IO thread count** Set Redis IO thread count. Changing this will cause a restart of the Redis service.



``redis_lfu_log_factor``
------------------------
*integer*

**Counter logarithm factor for volatile-lfu and allkeys-lfu maxmemory-policies** 



``redis_lfu_decay_time``
------------------------
*integer*

**LFU maxmemory-policy counter decay time in minutes** 



``redis_ssl``
-------------
*boolean*

**Require SSL to access Redis** 



``redis_timeout``
-----------------
*integer*

**Redis idle connection timeout in seconds** 



``redis_notify_keyspace_events``
--------------------------------
*string*

**Set notify-keyspace-events option** 



``redis_persistence``
---------------------
*string*

**Redis persistence** When persistence is 'rdb', Redis does RDB dumps each 10 minutes if any key is changed. Also RDB dumps are done according to backup schedule for backup purposes. When persistence is 'off', no RDB dumps and backups are done, so data can be lost at any moment if service is restarted for any reason, or if service is powered off. Also service can't be forked.



``redis_acl_channels_default``
------------------------------
*string*

**Default ACL for pub/sub channels used when Redis user is created** Determines default pub/sub channels' ACL for new users if ACL is not supplied. When this option is not defined, all_channels is assumed to keep backward compatibility. This option doesn't affect Redis configuration acl-pubsub-default.



``redis_version``
-----------------
*['string', 'null']*

**Redis major version** 



``service_to_fork_from``
------------------------
*['string', 'null']*

**Name of another service to fork from. This has effect only when a new service is being created.** 



``project_to_fork_from``
------------------------
*['string', 'null']*

**Name of another project to fork a service from. This has effect only when a new service is being created.** 



