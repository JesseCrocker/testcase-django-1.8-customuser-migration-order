Django projects that use a custom user model, and install an app that includes a model with a `models.ForeignKey(settings.AUTH_USER_MODEL)` and does not use migrations, will fail to syncdb on Django 1.8
### django == 1.7
``` shell
 ./manage.py migrate                                                      [12:27:54]
Operations to perform:
  Synchronize unmigrated apps: refsuser
  Apply all migrations: admin, myusers, contenttypes, auth, sessions
Synchronizing apps without migrations:
  Creating tables...
    Creating table refsuser_brokenmodel
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
$ ./manage.py migrate                                                      [12:25:52]
Operations to perform:
  Synchronize unmigrated apps: staticfiles, messages, refsuser
  Apply all migrations: admin, myusers, contenttypes, auth, sessions
Synchronizing apps without migrations:
  Creating tables...
    Creating table refsuser_brokenmodel
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
