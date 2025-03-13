
# 1. Instllation Django
``` python
pip install django-bootstrap-v5
pip install Pillow
# pip install whitenoise
```
# 2. START Django
``` python
django-admin startproject Core
```
``` bash
cd .\Core\
```
``` python
django-admin startapp Web  
```

# 2. Setup Django
## in Core\Core\urls.py 
``` python
from django.urls import include, path
from django.conf.urls.static import static
from django.conf import settings

#Add:
path('', include('Web.urls')),

#after urlpatterns = []
+ static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)

```
## in Core\Core\settting.py 

``` python
import os


# Add INSTALLED_APPS = [] Application definition
INSTALLED_APPS = [
    # ....
    'bootstrap5',
    'Web',
]

# Modify 
STATIC_ROOT = BASE_DIR / 'static'

STATIC_URL = 'static/'

STATICFILES_DIRS = [
    "static/media",
    "static/build/",
    "static/images/",
]

MEDIA_ROOT = os.path.join(BASE_DIR, 'static/media') # 'data' is my media folder
MEDIA_URL = '/media/'


# Default CNX
LOGIN_REDIRECT_URL = '/'
LOGOUT_REDIRECT_URL = '/'
LOGIN_URL = '/accounts/login/'

```
## makemigrations & migrate
``` python
py manage.py makemigrations
py manage.py migrate 


```
## createsuperuser Django
``` python
py manage.py createsuperuser
```
## runserver Django
``` python
py manage.py runserver 
```
## Reset database
``` python
python manage.py flush
```
# 3. data

# 4. Help With coding
## CSS
### 1. importez-les dans un fichier principal (par exemple, main.css)
``` css
@import url('reset.css');
@import url('typography.css');
@import url('layout.css');
@import url('components.css');
@import url('utilities.css');
```
### 1. Utiliser des variables CSS 
``` css
/* ========================= */
/* variables : CSS         */
/* ========================= */
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  --font-family: Arial, sans-serif;
  --spacing: 20px;
}

.header {
  background-color: var(--primary-color);
  padding: var(--spacing);
}

.btn-primary {
  background-color: var(--primary-color);
}
```
### 1. Grouper les styles par composants
``` css
/* ========================= */
/* COMPOSANT : CARTE         */
/* ========================= */
.card {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 20px;
}

.card__title {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.card__body {
  font-size: 1rem;
  color: #666;
}
```
### 1. structure logique
``` css
/* ========================= */
/* RESET OU NORMALISATION     */
/* ========================= */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```
### 1. structure logique
