# Deployment

### Software deployment is all of the activities that make a software system available for use:

* Copy/clone code
* Run composer, npm, gulp
* Run migrations
* Reload the web server
* Notify about the deployment

---

# Deployment Goals

---

# 1. One-click/command Deployment

![inline](images/push.gif)

---

# 2. Anytime/anywhere (Anyone with permission)

---

# 3. Zero Downtime Deployment

---

# 4. Reliable Rollbacks

![inline](images/rollback.gif)

---

# 5. Repeatable

<!-- Reusable and reproducible -->

---

# 6. Scalable

---

# Why automated deployments?

---

# 1. Less error-prone

![inline](images/well.gif)

### Just run this command they said. It’s straightforward they said. It can’t go wrong they said.

---

# 2. More time for developing software and less time doing stuff like this...

![inline](images/debugging.gif)

---

# 3. Release more frequently

---

![inline 200%](images/capistrano.png)

# A remote server automation and deployment tool written in Ruby.

## [http://capistranorb.com/](http://capistranorb.com/)

---

![inline 200%](images/capistrano.png)

* Uses [SSH](http://www.openssh.com/)
* Does everything in parallel
* Supports Git, SVN, Mercurial
* Easy to integrate with PHP projects
* Mostly used with rails projects

---

# Requirements

* Ruby >= 1.9.3
* SSH access to all servers with public keys (recommended)

---

# Terminologies

* Task
* Recipe
* Namespace
* Role
* Stages

---

# Task

### A concrete set of commands to execute.

---

# Recipe

### A collection of tasks.

---

# Namespace

### Organizes tasks within recipes and avoids naming collisions.

---

# Role

### Servers can have different roles like: app, demo, web

---

# Stages

### Refers to different set of environments (servers): dev, uat, qa, staging, production

### Can also include configuration per stage or even different tasks.

---

# Other Alternatives

* Fabric - Python
* Mina - Ruby
* Rocketeer - PHP
* Shipit - Javascript
* Deployer - PHP
* CI Services like Travis CI, Circle CI, Jenkins

---

# Demo

---

# Thank you

![inline](images/friday.gif)

### Let's hope your deployments won't be like this from now on.
