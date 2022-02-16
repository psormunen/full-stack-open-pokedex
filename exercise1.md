How to setup CI in PHP-project (example)
=======================================

With 6 people actively working on same project and with each of them working on a separate areas of interest which may sometimes overlap due to various reasons - then some common quality assurances can be achieved with well thought out CI-pipeline.

In this scenario development-to-production stages could be broken into following segments:

1. Individual developer working on a feature on his/her development environment (e.g. virtualised Linux server environment on top of Windows machine).
2. Github repository to which every developer pushes new commits. When new commits arrive then server-side git-hook is run that makes a POST-request to Jenkins-server
3. Jenkins-server runs predefined series of shell-scripts, that consists of:
 * git pull to our target branch (i.e. main)
 * updates our dependencies
 * runs our linting-tests (phplint)
 * runs our PHPUnit tests
 * if everything has gone well this far, then copies the codebase to our target server and then logins to it and runs procedures that must be run locally
4. If everything went well, project has now been updated on target server and everything should be working properly


Utilizing a cloud-based environment
-----------------------------------
If there are only 6 developers and company otherwise consists from small number of sales and/or support team, it should be quite sensible solution to specialize in code creation rather than to invest, protect, backup and maintain own server hardware and it's OS and virtualised environments. This option should be on the table when multiple providers for relatively cheap cloud based environments exists with a proven track record. So, it most likely would be the most worry free solution for this development team. Usually, it's also rather trivial to scale up these services when needed. And I suppose that the highly specialized nature of the cloud providers should also positively add to overall security of the projects implementation.
