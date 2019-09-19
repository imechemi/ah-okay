## Docker


### Container

Container is daemon process running in isolation under its own namespace and croot on host linux which enables virtualization 
and provides separate execution environment. 


### Bridge networks

This is link layer network bridge created using software on docker host through which two containers can connect in 
isolation from other containers on the host. However, network bridge is still a closed network which means it does not let 
any external host to connect to the bridge. There are default bridge and user-defined bridge. 
