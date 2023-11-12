# mymac

Working of [github.com/geerlingguy/mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook).

Ignore this repo an go to the source; GitHub Workflows disabled on this fork.

# Instructions to test this Ansible playbook

You better execute this on virtual machine with [Tart](https://tart.run).

Deploy on the MacOS release of your liking:

```bash
tart tart clone ghcr.io/cirruslabs/macos-ventura-base:latest mymac
tart run mymac
ssh -A admin@$(tart ip mymac)
```

Once inside `mymac` shell, install `ansible` and clone this repo (`brew` already installed on CirrusLabs base images):

```
brew update
brew upgrade
brew install ansible
git clone https://github.com/jig/mymac.git
cd mymac
ansible-galaxy install -r requirements.yml
ansible-playbook main.yml --ask-become-pass
```

The playbook will require your password. Default password for Tart images is admin.
