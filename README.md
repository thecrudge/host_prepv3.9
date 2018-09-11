# ocp-hostprep v 3.9

These are my host prep playbooks that are client agnostic. 

They contain a few roles, that will assist in docker clean up should you be installing from cloned, 
or an already installed cluster that is getting a rebuild. I would suggest running the 
adhoc/uninstall.yaml first, then run the host_prep. They also contain some artifacts from from
past versions that are no longer applicable, and post_install tasks.

subscribe_to_repos - Obvious, subscribe to repos. You'll need to add your pool id in 
the defaults/main.yaml

disable_yum_plugins - I found in one scenerio that one of the yum plugins was set
to a higher verbosity that kept the deploy_cluster.yaml from completing. The simple
fix was just to disable the plugins, and re-enble once the install finished.

host_prep - main playbook. Docker setup, add your block device in defaults/main.yaml,
          - Install pre requisite packages
          - Set selinux policy
          - Install atomic-openshift-utils
          - Install Docker
          - Check to see if Docker was previously installed. If so, run the docker-storage.yaml

    docker-storage.yaml - Completely wipes the docker block device. Removes the partitions on
                          the block device. Wipes everything, then recreates it and extends the
                          docker LVM to 100%

enable_yum_plugs - Re enables yum plugins

ldap_groupsync - Configures LDAP Group Sync based on AD

node-config - Adds kubeletAruments for resource management
