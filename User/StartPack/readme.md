# Créer une Application users Personnalisée
Si vous prévoyez d'avoir des utilisateurs avec des champs personnalisés (ex : rôle, avatar, bio), il est préférable de créer une application users.

Étapes pour créer l'application users :
## 1. Créer l'application users :
```bash
python manage.py startapp users
```
## 2. Définir un modèle User personnalisé :
   Dans users/models.py, étendez le modèle AbstractUser de Django :
```python
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    bio = models.TextField(blank=True, help_text="Une courte biographie de l'utilisateur")
    avatar = models.ImageField(upload_to="avatars/", blank=True, null=True)
    role = models.CharField(max_length=50, blank=True, choices=[("admin", "Admin"), ("user", "User")])

    def __str__(self):
        return self.username
```
## 3. Configurer Django pour utiliser ce modèle :
Dans settings.py, ajoutez :
```python
AUTH_USER_MODEL = 'users.User'
```
## 4. Appliquer les migrations :
```bash
python manage.py makemigrations users
python manage.py migrate
```
## 5. Utiliser le modèle User personnalisé :
Dans vos autres modèles, importez-le comme suit :
```python
from users.models import User

class CommandTemplate(models.Model):
    name = models.CharField(max_length=200, unique=True, help_text="Nom unique de la commande")
    description = models.TextField(blank=True, help_text="Description de la commande")
    author = models.ForeignKey(User, on_delete=models.CASCADE, related_name="command_templates")
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    # ... autres champs
```

# Avantages :
  - Personnalisation facile des utilisateurs.
  - Ajout de champs supplémentaires sans modifier le modèle de base.

# Inconvénients :
  - Nécessite un peu plus de configuration initiale.
