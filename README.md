

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
            left: 280px;
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
            width: 280px;
            height: 100vh;
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
            color: white;
            overflow-y: auto;
            box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease;
            z-index: 200;
        }

        .autre-header {
            padding: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .encore {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .utilise {
            font-size: 16px;
            font-weight: bold;
            color: #ecf0f1;
        }

        .deconnexion {
            background: linear-gradient(135deg, #e74c3c 0%, #c0392b 100%);
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 15px;
            cursor: pointer;
            font-size: 11px;
            transition: all 0.3s ease;
        }

        .deconnexion:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
        }

        .liste {
            padding: 0 20px 20px;
        }

        .liste strong {
            display: block;
            margin-bottom: 15px;
            color: #ecf0f1;
            font-size: 14px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 8px;
        }

        .user-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            margin: 5px 0;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .user-item:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(5px);
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .user-status {
            width: 8px;
            height: 8px;
            background: #27ae60;
            border-radius: 50%;
            border: 2px solid white;
        }

        .user-name {
            font-size: 13px;
            color: #ecf0f1;
        }

        .notification-badge {
            background: #e74c3c;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: none;
            align-items: center;
            justify-content: center;
            font-size: 11px;
            font-weight: bold;
            position: absolute;
            right: 5px;
            top: 5px;
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .tous {
            position: relative;
            left: 280px;
            width: calc(100% - 280px);
            height: 100vh;
            transition: all 0.3s ease;
        }

        .entete {
            position: fixed;
            top: 0;
            left: 280px;
            width: calc(100% - 280px);
            height: 70px;
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-bottom: 1px solid #e9ecef;
            display: flex;
            align-items: center;
            justify-content: space-between;
            z-index: 150;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 0 30px;
            transition: all 0.3s ease;
        }

        .entete h3 {
            color: #2c3e50;
            font-size: 18px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .chat-actions {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 20px;
            color: #2c3e50;
            cursor: pointer;
            padding: 10px;
        }

        .zone_chat {
            position: fixed;
            top: 70px;
            left: 280px;
            width: calc(100% - 280px);
            height: calc(100vh - 170px);
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            overflow-y: auto;
            padding: 20px;
            scroll-behavior: smooth;
            transition: all 0.3s ease;
        }

        .info {
            position: fixed;
            bottom: 0;
            left: 280px;
            width: calc(100% - 280px);
            background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
            border-top: 1px solid #e9ecef;
            padding: 15px 30px;
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .message-input-container {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 10px;
        }

        .reply-indicator {
            display: none;
            background: rgba(52, 152, 219, 0.1);
            border-left: 3px solid #3498db;
            padding: 8px 12px;
            border-radius: 5px;
            margin-bottom: 10px;
            font-size: 12px;
            color: #666;
        }

        .reply-close {
            float: right;
            cursor: pointer;
            color: #999;
            font-weight: bold;
        }

        #message {
            flex: 1;
            height: 45px;
            border: 2px solid #e9ecef;
            border-radius: 22px;
            padding: 0 20px;
            font-size: 14px;
            transition: all 0.3s ease;
            background: #ffffff;
        }

        #message:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }

        .bas {
            height: 45px;
            padding: 0 18px;
            border: none;
            border-radius: 22px;
            cursor: pointer;
            font-size: 13px;
            font-weight: 600;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        #envoi {
            background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
            color: white;
        }

        #emoji {
            background: linear-gradient(135deg, #f39c12 0%, #e67e22 100%);
            color: white;
        }

        #image {
            background: linear-gradient(135deg, #27ae60 0%, #229954 100%);
            color: white;
        }

        .bas:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }

        .message {
            margin-bottom: 15px;
            padding: 12px 16px;
            border-radius: 18px;
            max-width: 70%;
            word-wrap: break-word;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            position: relative;
            animation: messageSlide 0.3s ease-out;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .message:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
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

        .message.private {
            background: linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%);
            color: white;
            border: 2px solid #7d3c98;
        }

        .message.system {
            background: linear-gradient(135deg, #17a2b8 0%, #138496 100%);
            color: white;
            text-align: center;
            margin: 10px auto;
            font-size: 13px;
            max-width: 90%;
        }

        .message-header {
            font-size: 11px;
            opacity: 0.8;
            margin-bottom: 4px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .message-reply {
            background: rgba(255, 255, 255, 0.2);
            border-left: 3px solid rgba(255, 255, 255, 0.5);
            padding: 6px 10px;
            margin-bottom: 8px;
            border-radius: 4px;
            font-size: 11px;
            opacity: 0.9;
        }

        .message.received .message-reply {
            background: rgba(0, 0, 0, 0.05);
            border-left-color: rgba(0, 0, 0, 0.2);
        }

        .message-text {
            font-size: 14px;
            line-height: 1.4;
        }

        .emo {
            display: none;
            position: absolute;
            bottom: 80px;
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
        }

        .emo span {
            cursor: pointer;
            font-size: 22px;
            margin: 6px;
            display: inline-block;
            transition: transform 0.2s ease;
            padding: 4px;
            border-radius: 6px;
        }

        .emo span:hover {
            transform: scale(1.3);
            background: rgba(52, 152, 219, 0.1);
        }

        .anonyme {
            height: 40px;
            padding: 0 16px;
            border-radius: 20px;
            background: linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%);
            border: none;
            color: white;
            font-weight: 600;
            font-size: 13px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .anonyme:hover {
            background: linear-gradient(135deg, #8e44ad 0%, #7d3c98 100%);
            transform: translateY(-2px);
        }

        /* Styles de connexion */
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
        }

        #connexion {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: var(--bg-primary);
            border-radius: 24px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            width: 100%;
            max-width: 420px;
            padding: 40px;
            z-index: 1000;
        }

        .lui h3 {
            color: var(--primary-color);
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            margin-bottom: 30px;
            font-size: 1.8rem;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            color: var(--text-primary);
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 0.9rem;
        }

        .nom {
            width: 100%;
            padding: 14px 18px;
            border: 2px solid var(--border-color);
            border-radius: 12px;
            font-size: 0.95rem;
            background: var(--bg-secondary);
            transition: all 0.3s ease;
            outline: none;
        }

        .nom:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .btn-primary {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 12px 20px;
            border-radius: 8px;
            color: white;
            font-size: 13px;
            font-weight: 600;
            z-index: 9999;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            transform: translateX(400px);
            transition: all 0.4s ease;
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

        #photoPreview {
            display: none;
            margin-bottom: 10px;
            border-radius: 10px;
            max-width: 200px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        /* RESPONSIVE MOBILE */
        @media (max-width: 768px) {
            .autre {
                transform: translateX(-100%);
                width: 100%;
                z-index: 300;
            }

            .autre.mobile-open {
                transform: translateX(0);
            }

            .sidebar {
                display: none;
            }

            .tous {
                left: 0;
                width: 100%;
            }

            .entete {
                left: 0;
                width: 100%;
                padding: 0 15px;
                height: 60px;
            }

            .entete h3 {
                font-size: 16px;
            }

            .mobile-menu-btn {
                display: block;
            }

            .chat-actions {
                gap: 5px;
            }

            .anonyme {
                height: 35px;
                padding: 0 12px;
                font-size: 12px;
            }

            .zone_chat {
                left: 0;
                width: 100%;
                top: 60px;
                height: calc(100vh - 140px);
                padding: 15px;
            }

            .info {
                left: 0;
                width: 100%;
                padding: 10px 15px;
                height: 80px;
            }

            .message-input-container {
                gap: 8px;
                margin-bottom: 5px;
            }

            #message {
                height: 40px;
                font-size: 13px;
                padding: 0 15px;
            }

            .bas {
                height: 40px;
                padding: 0 12px;
                font-size: 12px;
                gap: 4px;
            }

            .message {
                max-width: 85%;
                padding: 10px 14px;
                font-size: 13px;
            }

            .emo {
                width: calc(100% - 30px);
                left: 15px;
                bottom: 90px;
            }

            #connexion {
                margin: 20px;
                max-width: calc(100% - 40px);
                padding: 30px 25px;
            }

            .lui h3 {
                font-size: 1.5rem !important;
            }

            .liste {
                padding: 0 15px 15px;
            }

            .user-item {
                padding: 8px;
                margin: 3px 0;
            }

            .user-name {
                font-size: 12px;
            }

            .autre-header {
                padding: 15px;
            }

            .utilise {
                font-size: 14px;
            }

            .deconnexion {
                padding: 5px 10px;
                font-size: 10px;
            }
        }

        @media (max-width: 480px) {
            .message {
                max-width: 90%;
                padding: 8px 12px;
            }

            .bas {
                padding: 0 8px;
            }

            .bas span {
                display: none;
            }

            .info {
                height: 70px;
            }

            .zone_chat {
                height: calc(100vh - 130px);
            }
        }

        /* Overlay pour mobile */
        .mobile-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 250;
        }

        .mobile-overlay.active {
            display: block;
        }

        /* Private chat indicator */
        .private-chat-indicator {
            background: linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 12px;
            margin-left: 10px;
            display: none;
        }

        .private-chat-indicator.active {
            display: inline-block;
        }
    </style>
</head>

<body>
    <div id="connexion" style="display: block;">
        <div class="lui">
            <h3>
                <i class="fas fa-sign-in-alt"></i> Connexion
            </h3>
        </div>
        <div id="formConnexion" class="form-toggle active">
            <div class="form-group">
                <label for="">Entrez votre prénom*</label>
                <input type="text" name="nom" class="nom" id="nom" placeholder="Brayan" required>
            </div>
            <div class="form-group">
                <label for="">Entrez votre email*</label>
                <input type="email" name="email" class="nom" id="email" placeholder="brayan@gmail.com" required>
            </div>
            <div class="form-group">
                <label for="">Entrez votre mot de passe*</label>
                <input type="password" name="motdepasse" class="nom" id="motdepasse" placeholder="••••••••" required>
            </div>
            <button id="btnSeConnecter" class="btn-primary">
                <i class="fas fa-sign-in-alt"></i>
                Se connecter
            </button>
        </div>
    </div>

    <div style="display:none;" id="letous">
        <!-- Mobile Overlay -->
        <div class="mobile-overlay" id="mobileOverlay"></div>

        <!-- Sidebar -->
        <div class="autre" id="sidebar">
            <div class="autre-header">
                <div class="encore">
                    <div>
                        <h2 class="utilise" id="currentUserName">Utilisateur</h2>
                        <p style="font-size: 11px; opacity: 0.8; margin-top: 3px;">BTS Niveau 2 - PERLE</p>
                    </div>
                    <button class="deconnexion" id="deconnexion">
                        <i class="fas fa-sign-out-alt"></i>
                        <span>Déconnexion</span>
                    </button>
                </div>
            </div>

            <div class="liste">
                <strong>Utilisateurs connectés <span id="userCount">(0)</span></strong>
                <div id="usersList">
                    <!-- Liste des utilisateurs -->
                </div>
            </div>
        </div>
        
        <div class="sidebar"></div>
        
        <!-- Main Chat Area -->
        <div class="tous">
            <div class="entete">
                <div style="display: flex; align-items: center;">
                    <button class="mobile-menu-btn" id="mobileMenuBtn">
                        <i class="fas fa-bars"></i>
                    </button>
                    <h3 id="chatTitle">
                        <i class="fa-solid fa-comment"></i> 
                        Discussion générale
                    </h3>
                    <div class="private-chat-indicator" id="privateChatIndicator">
                        <i class="fas fa-lock"></i> Chat privé
                    </div>
                </div>
                <div class="chat-actions">
                    <button class="anonyme" id="modeAnonyme">
                        <i class="fas fa-user-secret"></i>
                        <span>Mode anonyme</span>
                    </button>
                </div>
            </div>
            
            <div class="zone_chat" id="zone_chat">
                <img src="" id="photoPreview" style="display: none;">
                
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
                <div class="reply-indicator" id="replyIndicator">
                    <span id="replyText">Réponse à...</span>
                    <span class="reply-close" id="replyClose">×</span>
                </div>
                <div class="message-input-container">
                    <input type="text" id="message" placeholder="Tapez votre message...">
                    <button id="envoi" class="bas">
                        <i class="fas fa-paper-plane"></i> 
                        <span>Envoyer</span>
                    </button>
                    <button id="emoji" class="bas">
                        <i class="fa-regular fa-face-laugh"></i> 
                        <span>Emoji</span>
                    </button>
                    <button id="image" class="bas">
                        <i class="fa-solid fa-images"></i> 
                        <span>Image</span>
                    </button>
                </div>
                <input type="file" id="camer" accept="image/*" style="display:none;">
            </div>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import {
            getFirestore, collection, addDoc, doc, getDoc, getDocs,
            onSnapshot, query, orderBy, updateDoc, setDoc, limit, where
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
        let connectedUsers = new Map();
        let currentPrivateChat = null;
        let replyingTo = null;
        let privateChatNotifications = new Map();

        // Éléments DOM
        const connexionDiv = document.getElementById('connexion');
        const letousDiv = document.getElementById('letous');
        const inscription = document.getElementById('btnSeConnecter');
        const zone_chat = document.getElementById('zone_chat');
        const message = document.getElementById('message');
        const sidebar = document.getElementById('sidebar');
        const mobileOverlay = document.getElementById('mobileOverlay');
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');

        // Fonctions utilitaires
        function showNotification(text, type = 'info') {
            const existingNotif = document.querySelector('.notification');
            if (existingNotif) existingNotif.remove();

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

        function formatTime(timestamp) {
            const date = new Date(timestamp);
            const now = new Date();
            const diff = now - date;
            
            if (diff < 60000) return 'À l\'instant';
            if (diff < 3600000) return `${Math.floor(diff / 60000)} min`;
            if (diff < 86400000) return date.toLocaleTimeString('fr-FR', { hour: '2-digit', minute: '2-digit' });
            return date.toLocaleDateString('fr-FR', { day: '2-digit', month: '2-digit' });
        }

        function scrollToBottom() {
            zone_chat.scrollTop = zone_chat.scrollHeight;
        }

        // Mobile menu toggle
        mobileMenuBtn.addEventListener('click', () => {
            sidebar.classList.toggle('mobile-open');
            mobileOverlay.classList.toggle('active');
        });

        mobileOverlay.addEventListener('click', () => {
            sidebar.classList.remove('mobile-open');
            mobileOverlay.classList.remove('active');
        });

        // Fonction pour créer un message
        function createMessageElement(messageData, isSent = false) {
            const messageDiv = document.createElement('div');
            let messageClass = `message ${isSent ? 'sent' : 'received'} message-enter`;
            
            if (messageData.isPrivate) {
                messageClass += ' private';
            }
            if (messageData.isSystem) {
                messageClass += ' system';
            }
            
            messageDiv.className = messageClass;
            messageDiv.dataset.messageId = messageData.id || Date.now();
            messageDiv.dataset.author = messageData.auteur;
            
            let messageHTML = '';
            
            if (!messageData.isSystem) {
                messageHTML += `<div class="message-header">
                    <span>${messageData.auteur}</span>
                    <span>${formatTime(messageData.timestamp)}</span>
                </div>`;
            }
            
            if (messageData.replyTo) {
                messageHTML += `<div class="message-reply">
                    <strong>${messageData.replyTo.author}:</strong> ${messageData.replyTo.text.substring(0, 50)}${messageData.replyTo.text.length > 50 ? '...' : ''}
                </div>`;
            }
            
            messageHTML += `<div class="message-text">${messageData.text}</div>`;
            
            if (messageData.image) {
                messageHTML += `<img src="${messageData.image}" style="max-width: 100%; border-radius: 8px; margin-top: 8px;">`;
            }
            
            messageDiv.innerHTML = messageHTML;
            
            // Ajouter event listener pour répondre
            if (!messageData.isSystem) {
                messageDiv.addEventListener('click', () => {
                    if (!isSent) {
                        replyToMessage(messageData);
                    }
                });
            }
            
            return messageDiv;
        }

        // Fonction pour répondre à un message
        function replyToMessage(messageData) {
            replyingTo = {
                id: messageData.id,
                author: messageData.auteur,
                text: messageData.text
            };
            
            const replyIndicator = document.getElementById('replyIndicator');
            const replyText = document.getElementById('replyText');
            
            replyText.textContent = `Réponse à ${messageData.auteur}: ${messageData.text.substring(0, 30)}${messageData.text.length > 30 ? '...' : ''}`;
            replyIndicator.style.display = 'block';
            message.focus();
        }

        // Fermer la réponse
        document.getElementById('replyClose').addEventListener('click', () => {
            replyingTo = null;
            document.getElementById('replyIndicator').style.display = 'none';
        });

        // Fonction pour mettre à jour la liste des utilisateurs
        function updateUsersList() {
            const usersList = document.getElementById('usersList');
            const userCount = document.getElementById('userCount');
            
            usersList.innerHTML = '';
            let onlineCount = 0;
            
            connectedUsers.forEach((userData, userId) => {
                if (userId === currentUser?.email) return; // Ne pas afficher l'utilisateur actuel
                
                onlineCount++;
                const userItem = document.createElement('div');
                userItem.className = 'user-item';
                userItem.dataset.userId = userId;
                
                const notificationCount = privateChatNotifications.get(userId) || 0;
                
                userItem.innerHTML = `
                    <div class="user-info">
                        <div class="user-status"></div>
                        <div class="user-name">${userData.nom}</div>
                    </div>
                    <div class="notification-badge" style="display: ${notificationCount > 0 ? 'flex' : 'none'}">${notificationCount}</div>
                `;
                
                userItem.addEventListener('click', () => {
                    startPrivateChat(userId, userData.nom);
                    // Réinitialiser les notifications pour cet utilisateur
                    privateChatNotifications.set(userId, 0);
                    updateUsersList();
                    
                    // Fermer le menu mobile si ouvert
                    if (window.innerWidth <= 768) {
                        sidebar.classList.remove('mobile-open');
                        mobileOverlay.classList.remove('active');
                    }
                });
                
                usersList.appendChild(userItem);
            });
            
            userCount.textContent = `(${onlineCount + 1})`; // +1 pour l'utilisateur actuel
        }

        // Fonction pour démarrer un chat privé
        function startPrivateChat(userId, userName) {
            currentPrivateChat = userId;
            document.getElementById('chatTitle').innerHTML = `<i class="fas fa-lock"></i> Chat avec ${userName}`;
            document.getElementById('privateChatIndicator').classList.add('active');
            
            // Vider le chat et charger les messages privés
            const messages = zone_chat.querySelectorAll('.message');
            messages.forEach(msg => msg.remove());
            
            loadPrivateMessages(userId);
            showNotification(`Chat privé avec ${userName} démarré 🔒`, 'info');
        }

        // Fonction pour revenir au chat général
        function backToGeneralChat() {
            currentPrivateChat = null;
            document.getElementById('chatTitle').innerHTML = `<i class="fa-solid fa-comment"></i> Discussion générale`;
            document.getElementById('privateChatIndicator').classList.remove('active');
            
            // Vider le chat et charger les messages généraux
            const messages = zone_chat.querySelectorAll('.message');
            messages.forEach(msg => msg.remove());
            
            loadMessages();
            showNotification('Retour au chat général 💬', 'info');
        }

        // Double clic sur le titre pour revenir au chat général
        document.getElementById('chatTitle').addEventListener('dblclick', () => {
            if (currentPrivateChat) {
                backToGeneralChat();
            }
        });

        // Fonction d'envoi de message
        async function envoyerMessage() {
            const messageText = message.value.trim();
            const hasImage = document.getElementById('photoPreview').style.display !== 'none';

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
                    userId: currentUser.email, // Utiliser l'email comme identifiant cohérent
                    isAnonymous: isAnonymous,
                    isPrivate: !!currentPrivateChat,
                    recipientId: currentPrivateChat || null
                };

                if (hasImage) {
                    messageData.image = document.getElementById('photoPreview').src;
                }

                if (replyingTo) {
                    messageData.replyTo = replyingTo;
                }

                // Choisir la collection appropriée
                const collectionName = currentPrivateChat ? "privateMessages" : "messages";
                await addDoc(collection(db, collectionName), messageData);
                
                // Réinitialiser les champs
                message.value = '';
                document.getElementById('photoPreview').style.display = 'none';
                document.getElementById('photoPreview').src = '';
                replyingTo = null;
                document.getElementById('replyIndicator').style.display = 'none';
                
                showNotification('Message envoyé ! ✅', 'info');
                
            } catch (error) {
                console.error("Erreur envoi message:", error);
                showNotification("Erreur lors de l'envoi du message", 'error');
            }
        }

        // Fonction pour charger les messages généraux
        function loadMessages() {
            const messagesQuery = query(
                collection(db, "messages"), 
                orderBy("timestamp", "asc"),
                limit(50)
            );

            onSnapshot(messagesQuery, (snapshot) => {
                snapshot.docChanges().forEach((change) => {
                    if (change.type === "added" && !currentPrivateChat) {
                        const messageData = { ...change.doc.data(), id: change.doc.id };
                        
                        // Ne pas afficher si c'est un message privé
                        if (messageData.isPrivate) return;
                        
                        const isSent = auth.currentUser && messageData.userId === auth.currentUser.uid;
                        const messageElement = createMessageElement(messageData, isSent);
                        
                        // Insérer avant les éléments de contrôle
                        const controlElements = zone_chat.querySelectorAll('#photoPreview, .emo');
                        if (controlElements.length > 0) {
                            zone_chat.insertBefore(messageElement, controlElements[0]);
                        } else {
                            zone_chat.appendChild(messageElement);
                        }
                        
                        scrollToBottom();
                    }
                });
            });
        }

        // Fonction pour charger les messages privés
        function loadPrivateMessages(userId) {
            const messagesQuery = query(
                collection(db, "privateMessages"),
                orderBy("timestamp", "asc"),
                limit(50)
            );

            onSnapshot(messagesQuery, (snapshot) => {
                const existingMessageIds = new Set();
                const existingMessages = zone_chat.querySelectorAll('.message');
                existingMessages.forEach(msg => {
                    if (msg.dataset.messageId) {
                        existingMessageIds.add(msg.dataset.messageId);
                    }
                });

                snapshot.docChanges().forEach((change) => {
                    if (change.type === "added") {
                        const messageData = { ...change.doc.data(), id: change.doc.id };
                        
                        // Vérifier si le message n'existe pas déjà
                        if (existingMessageIds.has(messageData.id)) return;
                        
                        // Debug: afficher les IDs pour vérifier
                        console.log('Message data:', {
                            messageUserId: messageData.userId,
                            messageRecipientId: messageData.recipientId,
                            currentUserEmail: currentUser?.email,
                            targetUserId: userId
                        });
                        
                        // Afficher seulement les messages entre l'utilisateur actuel et l'utilisateur sélectionné
                        const isConversationMessage = 
                            (messageData.userId === currentUser?.email && messageData.recipientId === userId) ||
                            (messageData.recipientId === currentUser?.email && messageData.userId === userId);
                        
                        if (isConversationMessage) {
                            const isSent = messageData.userId === currentUser?.email;
                            const messageElement = createMessageElement(messageData, isSent);
                            messageElement.dataset.messageId = messageData.id;
                            
                            const controlElements = zone_chat.querySelectorAll('#photoPreview, .emo');
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

            // Écouter les nouveaux messages privés pour les notifications
            onSnapshot(query(collection(db, "privateMessages"), orderBy("timestamp", "asc")), (snapshot) => {
                snapshot.docChanges().forEach((change) => {
                    if (change.type === "added") {
                        const messageData = change.doc.data();
                    }
                });
            });
        }         
        // Fonction pour écouter les notifications de messages privés
        function listenToPrivateNotifications() {
            onSnapshot(query(collection(db, "privateMessages"), orderBy("timestamp", "asc")), (snapshot) => {
                snapshot.docChanges().forEach((change) => {
                    if (change.type === "added") {
                        const messageData = change.doc.data();
                        
                        // Si c'est un message privé pour l'utilisateur actuel et qu'il n'est pas dans ce chat
                        if (messageData.recipientId === currentUser?.email && 
                            messageData.userId !== currentUser?.email &&
                            currentPrivateChat !== messageData.userId) {
                            
                            // Incrémenter les notifications
                            const currentCount = privateChatNotifications.get(messageData.userId) || 0;
                            privateChatNotifications.set(messageData.userId, currentCount + 1);
                            updateUsersList();
                            
                            showNotification(`Nouveau message privé de ${messageData.auteur} 💌`, 'info');
                        }
                    }
                });
            });
        }

        // Fonction pour gérer les utilisateurs connectés
        function manageConnectedUsers() {
            if (!currentUser) return;

            // Ajouter l'utilisateur actuel à la liste
            const userRef = doc(db, "connectedUsers", currentUser.email);
            setDoc(userRef, {
                nom: currentUser.nom,
                email: currentUser.email,
                lastSeen: Date.now(),
                isOnline: true
            });

            // Écouter les changements d'utilisateurs connectés
            onSnapshot(collection(db, "connectedUsers"), (snapshot) => {
                const previousUsers = new Set(connectedUsers.keys());
                connectedUsers.clear();

                snapshot.forEach((doc) => {
                    const userData = doc.data();
                    const userId = doc.id;
                    
                    // Considérer comme en ligne si vu dans les 30 dernières secondes
                    if (Date.now() - userData.lastSeen < 30000) {
                        connectedUsers.set(userId, userData);
                        
                        // Si c'est un nouvel utilisateur
                        if (!previousUsers.has(userId) && userId !== currentUser.email) {
                            addSystemMessage(`${userData.nom} a rejoint le chat 👋`);
                        }
                    }
                });

                updateUsersList();
            });

            // Mettre à jour la présence toutes les 15 secondes
            setInterval(() => {
                if (currentUser) {
                    updateDoc(doc(db, "connectedUsers", currentUser.email), {
                        lastSeen: Date.now()
                    });
                }
            }, 15000);
        }

        // Fonction pour ajouter un message système
        function addSystemMessage(text) {
            if (currentPrivateChat) return; // Ne pas afficher dans les chats privés

            const systemMessage = {
                text: text,
                timestamp: Date.now(),
                isSystem: true,
                auteur: 'Système'
            };

            const messageElement = createMessageElement(systemMessage, false);
            
            const controlElements = zone_chat.querySelectorAll('#photoPreview, .emo');
            if (controlElements.length > 0) {
                zone_chat.insertBefore(messageElement, controlElements[0]);
            } else {
                zone_chat.appendChild(messageElement);
            }
            
            scrollToBottom();
        }

        // Gestion de la connexion
        inscription.addEventListener('click', async function() {
            const nom = document.getElementById('nom').value.trim();
            const email = document.getElementById('email').value.trim();
            const motdepasse = document.getElementById('motdepasse').value;

            // Validation des champs
            if (!nom || !email || !motdepasse) {
                showNotification('Veuillez remplir tous les champs', 'error');
                return;
            }

            if (nom.length < 2) {
                showNotification('Le nom doit contenir au moins 2 caractères', 'error');
                return;
            }

            inscription.disabled = true;
            inscription.textContent = 'Connexion...';

            try {
                // Essayer de se connecter d'abord
                try {
                    await signInWithEmailAndPassword(auth, email, motdepasse);
                    showNotification('Connexion réussie ! 🎉', 'info');
                } catch (signInError) {
                    // Si la connexion échoue, créer un nouveau compte
                    if (signInError.code === 'auth/user-not-found' || signInError.code === 'auth/wrong-password') {
                        await createUserWithEmailAndPassword(auth, email, motdepasse);
                        showNotification('Compte créé et connecté avec succès ! 💪', 'info');
                        
                        // Sauvegarder les informations utilisateur
                        await setDoc(doc(db, "users", email), {
                            nom: nom,
                            email: email,
                            dateCreation: Date.now()
                        });
                    } else {
                        throw signInError;
                    }
                }

                currentUser = { nom, email };
                document.getElementById('currentUserName').textContent = nom;
                connexionDiv.style.display = 'none';
                letousDiv.style.display = 'block';
                
                // Gérer les utilisateurs connectés et charger les messages
                manageConnectedUsers();
                loadMessages();
                listenToPrivateNotifications();
                
            } catch (error) {
                console.error('Erreur:', error);
                let errorMessage = 'Erreur lors de la connexion';
                
                if (error.code === 'auth/email-already-in-use') {
                    errorMessage = 'Cette adresse email est déjà utilisée';
                } else if (error.code === 'auth/weak-password') {
                    errorMessage = 'Le mot de passe est trop faible';
                } else if (error.code === 'auth/invalid-email') {
                    errorMessage = 'Adresse email invalide';
                }
                
                showNotification(errorMessage, 'error');
            } finally {
                inscription.disabled = false;
                inscription.innerHTML = '<i class="fas fa-sign-in-alt"></i> Se connecter';
            }
        });

        // Gestion de la déconnexion
        document.getElementById('deconnexion').addEventListener('click', async function() {
            try {
                // Marquer comme déconnecté
                if (currentUser) {
                    await updateDoc(doc(db, "connectedUsers", currentUser.email), {
                        isOnline: false,
                        lastSeen: Date.now()
                    });
                }
                
                await auth.signOut();
                showNotification('Vous avez été déconnecté avec succès ! 👋', 'info');
                connexionDiv.style.display = 'block';
                letousDiv.style.display = 'none';
                zone_chat.innerHTML = '';
                currentUser = null;
                currentPrivateChat = null;
                connectedUsers.clear();
                privateChatNotifications.clear();
            } catch (error) {
                console.error('Erreur lors de la déconnexion:', error);
                showNotification('Erreur lors de la déconnexion', 'error');
            }
        });

        // Mode anonyme
        document.getElementById('modeAnonyme').addEventListener('click', function() {
            isAnonymous = !isAnonymous;
            const btn = this;
            if (isAnonymous) {
                btn.innerHTML = '<i class="fas fa-user"></i> <span>Mode normal</span>';
                btn.style.background = 'linear-gradient(135deg, #e74c3c 0%, #c0392b 100%)';
                showNotification('Mode anonyme activé 🥸', 'info');
            } else {
                btn.innerHTML = '<i class="fas fa-user-secret"></i> <span>Mode anonyme</span>';
                btn.style.background = 'linear-gradient(135deg, #9b59b6 0%, #8e44ad 100%)';
                showNotification('Mode normal activé 👤', 'info');
            }
        });

        // Gestion des images
        document.getElementById('image').addEventListener('click', () => {
            document.getElementById('camer').click();
        });
        
        document.getElementById('camer').addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function() {
                document.getElementById('photoPreview').src = reader.result;
                document.getElementById('photoPreview').style.display = 'block';
                showNotification('Image sélectionnée ! 📸', 'info');
            };
            reader.readAsDataURL(file);
        });

        // Gestion des emojis
        document.getElementById('emoji').addEventListener('click', function() {
            const emoDiv = document.getElementById('emo');
            emoDiv.style.display = emoDiv.style.display === 'block' ? 'none' : 'block';
        });

        document.getElementById('emo').querySelectorAll('span').forEach(span => {
            span.addEventListener('click', function() {
                message.value += span.textContent;
                document.getElementById('emo').style.display = 'none';
                message.focus();
            });
        });

        // Events
        document.getElementById('envoi').addEventListener('click', envoyerMessage);

        message.addEventListener('keypress', function(e) {
            if (e.key === 'Enter' && !e.shiftKey) {
                e.preventDefault();
                envoyerMessage();
            }
        });

        // Fermer les emojis en cliquant ailleurs
        document.addEventListener('click', function(e) {
            if (!e.target.closest('#emoji') && !e.target.closest('.emo')) {
                document.getElementById('emo').style.display = 'none';
            }
        });

        // Notification de bienvenue
        setTimeout(() => {
            showNotification("Bienvenue dans BTS Niveau 2 de la PERLE ❤️", "info");
        }, 1000);

        // Messages de bienvenue automatiques
        setTimeout(() => {
            if (currentUser && !currentPrivateChat) {
                addSystemMessage("👋 Bienvenue ! Cliquez sur un utilisateur pour discuter en privé");
            }
        }, 3000);

    </script>
</body>

</html>
