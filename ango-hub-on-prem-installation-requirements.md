---
description: System requirements to install Ango Hub on-premises, in your own datacenter.
---

# Ango Hub On-Prem Installation Requirements

Ango Hub can be installed on-premise and deployed directly onto your cloud/virtualized infrastructure or on your own hardware.

Ango Hub itself runs in a containerized environment. Ango Hub supports using, out of the box, existing NFS or Kubernetes Supported Block storage services like Ceph, Longhorn, Open EBS and more.

{% hint style="info" %}
For enterprise customers we provide specialized installation scripts that automate installing software requirements and volume adjustments based on their server setups.
{% endhint %}

LDAP is fully supported.

Contact our team at support@ango.ai for more information and for further customization options.

## Minimum Requirements <a href="#minimum-hardware-requirements-for-single-node-installation" id="minimum-hardware-requirements-for-single-node-installation"></a>

| Item    | Minimum Requirements                                                                                               |
| ------- | ------------------------------------------------------------------------------------------------------------------ |
| OS      | <p>Red Hat Enterprise Linux 8 or newer<br>CentOS 8 or newer<br>Ubuntu 18.04 or newer<br>Debian Buster or newer</p> |
| CPU     | 8-Core                                                                                                             |
| RAM     | 32 GB                                                                                                              |
| Storage | 500 GB (varies depending on your data)                                                                             |
