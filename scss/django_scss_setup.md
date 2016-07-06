using torchbox/django-libsass

1. pip install django-compressor

2. required settings:
INSTALLED_APPS = [
    ...
    'compressor', # can go anywhere in list
]

STATICFILES_FINDERS = [
    ...
    'compressor.finders.CompressorFinder', # so can use static file template tag instide compressor template tag
]

COMPRESS_ENABLED = True # so compression happens on dev server (default -> only on production server)

3. pip install django-libsass

4. required settings:
COMPRESS_PRECOMPILERS = (
    ('text/x-scss', 'django_libsass.SassCompiler'),
)

5. in template file:
{% load staticfiles compress %}

...

{% compress css %}
    <link rel="stylesheet" type="text/x-scss" href="{% static "scss/main.scss" %}" />
{% endcompress %}
