---
layout: post
title: "Ubuntu Server Development Summary - 02 Jun 2017"
date: 2017-06-02 11:13
comments: false
categories: ubuntu
---

The purpose of this weekly summary is to make sure our community can
follow development with toes dipped in before & between jumping headlong
into helping shape Ubuntu Server.

Ubuntu Server Packages
---

- Uploads/Changes:
  - 11 packages uploaded to Artful
  - 48 packages uploaded to Stable Releases
  - [Full List](http://bit.ly/2rsZJce)
  - [Future](https://merges.ubuntu.com/main.html)

Cloud-init/Curtin
---

- cloud-init:
  - Enabled Aliyun datasource (LP:#1638931).   After SRU, Ubuntu
    images will work on Alibaba Cloud.
  - Accepted merge to add schema definition and validation to NTP
    module
  - Accepted merge to handle multi-line bridge parameters to E/N/I
  - Accepted merge to discontinue writing systemd link files
  - Fixed LP:#1693939 Azure chassis asset tag value
  - Fixed LP:#1692093 to prevent re-executing disk setup on reboot
- curtin:
  - Fixed package build issue after escaping udevadm command
  - All integration VM tests back to green status

Triage Queue
---

- 63 bugs reviewed, 1 accepted, 445 in backlog
- [Backlog](https://bugs.launchpad.net/~ubuntu-server/+subscribedbugs)
- [Notes on daily bug triage](https://wiki.ubuntu.com/ServerTeam/KnowledgeBase#Bug_Triage)

IRC Meeting
---

- [Log](http://bit.ly/2smBqg0)
- [General Info](https://wiki.ubuntu.com/ServerTeam/Meeting)

Server ISOs
---

- Publishing of new daily Artful server ISOs is currently blocked by
  LP:#1694531
