# unibet-vagrant

[![Build Status](https://secure.travis-ci.org/unibet/puppet-vagrant.png)](http://travis-ci.org/unibet/puppet-vagrant)

## Overview

This module ment to take care of vagrant installation, its plugins and boxes. It focuses on the latest vagrant versions
and therefore might not work properly with older releases requiring special setup, but it is still possible to
request a specific version.

It was inspiried by code from [mjanser](https://github.com/mjanser/puppet-vagrant) and [emyl](https://github.com/emyl/puppet-vagrant) modules, but forked due to their inactivity.

## Description

This module uses $::osfamily and $::architecture to determine what package to install.

Currently supports:
* CentOS and Redhat (i386 and x86)
* Ubuntu and Debian (i386 and x86)
* Windows (not tested)
* Darwin (not tested)

## Usage

### vagrant

Install latest version
```
include vagrant
```

Install 1.6.3
```
class { 'vagrant':
  version => '1.6.3'
}
```

### vagrant::plugin

Install plugin
```
vagrant::plugin { 'vagrant-hostmanager':
  user => 'myuser'
}
```

Install plugin in specific version
```
vagrant::plugin { 'vagrant-hostmanager':
  user    => 'myuser',
  version => 0.8.0
}
```

There are some more options which are the same as supported by the *vagrant plugin* command.
- prerelease
- source
- entry_point

### vagrant::box

Add a vagrant box for the specified user.
```
vagrant::box { 'puppetlabs/centos-6.6-64-puppet':
  user => 'vagrant'
}
```

## Limitations

The user parameter is currently ignored on Windows systems (current user is assumed).

$::osfamily usage requires Facter 1.6.1 or later.