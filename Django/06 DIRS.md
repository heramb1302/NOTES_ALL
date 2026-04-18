
In Django, **`DIRS`** is a configuration setting found within the `TEMPLATES` dictionary in your `settings.py` file. It defines a list of absolute paths (directories) where the Django template engine should look for template files.

Here is a breakdown of why it is used and how to configure it.

### Why do you need `DIRS`?

By default (when the `APP_DIRS` setting is `True`), Django automatically searches for templates inside a `templates` folder within each of your installed apps.

However, you will almost always have project-wide templates that don't belong to a single specific app—such as a shared `base.html` layout, a global navigation bar, or the main homepage.

You use `DIRS` to point Django to a central, project-level `templates` folder that lives outside of any individual app directory.

### How to configure it

In modern Django projects (Django 3.1+), the `BASE_DIR` is defined using Python's `pathlib` module. You can use this to easily point `DIRS` to a `templates` folder in your root project directory.

```python
from pathlib import Path

# Build paths inside the project like this: BASE_DIR / 'subdir'.
BASE_DIR = Path(__file__).resolve().parent.parent

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        # Add your project-level templates directory here:
        'DIRS': [BASE_DIR / 'templates'], 
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```