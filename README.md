# Ansible Role: Path

A small Ansible Role that permanently sets a path by adding the required files to /etc/profile.d.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    path_to_add:
      - "/usr/local/bin"
      - "/usr/local/go/bin"

path_to_add is a list of all paths to add to the system wide profile.
The role will generate a path-specific script in /etc/profile.d (e.g. /etc/profile.d/usr_local_bin.sh) that adds the folder to the PATH variable.

## Dependencies

none


## Example Playbook


With path_to_add set - e.g. in a variable file like ./vars/testdata.yml:

```yaml
---
path_to_add:
  - "/usr/local/bin"
  - "~/.somename/bin"
```

the playbook would look like

```yaml
---
- name: Converge
  hosts: all
  gather_facts: no
  tasks:
    - name: Get test data - Include all vars from ./vars/*.yml
      include_vars:
        dir: vars
        extensions:
          - yml

    - name: "Include role cvstebut.path"
      include_role:
        name: "cvstebut.path"
```

## Compatibility


This role has been tested on these [container images](https://hub.docker.com/):

|container|tags|
|---------|----|
|debian|9|
|el|7, 8|
|ubuntu|bionic, focal|

The containers used were adapted images for ansible testing graciously provided by the Jeff Geerling aka the geerlingguy.
(e.g. geerlingguy/docker-ubuntu2004-ansible. See ./molecule/default/molecule.yml for details.)

The tests were done using Ansible 2.9 but should also run on lower versions.

## License

Apache 2

## Author Information

This role was created in 2020 by Christian von Stebut

## Thanks

Thanks to Jeff Geerling (geerlingguy) and Robert de Bock (robertdebock) for a lot of excellent roles and to be so kind to provide lots of samples to copy stuff from. 

And a lot of thanks to Percy Grunwald for [a very nice video on Ansible and Testing](https://www.youtube.com/watch?v=DAnMyBZ8-Qs).

All errors made are - of course - proudly owned by myself :-) <br>
But even while making mistakes is part of learning, please contact me if you find any. I will be happy to learn about and correct them.
