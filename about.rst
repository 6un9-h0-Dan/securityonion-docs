.. _about:

About
=====

Security Onion
--------------
Security Onion is a free and open source Linux distribution for threat hunting, enterprise security monitoring, and log management. It includes :ref:`hive`, :ref:`playbook`, :ref:`fleet`, :ref:`cyberchef`, :ref:`elasticsearch`, :ref:`logstash`, :ref:`kibana`, :ref:`suricata`, :ref:`zeek`, :ref:`wazuh`, and many other security tools. Security Onion has been downloaded over 1 million times and is being used by security teams around the world to monitor and defend their enterprises. Our easy-to-use Setup wizard allows you to build an army of distributed sensors for your enterprise in minutes!

.. note::

   Security Onion started in 2008 and was originally based on the Ubuntu Linux distribution. Throughout the years, the Security Onion version tracked the version of Ubuntu it was based on. For example, the last major version of Security Onion was based on Ubuntu 16.04 and so it was called Security Onion 16.04. Security Onion is now container based and thus no longer limited to just Ubuntu. To signify this change, Security Onion now has its own versioning scheme and the current version of this new platform is Security Onion 2.1.

   Here are some high level system differences between Security Onion 2.1 and the older legacy versions:

    - Move from Ubuntu packages to containers
    - Support both CentOS 7 and Ubuntu 18.04
    - Change pcap collection tool from netsniff-ng to Google Stenographer
    - Upgrade to Elastic Stack 7.x and support the Elastic Common Schema (ECS)
    - Remove unsigned kernel module PF_RING and completely replace with AF_PACKET
    - Suricata completely replaces Snort. (We may elect to add Snort back after Snort 3.0 is officially released.)
    - Sguil, Squert, and capME are removed
    - Storage Nodes are now known as Search Nodes
    - Incorporate new tech: TheHive, Strelka, support for Sigma rules, Grafana/influx (independent health monitoring/alerting), Fleet (osquery management), Playbook (detection playbook tool), Onion Hunt (hunting tool), Security Onion Console (PCAP collection tool)

For more information about Security Onion not contained in this Documentation, please see our community site at https://securityonion.net.

Security Onion Solutions, LLC
-----------------------------
Doug Burks started Security Onion as a free and open source project in 2008 and then founded Security Onion Solutions, LLC in 2014.  

.. important::

   Security Onion Solutions, LLC is the only official provider of hardware appliances, training, and professional services for Security Onion.

For more information about these products and services, please see our company site at https://securityonionsolutions.com.

Documentation
-------------

.. warning::

   We've started updating this documentation for the new Security Onion 2.1. However, please note that this is a work in progress. Many pages have not been updated yet and thus may have incorrect or missing information.
   
Formats
~~~~~~~

This documentation is published online at https://securityonion.net/docs/2.1.  If you are viewing an offline version of this documentation but have Internet access, you might want to switch to the online version at https://securityonion.net/docs/2.1 to see the latest version.

This documentation is also available in PDF format at https://readthedocs.org/projects/securityonion/downloads/pdf/2.1/.

| Many folks have asked for a printed version of our documentation.  Whether you work on airgapped networks or simply want a portable reference that doesn't require an Internet connection or batteries, this is what you've been asking for.  Thanks to Richard Bejtlich for writing the inspiring foreword!  Proceeds go to the Rural Technology Fund! Please note that the print version is currently based on the older Security Onion 16.04 documentation.
| https://securityonion.net/book

Authors
~~~~~~~

Security Onion Solutions is the primary author and maintainer of this documentation.  Some content has been contributed by members of our community.  Thanks to all the folks who have contributed to this documentation over the years!

Contributing
~~~~~~~~~~~~
We welcome your contributions to our documentation!  We will review any suggestions and apply them if appropriate.

If you are accessing the online version of the documentation and notice that a particular page has incorrect information, you can submit corrections by clicking the ``Edit on GitHub`` button in the upper right corner of each page.

To submit a new page, you can submit a pull request (PR) to the 2.1 branch of the ``securityonion-docs`` repo at https://github.com/Security-Onion-Solutions/securityonion-docs.

Pages are written in RST format and you can find several RST guides on the Internet including https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html.

Naming Convention
~~~~~~~~~~~~~~~~~
Our goal is to allow you to easily guess and type the URL of the documentation you want to go to.

| For example, if you want to read more about Suricata, you can type the following into your browser: 
| https://securityonion.net/docs/suricata

To achieve this goal, new documentation pages should use the following naming convention:

- all lowercase
- ``.rst`` file extension
- ideally, the name of the page should be one simple word (for example: ``suricata.rst``)
- try to avoid symbols if possible
- if symbols are required, use hyphens (NOT underscores)
