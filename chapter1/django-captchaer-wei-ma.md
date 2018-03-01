#### 1.Django-captcha 二维码

下载链接 : [django-captcha](http://django-simple-captcha.readthedocs.io/en/latest/usage.html#installation)

> workon 到django的env中

1. Install django-simple-captcha via pip: `pip install  django-simple-captcha`

* Add `captcha` to the `INSTALLED_APPS` in  `settings.py`

* Add an entry to  `urls.py`:

```
# django 1.9

urlpatterns = [
    url(r'^captcha/', include('captcha.urls')),
]


# django 2.0

    from django.urls import path, include

    path("captcha/", include('captcha.urls'))
```

* Run python `manage.py task`

  ```
    makemigrations

    migrage
  ```

  ![](/assets/captcha.jpg)
  
- 生成的表

  ![](/assets/capt.png)
  

#### 2.将验证码展示到页面

> users/forms.py中

```python
# 引入captchaField
from captcha.fields import CaptchaField

class RegisterForm(forms.Form):
    # 此处的email与前端的name保持一致
    email = forms.EmailField(required=True)
    password = forms.CharField(required=True, min_length=5)
    # 应用验证码
    captcha = CaptchaField()
```

#### 3.前端获取验证码
- 前端

![](/assets/cap1.png)

- 后台数据库

![](/assets/33.png)



