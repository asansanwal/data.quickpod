# Environment Variables

When you create a template and specify the startup command, it is sometimes necessary to know the port mappings, public ip address etc. The following environment variables are available to use in your startup scripts&#x20;

$PUBLIC\_IPADDR Public IP address of the machine hosting your pod

$SSH\_PUBLIC\_KEY Your ssh public key

$CONTAINER\_LABEL The label of the container/Pod, this is also the POD api key&#x20;

$GPU\_COUNT The number of GPUs in your Pod&#x20;

$QUICKPOD\_PORT\_XXXX The externally mapped port for your specified internal port XXXX e.g. you mapped with -p 3000:3000 and quickpod mapped the machine port to 41000 then $QUICKPOD\_PORT\_3000 will give you the value 41000. This is dynamic mapping.

SYMMETRICAL PORTS are ports >= 70000 provided in -p 70000:70000, they map the same internal and external ports and are available through the variable $QUICKPOD\_PORT\_XXXX (e.g. $QUICKPOD\_PORT\_70000)
