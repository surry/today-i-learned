# Generating Django Secret Keys

Django can generate a random SECRET_KEY for your project when it is created via `django-admin startproject`.
If you've skipped that step, you can generate an appropriate key later on using the same code as `django-admin`:

```
$ python
>>> import django.core.management.utils as utils
>>> utils.get_random_secret_key()
```

See the [Django documentation on SECRET_KEY](https://docs.djangoproject.com/en/1.11/ref/settings/#secret-key) for
more information, including what metadata is invalidated when the `SECRET_KEY` is rotated.
