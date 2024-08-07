# 🚀 Backup Jenkins data and configurations to external disk

---
> [!NOTE]
> Before starting, ensure you have basic understanding of Linux and Jenkins plugins.

## 🎤 Introduction

It is very important to have Jenkins backup with its data and configurations. It includes job configs, builds logs, plugins, plugin configuration, etc.

Jenkins requires regular patching and plugin updates. During these processes, there is a risk of configuration issues, which could potentially lead to a Jenkins crash.

On the other hand, Jenkins is not required to run continuously, some interruptions can be accaptable. Because of that, we usually use spot instance for cost-optimization, with an external disk, we can ensure our CI server could always being restored easily.

This workshop will cover the following two ways to back up Jenkins:

- Backup Jenkins with Thin Backup plugin
- Backup Jenkins using Disk snapshots

---

## 📝 Prerequisites

1. You must have an already installed Jenkins on a Linux.
2. Your Linux machine must have mounted an external disk on a path, ensure jenkins user has permissions to write data on it.

---

## 👉 Details

### 1. Backup Jenkins with Thin Backup plugin

#### Step 1: Install Thin plugin

- Go to __Manage Jenkins__
![1_1](/1_Backup/1_1.png)
- Scroll down and select __Plugins__
![1_2](/1_Backup/1_2.png)
- Click __Available plugins__ and search for __ThinBackup__
![1_3](/1_Backup/1_3.png)
- Select the extension and click __Install__
![1_4](/1_Backup/1_4.png)
- Restart Jenkins

#### Step 2: ThinBackup configuration

After successfully install the plugin, we have to configure it

- Go to __Manage Jenkins__, select __System__ section:
![1_5](/1_Backup/1_5.png)
- Scroll down to section __ThinBackup Configuration__:

  - Fill in as we wish:

> ![NOTE]
> Backup directory is where we mounted our external directory

![1_6](/1_Backup/1_6.png)
![1_7](/1_Backup/1_7.png)

- Click __Save__
![1_8](/1_Backup/1_8.png)
- Later, if you want to restore, you can easily do as follow:
  - Select __Manage_Jenkins__, then scroll down, select __ThinBackup__:
![1_9](/1_Backup/1_9.png)
  - Click __Restore__:
![1_10](/1_Backup/1_10.png)
  - Choose your backup:
![1_11](/1_Backup/1_11.png)

### 2. Backup Jenkins using Disk snapshots

As you know, Jenkins store all of its data and configuration in */var/lib/jenkins/*, we just need to make a symlink from it to where we mount the external disk, here we suppose that it is */data/*

- If you have existing data, move all data from */var/lib/jenkins/* to */data/*
- Symlink */var/lib/jenkins/* to */data/*
- Restart Jenkins
- After that, we can make daily snapshot of the external disk. If you're using EBS, it has a feature called EBS Snapshot.

For some reason, if your Jenkins server crashes or data gets corrupted, create a new disk from the existing snapshot backup and replace it in the Jenkins server. Jenkins will have all the data from the snapshot point in time backup.
