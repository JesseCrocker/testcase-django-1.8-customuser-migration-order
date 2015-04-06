### django == 1.7
``` shell
$ ./manage.py migrate                                                                                                      [12:13:57]
Operations to perform:
  Synchronize unmigrated apps: notifications
  Apply all migrations: admin, myusers, contenttypes, auth, sessions
Synchronizing apps without migrations:
  Creating tables...
    Creating table notifications_noticetype
    Creating table notifications_noticesetting
    Creating table notifications_noticequeuebatch
  Installing custom SQL...
  Installing indexes...
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying myusers.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying sessions.0001_initial... OK
```

### django == 1.8
``` shell
./manage.py migrate                                                                                                      [12:15:02]
/Users/jesse/python/testapp/lib/python2.7/site-packages/pinax/notifications/compat.py:17: RemovedInDjango19Warning: django.contrib.contenttypes.generic is deprecated and will be removed in Django 1.9. Its contents have been moved to the fields, forms, and admin submodules of django.contrib.contenttypes.
  from django.contrib.contenttypes.generic import GenericForeignKey

/Users/jesse/python/testapp/lib/python2.7/site-packages/django/contrib/sites/models.py:78: RemovedInDjango19Warning: Model class django.contrib.sites.models.Site doesn't declare an explicit app_label and either isn't in an application in INSTALLED_APPS or else was imported before its application was loaded. This will no longer be supported in Django 1.9.
  class Site(models.Model):

Operations to perform:
  Synchronize unmigrated apps: staticfiles, notifications, messages
  Apply all migrations: admin, myusers, contenttypes, auth, sessions
Synchronizing apps without migrations:
  Creating tables...
    Creating table notifications_noticetype
    Creating table notifications_noticesetting
    Creating table notifications_noticequeuebatch
    Running deferred SQL...
Traceback (most recent call last):
  File "./manage.py", line 10, in <module>
    execute_from_command_line(sys.argv)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/__init__.py", line 338, in execute_from_command_line
    utility.execute()
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/__init__.py", line 330, in execute
    self.fetch_command(subcommand).run_from_argv(self.argv)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/base.py", line 390, in run_from_argv
    self.execute(*args, **cmd_options)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/base.py", line 441, in execute
    output = self.handle(*args, **options)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/commands/migrate.py", line 179, in handle
    created_models = self.sync_apps(connection, executor.loader.unmigrated_apps)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/core/management/commands/migrate.py", line 317, in sync_apps
    cursor.execute(statement)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/db/backends/utils.py", line 79, in execute
    return super(CursorDebugWrapper, self).execute(sql, params)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/db/backends/utils.py", line 64, in execute
    return self.cursor.execute(sql, params)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/db/utils.py", line 97, in __exit__
    six.reraise(dj_exc_type, dj_exc_value, traceback)
  File "/Users/jesse/python/testapp/lib/python2.7/site-packages/django/db/backends/utils.py", line 62, in execute
    return self.cursor.execute(sql)
django.db.utils.ProgrammingError: relation "myusers_customuser" does not exist
```
