.. _release-notes:

Release Notes
=============

Before downloading, please review the notes for this release.

Security Onion 2.1 Release Candidate 2 (RC2) is here!

.. warning::

  This is our second Release Candidate, so we're getting closer to a final release, but we're not quite there yet. Please be reminded of the usual pre-release warnings and disclaimers:

  - If this breaks your system, you get to keep both pieces!
  - This is a work in progress and is in constant flux.
  - This configuration may change drastically over time leading up to the final release.
  - Do NOT run this on a system that you care about!
  - Do NOT run this on a system that has data that you care about!
  - This should only be run on a TEST box with TEST data!
  - May result in nausea, vomiting, or a burning sensation.

Known Issues
------------

- You cannot add NEW nodes with the RC1 ISO once your grid has been updated to RC2. This has to do with changes to the setup script for RC2.
- Shipping Windows Eventlogs with Osquery will fail intermittently with utf8 errors logged in the Application log - This will be fixed in Osquery 4.5

2.1.0 Changes
-------------

- Moved static.sls to global.sls to align the name with the functionality
- Event pipeline now is completely encrypted in transport
- Playbook
  - Elastalert now runs active Plays every 3 minutes
  - Changed default rule-update config to only import Windows rules from the Sigma Community repo
  - Lots of bug fixes & stability improvements
- Ingest Node parsing updates for Osquery and Winlogbeat - implemented single pipeline for Windows eventlogs & sysmon logs
- Upgraded Osquery to 4.4 and re-enabled auto-updates


2.0.3 Changes
-------------

- Resolved an issue with large drives and the ISO install  
- Modified ISO installation to use Logical Volume Management (LVM) for disk partitioning
- Updated Elastic Stack components to version 7.8.1
- Updated Zeek to version 3.0.8

2.0.2 Changes
-------------

- | Sensoroni fails on 2.0.1 ISO EVAL installation #1089
  | https://github.com/Security-Onion-Solutions/securityonion/issues/1089
  
2.0.1 Changes
-------------

- | Security Fix: variables.txt from ISO install stays on disk for 10 days
  | https://github.com/Security-Onion-Solutions/securityonion/issues/1067
  
- | Security Fix: Remove user values from static.sls
  | https://github.com/Security-Onion-Solutions/securityonion/issues/1068
  
- | Fix distributed deployment sensor interval issue allowing PCAP
  | https://github.com/Security-Onion-Solutions/securityonion/issues/1059
  
- | Support for passwords that start with special characters
  | https://github.com/Security-Onion-Solutions/securityonion/issues/1058
  
- Minor soup updates

2.0.0 Changes
-------------

- This version requires a fresh install, but there is good news - we have brought back :ref:`soup`! From now on, you should be able to run :ref:`soup` on the manager to upgrade your environment to RC2 and beyond!
- Re-branded 2.0 to give it a fresh look
- All documentation has moved to our docs site
- soup is alive! Note: This tool only updates Security Onion components. Please use the built-in OS update process to keep the OS and other components up to date
- so-import-pcap is back! See the docs here
- Fixed issue with so-features-enable
- Users can now pivot to PCAP from Suricata alerts
- ISO install now prompts users to create an admin/sudo user instead of using a default account name
- The web email & password set during setup is now used to create the initial accounts for TheHive, Cortex, and Fleet
- Fixed issue with disk cleanup
- Changed the default permissions for /opt/so to keep non-priviledged users from accessing salt and related files
- Locked down access to certain SSL keys
- Suricata logs now compress after they roll over
- Users can now easily customize shard counts per index
- Improved Elastic ingest parsers including Windows event logs and Sysmon logs shipped with WinLogbeat and Osquery (ECS)
- Elastic nodes are now "hot" by default, making it easier to add a warm node later
- so-allow now runs at the end of an install so users can enable access right away
- Alert severities across Wazuh, Suricata and Playbook (Sigma) have been standardized and copied to event.severity:

  - 1-Low / 2-Medium / 3-High / 4-Critical
  
- Initial implementation of alerting queues:

  - Low & Medium alerts are accessible through Kibana & Hunt
  - High & Critical alerts are accessible through Kibana, Hunt and sent to TheHive for immediate analysis
  
- ATT&CK Navigator is now a statically-hosted site in the nginx container
- Playbook

  - All Sigma rules in the community repo (500+) are now imported and kept up to date
  - Initial implementation of automated testing when a Play's detection logic has been edited (i.e., Unit Testing)
  - Updated UI Theme
  - Once authenticated through SOC, users can now access Playbook with analyst permissions without login
  
- Kolide Launcher has been updated to include the ability to pass arbitrary flags - new functionality sponsored by SOS
- Fixed issue with Wazuh authd registration service port not being correctly exposed
- Added option for exposure of Elasticsearch REST API (port 9200) to so-allow for easier external querying/integration with other tools
- Added option to so-allow for external Strelka file uploads (e.g., via strelka-fileshot)
- Added default YARA rules for Strelka -- default rules are maintained by Florian Roth and pulled from https://github.com/Neo23x0/signature-base
- Added the ability to use custom Zeek scripts
- Renamed "master server" to "manager node"
- Improved unification of Zeek and Strelka file data
