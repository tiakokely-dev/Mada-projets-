# PAN-AFRICA VISION 2030

Application web de vision stratégique pour l'Afrique, propulsée par l'IA.

## 🚀 Lancement Rapide (Termux/Android)

Ce guide explique comment lancer l'application sur **Termux** (Android) avec ou sans environnement Debian.

### Option 1 : Lancement Direct dans Termux (Recommandé)

C'est la méthode la plus simple et la plus rapide.

1.  **Ouvrez Termux** sur votre Android.
2.  **Mettez à jour les paquets** :
    ```bash
    pkg update && pkg upgrade -y
    ```
3.  **Installez PHP** :
    ```bash
    pkg install php -y
    ```
4.  **Accédez au dossier du projet** (adaptez le chemin si nécessaire) :
    ```bash
    cd /storage/emulated/0/Download/PAN_AFRICA_VISION
    # OU si vous avez cloné le projet ailleurs
    cd ~/PAN_AFRICA_VISION
    ```
    *Note : Si vos fichiers sont dans un dossier différent, utilisez `cd` pour y aller.*
5.  **Lancez le serveur web** :
    ```bash
    php -S 0.0.0.0:8080
    ```
    *Le serveur écoute maintenant sur toutes les interfaces réseau.*
6.  **Ouvrez votre navigateur** (Chrome, Firefox, etc.) sur Android et tapez :
    ```
    http://localhost:8080
    ```
    ou
    ```
    http://127.0.0.1:8080
    ```

### Option 2 : Via un environnement Debian (Proot-Distro)

Si vous préférez utiliser une distribution Debian complète dans Termux.

1.  **Installez `proot-distro`** dans Termux :
    ```bash
    pkg install proot-distro -y
    ```
2.  **Installez Debian** :
    ```bash
    proot-distro install debian
    ```
3.  **Lancez Debian** :
    ```bash
    proot-distro login debian
    ```
4.  **Dans Debian, installez PHP** :
    ```bash
    apt update && apt install php -y
    ```
5.  **Naviguez vers votre projet** (le stockage Android est monté dans `/sdcard`) :
    ```bash
    cd /sdcard/Download/PAN_AFRICA_VISION
    # Adaptez le chemin selon l'emplacement réel de vos fichiers
    ```
6.  **Lancez le serveur** :
    ```bash
    php -S 0.0.0.0:8080
    ```
7.  **Ouvrez votre navigateur** Android et allez sur :
    ```
    http://localhost:8080
    ```

## 🖥️ Lancement sur PC (Linux/Mac/Windows WSL)

1.  Ouvrez un terminal dans le dossier du projet.
2.  Lancez le serveur PHP :
    ```bash
    php -S localhost:8080
    ```
3.  Ouvrez votre navigateur : `http://localhost:8080`

## 🛠️ Dépannage

*   **"Command not found" (php)** : Assurez-vous que PHP est bien installé (`pkg install php` sur Termux ou `apt install php` sur Debian).
*   **Page blanche ou erreur 500** : Vérifiez les logs dans le terminal où le serveur tourne. Assurez-vous que les permissions d'écriture sont correctes pour le dossier `cache/` et `logs/`.
    ```bash
    chmod 755 cache logs
    ```
*   **Impossible de se connecter** :
    *   Vérifiez que le serveur tourne bien (message "Development Server ... started").
    *   Sur Termux, assurez-vous d'avoir accordé la permission de stockage si les fichiers sont sur le téléphone : `termux-setup-storage`.
    *   Essayez de redémarrer le serveur.

## 📄 Structure du projet

- `index.php` : Point d'entrée principal.
- `mistral_proxy.php` : Proxy pour les appels API (nécessite une clé API valide pour fonctionner pleinement).
- `app.js` : Logique frontend.
- `style.css` : Styles de l'application.
- `V2/`, `V3/`, `V4/` : Versions précédentes ou alternatives.

## ⚠️ Note sur l'API

L'application utilise un proxy pour communiquer avec l'IA Mistral. Les clés API incluses sont des exemples. Pour une fonctionnalité complète, remplacez-les par vos propres clés dans `mistral_proxy.php`.
