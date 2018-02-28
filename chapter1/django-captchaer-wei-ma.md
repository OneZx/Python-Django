#### Django-captcha 二维码
[django-captcha](http://django-simple-captcha.readthedocs.io/en/latest/usage.html#installation)

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

##### 将验证码展示到页面
> users/forms.py中

```
from captcha.fields import CaptchaField

class RegisterForm(forms.Form):
    email = forms.EmailField(required=True)
    password = forms.CharField(required=True, min_length=5)
    captcha = CaptchaField()
    
```
