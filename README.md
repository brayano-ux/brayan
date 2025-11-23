<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formation JavaScript Complète - Version Interactive</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .badge {
            display: inline-block;
            background: rgba(255,255,255,0.2);
            padding: 5px 15px;
            border-radius: 20px;
            margin: 5px;
            font-size: 0.9em;
        }

        .nav {
            background: #2d3748;
            padding: 15px;
            position: sticky;
            top: 0;
            z-index: 100;
            overflow-x: auto;
        }

        .nav ul {
            list-style: none;
            display: flex;
            gap: 10px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .nav a {
            color: white;
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 5px;
            transition: all 0.3s;
            white-space: nowrap;
        }

        .nav a:hover {
            background: #667eea;
            transform: translateY(-2px);
        }

        .content {
            padding: 40px;
        }

        section {
            margin-bottom: 60px;
            scroll-margin-top: 80px;
        }

        h2 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 3px solid #667eea;
        }

        h3 {
            color: #764ba2;
            font-size: 1.5em;
            margin: 30px 0 15px;
        }

        h4 {
            color: #2d3748;
            font-size: 1.2em;
            margin: 20px 0 10px;
        }

        /* ÉDITEUR DE CODE INTERACTIF */
        .code-editor {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin: 20px 0;
            border: 2px solid #667eea;
            border-radius: 10px;
            overflow: hidden;
            background: #1e1e1e;
        }

        .editor-panel {
            display: flex;
            flex-direction: column;
        }

        .editor-header {
            background: #2d3748;
            color: white;
            padding: 10px 15px;
            font-weight: bold;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .editor-content {
            flex: 1;
            position: relative;
        }

        .code-input {
            width: 100%;
            height: 300px;
            padding: 15px;
            background: #1e1e1e;
            color: #e0e0e0;
            border: none;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            resize: vertical;
            outline: none;
        }

        .output-area {
            background: white;
            color: #333;
            padding: 15px;
            height: 300px;
            overflow-y: auto;
            font-family: 'Courier New', monospace;
            font-size: 14px;
        }

        .run-button {
            background: #4caf50;
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9em;
            transition: all 0.3s;
        }

        .run-button:hover {
            background: #45a049;
            transform: scale(1.05);
        }

        .reset-button {
            background: #ff9800;
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 0.9em;
            margin-left: 5px;
        }

        /* CODE STATIQUE */
        .code-block {
            background: #2d3748;
            color: #e2e8f0;
            padding: 20px;
            border-radius: 8px;
            margin: 20px 0;
            overflow-x: auto;
            font-family: 'Courier New', monospace;
            position: relative;
            font-size: 14px;
            line-height: 1.5;
        }

        .code-block::before {
            content: 'JavaScript';
            position: absolute;
            top: 5px;
            right: 10px;
            background: #667eea;
            color: white;
            padding: 2px 10px;
            border-radius: 3px;
            font-size: 0.8em;
        }

        .copy-button {
            position: absolute;
            top: 40px;
            right: 10px;
            background: #667eea;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            font-size: 0.8em;
            opacity: 0.7;
            transition: opacity 0.3s;
        }

        .copy-button:hover {
            opacity: 1;
        }

        .info-box {
            background: #e3f2fd;
            border-left: 4px solid #2196f3;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .warning-box {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .success-box {
            background: #d4edda;
            border-left: 4px solid #28a745;
            padding: 20px;
            margin: 20px 0;
            border-radius: 5px;
        }

        .example {
            background: #f8f9fa;
            border: 2px solid #dee2e6;
            border-radius: 8px;
            padding: 20px;
            margin: 20px 0;
        }

        .example-title {
            font-weight: bold;
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        button:not(.run-button):not(.reset-button):not(.copy-button) {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: transform 0.2s, box-shadow 0.2s;
            margin: 5px;
        }

        button:hover:not(.run-button):not(.reset-button) {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .console-output {
            background: #1e1e1e;
            color: #4caf50;
            padding: 15px;
            border-radius: 5px;
            margin: 10px 0;
            font-family: 'Courier New', monospace;
            min-height: 100px;
            max-height: 300px;
            overflow-y: auto;
        }

        .console-line {
            margin: 5px 0;
            padding: 5px;
            border-left: 3px solid #4caf50;
            padding-left: 10px;
        }

        .console-error {
            color: #f44336;
            border-left-color: #f44336;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }

        table th {
            background: #667eea;
            color: white;
            padding: 12px;
            text-align: left;
        }

        table td {
            padding: 12px;
            border-bottom: 1px solid #dee2e6;
        }

        ul, ol {
            margin: 15px 0 15px 30px;
        }

        li {
            margin-bottom: 8px;
        }

        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            border-bottom: 2px solid #dee2e6;
        }

        .tab {
            padding: 10px 20px;
            background: transparent;
            border: none;
            cursor: pointer;
            color: #666;
            transition: all 0.3s;
        }

        .tab.active {
            color: #667eea;
            border-bottom: 3px solid #667eea;
            margin-bottom: -2px;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        footer {
            background: #2d3748;
            color: white;
            padding: 30px;
            text-align: center;
        }

        @media (max-width: 768px) {
            .code-editor {
                grid-template-columns: 1fr;
            }
            
            header h1 {
                font-size: 1.8em;
            }
            
            .content {
                padding: 20px;
            }
        }

        /* Animation pour les résultats */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .animated {
            animation: fadeIn 0.3s ease-in;
        }
    </style>
</head>
 <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .activation-container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            max-width: 500px;
            width: 100%;
            padding: 50px 40px;
            text-align: center;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .lock-icon {
            font-size: 4em;
            margin-bottom: 20px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.1);
            }
        }

        h1 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #666;
            margin-bottom: 40px;
            font-size: 1.1em;
        }

        .input-group {
            margin-bottom: 30px;
        }

        label {
            display: block;
            text-align: left;
            color: #333;
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 1.1em;
        }

        input[type="text"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1.1em;
            font-family: 'Courier New', monospace;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: all 0.3s;
        }

        input[type="text"]:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .activate-btn {
            width: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 18px;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-bottom: 20px;
        }

        .activate-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
        }

        .activate-btn:active {
            transform: translateY(0);
        }

        .message {
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            font-weight: bold;
            display: none;
            animation: fadeIn 0.3s;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }

            to {
                opacity: 1;
            }
        }

        .message.success {
            background: #d4edda;
            color: #155724;
            border: 2px solid #c3e6cb;
        }

        .message.warning {
            background: #fff3cd;
            color: #856404;
            border: 2px solid #ffeeba;
        }

        .message.error {
            background: #f8d7da;
            color: #721c24;
            border: 2px solid #f5c6cb;
        }

        .help-text {
            color: #999;
            font-size: 0.9em;
            margin-top: 30px;
            padding-top: 30px;
            border-top: 1px solid #e0e0e0;
        }

        .help-text a {
            color: #667eea;
            text-decoration: none;
            font-weight: bold;
        }

        .help-text a:hover {
            text-decoration: underline;
        }

        .loading {
            display: none;
            margin-top: 20px;
        }

        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #667eea;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }

            100% {
                transform: rotate(360deg);
            }
        }

        .example-key {
            background: #f8f9fa;
            border: 1px dashed #ccc;
            padding: 10px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            color: #667eea;
            margin-top: 10px;
            font-size: 0.9em;
        }

        .license-success-box {
            background: linear-gradient(135deg, #4caf50 0%, #45a049 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin: 20px 0;
            text-align: center;
            display: none;
            animation: slideIn 0.5s ease-out;
        }

        .license-success-box h3 {
            color: white;
            margin-bottom: 15px;
            font-size: 1.5em;
        }

        .generated-key {
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid white;
            padding: 20px;
            border-radius: 10px;
            font-family: 'Courier New', monospace;
            font-size: 1.5em;
            font-weight: bold;
            letter-spacing: 3px;
            margin: 20px 0;
            word-break: break-all;
        }

        .copy-key-btn {
            background: white;
            color: #4caf50;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            margin: 10px 5px;
            transition: all 0.3s;
        }

        .copy-key-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .copy-key-btn.copied {
            background: #2196f3;
            color: white;
        }

        .email-note {
            background: #fff3cd;
            border: 2px solid #ffc107;
            border-radius: 10px;
            padding: 15px;
            margin: 20px 0;
            color: #856404;
            font-size: 0.95em;
        }
        /* Animation de transition */
.tous, .container {
    transition: opacity 0.3s ease-in-out;
}

/* Style pour l'écran d'authentification */
.activation-container {
    background: white;
    border-radius: 20px;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    max-width: 500px;
    width: 100%;
    padding: 50px 40px;
    text-align: center;
    animation: slideIn 0.5s ease-out;
}

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateY(-30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Message d'erreur */
.message {
    padding: 15px;
    border-radius: 10px;
    margin-top: 20px;
    font-weight: bold;
    display: none;
    animation: fadeIn 0.3s;
}

.message.error {
    background: #f8d7da;
    color: #721c24;
    border: 2px solid #f5c6cb;
}
    </style>
</head>

<body>
   <div class="tous" style="display: block;">
    <div class="activation-container">
        <div class="lock-icon">🔐</div>
        <h1 id="pageTitle">Activation de la Formation</h1>
        <p class="subtitle">Entrez votre clé de licence pour accéder à la formation complète</p>
        <div class="input-group">
            <label for="licenseKey">Clé de Licence</label>
            <input type="text" id="licenseKey" name="licenseKey" placeholder="XXXX-XXXX-XXXX-XXXX" maxlength="19" autocomplete="off">
        </div>
        <button type="submit" class="activate-btn" id="activateBtn">
            🚀 Activer Ma Formation
        </button>
    </div>
</div>
            <script>
               (function(){
    const CLE_ACCES = 'brayanoformation199';
    const ACT_KEY = 'formationJsActivated';
    const LICENSE_KEY = 'formationJsLicense';

    function readLocalDB() {
        try { 
            return JSON.parse(localStorage.getItem('licensesDB') || '{}'); 
        } catch(e) { 
            return {}; 
        }
    }

    function isExpired(iso) {
        if (!iso) return false;
        try { 
            return new Date(iso).getTime() <= Date.now(); 
        } catch(e) { 
            return false; 
        }
    }

    function isValidLicense(key) {
        if (!key) return false;
        key = key.trim();
        if (key === CLE_ACCES) return true;
        const db = readLocalDB();
        if (db && db[key] && db[key].actif) return true;
        
        // Vérifier la licence sauvegardée
        try {
            const saved = JSON.parse(localStorage.getItem(LICENSE_KEY) || '{}');
            if (saved && saved.licenseKey === key && !isExpired(saved.expiresAt)) {
                return true;
            }
        } catch(e) {}
        return false;
    }

    function saveActivation(key) {
        const now = Date.now();
        const expiresMs = 365 * 24 * 60 * 60 * 1000; // 1 an
        const activationData = {
            licenseKey: key,
            activatedAt: new Date(now).toISOString(),
            expiresAt: new Date(now + expiresMs).toISOString()
        };
        localStorage.setItem(LICENSE_KEY, JSON.stringify(activationData));
        localStorage.setItem(ACT_KEY, 'true');
    }

    function showContent() {
        // Afficher la formation
        const containers = document.querySelectorAll('.container');
        containers.forEach(c => {
            c.style.display = 'block';
        });
        
        // Masquer l'écran d'authentification
        const wrapper = document.querySelector('.tous');
        if (wrapper) wrapper.style.display = 'none';
        
        // Scroll en haut
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function showAuthScreen() {
        // Afficher l'écran d'authentification
        const wrapper = document.querySelector('.tous');
        if (wrapper) wrapper.style.display = 'block';
        
        // Masquer la formation
        const containers = document.querySelectorAll('.container');
        containers.forEach(c => {
            c.style.display = 'none';
        });
    }

    // Vérification automatique au chargement
    document.addEventListener('DOMContentLoaded', function(){
        if (localStorage.getItem(ACT_KEY) === 'true') {
            try {
                const saved = JSON.parse(localStorage.getItem(LICENSE_KEY) || '{}');
                if (saved.licenseKey && !isExpired(saved.expiresAt) && isValidLicense(saved.licenseKey)) {
                    showContent();
                    return;
                } else {
                    // Licence expirée ou invalide
                    localStorage.removeItem(ACT_KEY);
                    localStorage.removeItem(LICENSE_KEY);
                    showAuthScreen();
                }
            } catch(e) { 
                console.warn('Erreur vérification licence:', e);
                showAuthScreen();
            }
        } else {
            showAuthScreen();
        }
    });

    // Gestion du bouton d'activation
    const activateBtn = document.getElementById('activateBtn');
    const licenseInput = document.getElementById('licenseKey');

    if (activateBtn && licenseInput) {
        activateBtn.addEventListener('click', function(){
            const key = (licenseInput.value || '').trim();
            
            if (!key) { 
                alert('Erreur: La clé de licence ne peut pas être vide.'); 
                licenseInput.focus(); 
                return; 
            }
            
            if (isValidLicense(key)) {
                saveActivation(key);
                alert('Félicitations! Votre formation a été activée avec succès.');
                showContent();
            } else {
                alert('Erreur: Clé de licence invalide. Veuillez réessayer.');
            }
        });

        // Activation avec la touche Entrée
        licenseInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                activateBtn.click();
            }
        });
    }
})();
            </script>

<body>
    <div class="container" style="display: none;">
        <header>
            <h1>🚀 Formation JavaScript Complète</h1>
            <p>Apprenez JavaScript ES6+ avec des exemples interactifs en temps réel</p>
            <div>
                <span class="badge">✅ 100% Interactif</span>
                <span class="badge">🎯 ES6+</span>
                <span class="badge">💻 Testez en Live</span>
                <span class="badge">📱 Responsive</span>
            </div>
        </header>

        <nav class="nav">
            <ul>
                <li><a href="#intro">🏠 Introduction</a></li>
                <li><a href="#variables">📦 Variables</a></li>
                <li><a href="#fonctions">⚙️ Fonctions</a></li>
                <li><a href="#tableaux">📊 Tableaux</a></li>
                <li><a href="#objets">🎁 Objets</a></li>
                <li><a href="#dom">🌳 DOM</a></li>
                <li><a href="#async">⏱️ Async</a></li>
                <li><a href="#projets">🎮 Projets</a></li>
            </ul>
        </nav>

        <div class="content">
            <!-- INTRODUCTION -->
            <section id="intro">
                <h2>📚 Bienvenue dans la Formation Interactive</h2>
                
                <div class="success-box">
                    <strong>🎉 Particularité de cette formation :</strong>
                    <ul>
                        <li>✅ <strong>Testez chaque exemple en temps réel</strong> dans votre navigateur</li>
                        <li>✅ Modifiez le code et voyez les résultats instantanément</li>
                        <li>✅ Console JavaScript intégrée pour chaque exercice</li>
                        <li>✅ Pas besoin d'installer quoi que ce soit</li>
                    </ul>
                </div>

                <h3>Comment utiliser cette formation ?</h3>
                <div class="info-box">
                    <ol>
                        <li>📖 <strong>Lisez</strong> les explications théoriques</li>
                        <li>👀 <strong>Observez</strong> les exemples de code</li>
                        <li>✏️ <strong>Modifiez</strong> le code dans l'éditeur interactif</li>
                        <li>▶️ <strong>Cliquez sur "Exécuter"</strong> pour voir le résultat</li>
                        <li>🔄 <strong>Expérimentez</strong> jusqu'à maîtriser le concept</li>
                    </ol>
                </div>
            </section>

            <!-- VARIABLES -->
            <section id="variables">
                <h2>📦 Variables et Types de Données</h2>

                <h3>Déclaration de Variables</h3>
                <div class="code-block">
                    <button class="copy-button" onclick="copierCode(this)">📋 Copier</button>
// Utilisez const par défaut
const nom = "Alice";
const age = 25;

// Utilisez let si la valeur doit changer
let compteur = 0;
compteur = compteur + 1;

// ❌ N'utilisez jamais var (obsolète)
var ancien = "déconseillé";</div>

                <h3>🎯 Testez en Direct !</h3>
                <div class="code-editor">
                    <div class="editor-panel">
                        <div class="editor-header">
                            ✏️ Éditeur JavaScript
                            <div>
                                <button class="run-button" onclick="executerCode('editor1', 'output1')">▶ Exécuter</button>
                                <button class="reset-button" onclick="resetCode('editor1', codeExemples.variables)">🔄 Reset</button>
                            </div>
                        </div>
                        <div class="editor-content">
                            <textarea id="editor1" class="code-input">// Testez les variables !
const prenom = "Alice";
const age = 25;

console.log(`Je m'appelle ${prenom}`);
console.log(`J'ai ${age} ans`);

// Modifiez et ajoutez votre code ici
const ville = "Paris";
console.log(`J'habite à ${ville}`);</textarea>
                        </div>
                    </div>
                    <div class="editor-panel">
                        <div class="editor-header">📟 Console / Résultat</div>
                        <div class="editor-content">
                            <div id="output1" class="output-area">Cliquez sur "Exécuter" pour voir le résultat...</div>
                        </div>
                    </div>
                </div>

                <h3>Types de Données</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Type</th>
                            <th>Exemple</th>
                            <th>typeof</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr><td>Number</td><td>42, 3.14</td><td>"number"</td></tr>
                        <tr><td>String</td><td>"Hello", 'World'</td><td>"string"</td></tr>
                        <tr><td>Boolean</td><td>true, false</td><td>"boolean"</td></tr>
                        <tr><td>Array</td><td>[1, 2, 3]</td><td>"object"</td></tr>
                        <tr><td>Object</td><td>{nom: "Alice"}</td><td>"object"</td></tr>
                    </tbody>
                </table>

                <div class="code-editor">
                    <div class="editor-panel">
                        <div class="editor-header">
                            ✏️ Testez typeof
                            <button class="run-button" onclick="executerCode('editor2', 'output2')">▶ Exécuter</button>
                        </div>
                        <div class="editor-content">
                            <textarea id="editor2" class="code-input">// Testez typeof sur différentes valeurs
console.log(typeof 42);
console.log(typeof "Hello");
console.log(typeof true);
console.log(typeof [1,2,3]);
console.log(typeof {nom: "Alice"});
console.log(typeof undefined);
console.log(typeof null); // Bug historique!</textarea>
                        </div>
                    </div>
                    <div class="editor-panel">
                        <div class="editor-header">📟 Résultat</div>
                        <div class="editor-content">
                            <div id="output2" class="output-area">En attente d'exécution...</div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- FONCTIONS -->
            <section id="fonctions">
                <h2>⚙️ Fonctions</h2>

                <h3>Déclaration et Arrow Functions</h3>
                <div class="code-block">
                    <button class="copy-button" onclick="copierCode(this)">📋 Copier</button>
// Fonction classique
function addition(a, b) {
    return a + b;
}

// Arrow function (recommandé)
const addition2 = (a, b) => a + b;

// Arrow function avec corps
const saluer = (nom) => {
    const message = `Bonjour ${nom}!`;
    return message;
};</div>

                <div class="code-editor">
                    <div class="editor-panel">
                        <div class="editor-header">
                            ✏️ Créez vos fonctions
                            <button class="run-button" onclick="executerCode('editor3', 'output3')">▶ Exécuter</button>
                        </div>
                        <div class="editor-content">
                            <textarea id="editor3" class="code-input">// Fonction qui calcule le carré
const carre = (x) => x * x;

console.log(carre(5)); // 25
console.log(carre(10)); // 100

// Créez votre propre fonction
const triple = (x) => x * 3;
console.log(triple(4)); // 12

// Fonction avec plusieurs paramètres
const calculerAire = (longueur, largeur) => {
    return longueur * largeur;
};

console.log(calculerAire(5, 3)); // 15</textarea>
                        </div>
                    </div>
                    <div class="editor-panel">
                        <div class="editor-header">📟 Résultat</div>
                        <div class="editor-content">
                            <div id="output3" class="output-area">En attente...</div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- TABLEAUX -->
            <section id="tableaux">
                <h2>📊 Tableaux et Méthodes</h2>

                <h3>Méthodes Essentielles</h3>
                <div class="tabs">
                    <button class="tab active" onclick="changerTab(0)">map()</button>
                    <button class="tab" onclick="changerTab(1)">filter()</button>
                    <button class="tab" onclick="changerTab(2)">reduce()</button>
                    <button class="tab" onclick="changerTab(3)">forEach()</button>
                </div>

                <div class="tab-content active">
                    <div class="code-editor">
                        <div class="editor-panel">
                            <div class="editor-header">
                                ✏️ map() - Transformer
                                <button class="run-button" onclick="executerCode('editor4', 'output4')">▶ Exécuter</button>
                            </div>
                            <div class="editor-content">
                                <textarea id="editor4" class="code-input">// map() transforme chaque élément
const nombres = [1, 2, 3, 4, 5];

// Doubler chaque nombre
const doubles = nombres.map(n => n * 2);
console.log("Doubles:", doubles);

// Créer des objets
const personnes = ["Alice", "Bob", "Charlie"];
const objets = personnes.map((nom, index) => ({
    id: index + 1,
    nom: nom,
    email: `${nom.toLowerCase()}@example.com`
}));

console.log("Objets:", objets);</textarea>
                            </div>
                        </div>
                        <div class="editor-panel">
                            <div class="editor-header">📟 Résultat</div>
                            <div class="editor-content">
                                <div id="output4" class="output-area">En attente...</div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="tab-content">
                    <div class="code-editor">
                        <div class="editor-panel">
                            <div class="editor-header">
                                ✏️ filter() - Filtrer
                                <button class="run-button" onclick="executerCode('editor5', 'output5')">▶ Exécuter</button>
                            </div>
                            <div class="editor-content">
                                <textarea id="editor5" class="code-input">// filter() garde les éléments qui satisfont la condition
const nombres = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Garder les pairs
const pairs = nombres.filter(n => n % 2 === 0);
console.log("Pairs:", pairs);

// Garder les nombres > 5
const grands = nombres.filter(n => n > 5);
console.log("Grands:", grands);

// Étudiants admis
const etudiants = [
    {nom: "Alice", note: 15},
    {nom: "Bob", note: 8},
    {nom: "Charlie", note: 12}
];

const admis = etudiants.filter(e => e.note >= 10);
console.log("Admis:", admis);</textarea>
                            </div>
                        </div>
                        <div class="editor-panel">
                            <div class="editor-header">📟 Résultat</div>
                            <div class="editor-content">
                                <div id="output5" class="output-area">En attente...</div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="tab-content">
                    <div class="code-editor">
                        <div class="editor-panel">
                            <div class="editor-header">
                                ✏️ reduce() - Réduire
                                <button class="run-button" onclick="executerCode('editor6', 'output6')">▶ Exécuter</button>
                            </div>
                            <div class="editor-content">
                                <textarea id="editor6" class="code-input">// reduce() réduit le tableau à une valeur
const nombres = [1, 2, 3, 4, 5];

// Somme
const somme = nombres.reduce((acc, n) => acc + n, 0);
console.log("Somme:", somme);

// Produit
const produit = nombres.reduce((acc, n) => acc * n, 1);
console.log("Produit:", produit);

// Maximum
const max = nombres.reduce((acc, n) => n > acc ? n : acc);
console.log("Maximum:", max);

// Compter occurrences
const fruits = ["pomme", "banane", "pomme", "orange"];
const compte = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});
console.log("Compte:", compte);</textarea>
                            </div>
                        </div>
                        <div class="editor-panel">
                            <div class="editor-header">📟 Résultat</div>
                            <div class="editor-content">
                                <div id="output6" class="output-area">En attente...</div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="tab-content">
                    <p>forEach() permet d'itérer sans retourner de nouveau tableau.</p>
                </div>
            </section>

            <!-- OBJETS -->
            <section id="objets">
                <h2>🎁 Objets et Destructuration</h2>

                <div class="code-editor">
                    <div class="editor-panel">
                        <div class="editor-header">
                            ✏️ Objets JavaScript
                            <button class="run-button" onclick="executerCode('editor7', 'output7')">▶ Exécuter</button>
                        </div>
                        <div class="editor-content">
                            <textarea id="editor7" class="code-input">// Créer un objet
const personne = {
    nom: "Alice",
    age: 25,
    ville: "Paris",
    sePresenter() {
        return `Je m'appelle ${this.nom}, j'ai ${this.age} ans`;
    }
};

console.log(personne.sePresenter());

// Destructuration
const {nom, age} = personne;
console.log(`Nom: ${nom}, Âge: ${age}`);

// Spread operator
const nouvellePersonne = {
    ...personne,
    age: 26,
    pays: "France"
};
console.log("Nouvelle personne:", nouvellePersonne);

// Object.keys, values, entries
console.log("Clés:", Object.keys(personne));
console.log("Valeurs:", Object.values(personne));</textarea>
                        </div>
                    </div>
                    <div class="editor-panel">
                        <div class="editor-header">📟 Résultat</div>
                        <div class="editor-content">
                            <div id="output7" class="output-area">En attente...</div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- DOM -->
            <section id="dom">
                <h2>🌳 Manipulation du DOM</h2>

                <div class="warning-box">
                    <strong>⚠️ Note:</strong> Les exemples DOM nécessitent des éléments HTML existants. 
                    Testez le code dans la console de votre navigateur avec de vrais éléments HTML.
                </div>

                <div class="code-block">
                    <button class="copy-button" onclick="copierCode(this)">📋 Copier</button>
// Sélectionner des éléments
const element = document.querySelector('#monId');
const elements = document.querySelectorAll('.maClasse');

// Modifier le contenu
element.textContent = 'Nouveau texte';
element.innerHTML = '&lt;strong&gt;Texte en gras&lt;/strong&gt;';

// Modifier les styles
element.style.color = 'red';
element.style.backgroundColor = 'yellow';

// Ajouter/Retirer des classes
element.classList.add('active');
element.classList.remove('inactive');
element.classList.toggle('highlight');

// Créer et ajouter des éléments
const div = document.createElement('div');
div.textContent = 'Nouveau div';
document.body.appendChild(div);</div>

                <div class="example">
                    <div class="example-title">🎯 Test DOM Interactif</div>
                    <div id="demo-box" style="padding: 20px; background: #f0f0f0; border-radius: 5px; margin: 10px 0;">
                        <p id="demo-text">Texte à modifier</p>
                    </div>
                    <input type="text" id="demo-input" placeholder="Nouveau texte" value="Bonjour le DOM!">
                    <button onclick="changerTexteDom()">Changer Texte</button>
                    <button onclick="changerCouleurDom()">Changer Couleur</button>
                    <button onclick="ajouterElementDom()">Ajouter Élément</button>
                </div>
            </section>

            <!-- ASYNC -->
            <section id="async">
                <h2>⏱️ JavaScript Asynchrone</h2>

                <h3>Promises et Async/Await</h3>
                <div class="code-editor">
                    <div class="editor-panel">
                        <div class="editor-header">
                            ✏️ Async/Await
                            <button class="run-button" onclick="executerCodeAsync('editor8', 'output8')">▶ Exécuter</button>
                        </div>
                        <div class="editor-content">
                            <textarea id="editor8" class="code-input">// Fonction asynchrone
async function chargerDonnees() {
    console.log("Début du chargement...");
    
    // Simuler un délai
    await new Promise(resolve => setTimeout(resolve, 1000));
    
    console.log("Données chargées!");
    return {nom: "Alice", age: 25};
}

// Utilisation
chargerDonnees().then(data => {
    console.log("Résultat:", data);
});

// Avec try/catch
async function exemple() {
    try {
        const resultat = await chargerDonnees();
        console.log("Success:", resultat);
    } catch (error) {
        console.error("Erreur:", error);
    }
}

exemple();</textarea>
                        </div>
                    </div>
                    <div class="editor-panel">
                        <div class="editor-header">📟 Résultat</div>
                        <div class="editor-content">
                            <div id="output8" class="output-area">En attente...</div>
                        </div>
                    </div>
                </div>

                <h3>Fetch API - Appels HTTP</h3>
                <div class="example">
                    <div class="example-title">🌐 Tester une API en Direct</div>
                    <button onclick="testerAPI()">🔄 Charger une Citation</button>
                    <div id="api-result" style="margin-top: 15px; padding: 15px; background: white; border-radius: 5px; min-height: 100px;"></div>
                </div>
            </section>

            <!-- PROJETS -->
            <section id="projets">
                <h2>🎮 Projets Pratiques Complets</h2>

                <h3>Projet 1: Todo List Interactive</h3>
                <div class="example">
                    <div style="max-width: 600px; margin: 0 auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
                        <h4 style="text-align: center; color: #667eea;">📝 Ma Todo List</h4>
                        <div style="display: flex; gap: 10px; margin: 20px 0;">
                            <input type="text" id="todo-input" placeholder="Nouvelle tâche..." style="flex: 1; padding: 10px; border: 2px solid #ddd; border-radius: 5px;">
                            <button onclick="ajouterTodo()" style="padding: 10px 20px;">➕ Ajouter</button>
                        </div>
                        <ul id="todo-list" style="list-style: none; padding: 0;"></ul>
                        <div id="todo-stats" style="text-align: center; margin-top: 15px; color: #666; font-size: 0.9em;"></div>
                    </div>
                </div>

                <h3>Projet 2: Calculatrice</h3>
                <div class="example">
                    <div style="max-width: 300px; margin: 0 auto; background: #2d3748; padding: 20px; border-radius: 10px;">
                        <input type="text" id="calc-display" readonly style="width: 100%; padding: 15px; font-size: 1.5em; text-align: right; border: none; border-radius: 5px; margin-bottom: 10px; background: #1a202c; color: white;">
                        <div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px;">
                            <button onclick="ajouterCalc('7')" style="padding: 15px; font-size: 1.2em;">7</button>
                            <button onclick="ajouterCalc('8')" style="padding: 15px; font-size: 1.2em;">8</button>
                            <button onclick="ajouterCalc('9')" style="padding: 15px; font-size: 1.2em;">9</button>
                            <button onclick="ajouterCalc('/')" style="padding: 15px; font-size: 1.2em; background: #ff9800;">÷</button>
                            <button onclick="ajouterCalc('4')" style="padding: 15px; font-size: 1.2em;">4</button>
                            <button onclick="ajouterCalc('5')" style="padding: 15px; font-size: 1.2em;">5</button>
                            <button onclick="ajouterCalc('6')" style="padding: 15px; font-size: 1.2em;">6</button>
                            <button onclick="ajouterCalc('*')" style="padding: 15px; font-size: 1.2em; background: #ff9800;">×</button>
                            <button onclick="ajouterCalc('1')" style="padding: 15px; font-size: 1.2em;">1</button>
                            <button onclick="ajouterCalc('2')" style="padding: 15px; font-size: 1.2em;">2</button>
                            <button onclick="ajouterCalc('3')" style="padding: 15px; font-size: 1.2em;">3</button>
                            <button onclick="ajouterCalc('-')" style="padding: 15px; font-size: 1.2em; background: #ff9800;">−</button>
                            <button onclick="ajouterCalc('0')" style="padding: 15px; font-size: 1.2em; grid-column: 1/3;">0</button>
                            <button onclick="calculer()" style="padding: 15px; font-size: 1.2em; background: #4caf50;">=</button>
                            <button onclick="ajouterCalc('+')" style="padding: 15px; font-size: 1.2em; background: #ff9800;">+</button>
                            <button onclick="effacerCalc()" style="padding: 15px; font-size: 1.2em; grid-column: 1/5; background: #f44336;">C</button>
                        </div>
                    </div>
                </div>

                <h3>Projet 3: Générateur de Couleurs</h3>
                <div class="example">
                    <div style="text-align: center;">
                        <div id="color-display" style="width: 200px; height: 200px; margin: 20px auto; border-radius: 10px; background: #667eea; box-shadow: 0 4px 15px rgba(0,0,0,0.2); transition: all 0.3s;"></div>
                        <div id="color-code" style="font-size: 1.5em; font-weight: bold; margin: 10px 0; font-family: monospace;">#667eea</div>
                        <button onclick="genererCouleur()">🎨 Générer une Couleur</button>
                        <button onclick="copierCouleur()">📋 Copier le Code</button>
                    </div>
                </div>
            </section>

        </div>

        <footer>
            <h3>🎓 Formation JavaScript Interactive</h3>
            <p>Continuez à pratiquer et expérimenter avec chaque exemple</p>
            <p style="margin-top: 20px; opacity: 0.8;">© 2024 - Tous droits réservés</p>
        </footer>
    </div>

    <script>
        // Exemples de code par défaut
        const codeExemples = {
            variables: `// Testez les variables !
const prenom = "Alice";
const age = 25;

console.log(\`Je m'appelle \${prenom}\`);
console.log(\`J'ai \${age} ans\`);

// Modifiez et ajoutez votre code ici
const ville = "Paris";
console.log(\`J'habite à \${ville}\`);`
        };

        // Fonction pour exécuter le code JavaScript
        function executerCode(editorId, outputId) {
            const editor = document.getElementById(editorId);
            const output = document.getElementById(outputId);
            const code = editor.value;

            // Capturer console.log
            let logs = [];
            const originalLog = console.log;
            console.log = function(...args) {
                logs.push(args.map(arg => {
                    if (typeof arg === 'object') {
                        return JSON.stringify(arg, null, 2);
                    }
                    return String(arg);
                }).join(' '));
                originalLog.apply(console, args);
            };

            try {
                // Exécuter le code
                eval(code);
                
                // Afficher les résultats
                if (logs.length > 0) {
                    output.innerHTML = logs.map(log => 
                        `<div class="console-line">${log}</div>`
                    ).join('');
                } else {
                    output.innerHTML = '<div class="console-line">Code exécuté avec succès (pas de sortie console)</div>';
                }
                
                output.classList.add('animated');
            } catch (error) {
                output.innerHTML = `<div class="console-line console-error">❌ Erreur: ${error.message}</div>`;
            } finally {
                // Restaurer console.log
                console.log = originalLog;
                
                // Retirer l'animation après
                setTimeout(() => output.classList.remove('animated'), 300);
            }
        }

        // Fonction pour exécuter du code asynchrone
        async function executerCodeAsync(editorId, outputId) {
            const editor = document.getElementById(editorId);
            const output = document.getElementById(outputId);
            const code = editor.value;

            let logs = [];
            const originalLog = console.log;
            console.log = function(...args) {
                logs.push(args.map(arg => {
                    if (typeof arg === 'object') {
                        return JSON.stringify(arg, null, 2);
                    }
                    return String(arg);
                }).join(' '));
                originalLog.apply(console, args);
            };

            try {
                // Créer une fonction async et l'exécuter
                const asyncFunc = new Function(`
                    return (async () => {
                        ${code}
                    })();
                `);
                
                await asyncFunc();
                
                if (logs.length > 0) {
                    output.innerHTML = logs.map(log => 
                        `<div class="console-line">${log}</div>`
                    ).join('');
                } else {
                    output.innerHTML = '<div class="console-line">Code exécuté (pas de sortie)</div>';
                }
            } catch (error) {
                output.innerHTML = `<div class="console-line console-error">❌ Erreur: ${error.message}</div>`;
            } finally {
                console.log = originalLog;
            }
        }

        // Reset le code
        function resetCode(editorId, defaultCode) {
            document.getElementById(editorId).value = defaultCode;
        }

        // Copier le code
        function copierCode(button) {
            const codeBlock = button.parentElement;
            const code = codeBlock.textContent.replace('📋 Copier', '').replace('JavaScript', '').trim();
            
            navigator.clipboard.writeText(code).then(() => {
                const originalText = button.textContent;
                button.textContent = '✅ Copié!';
                setTimeout(() => {
                    button.textContent = originalText;
                }, 2000);
            });
        }

        // Gestion des tabs
        let currentTab = 0;
        function changerTab(index) {
            const tabs = document.querySelectorAll('.tab');
            const contents = document.querySelectorAll('.tab-content');
            
            tabs.forEach((tab, i) => {
                if (i === index) {
                    tab.classList.add('active');
                    contents[i].classList.add('active');
                } else {
                    tab.classList.remove('active');
                    contents[i].classList.remove('active');
                }
            });
            
            currentTab = index;
        }

        // Manipulation DOM
        function changerTexteDom() {
            const texte = document.getElementById('demo-input').value;
            document.getElementById('demo-text').textContent = texte;
        }

        function changerCouleurDom() {
            const couleurs = ['#ffcdd2', '#c8e6c9', '#bbdefb', '#f8bbd0', '#d1c4e9', '#ffe0b2'];
            const couleur = couleurs[Math.floor(Math.random() * couleurs.length)];
            document.getElementById('demo-box').style.backgroundColor = couleur;
        }

        function ajouterElementDom() {
            const p = document.createElement('p');
            p.textContent = `Ajouté à ${new Date().toLocaleTimeString()}`;
            p.style.color = '#667eea';
            p.style.animation = 'fadeIn 0.3s';
            document.getElementById('demo-box').appendChild(p);
        }

        // Test API
        async function testerAPI() {
            const result = document.getElementById('api-result');
            result.innerHTML = '<div style="text-align: center;">⏳ Chargement...</div>';
            
            try {
                const response = await fetch('https://api.quotable.io/random');
                const data = await response.json();
                
                result.innerHTML = `
                    <blockquote style="border-left: 4px solid #667eea; padding-left: 15px; font-style: italic; margin: 0;">
                        <p style="font-size: 1.1em; margin-bottom: 10px;">"${data.content}"</p>
                        <footer style="text-align: right; color: #666;">— ${data.author}</footer>
                    </blockquote>
                `;
            } catch (error) {
                result.innerHTML = '<div style="color: red;">❌ Erreur de chargement</div>';
            }
        }

        // Todo List
        let todos = [];
        let todoId = 0;

        function ajouterTodo() {
            const input = document.getElementById('todo-input');
            const texte = input.value.trim();
            
            if (texte) {
                todos.push({
                    id: todoId++,
                    texte: texte,
                    complete: false
                });
                input.value = '';
                afficherTodos();
            }
        }

        function toggleTodo(id) {
            const todo = todos.find(t => t.id === id);
            if (todo) {
                todo.complete = !todo.complete;
                afficherTodos();
            }
        }

        function supprimerTodo(id) {
            todos = todos.filter(t => t.id !== id);
            afficherTodos();
        }

        function afficherTodos() {
            const liste = document.getElementById('todo-list');
            const stats = document.getElementById('todo-stats');
            
            if (todos.length === 0) {
                liste.innerHTML = '<li style="text-align: center; color: #999; padding: 20px;">Aucune tâche</li>';
                stats.innerHTML = '';
                return;
            }
            
            liste.innerHTML = todos.map(todo => `
                <li style="display: flex; align-items: center; gap: 10px; padding: 12px; background: ${todo.complete ? '#f0f0f0' : 'white'}; margin: 8px 0; border-radius: 5px; border: 1px solid #ddd; transition: all 0.3s;">
                    <input type="checkbox" ${todo.complete ? 'checked' : ''} 
                           onchange="toggleTodo(${todo.id})" 
                           style="width: 18px; height: 18px; cursor: pointer;">
                    <span style="flex: 1; ${todo.complete ? 'text-decoration: line-through; color: #999;' : ''}">${todo.texte}</span>
                    <button onclick="supprimerTodo(${todo.id})" 
                            style="background: #f44336; padding: 5px 10px; font-size: 0.9em; border-radius: 3px;">
                        🗑️
                    </button>
                </li>
            `).join('');
            
            const actifs = todos.filter(t => !t.complete).length;
            const completes = todos.filter(t => t.complete).length;
            stats.innerHTML = `${actifs} active${actifs > 1 ? 's' : ''} • ${completes} terminée${completes > 1 ? 's' : ''}`;
        }

        // Calculatrice
        let calcDisplay = '';

        function ajouterCalc(valeur) {
            calcDisplay += valeur;
            document.getElementById('calc-display').value = calcDisplay;
        }

        function calculer() {
            try {
                calcDisplay = eval(calcDisplay.replace('×', '*').replace('÷', '/').replace('−', '-')).toString();
                document.getElementById('calc-display').value = calcDisplay;
            } catch {
                document.getElementById('calc-display').value = 'Erreur';
                calcDisplay = '';
            }
        }

        function effacerCalc() {
            calcDisplay = '';
            document.getElementById('calc-display').value = '';
        }

        // Générateur de couleurs
        function genererCouleur() {
            const r = Math.floor(Math.random() * 256);
            const g = Math.floor(Math.random() * 256);
            const b = Math.floor(Math.random() * 256);
            const hex = '#' + [r, g, b].map(x => x.toString(16).padStart(2, '0')).join('');
            
            document.getElementById('color-display').style.backgroundColor = hex;
            document.getElementById('color-code').textContent = hex;
        }

        function copierCouleur() {
            const code = document.getElementById('color-code').textContent;
            navigator.clipboard.writeText(code).then(() => {
                const btn = event.target;
                const originalText = btn.textContent;
                btn.textContent = '✅ Copié!';
                setTimeout(() => {
                    btn.textContent = originalText;
                }, 2000);
            });
        }

        // Initialisation
        document.addEventListener('DOMContentLoaded', () => {
            console.log('Formation JavaScript Interactive chargée!');
        });
    </script>
</body>
