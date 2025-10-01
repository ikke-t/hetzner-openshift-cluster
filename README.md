# OCP Cluster at Hetzner Cloud

This repo holds automation for setting up base infra for hosting
[OpenShift](https://www.redhat.com/openshift) at Hetzner. It consists
of ansible playbooks to set up the infra. It also requires some manual steps.

I'll write a blog around this once done.

# Setup the infra

Playbooks:

* **[01-infra](./01-infra.yml)** - Sets up the bastion VM and basic networks
* **[02-controllers](./02-controllers.yml)** - Sets up OCP controllers, and LB
* **[03-probe-settings](./03-probe-settings.yml)** - Fetches settings needed for agent-install
* **[04-collect-settings](./04-collect-settings.yml)** - Writes config files for agent-install

# Create Agent installer

After running the previous, you need to create ISO image for the installation.
Download the openshift-install tool from
[Red Hat Downloads](https://console.redhat.com/openshift/downloads).

```
mkdir agent; cd agent
cp ../agent-config.yaml install-config.yaml .
./openshift-install --dir . agent create image
```
