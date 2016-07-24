# OpenShift OpenERP quickstart

This quickstart contains an OpenERP installation ready to run on OpenShift. This uses Odoo 9.0 version

## Create your app

First, create an application with PostgreSQL:

```
$ rhc app create <your_app_name> python-2.7 postgresql-9
```

Then, merge and push this repo into your new app.

```
$ cd <your_app_name>/
$ git remote add upstream https://github.com/afarguellesd/openshift-odoo-quickstart.git
$ git pull -s recursive -X theirs upstream 9.0
$ git push
```

Due to the many requirements, you have to run also the next command:

```
rhc app-ssh --app <your_app_name> --command $OPENSHIFT_REPO_DIR/setup
```

That's it!

Before pushing, if you don't want demo data loaded in your instance, delete the **--without-demo** flag from **post_deploy** openshift action hook.
```
sed -i 's/--without-demo=True//' install_scripts/post_deploy
```

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

## HTTPS Routing

The source includes a .htaccess file for routing all request via https

## Upgrade

To use master version pull master on previus commands.


