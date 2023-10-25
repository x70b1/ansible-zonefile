# ansible-zonefile

[![CI/CD](https://github.com/x70b1/ansible-zonefile/actions/workflows/shellcheck.yml/badge.svg?branch=main)](https://github.com/x70b1/ansible-zonefile/actions)
[![GitHub contributors](https://img.shields.io/github/contributors/x70b1/ansible-zonefile.svg)](https://github.com/x70b1/ansible-zonefile/graphs/contributors)
[![License](https://img.shields.io/github/license/x70b1/ansible-zonefile.svg)](https://github.com/x70b1/ansible-zonefile/blob/master/LICENSE)

Maintain the existence and SOA settings for a zone file managed by [Knot DNS](https://www.knot-dns.cz/).
This works fine together with [StackExchange/dnscontrol](https://github.com/StackExchange/dnscontrol).


## Setup

Clone this repo to the Ansible Library in your current project:

```
git clone https://github.com/x70b1/ansible-zonefile.git library/
```


## How to use

Background knowledge of the structure of an [SOA record](https://en.wikipedia.org/wiki/SOA_record) is highly recommended.

The module supports the following arguments:

```yaml
- name: "Zonefiles"
  zonefile:
    name: example.org
    ttl: 14400
    mname: ns1.example.org
    rname: mail@example.org
    refresh: 3600
    retry: 600
    expire: 1209600
    minimum: 600
```

You can use a preformatted `rname` but you have to use escaped backslashes:

```yaml
- name: "Zonefile"
  zonefile:
    ...
    rname: we\\.are\\.online.example.org.   # we.are.online@example.org
    ...
```
