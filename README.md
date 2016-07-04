# OpenShift OpenERP quickstart

This quickstart contains an OpenERP installation ready to run on OpenShift. This uses Odoo 9.0 version

## Create your app

First, create an application with PostgreSQL:

```
$ rhc app create <your_app_name> python-2.7 postgresql-9
```

Then, merge and push this repo into your new app. Please be patient, this operation may last for a long time.

```
$ cd <your_app_name>/
$ git remote add upstream https://github.com/afarguellesd/openshift-odoo-quickstart.git
$ git pull -s recursive -X theirs upstream 9.0
$ git push
```

That's it!

Now put your own modules in addons dir and do another 
```
git push
```

Point your browser to [https://your_app_name-$namespace.rhcloud.com](https://<your_app_name>-$namespace.rhcloud.com) and login.
Default credentials are:

```
Username: admin
Password: admin
```

## Upgrade

To use master version pull master on previus commands.


