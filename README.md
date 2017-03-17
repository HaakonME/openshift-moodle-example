Moodle on OpenShift
===================

This git repository helps you get up and running quickly w/ a Moodle installation on OpenShift.  

Running Moodle 3.2 on OpenShift
----------------------------

Create an account at https://www.openshift.com and install the client tools (run 'rhc setup' first)

Create a php-5.4 application (you can call your application whatever you want)


	rhc app-create your_app_name php-5.4 postgresql-9.2 cron --namespace your_namespace --from-code=https://github.com/HaakonME/openshift-moodle-example.git -l your@email.address -p your_account_password

That's it, you can now checkout your application at:

	http://your_app_name-$your_namespace.rhcloud.com

You'll be prompted to set an admin password and name your Moodle site the first time you visit this
page.

Notes
=====

GIT_ROOT/.openshift/action_hooks/deploy:
    This script is executed with every 'git push'.  Feel free to modify this script
    to learn how to use it to your advantage.  By default, this script will create
    the database tables that this example uses.

    If you need to modify the schema, you could create a file
    GIT_ROOT/.openshift/action_hooks/alter.sql and then use
    GIT_ROOT/.openshift/action_hooks/deploy to execute that script (make sure to
    back up your application + database w/ 'rhc app snapshot save' first :) )
