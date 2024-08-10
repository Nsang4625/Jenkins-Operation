# 🚀 Jenkins security's aspects

---
> [!NOTE]
> Before starting, ensure you have basic understanding of Linux and Jenkins plugins.

## 🎤 Introduction

Jenkins user management involves controlling access and permissions within the Jenkins environment. It allows administrators to create, configure, and manage user accounts, defining roles and privileges to ensure that users have appropriate access to perform their tasks while maintaining the security and integrity of the Jenkins system.

This workshop will guide you how to manage users and roles in Jenkins.

## 📝 Prerequisites

You must have an already installed Jenkins on a machine(with any OS).

## 👉 Details

### 1. Install required plugin

- Go to __Manage Jenkins__
![1_1](/1_Backup/1_1.png)
- Scroll down and select __Plugins__
![1_2](/1_Backup/1_2.png)
- Click __Available plugins__ and search for __Role-based__
![3_1](./3_1.png)
- Select the extension and click __Install__
![3_2](./3_2.png)
- Restart Jenkins

### 2. Enable Role-based authorization

- Go to __Manage Jenkins__, scroll down and select __Security__:
![3_3](./3_3.png)
- Under __Authorization__ section, select __Role-Based Strategy__, then click __Save__:
![3_4](./3_4.png)

### 3. Manage users

- To create a new user in Jenkins:
  - On our __Dashboard__, select __Manage Jenkins__ and then choose __Users__ under __Security__ section:
![3_5](./3_5.png)
  - Select __Create user__: 
![3_6](./3_6.png)
  - Enter your new user's information, then select __Create user__:
![3_7](./3_7.png)
- To update or delete user, select:
![3_8](./3_8.png)

### 4. Manage roles

- Go to __Manage and Assign Roles__:
![3_9](./3_9.png)
- To create a new role, select __Manage Roles__:
![3_10](./3_10.png)
- Here I will create a role for developer, called *dev* which grant permissions for accessing Job and View:
![3_11](./3_11.png)
![3_12](./3_12.png)
- To assign this role for *tndev* user, do as follow:
![3_13](./3_13.png)
![3_14](./3_14.png)
![3_15](./3_15.png)
![3_16](./3_16.png)
- Result:
![3_17](./3_17.png)