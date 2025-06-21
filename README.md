# 🚀 PHP API Client

Une bibliothèque PHP simple et efficace pour interagir avec des API RESTful, conçue pour simplifier vos requêtes HTTP (GET, POST, PUT, DELETE). Idéale pour les développeurs PHP qui ont besoin d'une solution rapide et robuste pour leurs intégrations d'API.

---

## ✨ Fonctionnalités

* **Opérations CRUD Complètes**: Supporte les méthodes HTTP `GET`, `POST`, `PUT`, et `DELETE`.
* **Gestion des Requêtes**: Gère l'encodage des données JSON et les en-têtes `Content-Type`.
* **Options cURL Personnalisables**: Permet de passer des options cURL supplémentaires pour une flexibilité maximale (gestion des certificats SSL, timeouts, etc.).
* **Gestion des Erreurs**: Inclut une gestion robuste des erreurs cURL et des codes de statut HTTP pour des retours clairs.
* **Facile à Utiliser**: Une API statique simple pour des appels de fonction directs.

---

## 🛠️ Installation

Cette bibliothèque est conçue pour être facilement installable via Composer. 
Elle nécessite les extensions PHP standards comme `cURL`.

1.  **Exigence :** Assurez-vous d'avoir [Composer](https://getcomposer.org/) installé sur votre système.
2.  **Ajoutez la dépendance** à votre projet via Composer :

    ```bash
    composer require beriyack/apiclient
    ```

    Cela installera la librairie dans votre dossier `vendor/` et mettra à jour l'autoloader de Composer.

3.  **Utilisez l'autoloader de Composer** dans votre projet :

    ```php
    <?php
    require_once 'vendor/autoload.php';

    use Beriyack\ApiClient;
    ?>
    ```

---

## 📖 Utilisation

Toutes les méthodes de la classe `ApiClient` sont statiques pour chaque type de requête HTTP, ce qui les rend faciles à appeler directement.

### Récupérer des données (GET)

```php
use Beriyack\ApiClient;

try {
    $data = ApiClient::get('https://jsonplaceholder.typicode.com/posts/1');
    print_r($data);
} catch (Exception $e) {
    echo "Erreur : " . $e->getMessage();
}
```

### Créer une ressource (POST)

```php
use Beriyack\ApiClient;

try {
    $newPost = [
        'title' => 'Mon Nouveau Titre',
        'body' => 'Contenu de mon nouveau post.',
        'userId' => 1
    ];
    $response = ApiClient::post('https://jsonplaceholder.typicode.com/posts', $newPost);
    print_r($response);
} catch (Exception $e) {
    echo "Erreur : " . $e->getMessage();
}
```

### Mettre à jour une ressource (PUT)

```php
use Beriyack\ApiClient;

try {
    $updatedPost = [
        'id' => 1,
        'title' => 'Titre Mis à Jour',
        'body' => 'Nouveau contenu pour le post.',
        'userId' => 1
    ];
    $response = ApiClient::put('https://jsonplaceholder.typicode.com/posts/1', $updatedPost);
    print_r($response);
} catch (Exception $e) {
    echo "Erreur : " . $e->getMessage();
}
```

### Supprimer une ressource (DELETE)

```php
use Beriyack\ApiClient;

try {
    $response = ApiClient::delete('https://jsonplaceholder.typicode.com/posts/1');
    print_r($response); // Souvent vide ou un objet vide pour une suppression réussie
} catch (Exception $e) {
    echo "Erreur : " . $e->getMessage();
}
```

### Options cURL avancées

Vous pouvez passer un tableau d'options cURL supplémentaires à toutes les méthodes.

```php
use Beriyack\ApiClient;

try {
    $options = [
        CURLOPT_TIMEOUT => 10, // Timeout de 10 secondes
        CURLOPT_SSL_VERIFYPEER => false // ATTENTION: À utiliser avec précaution et jamais en production sans bonne raison !
    ];
    $data = ApiClient::get('https://some-api.com/data', $options);
    print_r($data);
} catch (Exception $e) {
    echo "Erreur : " . $e->getMessage();
}
```

---

## 🤝 Contribution

Les contributions sont les bienvenues \! Si vous avez des idées d'améliorations, de nouvelles fonctionnalités ou des corrections de bugs, n'hésitez pas à ouvrir une *issue* ou à soumettre une *pull request*.

---

## 📄 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](https://www.google.com/search?q=LICENSE) pour plus de détails.

-----

## 📧 Contact

Pour toute question ou suggestion, vous pouvez me contacter via [Beriyack](https://github.com/Beriyack).

-----
