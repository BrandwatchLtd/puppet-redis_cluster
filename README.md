# redis_cluster

#### Table of Contents

1. [Overview](#overview)
2. [Requirements](#requirements)
3. [Beginning with redis_cluster (example)](#beginning)
4. [Development](#development)

## Overview

The redis_cluster module lets you use Puppet to install and configure multiple instances of Redis in the same node.

Redis_cluster module Features:
- Redis cluster configuration (Redis >= 3.0)
- Redis configuration (with Augeas)
- Multiple Redis Instances in the same node (with an alternative /etc/init.d/ script)

## Requirements

- Operating system: Debian >= Jessie 
- Puppet module stdlib: https://forge.puppetlabs.com/puppetlabs/stdlib 
- Puppet module apt: https://forge.puppetlabs.com/puppetlabs/apt

## Beginning with redis_cluster (example)

To use the redis_cluster module with two instances:

~~~puppet
# The global redis preferences (required by redis_cluster::instance class)
class {'redis_cluster':
  redis_version   => 'present',
}

# The first redis instance
redis_cluster::instance{'master':
  ip   => '127.0.0.1',
  port => '7000',
}

# The second redis instance
redis_cluster::instance{'slave':
  ip   => '127.0.0.1',
  port => '7001',
}
~~~

**Note:** The main `redis_cluster` class is required by all other classes (redis_cluster::instance for example). You must declare it whenever you use the module.

## Development

This Puppet module is an open project, and community contributions are essential for keeping it great. I can't access the huge number of platforms and myriad hardware, software, and deployment configurations that Puppet is intended to serve. Send me your pull requests on Github! 
