Ansible Java
=========

This module install Azul Zulu OpenJDK on the host.

Role Variables
--------------

```yaml
java_version: 11.2.3
```

Typically, using the default `java_version` is recommended (it will be updated by Humio staff as needed), but you can
find valid versions by taking a look at Zulu's [list of binaries](http://static.azul.com/zulu/bin/). Note that the role
will automatically convert `11.2.3` to `11.2+3` behind the scenes. In the previously linked list, mentions of `11.2+3`
should be specified in `java_version` as `11.2.3` for this reason.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - role: humio.java

License
-------

Apache 2.0

Author Information
------------------

If you're having issues with this module please to not hesitate to reach out to us on the #ansible channel on our [Slack community team](https://community.humio.com/).
