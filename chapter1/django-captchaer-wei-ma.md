#### Django-captcha 二维码

> workon 到django的env中

- Install django-simple-captcha via pip: `pip install  django-simple-captcha`

- Add `captcha` to the `INSTALLED_APPS` in your `settings.py`

- Add an entry to your `urls.py`:

```
# django 1.9

urlpatterns = [
    url(r'^captcha/', include('captcha.urls')),
]


# django 2.0

	from django.urls import path, include

    path("captcha/", include('captcha.urls'))
```
- Run python `manage.py task`
```
	makemigrations

	migrage
```
![](/assets/captcha.jpg)