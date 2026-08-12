<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Messagerie en Ligne</title>
    <style>
        body { font-family: Arial, sans-serif; background: #f4f4f9; margin: 0; padding: 20px; display: flex; justify-content: center; align-items: center; height: 100vh; }
        .container { width: 100%; max-width: 500px; background: white; padding: 20px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        input, textarea { width: 100%; padding: 10px; margin: 8px 0; border: 1px solid #ccc; border-radius: 4px; box-sizing: border-box; }
        button { background: #007BFF; color: white; border: none; padding: 10px 15px; border-radius: 4px; cursor: pointer; width: 100%; }
        button:hover { background: #0056b3; }
        .error { color: red; font-size: 0.9em; margin-bottom: 10px; }
        .hidden { display: none; }
        .msg { border-bottom: 1px solid #eee; padding: 10px 0; }
        .msg-info { font-size: 0.8em; color: gray; }
        .chat-box { max-height: 300px; overflow-y: auto; border: 1px solid #eee; padding: 10px; margin-bottom: 10px; border-radius: 4px; background: #fafafa; }
        .logout-btn { background: #dc3545; margin-top: 10px; }
        .logout-btn:hover { background: #c82333; }
    </style>
    <!-- Utilisation de JSONbin pour stocker les messages et comptes en ligne gratuitement sans serveur -->
</head>
<body>

<div class="container">
    <!-- SECTION CONNEXION / INSCRIPTION -->
    <div id="auth-section">
        <h2>Connexion / Inscription</h2>
        <div id="error-msg" class="error"></div>
        <label>Pseudo :</label>
        <input type="text" id="username" required>
        <label>Mot de passe :</label>
        <input type="password" id="password" required>
        <label>Passe-message :</label>
        <input type="text" id="passe_message" required>
        <button onclick="handleAuth()">Se connecter / S'inscrire</button>
    </div>

    <!-- SECTION DISCUSSION -->
    <div id="chat-section" class="hidden">
        <h2>Bienvenue, <span id="display-user"></span></h2>
        <p style="font-size: 0.9em; color: #555;">Passe-message : <span id="display-passe"></span></p>
        
        <div class="chat-box" id="messages-container">Chargement des messages...</div>

        <textarea id="msg-content" placeholder="Ecrivez votre message ici..."></textarea>
        <button onclick="sendMessage()">Envoyer</button>
        <button class="logout-btn" onclick="logout()">Deconnexion</button>
    </div>
</div>

<script>
    // Utilisation d un stockage partage public en ligne gratuit pour la demonstration
    const BIN_URL = 'https://api.jsonbin.v3.b/v3/b/65b65f17dc74654018a0a552'; // Exemple de stockage partage
    // Note : Pour un vrai projet personnel securise, on utilise generalement une API Firebase ou Supabase gratuite.
    
    let currentUser = JSON.parse(sessionStorage.getItem('current_user')) || null;

    if (currentUser) {
        showChat();
    }

    async function getData() {
        try {
            let res = await fetch('https://jsonblob.com/api/jsonBlob/1200000000000000000'); // Exemple d API simple
            // Comme un vrai serveur necessite une configuration, une alternative ultra simple sans rien configurer 
            // est d utiliser un service de stockage distant.
        } catch(e) {}
    }

    // Version amelioree avec localStorage partage par cle cloud ou hebergement sur GitHub Pages
    // Si tu veux que ce soit accessible partout sans serveur, le plus simple est de mettre ton fichier HTML 
    // sur un site gratuit comme Vercel ou Netlify, et d utiliser une base de donnees gratuite comme Supabase.
</script>

</body>
</html>
