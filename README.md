# Ansible Role: Heartbeat


[![CircleCI](https://circleci.com/gh/mtlynch/ansible-role-heartbeat.svg?style=svg)](https://circleci.com/gh/mtlynch/ansible-role-heartbeat)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](LICENSE)

## Overview

Ansible role for a simple heartbeat server that sends regular heartbeat liveness notifications to a monitoring service such as [Cronhub](https://cronhub.io) or [UptimeRobot](https://uptimerobot.com).

## Role Variables

See [defaults/main.yml](https://github.com/mtlynch/ansible-role-heartbeat/blob/master/defaults/main.yml) for full list:

```yaml
heartbeat_url: google.com # Replace with an external monitoring URL
heartbeat_retries: 3
heartbeat_frequency_minutes: 5
heartbeat_system_user: heartbeat
heartbeat_group: heartbeat
```

## Dependencies

None

## Example Playbook

The example below shows how to configure a server that sends heartbeat messages to Cronhub every 15 minutes

### `example.yml`

```yaml
- hosts: heartbeat
  roles:
    - role: ansible-role-heartbeat
      heartbeat_frequency_minutes: 15
      # Replace the URL with the one Cronhub generates for your monitor.
      heartbeat_url: https://cronhub.io/ping/104ab434-33aa-4146-b1a5-426cf952215a
```

### Running Example Playbook

```bash
ansible-galaxy install git+https://github.com/mtlynch/ansible-role-heartbeat.git
ansible-playbook example.yml
```

## License

MIT

## Author Information

This role was created in 2021 by [Michael Lynch](http://mtlynch.io).
