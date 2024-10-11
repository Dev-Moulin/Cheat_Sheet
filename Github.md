# Cheatsheet Git


## Configuration de Git
```bash
# Configure ton nom d'utilisateur Git
git config --global user.name "TonNom"

# Configure ton email Git
git config --global user.email "ton.email@example.com"

# Vérifie la configuration actuelle
git config --list

```

---
## Initialiser un dépôt Git
```bash
# Initialise un nouveau dépôt dans le dossier actuel 
git init
```

---
# Statut du dépôt

```bash

git status                                       # Vérifie l'état des fichiers modifiés, ajoutés ou non suivis
```

---
# Ajouter des fichiers au suivi

```bash

git add nom_du_fichier                           # Ajoute un fichier spécifique pour le suivi
git add .                                        # Ajoute tous les fichiers pour le suivi
```

---
# Sauvegarder les changements (commits)
```bash

git commit -m "Message du commit"                # Crée un commit avec un message
git commit -am "Message du commit"               # Ajoute et commit en une seule commande
```

---
# Historique des commits
```bash

git log                                          # Affiche l'historique des commits
git log --oneline                                # Affiche l'historique condensé en une ligne par commit
```

---
# Gérer les branches
```bash

git branch                                       # Liste toutes les branches
git branch nom_de_branche                        # Crée une nouvelle branche
git checkout nom_de_branche                      # Bascule sur une branche
git checkout -b nom_de_branche                   # Crée une branche et bascule dessus
git branch -d nom_de_branche                     # Supprime une branche
```

---
# Fusionner des branches
```bash
git merge nom_de_branche                         # Fusionne une branche dans la branche actuelle
```

---
# Annuler des changements
```bash
git checkout -- nom_du_fichier                   # Annule les changements locaux (fichiers non encore ajoutés)
git reset nom_du_fichier                         # Annule les ajouts (retire un fichier de l'index)
git reset                                        # Réinitialise tout l'index (avant commit)
git reset --soft HEAD^                           # Annule le dernier commit (mais conserve les changements)
git reset --hard HEAD^                           # Annule le dernier commit et les changements associés
```

---
# Synchronisation avec un dépôt distant
```bash
git clone https://url_du_depot.git               # Clone un dépôt distant
git remote add origin https://url_du_depot.git   # Ajoute un dépôt distant
git push origin main                             # Pousse les changements locaux vers le dépôt distant
git pull origin main                             # Tire les mises à jour depuis le dépôt distant
```


# Remplacer la branche locale par celle du dépôt distant
```bash
git fetch origin                                 # Récupère les modifications du dépôt distant
git reset --hard origin/main                     # Réinitialise la branche locale avec la version distante
```

---
# Stash (mettre de côté les modifications)
```bash
git stash                                        # Enregistre temporairement les modifications sans les committer
git stash pop                                    # Applique les modifications mises en stash
git stash list                                   # Liste les stashes
```

---
# Afficher les différences
```bash
git diff                                         # Affiche les différences entre les fichiers modifiés et l'index
git diff --cached                                # Affiche les différences entre l'index et le dernier commit
```

---
# Suppression de fichiers suivis
```bash
git rm nom_du_fichier                            # Supprime un fichier du suivi et du système de fichiers
git rm --cached nom_du_fichier                   # Supprime un fichier du suivi sans le supprimer du système de fichiers
```
