## User create from django
djangoでデフォルトの設定でユーザーを作成する方法  

```myapp/view.py
from django.contrib.auth.models import User
from django.contrib.auth.forms import UserCreationForm
from django.urls import reverse
from django.views.generic.edit import CreateView

class AccountCreateView(CreateView):
  model = User
  form_class = UserCreationForm

  def get_success_url(self):
    return reverse('login') # urls.pyのnameを指定
```

```myapp/urls.py
urlpatterns = pattern(
  url(r'user_creation$', views.AccountCreateView.as_view()),
)
```

これで、デフォルトのユーザー作成フォームができる。  

### Customize user create
カスタマイズしたユーザー作成を作る方法  

1. 使用するフォームを変えたい場合
  `UserCreationForm`を継承し、新しいフォームを`form_class`に設定する  
2. 使用するモデルを変更したい場合
  `User`を継承し、新しいモデルを`model`に設定する  

### from django.views.generic.edit import CreateView
私が調べた限り、`CreateView`のパスが複数あるようだ。  
どれが良いかは、各自調べて使うように。  

    from django.views.generic.edit import CreateView
    from django.views.generic import CreateView

