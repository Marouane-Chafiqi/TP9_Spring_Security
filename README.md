# TP 9 : Authentification en mémoire avec Spring Security

## C'est quoi ce projet

Une petite application web sécurisée avec Spring Security. Les utilisateurs sont écrits directement dans le code (en mémoire), pas dans une base de données. Selon son rôle, chaque utilisateur a accès ou non à certaines pages.

## Outils utilisés

- Java 17 et Maven
- Spring Boot 3.5.11 (Web, Thymeleaf, Security)
- Thymeleaf pour les pages HTML
- IntelliJ IDEA

## Organisation du code

```
config      -> SecurityConfig (règles d'accès, utilisateurs, BCrypt)
web         -> HomeController (les routes)
templates   -> index, login, user_dashboard, admin_dashboard
```

## Comment lancer

1. Ouvrir le projet dans IntelliJ.
2. Lancer `SpringSecurityDemoApplication`.
3. Ouvrir http://localhost:8080/

Pas besoin de base de données pour ce TP.

## Les comptes

| Utilisateur | Mot de passe | Rôles |
|---|---|---|
| user | 1111 | USER |
| admin | 1234 | ADMIN, USER |

Les mots de passe sont cryptés avec BCrypt.

## Les règles d'accès

| URL | Qui peut entrer |
|---|---|
| / | tout le monde |
| /login | tout le monde |
| /user/** | rôle USER |
| /admin/** | rôle ADMIN |
| le reste | utilisateur connecté |

## Mes tests

### 1. La page d'accueil

La page d'accueil est publique. Elle a deux liens : Espace Utilisateur et Espace Administrateur.

<img width="570" height="239" alt="Capture d&#39;écran 2026-11-08 164448" src="https://github.com/user-attachments/assets/4e6e9b65-900b-476a-aed6-f98cd757471f" />


### 2. Mauvais mot de passe

Si on se trompe de nom d'utilisateur ou de mot de passe, la page de connexion revient avec le message "Identifiant ou mot de passe invalide."

<img width="523" height="278" alt="Capture d&#39;écran 2026-11-08 164518" src="https://github.com/user-attachments/assets/56168414-b74f-44ef-a76d-bbed706c8d63" />


<img width="265" height="144" alt="Capture d&#39;écran 2026-11-08 164525" src="https://github.com/user-attachments/assets/671f528e-d74c-417f-81ca-c21202257321" />



### 3. Connexion avec user

Avec `user` / `1111`, on arrive sur l'espace utilisateur. La page affiche "Connecté en tant que : user".

<img width="308" height="174" alt="Capture d&#39;écran 2026-11-08 171804" src="https://github.com/user-attachments/assets/4dd95677-e477-43aa-940f-43faef69c454" />


### 4. Connexion avec admin

Avec `admin` / `1234`, on arrive sur l'espace administrateur. La page affiche "Connecté en tant que : admin".

<img width="381" height="174" alt="Capture d&#39;écran 2026-11-08 171839" src="https://github.com/user-attachments/assets/d20df13a-2ffb-4522-8a3b-19b5214c73b8" />


