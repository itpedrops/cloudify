Comands about software Cloudify

# --Verify version

 $ cfy --version
OUTPUT:  
Premium edition
Cloudify CLI 4.4.0
Cloudify Manager 4.4 [ip=192.168.0.20]

## --list profiles
 $ cfy profiles list
 OUTPUT:
 Listing all profiles...

Profiles:
+---------------+--------------+----------+-------------------------------------+----------+-----------+---------------+------------------+----------------+-----------------+
|      name     |  manager_ip  | ssh_user |             ssh_key_path            | ssh_port | rest_port | rest_protocol | manager_username | manager_tenant | bootstrap_state |
+---------------+--------------+----------+-------------------------------------+----------+-----------+---------------+------------------+----------------+-----------------+
| *manager-cfy | 10.10.10.10 |  centos  | /Users/user/path/key.pem       |    22    |     80    |      https    |      administrator       | default_tenant |     Complete    |
+---------------+--------------+----------+-------------------------------------+----------+-----------+---------------+------------------+----------------+-----------------+

## --list services manager 
 $ cfy status
  OUTPUT:
 Retrieving manager services status... [ip=10.10.10.10]

Services:
+--------------------------------+---------+
|            service             |  status |
+--------------------------------+---------+
| InfluxDB                       | running |
| Cloudify Composer              | running |
| Logstash                       | running |
| AMQP InfluxDB                  | running |
| RabbitMQ                       | running |
| PostgreSQL                     | running |
| Webserver                      | running |
| Management Worker              | running |
| Syncthing                      | running |
| Cloudify Console               | running |
| Manager Rest-Service           | running |
| Consul                         | running |
| Riemann                        | running |
+--------------------------------+---------+


## --Configure profile to use CLOUDIFY
$ cfy profiles use --profile-name manager-ec2 192.168.0.20 -t default_tenant -u admin -p my-password-strong
OUTPUT: 

Attempting to connect to 192.168.0.20 through port 80, using http (SSL mode: False)...
Initializing profile manager-ec2...
Initialization completed successfully
Using manager 192.168.0.20 with port 80


## -- Deploy blueprint and create a deployment oneTIME

 $ cfy install PATH/blueprint.yaml -i PATH/inputs/inputs.yaml --task-retries=15 --task-retry-interval=15```
 
## --Upload blueprint
 $ cfy blueprints upload -b BLUEPRINT_NAME -p BLUEPRINT_FILE_LOCATION

## --Create deployment
 $ cfy deployments create -b BLUEPRINT_NAME DEPLOYMENT_NAME --inputs path/to/your/inputs.yaml
 
 

Reference: https://docs.cloudify.co/4.0.0/cli/overview/
