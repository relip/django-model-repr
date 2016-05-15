# django-model-repr
`django-model-repr` is a django library that overrides Model's `__repr__` and provides more detailed information with less effort.


## Installation

```sh
pip install django-model-repr
```

Add `django_model_repr` **in top of** `INSTALLED_APPS` in your `settings.py`:

```
INSTALLED_APPS = (
  "django_model_repr",
  # ...
  # ...
)
```

This library monkey-patches the django standard library `django.db.models.Model`. It means libraries like `django.contrib.auth` inherit `django.db.models.Model` to create their own models, putting `django_model_repr` somewhere in the middle of the `INSTALLED_APPS` can cause errors.

## Output
```
<User
    id: 2
    password: bcrypt_sha256$
    last_login: 2016-05-14 11:44:13.067599+00:00
    is_superuser: True
    email: admin@relip.org
    is_staff: True
    is_active: True
    date_joined: 2016-04-30 18:35:18.032927+00:00
    name:
    password_hint:
    groups: auth.Group.None
    user_permissions: auth.Permission.None
>
```

## Settings

### `MODEL_REPR_MONKEY_PATCHING`

Default: `True`

By default, it monkey-patches automatically when initializing. Setting this to `False` you can manually choose which model to be overrided. Import `django_model_repr.models.Model` and change your model to inherit it.
