<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chat Application</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            background-color: #f5f5f5;
            height: 100vh;
            overflow: hidden;
        }

        .sidebar {
            position: fixed;
            left: 20%;
            top: 0;
            width: 2px;
            height: 100vh;
            background-color: #ddd;
            z-index: 100;
        }

        .autre {
            position: fixed;
            left: 0;
            top: 0;
            width: 20%;
            height: 100vh;
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            padding: 20px;
            overflow-y: auto;
            box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
        }

        .encore {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
        }

        .utilise {
            font-size: 18px;
            font-weight: bold;
            color: #ecf0f1;
        }

        .deconnexion {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s ease;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        .deconnexion:hover {
            background: linear-gradient(135deg, #c0392b 0%, #a93226 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }

        .liste {
            margin-top: 20px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            backdrop-filter: blur(10px);
        }

        .liste strong {
            display: block;
            margin-bottom: 10px;
            color: #ecf0f1;
            font-size: 14px;
        }

        .liste span {
            color: #3498db;
            font-weight: bold;
        }

        .tous {
            position: relative;
            left: 20%;
            width: 80%;
            height: 100vh;
        }

        .entete {
            position: fixed;
            top: 0;
            left: 20%;
            width: 80%;
            height: 70px;
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-bottom: 1px solid #e9ecef;
            display: flex;
            align-items: center;
            justify-content: space-between;
            z-index: 50;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 0 30px;
        }

        .entete h3 {
            color: #2c3e50;
            font-size: 20px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .entete h3 i {
            color: #3498db;
        }

        .zone_chat {
            position: fixed;
            top: 70px;
            left: 20%;
            width: 80%;
            height: calc(100vh - 170px);
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            overflow-y: auto;
            padding: 20px;
            scroll-behavior: smooth;
        }

        .info {
            position: fixed;
            bottom: 0;
            left: 20%;
            width: 80%;
            height: 100px;
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-top: 1px solid #e9ecef;
            display: flex;
            align-items: center;
            padding: 0 30px;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
            gap: 15px;
        }

        #message {
            flex: 1;
            height: 50px;
            border: 2px solid #e9ecef;
            border-radius: 25px;
            padding: 0 20px;
            font-size: 16px;
            transition: all 0.3s ease;
            background: #ffffff;
        }

        #message:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }

        .bas {
            height: 50px;
            padding: 0 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        #envoi {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            color: white;
        }

        #envoi:hover {
            background: linear-gradient(135deg, #2980b9 0%, #21618c 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(52, 152, 219, 0.4);
        }

        #emoji {
            background: linear-gradient(135deg, #f39c12 0%, #e67e22 100%);
            color: white;
        }

        #emoji:hover {
            background: linear-gradient(135deg, #e67e22 0%, #d68910 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(243, 156, 18, 0.4);
        }

        #image {
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
        }

        #image:hover {
            background: linear-gradient(135deg, #229954 0%, #1e8449 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(39, 174, 96, 0.4);
        }

        .message {
            margin-bottom: 15px;
            padding: 15px 20px;
            border-radius: 20px;
            max-width: 70%;
            word-wrap: break-word;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: relative;
            animation: messageSlide 0.3s ease-out;
        }

        @keyframes messageSlide {
            from {
                opacity: 0;
                transform: translateY(20px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .message.sent {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            color: white;
            margin-left: auto;
            border-bottom-right-radius: 5px;
        }

        .message.received {
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            color: #2c3e50;
            margin-right: auto;
            border: 1px solid #e9ecef;
            border-bottom-left-radius: 5px;
        }

        .message-info {
            font-size: 11px;
            opacity: 0.8;
            margin-bottom: 5px;
        }

        .message-text {
            font-size: 14px;
            line-height: 1.4;
        }

        #photoPreview {
            display: none;
            margin-bottom: 10px;
            border-radius: 10px;
            max-width: 200px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .emo {
            display: none;
            position: absolute;
            bottom: 120px;
            left: 30px;
            width: 320px;
            height: 120px;
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border: 1px solid #e9ecef;
            border-radius: 15px;
            padding: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            z-index: 1000;
            overflow-y: auto;
            backdrop-filter: blur(10px);
        }

        .emo span {
            cursor: pointer;
            font-size: 24px;
            margin: 8px;
            display: inline-block;
            transition: transform 0.2s ease;
            padding: 5px;
            border-radius: 8px;
        }

        .emo span:hover {
            transform: scale(1.3);
            background: rgba(52, 152, 219, 0.1);
        }

        .anonyme {
            height: 45px;
            padding: 0 20px;
            border-radius: 25px;
            background: linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%);
            border: none;
            color: white;
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 2px 10px rgba(155, 89, 182, 0.3);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .anonyme:hover {
            background: linear-gradient(135deg, #8e44ad 0%, #7d3c98 100%);
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(155, 89, 182, 0.4);
        }

        /* Styles de connexion améliorés */
        :root {
            --primary-color: #667eea;
            --primary-dark: #5a6fd8;
            --secondary-color: #764ba2;
            --accent-color: #f093fb;
            --text-primary: #2d3748;
            --text-secondary: #718096;
            --bg-primary: #ffffff;
            --bg-secondary: #f7fafc;
            --border-color: #e2e8f0;
            --success-color: #48bb78;
            --error-color: #f56565;
            --shadow-light: 0 4px 6px rgba(0, 0, 0, 0.05);
            --shadow-medium: 0 10px 25px rgba(0, 0, 0, 0.1);
            --shadow-heavy: 0 20px 40px rgba(0, 0, 0, 0.15);
        }

        body::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: float 20s linear infinite;
            pointer-events: none;
            z-index: -1;
        }

        @keyframes float {
            0% {
                transform: translate(0, 0) rotate(0deg);
            }

            100% {
                transform: translate(-50px, -50px) rotate(360deg);
            }
        }

        #connexion {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: var(--bg-primary);
            border-radius: 24px;
            box-shadow: var(--shadow-heavy);
            width: 100%;
            max-width: 480px;
            overflow: hidden;
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 40px;
            z-index: 1000;
        }

        #connexion::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color), var(--primary-color));
            background-size: 200% 100%;
            animation: shimmer 3s ease-in-out infinite;
        }

        @keyframes shimmer {

            0%,
            100% {
                background-position: -200% 0;
            }

            50% {
                background-position: 200% 0;
            }
        }

        .lui {
            text-align: center;
            padding-bottom: 20px;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            margin: -40px -40px 30px -40px;
            padding: 40px 40px 20px;
        }

        .lui h3 {
            color: var(--text-primary);
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            margin-bottom: 30px !important;
            font-size: 2rem !important;
        }

        .lui h3 i {
            color: var(--primary-color);
            animation: pulse 2s ease-in-out infinite;
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

        .form-group {
            display: block;
            margin-bottom: 24px;
            position: relative;
        }

        .form-group label {
            display: block;
            color: var(--text-primary);
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 0.95rem;
        }

        .input-wrapper {
            position: relative;
        }

        .nom {
            width: 100%;
            padding: 16px 20px;
            border: 2px solid var(--border-color);
            border-radius: 12px;
            font-size: 1rem;
            background: var(--bg-secondary);
            color: var(--text-primary);
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
            outline: none;
        }

        .nom:focus {
            border-color: var(--primary-color);
            background: var(--bg-primary);
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
            transform: translateY(-2px);
        }

        .nom::placeholder {
            color: var(--text-secondary);
            opacity: 0.8;
        }

        .input-icon {
            position: absolute;
            right: 16px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-secondary);
            transition: color 0.3s ease;
        }

        .nom:focus+.input-icon {
            color: var(--primary-color);
        }

        .btn {
            width: 100%;
            padding: 16px;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .btn:active::before {
            width: 300px;
            height: 300px;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            box-shadow: var(--shadow-medium);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(102, 126, 234, 0.4);
        }

        .form-toggle {
            opacity: 1;
            visibility: visible;
            position: relative;
        }

        .form-toggle.active {
            opacity: 1;
            visibility: visible;
            transform: translateX(0);
        }

        .notification {
            position: fixed;
            top: 30px;
            right: 30px;
            padding: 15px 25px;
            border-radius: 10px;
            color: white;
            font-size: 14px;
            font-weight: 600;
            z-index: 9999;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
            transform: translateX(400px);
            transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
            backdrop-filter: blur(10px);
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.info {
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
        }

        .notification.error {
            background: linear-gradient(135deg, #dc3545 0%, #e74c3c 100%);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .autre {
                width: 100%;
                height: 80px;
                position: relative;
                flex-direction: row;
                align-items: center;
            }

            .sidebar {
                display: none;
            }

            .tous {
                left: 0;
                width: 100%;
                top: 80px;
                height: calc(100vh - 80px);
            }

            .entete {
                left: 0;
                width: 100%;
                top: 80px;
            }

            .zone_chat {
                left: 0;
                width: 100%;
                top: 150px;
                height: calc(100vh - 250px);
            }

            .info {
                left: 0;
                width: 100%;
                padding: 0 15px;
            }

            .message {
                max-width: 85%;
            }

            #connexion {
                margin: 20px;
                max-width: calc(100% - 40px);
            }
        }

        /* Animation d'entrée pour les messages */
        .message-enter {
            animation: messageEnter 0.5s ease-out;
        }

        @keyframes messageEnter {
            from {
                opacity: 0;
                transform: translateY(30px) scale(0.8);
            }

            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        /* Indicateur de frappe */
        .typing-indicator {
            display: none;
            padding: 15px 20px;
            margin: 10px 0;
            background: #f8f9fa;
            border-radius: 20px;
            max-width: 100px;
            border: 1px solid #e9ecef;
        }

        .typing-dots {
            display: flex;
            gap: 4px;
            align-items: center;
        }

        .typing-dots span {
            width: 8px;
            height: 8px;
            background: #6c757d;
            border-radius: 50%;
            animation: typing 1.4s infinite;
        }

        .typing-dots span:nth-child(2) {
            animation-delay: 0.2s;
        }

        .typing-dots span:nth-child(3) {
            animation-delay: 0.4s;
        }

        @keyframes typing {

            0%,
            60%,
            100% {
                transform: translateY(0);
            }

            30% {
                transform: translateY(-10px);
            }
        }
    </style>
</head>

<body>
    <div id="connexion" style="display: block;">
        <div class="lui">
            <h3 style="margin-bottom: 30px; color: var(--primary-color); font-size: 2rem; text-align: center;">
                <i class="fas fa-sign-in-alt"></i> Connexion
            </h3>
        </div>
        <div id="formConnexion" class="form-toggle active">
            <div class="form-group">
                <label for="">Entrez votre prénom*</label>
                <div class="input-wrapper">
                    <input type="text" name="nom" class="nom" id="nom" placeholder="Brayan" required>
                    <i class="fas fa-user input-icon"></i>
                </div>
            </div>
            <div class="form-group">
                <label for="">Entrez votre email*</label>
                <div class="input-wrapper">
                    <input type="email" name="email" class="nom" id="email" placeholder="brayan@gmail.com" required>
                    <i class="fas fa-envelope input-icon"></i>
                </div>
            </div>
            <div class="form-group">
                <label for="">Entrez votre mot de passe*</label>
                <div class="input-wrapper">
                    <input type="password" name="motdepasse" class="nom" id="motdepasse" placeholder="••••••••"
                        required>
                    <i class="fas fa-lock input-icon"></i>
                </div>
            </div>
            <button id="btnSeConnecter" class="btn btn-primary">
                <i class="fas fa-sign-in-alt"></i>
                Se connecter
            </button>
        </div>
    </div>

    <div style="display:none;" id="letous">
        <div class="autre">
            <div class="encore">
                <div>
                    <h2 class="utilise">Utilisateur</h2>
                    <p style="font-size: 12px; opacity: 0.8; margin-top: 5px;">BTS Niveau 2 - PERLE</p>
                </div>
                <button class="deconnexion" id="deconnexion">
                    <i class="fas fa-sign-out-alt"></i>
                    Déconnexion
                </button>
            </div>

            <div class="liste">
                <strong>Utilisateurs connectés <span id="userCount">(1)</span></strong>
                <div id="usersList" style="margin-top: 10px; font-size: 12px;">
                    <!-- Liste des utilisateurs connectés -->
                </div>
            </div>
        </div>

        <div class="sidebar"></div>

        <div class="tous">
            <div class="entete">
                <h3>
                    <i class="fa-solid fa-comment"></i>
                    Discussion générale
                </h3>
                <button class="anonyme" id="modeAnonyme">
                    <i class="fas fa-user-secret"></i>
                    Mode anonyme
                </button>
            </div>

            <div class="zone_chat" id="zone_chat">
                <img src="" id="photoPreview" style="display: none;">

                <div class="typing-indicator" id="typingIndicator">
                    <div class="typing-dots">
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>
                </div>

                <div class="emo" id="emo">
                    <span>😂</span> <span>🤣</span> <span>😅</span>
                    <span>😉</span> <span>😎</span> <span>😍</span>
                    <span>🥰</span> <span>😘</span> <span>🤩</span>
                    <span>😥</span> <span>😴</span> <span>😪</span>
                    <span>🤐</span> <span>🙄</span> <span>🥱</span>
                    <span>😛</span> <span>☝️</span> <span>👏</span>
                    <span>🙏</span> <span>💪</span> <span>❤️</span>
                    <span>👍</span> <span>👎</span> <span>🔥</span>
                    <span>⭐</span> <span>🎉</span> <span>🚀</span>
                </div>
            </div>

            <div class="info">
                <input type="text" id="message" placeholder="Tapez votre message...">
                <button id="envoi" class="bas">
                    <i class="fas fa-paper-plane"></i>
                    Envoyer
                </button>
                <button id="emoji" class="bas">
                    <i class="fa-regular fa-face-laugh"></i>
                    Emoji
                </button>
                <button id="image" class="bas">
                    <i class="fa-solid fa-images"></i>
                    Image
                </button>
                <input type="file" id="camer" accept="image/*" style="display:none;">
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import {
            getFirestore, collection, addDoc, doc, getDoc, getDocs,
            onSnapshot, query, orderBy, updateDoc, setDoc, limit
        } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";
        import {
            getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword,
            onAuthStateChanged
        } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";

        // Configuration Firebase
        const firebaseConfig = {
            apiKey: "AIzaSyAigx8KtDCEulSWjpu17fnYsrqK7C9o3R8",
            authDomain: "petit-jobs-express.firebaseapp.com",
            projectId: "petit-jobs-express",
            storageBucket: "petit-jobs-express.appspot.com",
            messagingSenderId: "446118780236",
            appId: "1:446118780236:web:08c3a87d56bcd67399c3e9"
        };

        const app = initializeApp(firebaseConfig);
        const db = getFirestore(app);
        const auth = getAuth(app);

        // Variables globales
        let currentUser = null;
        let isAnonymous = false;
        let typingTimeout;

        // Éléments DOM
        const connexionDiv = document.getElementById('connexion');
        const letousDiv = document.getElementById('letous');
        const inscription = document.getElementById('btnSeConnecter');
        const emoji = document.getElementById('emoji');
        const envoie = document.getElementById('envoi');
        const photoPreview = document.getElementById('photoPreview');
        const camer = document.getElementById('camer');
        const imageBtn = document.getElementById('image');
        const zone_chat = document.getElementById('zone_chat');
        const message = document.getElementById('message');
        const emo = document.getElementById('emo');
        const deconnexion = document.getElementById('deconnexion');
        const modeAnonyme = document.getElementById('modeAnonyme');

        // Fonction pour afficher les notifications
        function showNotification(text, type = 'info') {
            const existingNotif = document.querySelector('.notification');
            if (existingNotif) {
                existingNotif.remove();
            }

            const notif = document.createElement('div');
            notif.className = `notification ${type}`;
            notif.textContent = text;
            document.body.appendChild(notif);

            setTimeout(() => notif.classList.add('show'), 100);
            setTimeout(() => {
                notif.classList.remove('show');
                setTimeout(() => notif.remove(), 400);
            }, 4000);
        }

        // Fonction pour formater le timestamp
        function formatTime(timestamp) {
            const date = new Date(timestamp);
            const now = new Date();
            const diff = now - date;

            if (diff < 60000) return 'À l\'instant';
            if (diff < 3600000) return `${Math.floor(diff / 60000)} min`;
            if (diff < 86400000) return date.toLocaleTimeString('fr-FR', { hour: '2-digit', minute: '2-digit' });
            return date.toLocaleDateString('fr-FR', { day: '2-digit', month: '2-digit' });
        }

        // Fonction pour créer un message
        function createMessageElement(messageData, isSent = false) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${isSent ? 'sent' : 'received'} message-enter`;

            const messageInfo = document.createElement('div');
            messageInfo.className = 'message-info';
            messageInfo.textContent = `${messageData.auteur} • ${formatTime(messageData.timestamp)}`;
            messageInfo.style.cursor = 'pointer';
            const messageText = document.createElement('div');
            messageText.className = 'message-text';
            messageText.textContent = messageData.text;

            messageDiv.appendChild(messageInfo);
            messageDiv.appendChild(messageText);

            return messageDiv;
        }

        function scrollToBottom() {
            zone_chat.scrollTop = zone_chat.scrollHeight;
        }

        // Notification de bienvenue
        setTimeout(() => {
            showNotification("Bienvenue dans BTS Niveau 2 de la PERLE ❤️", "info");
        }, 3000);

        // Gestion de la connexion
        inscription.addEventListener('click', async function () {
            const nom = document.getElementById('nom').value.trim();
            const email = document.getElementById('email').value.trim();
            const motdepasse = document.getElementById('motdepasse').value;

            if (!nom || !email || !motdepasse) {
                showNotification('Veuillez remplir tous les champs', 'error');
                return;
            }

            if (nom.length < 2) {
                showNotification('Le nom doit contenir au moins 2 caractères', 'error');
                return;
            }

            if (motdepasse.length < 6) {
                showNotification('Le mot de passe doit contenir au moins 6 caractères', 'error');
                return;
            }

            inscription.classList.add('loading');
            inscription.disabled = true;

            try {
                await createUserWithEmailAndPassword(auth, email, motdepasse);
                showNotification('Compte créé et connecté avec succès ! 💪', 'info');

                // Sauvegarder les informations utilisateur
                await setDoc(doc(db, "users", email), {
                    nom: nom,
                    email: email,
                    dateCreation: Date.now(),
                    lastActive: Date.now()
                });
            } catch (error) {
                console.error('Erreur lors de la création du compte:', error);
            }

            currentUser = { nom, email };
            document.querySelector('.utilise').textContent = nom;
            connexionDiv.style.display = 'none';
            letousDiv.style.display = 'block';
            loadMessages();


            if (error.code === 'auth/email-already-in-use') {
                errorMessage = 'Cette adresse email est déjà utilisée';
            } else if (error.code === 'auth/weak-password') {
                errorMessage = 'Le mot de passe est trop faible';
            } else if (error.code === 'auth/invalid-email') {
                errorMessage = 'Adresse email invalide';
            }

            showNotification(errorMessage, 'error');
        }
        );

        deconnexion.addEventListener('click', async function () {
            try {
                await auth.signOut();
                showNotification('Vous avez été déconnecté avec succès ! 👋', 'info');
                connexionDiv.style.display = 'block';
                letousDiv.style.display = 'none';
                zone_chat.innerHTML = '';
                currentUser = null;
            } catch (error) {
                console.error('Erreur lors de la déconnexion:', error);
                showNotification('Erreur lors de la déconnexion', 'error');
            }
        });

        // Gestion du mode anonyme
        modeAnonyme.addEventListener('click', function () {
            isAnonymous = !isAnonymous;
            if (isAnonymous) {
                modeAnonyme.innerHTML = '<i class="fas fa-user"></i> Mode normal';
                modeAnonyme.style.background = 'linear-gradient(135deg, #e74c3c 0%, #c0392b 100%)';
                showNotification('Mode anonyme activé 🥸', 'info');
            } else {
                modeAnonyme.innerHTML = '<i class="fas fa-user-secret"></i> Mode anonyme';
                modeAnonyme.style.background = 'linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%)';
                showNotification('Mode normal activé 👤', 'info');
            }
        });

        // Gestion des images
        imageBtn.addEventListener('click', () => camer.click());

        camer.addEventListener('change', function (e) {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function () {
                photoPreview.src = reader.result;
                photoPreview.style.display = 'block';
                showNotification('Image sélectionnée ! 📸', 'info');
            };
            reader.readAsDataURL(file);
        });

        // Fonction d'envoi de message
        async function envoyerMessage() {
            const messageText = message.value.trim();
            const hasImage = photoPreview.style.display !== 'none';

            if (!messageText && !hasImage) {
                showNotification('Veuillez entrer un message ou sélectionner une image', 'error');
                return;
            }

            if (!currentUser) {
                showNotification('Veuillez vous connecter d\'abord', 'error');
                return;
            }

            try {
                const messageData = {
                    auteur: isAnonymous ? 'Anonyme' : currentUser.nom,
                    text: messageText,
                    timestamp: Date.now(),
                    userId: auth.currentUser?.uid || 'anonymous',
                    isAnonymous: isAnonymous
                };

                if (hasImage) {
                    messageData.image = photoPreview.src;
                }

                // Ajouter le message à Firestore
                await addDoc(collection(db, "messages"), messageData);

                // Réinitialiser les champs
                message.value = '';
                photoPreview.style.display = 'none';
                photoPreview.src = '';

                showNotification('Message envoyé ! ✅', 'info');

            } catch (error) {
                console.error("Erreur envoi message:", error);
                showNotification("Erreur lors de l'envoi du message", 'error');
            }
        }

        // Fonction pour charger les messages
        function loadMessages() {
            const messagesQuery = query(
                collection(db, "messages"),
                orderBy("timestamp", "asc"),
                limit(50)
            );

            onSnapshot(messagesQuery, (snapshot) => {
                const existingMessages = zone_chat.querySelectorAll('.message');
                const existingIds = new Set();

                existingMessages.forEach(msg => {
                    if (msg.dataset.messageId) {
                        existingIds.add(msg.dataset.messageId);
                    }
                });

                snapshot.docChanges().forEach((change) => {
                    if (change.type === "added") {
                        const messageData = change.doc.data();
                        const messageId = change.doc.id;

                        if (!existingIds.has(messageId)) {
                            const isSent = auth.currentUser && messageData.userId === auth.currentUser.uid;
                            const messageElement = createMessageElement(messageData, isSent);
                            messageElement.dataset.messageId = messageId;

                            const controlElements = zone_chat.querySelectorAll('#photoPreview, .emo, .typing-indicator');
                            if (controlElements.length > 0) {
                                zone_chat.insertBefore(messageElement, controlElements[0]);
                            } else {
                                zone_chat.appendChild(messageElement);
                            }

                            scrollToBottom();
                        }
                    }
                });
            });
        }

        // Gestion des événements de clic
        envoie.addEventListener('click', envoyerMessage);

        // Gestion des emojis
        emoji.addEventListener('click', function () {
            emo.style.display = emo.style.display === 'block' ? 'none' : 'block';
        });

        emo.querySelectorAll('span').forEach(span => {
            span.addEventListener('click', function () {
                message.value += span.textContent;
                emo.style.display = 'none';
                message.focus();
            });
        });

        // Fermer les emojis en cliquant ailleurs
        document.addEventListener('click', function (e) {
            if (!e.target.closest('#emoji') && !e.target.closest('.emo')) {
                emo.style.display = 'none';
            }
        });

        // Gestion de la touche Entrée
        message.addEventListener('keypress', function (e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                envoyerMessage();
            }
        });

        // Simuler l'indicateur de frappe
        message.addEventListener('input', function () {
            const typingIndicator = document.getElementById('typingIndicator');

            if (this.value.trim()) {
                typingIndicator.style.display = 'block';
                scrollToBottom();

                clearTimeout(typingTimeout);
                typingTimeout = setTimeout(() => {
                    typingIndicator.style.display = 'none';
                }, 1000);
            } else {
                typingIndicator.style.display = 'none';
            }
        });

        // Mise à jour du compteur d'utilisateurs (simulation)
        function updateUserCount() {
            const userCount = document.getElementById('userCount');
            const randomCount = Math.floor(Math.random() * 10) + 1;
            userCount.textContent = `(${randomCount})`;
        }

        // Mettre à jour le compteur toutes les 30 secondes
        setInterval(updateUserCount, 30000);
        updateUserCount();

        // Gestion de l'état d'authentification
        onAuthStateChanged(auth, (user) => {
            if (user && currentUser) {
                // Utilisateur connecté
                console.log("Utilisateur connecté:", user.email);
            } else if (!user) {
                // Utilisateur déconnecté
                console.log("Utilisateur déconnecté");
            }
        });

        // Animation de chargement initial
        window.addEventListener('load', function () {
            document.body.style.opacity = '0';
            setTimeout(() => {
                document.body.style.transition = 'opacity 0.5s ease';
                document.body.style.opacity = '1';
            }, 100);
        });

        // Messages automatiques de bienvenue
        setTimeout(() => {
            if (zone_chat.children.length <= 3) { // Si peu de messages
                const welcomeMessages = [
                    "👋 Bienvenue dans le chat BTS Niveau 2 !",
                    "💬 N'hésitez pas à poser vos questions",
                    "🎓 Bon apprentissage à tous !"
                ];

                welcomeMessages.forEach((text, index) => {
                    setTimeout(() => {
                        const welcomeMsg = createMessageElement({
                            auteur: "Système",
                            text: text,
                            timestamp: Date.now()
                        }, false);
                        welcomeMsg.style.background = 'linear-gradient(135deg, #17a2b8 0%, #138496 100%)';
                        welcomeMsg.style.color = 'white';
                        zone_chat.appendChild(welcomeMsg);
                        scrollToBottom();
                    }, index * 2000);
                });
            }
        }, 5000);

    </script>
</body>

</html>
