### 1. **Variables locales**


```ruby
defined? count
"local-variable"
```



- **Portée** : Les **variables locales** sont accessibles uniquement dans le bloc de code où elles sont définies (comme à l'intérieur d'une méthode ou d'un bloc).
- **Syntaxe** : Une variable locale commence par une lettre minuscule ou un underscore `_` (comme `count` dans ton exemple).

#### Exemple :

```ruby
def calculer   count = 10  # Variable locale   puts count  # On peut accéder à count dans cette méthode end  calculer  # Affiche 10 puts count  # Erreur : count n'existe pas en dehors de la méthode
```

- **Utilité** : Les variables locales sont utilisées pour stocker des valeurs temporaires et n'affectent que la partie du code où elles sont définies. Elles sont utiles pour éviter que des valeurs soient accessibles ou modifiées ailleurs dans le programme.

### 2. **Variables d'instance (@)**

```ruby
defined? @id "instance-variable"
```

- **Portée** : Les **variables d'instance** appartiennent à une **instance** d'une classe (un objet). Chaque objet d'une classe peut avoir ses propres variables d'instance.
- **Syntaxe** : Elles commencent par un `@` (comme `@id` dans ton exemple).

#### Exemple :

```ruby
class Utilisateur   def initialize(nom, id)     @nom = nom  # Variable d'instance     @id = id  # Variable d'instance   end    def afficher_id     puts @id  # On peut accéder à @id dans toute l'instance   end end  u1 = Utilisateur.new("Alice", 1) u2 = Utilisateur.new("Bob", 2)  u1.afficher_id  # Affiche 1 u2.afficher_id  # Affiche 2
```

- **Utilité** : Elles sont utilisées pour stocker des informations spécifiques à chaque instance d'une classe. Par exemple, dans une application avec plusieurs utilisateurs, chaque utilisateur pourrait avoir une variable `@id` différente, propre à lui.

### 3. **Variables de classe (@@)**

ruby

```ruby
defined? @@name "class variable"
```

- **Portée** : Les **variables de classe** sont partagées par **toutes les instances** d'une classe. Contrairement aux variables d'instance, qui sont propres à chaque objet, les variables de classe sont globales à la classe et à ses instances.
- **Syntaxe** : Elles commencent par `@@` (comme `@@name`).

#### Exemple :

```ruby
class Utilisateur   @@nombre_utilisateurs = 0  # Variable de classe    def initialize(nom)     @nom = nom     @@nombre_utilisateurs += 1  # On incrémente chaque fois qu'un utilisateur est créé   end    def self.nombre_total     @@nombre_utilisateurs  # Méthode de classe qui retourne la variable de classe   end end  u1 = Utilisateur.new("Alice") u2 = Utilisateur.new("Bob")  puts Utilisateur.nombre_total  # Affiche 2, car 2 utilisateurs ont été créés
```

- **Utilité** : Les variables de classe sont utiles lorsque tu veux partager une information entre toutes les instances d'une classe. Par exemple, garder une trace du nombre total d'objets créés dans une classe.

### 4. **Variables globales ($)**

```ruby
defined? $version "global-variable"
```

- **Portée** : Les **variables globales** sont accessibles **partout dans le programme**, quelle que soit la classe, la méthode ou le module. Leur portée est donc très large.
- **Syntaxe** : Elles commencent par un signe `$` (comme `$version`).

#### Exemple :

```ruby
$version = "1.0"  # Variable globale  class Utilisateur   def afficher_version     puts "Version: #{$version}"  # On peut accéder à $version ici   end end  u = Utilisateur.new u.afficher_version  # Affiche "Version: 1.0"
```

- **Utilité** : Les variables globales sont rarement utilisées car elles peuvent rendre le code difficile à maintenir. Elles sont pratiques dans des cas où tu as vraiment besoin d'une valeur accessible partout, mais elles doivent être utilisées avec prudence pour éviter des conflits de noms et des erreurs difficiles à déboguer.

### 5. **Constantes**

```ruby
defined? PI "constant"
```

- **Portée** : Une **constante** est une variable dont la valeur ne change pas. Elle est accessible dans toute la classe ou le module où elle est définie, mais elle peut aussi être accessible globalement si elle est définie au niveau supérieur.
- **Syntaxe** : Les constantes commencent par une **lettre majuscule** (comme `PI`).

#### Exemple :

```ruby
PI = 3.14159  # Constante globale  class Cercle   def initialize(rayon)     @rayon = rayon   end    def perimetre     2 * PI * @rayon  # Utilisation de la constante PI   end end  cercle = Cercle.new(5) puts cercle.perimetre  # Affiche le périmètre : 31.4159
```

- **Utilité** : Les constantes sont utilisées pour les valeurs qui ne doivent pas changer au cours du programme, comme `PI` dans le cas des calculs mathématiques. Elles permettent de rendre le code plus clair et d'éviter des erreurs liées à des valeurs qui changent par accident.

### Résumé de l'utilisation de ces variables :

- **Variables locales** : Pour les données temporaires, accessibles uniquement dans une méthode ou un bloc.
- **Variables d'instance (`@`)** : Pour des données spécifiques à chaque objet (instance). Chaque objet a sa propre version de ces variables.
- **Variables de classe (`@@`)** : Partagées par toutes les instances d'une classe. Utiles pour des informations communes à tous les objets (par exemple, un compteur d'objets).
- **Variables globales (`$`)** : Accessibles partout dans le programme. À utiliser avec prudence.
- **Constantes** : Des valeurs fixes qui ne doivent pas changer. Utilisées pour des informations qui sont censées rester constantes tout au long du programme.
