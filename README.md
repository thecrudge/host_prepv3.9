# ocp-hostprep v 3.9

These are my host prep playbooks that are client agnostic. 

They contain a few roles, that will assist in docker clean up should you be installing from cloned, 
or an already installed cluster that is getting a rebuild. I would suggest running the 
adhoc/uninstall.yaml first, then run the host_prep.

disable_yum_plugins - I found in one scenerio that one of the yum plugins was set
to a higher verbosity that kept the deploy_cluster.yaml from completing. The simple
fix was just to disable the plugins, and re-enble once the install finished.


