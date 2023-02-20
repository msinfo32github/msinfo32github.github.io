---
title: Backups!
date: 2023-02-20 15:55:00 +0100
categories: [storage,backups]
tags: [servers,backup,homelab,hardware]
---

Question: ***How can you never lose data?***

By following the 3-2-1 backup plan!

## But what is 3-2-1?

3-2-1 is the idea to have:

- **3** copies of your data
- **2** different media types (such as using **LTO tape** in conjunction with **HDDs**!)
- **1** copy of your data **offsite** (such as away from other copies, or in the "cloud" using services such as [Hetzner Storage Box](https://www.hetzner.com/storage/storage-box) or [Backblaze](https://www.backblaze.com/))

# What should I backup?

This is up to personal preference, but most backups include multiple copies of photos, videos and password manager databases, or anything else deemed **important**.

# Why?

Backups should be planned as an important part of anything you do, such as thinking of how to recover in a "disaster scenario". They are also useful for recovery of deleted, corrupted or lost files.

# How?
How you backup your data is up to personal preference but these guidelines are useful to use:

- Online/Offline backups
- Storage medium
- Filesystem
- Backup software

# My Local Backup Plan

## Software:
- [FreeFileSync](https://freefilesync.org/) to manually backup from [TrueNAS](truenas.com) NAS to USB HDD Manually
- TrueNAS Replication to Backup NAS (does not protect from ransomware)

## Hardware:
- 1x Seagate Ironwolf 4TB 5400RPM
- 2x Seagate Barracuda 2TB 7200RPM
- USB HDD enclosure (with power adapter)

## Alternative software:

- [Borgbackup](https://github.com/borgbackup/borg)
- [UrBackup](https://www.urbackup.org/)
- [Duplicati](https://www.duplicati.com/)

# My Offsite Backup Plan

***OFFSITE BACKUPS SHOULD ALWAYS BE ENCRYPTED!***

## Hetzner Storage Box:

Hetzner storage box is a very affordable backup plan, allowing you to have a offsite backup of your important data.

Using the Hetzner Storage Box BX11 plan you can get 1TB of storage, unlimited traffic and 10 snapshots!

You can then use this however you would like to backup (in my case, BorgBackup). It can be accessed using FTP/FTPS, SFTP/SCP, Rsync/BorgBackup, SMB/CIFS and HTTPS/WebDAV. A more detailed list can be seen [here](https://docs.hetzner.com/robot/storage-box/access/access-overview).

# Other Offsite backup services

***OFFSITE BACKUPS SHOULD ALWAYS BE ENCRYPTED!***

Examples of some other services you can use for offsite backups are:

**Pricing is accurate as of 20th February 2023 - this may change at any point**

- [Google One](https://one.google.com/about/plans?hl=en_GB) (200GB for £24.99/year, 2TB for £79.99/year, 5TB for £199.99/year)
- [Backblaze Personal](https://www.backblaze.com/backup-pricing.html) ("Unlimited", $7/month, $70/year, $130/2 years)
- [Backblaze B2](https://www.backblaze.com/b2/cloud-storage-pricing.html) ($0.005/GB/Month for storage, $0.01/GB for Download)
- [Amazon S3 Glacier](https://aws.amazon.com/s3/storage-classes/glacier/) (Pricing is more complicated, see link [here](https://aws.amazon.com/s3/pricing/))