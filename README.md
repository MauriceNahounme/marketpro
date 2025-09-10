# MarketPro

Application web de gestion de produits développée avec ASP.NET Core MVC et .NET 9.

## Description

MarketPro est une application de gestion de catalogue produits qui permet de :
- Créer, modifier et supprimer des produits
- Rechercher des produits par nom ou catégorie
- Consulter les détails des produits
- Gérer un inventaire simple avec nom, description, prix et catégorie

## Technologies utilisées

- **Framework** : ASP.NET Core MVC (.NET 9.0)
- **Base de données** : Entity Framework Core avec InMemory Database
- **Frontend** : Razor Views, Bootstrap, jQuery
- **Architecture** : MVC (Model-View-Controller)

## Prérequis

- .NET 9.0 SDK
- Visual Studio 2022 ou Visual Studio Code
- Navigateur web moderne

## Installation et lancement

1. **Cloner le projet**
   ```bash
   git clone <url-du-repo>
   cd marketpro
   ```

2. **Restaurer les dépendances**
   ```bash
   dotnet restore
   ```

3. **Lancer l'application**
   ```bash
   dotnet run
   ```

4. **Accéder à l'application**
   - Ouvrir le navigateur à l'adresse : `https://localhost:5001` ou `http://localhost:5000`

## Structure du projet

```
marketpro/
├── Controllers/           # Contrôleurs MVC
│   ├── HomeController.cs
│   └── ProductController.cs
├── Models/               # Modèles de données
│   ├── Product.cs
│   ├── ApplicationDbContext.cs
│   └── ErrorViewModel.cs
├── Views/                # Vues Razor
│   ├── Home/
│   ├── Product/
│   └── Shared/
├── wwwroot/              # Fichiers statiques (CSS, JS, images)
├── Properties/
│   └── launchSettings.json
├── Program.cs            # Point d'entrée de l'application
└── marketpro.csproj      # Configuration du projet
```

## Fonctionnalités

### Gestion des produits
- **Liste des produits** : Affichage de tous les produits avec recherche
- **Création** : Ajout de nouveaux produits avec validation
- **Modification** : Édition des informations produit
- **Suppression** : Suppression avec confirmation
- **Détails** : Vue détaillée d'un produit

### Modèle Product
```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }        // Requis
    public string Description { get; set; }
    public decimal Price { get; set; }      // > 0.01
    public string Category { get; set; }
}
```

## Configuration

### Base de données
L'application utilise une base de données en mémoire (InMemory Database) configurée dans `Program.cs` :
```csharp
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseInMemoryDatabase("MarketProDb"));
```

### Paramètres de lancement
Les ports et paramètres de développement sont configurés dans `Properties/launchSettings.json`.

## Développement

### Ajouter une nouvelle fonctionnalité
1. Créer/modifier le modèle dans `Models/`
2. Mettre à jour le DbContext si nécessaire
3. Créer/modifier le contrôleur dans `Controllers/`
4. Créer/modifier les vues dans `Views/`

### Structure MVC
- **Models** : Logique métier et accès aux données
- **Views** : Interface utilisateur (Razor)
- **Controllers** : Logique de contrôle et navigation

## Commandes utiles

```bash
# Compiler le projet
dotnet build

# Lancer en mode développement
dotnet run

# Publier l'application
dotnet publish -c Release

# Nettoyer les fichiers de build
dotnet clean
```

## Licence

Projet éducatif - ESTIAM

## Auteur

Maurice - Étudiant ESTIAM