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

> users/views.py 中

```
from .forms import LoginForm, RegisterForm

class RegisterView(View):
    def get(self, request):
        # 添加验证码
        register_form = RegisterForm()
        return render(request, 'register.html', {'register_form':register_form})
```
> register.html 中

![](/assets/a1.png)

---
#### 3.前端获取验证码
- 前端
    - 隐藏的hashkey被传到后台进行验证
    
![](/assets/cap1.png) 
    
- 后台数据库
    - 后台会将输入的验证码和hashkey一起比对
![](/assets/33.png)

#### 4.编写register view的后台逻辑


