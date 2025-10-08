
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bulletin de Notes - Système Moderne</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #667eea;
            --primary-dark: #5568d3;
            --secondary: #764ba2;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --info: #3b82f6;
            --bg-light: #f8fafc;
            --bg-card: #ffffff;
            --text-dark: #1e293b;
            --text-light: #64748b;
            --border: #e2e8f0;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
            --gradient: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
        }

        [data-theme="dark"] {
            --bg-light: #0f172a;
            --bg-card: #1e293b;
            --text-dark: #f1f5f9;
            --text-light: #94a3b8;
            --border: #334155;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.3);
            --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.3);
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            background: white;
            min-height: 100vh;
            padding: 20px;
            transition: all 0.3s ease;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        .header {
            background: var(--bg-card);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: var(--shadow-lg);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient);
        }

        .header-title {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .header-title i {
            font-size: 40px;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .header-title h1 {
            color: var(--text-dark);
            font-size: 32px;
            font-weight: 700;
        }

        .header-controls {
            display: flex;
            gap: 15px;
            align-items: center;
            flex-wrap: wrap;
        }

        .theme-toggle, .export-btn {
            background: var(--bg-light);
            border: 2px solid var(--border);
            border-radius: 50px;
            padding: 12px 20px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            color: var(--text-dark);
            font-size: 14px;
            font-weight: 500;
        }

        .theme-toggle:hover, .export-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow);
            border-color: var(--primary);
        }

        .card {
            background: var(--bg-card);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: var(--shadow-lg);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .card:hover::before {
            transform: scaleX(1);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }

        .card-title {
            color: var(--text-dark);
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .student-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .input-group {
            position: relative;
        }

        .input-group label {
            display: block;
            color: var(--text-light);
            font-size: 14px;
            font-weight: 500;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .input-group input, .input-group select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid var(--border);
            border-radius: 10px;
            font-size: 16px;
            color: var(--text-dark);
            background: var(--bg-light);
            transition: all 0.3s ease;
        }

        .input-group input:focus, .input-group select:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .photo-upload {
            text-align: center;
            padding: 30px;
            border: 2px dashed var(--border);
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .photo-upload:hover {
            border-color: var(--primary);
            background: var(--bg-light);
            transform: translateY(-2px);
        }

        .photo-upload i {
            font-size: 48px;
            color: var(--text-light);
            margin-bottom: 10px;
            transition: all 0.3s ease;
        }

        .photo-upload:hover i {
            color: var(--primary);
            transform: scale(1.1);
        }

        .grades-section {
            display: grid;
            grid-template-columns: 1fr auto;
            gap: 30px;
            align-items: start;
        }

        .grades-table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0 10px;
        }

        .grades-table thead th {
            color: var(--text-dark);
            font-weight: 600;
            text-align: left;
            padding: 15px;
            background: var(--bg-light);
            border-radius: 10px;
            position: sticky;
            top: 0;
        }

        .grades-table tbody tr {
            background: var(--bg-light);
            transition: all 0.3s ease;
            position: relative;
        }

        .grades-table tbody tr:hover {
            transform: scale(1.02);
            box-shadow: var(--shadow);
        }

        .grades-table tbody td {
            padding: 15px;
            color: var(--text-dark);
        }

        .grades-table tbody tr td:first-child {
            border-radius: 10px 0 0 10px;
            font-weight: 600;
        }

        .grades-table tbody tr td:last-child {
            border-radius: 0 10px 10px 0;
        }

        .grades-table input {
            width: 100%;
            padding: 10px;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-size: 16px;
            color: var(--text-dark);
            background: var(--bg-card);
            text-align: center;
            transition: all 0.3s ease;
        }

        .grades-table input:focus {
            outline: none;
            border-color: var(--primary);
            transform: scale(1.05);
        }

        .quick-stats {
            background: var(--bg-light);
            border-radius: 15px;
            padding: 25px;
            min-width: 300px;
        }

        .stat-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
            border-bottom: 1px solid var(--border);
        }

        .stat-item:last-child {
            border-bottom: none;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 14px;
        }

        .stat-value {
            font-size: 18px;
            font-weight: 600;
            color: var(--text-dark);
        }

        .results-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .result-card {
            background: var(--bg-light);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .result-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow);
        }

        .result-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: var(--gradient);
        }

        .result-icon {
            font-size: 40px;
            margin-bottom: 15px;
            opacity: 0.8;
        }

        .result-label {
            color: var(--text-light);
            font-size: 14px;
            font-weight: 500;
            text-transform: uppercase;
            margin-bottom: 10px;
        }

        .result-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--text-dark);
            margin-bottom: 10px;
        }

        .result-subtext {
            color: var(--text-light);
            font-size: 12px;
        }

        .appreciation-badge {
            padding: 12px 25px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            color: white;
            display: inline-block;
            margin-top: 10px;
        }

        .progress-ring {
            position: relative;
            width: 120px;
            height: 120px;
            margin: 0 auto 20px;
        }

        .progress-bg {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: var(--border);
            position: relative;
        }

        .progress-fill {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            clip: rect(0, 60px, 120px, 0);
            background: var(--gradient);
            transform: rotate(0deg);
            transition: transform 1s ease;
        }

        .progress-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            font-weight: 700;
            color: var(--text-dark);
        }

        .btn-primary {
            background: var(--gradient);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .btn-primary:hover::before {
            left: 100%;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(102, 126, 234, 0.3);
        }

        .btn-secondary {
            background: var(--bg-light);
            color: var(--text-dark);
            border: 2px solid var(--border);
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn-secondary:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow);
            border-color: var(--primary);
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
            margin-top: 30px;
        }

        .history-section {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid var(--border);
        }

        .history-list {
            max-height: 200px;
            overflow-y: auto;
        }

        .history-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 15px;
            background: var(--bg-light);
            border-radius: 10px;
            margin-bottom: 10px;
            transition: all 0.3s ease;
        }

        .history-item:hover {
            transform: translateX(5px);
        }

        .footer {
            text-align: center;
            color: white;
            margin-top: 40px;
            font-size: 14px;
            opacity: 0.8;
        }

        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background: var(--primary);
            opacity: 0;
            pointer-events: none;
        }

        @media (max-width: 1024px) {
            .grades-section {
                grid-template-columns: 1fr;
            }
            
            .quick-stats {
                min-width: auto;
            }
        }

        @media (max-width: 768px) {
            .header-title h1 {
                font-size: 24px;
            }

            .grades-table {
                font-size: 14px;
            }

            .action-buttons {
                flex-direction: column;
            }

            .btn-primary, .btn-secondary {
                width: 100%;
                justify-content: center;
            }

            .student-info {
                grid-template-columns: 1fr;
            }
        }

        @media print {
            body {
                background: white;
            }
            .header-controls, .action-buttons, .export-btn {
                display: none;
            }
            .card {
                box-shadow: none;
                border: 1px solid #ddd;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="header-title">
                <i class="fas fa-graduation-cap"></i>
                <h1>Bulletin de Notes - Système Moderne</h1>
            </div>
            <div class="header-controls">
                <button class="theme-toggle" onclick="toggleTheme()">
                    <i class="fas fa-moon" id="themeIcon"></i>
                    <span id="themeText">Mode Sombre</span>
                </button>
                <button class="export-btn" onclick="exporterPDF()">
                    <i class="fas fa-file-pdf"></i>
                    Exporter PDF
                </button>
            </div>
        </div>

        <div class="card">
            <h2 class="card-title">
                <i class="fas fa-user-graduate"></i>
                Informations de l'Étudiant
            </h2>
            <div class="student-info">
                <div class="input-group">
                    <label>Nom</label>
                    <input type="text" id="nom" placeholder="Entrez le nom">
                </div>
                <div class="input-group">
                    <label>Prénom</label>
                    <input type="text" id="prenom" placeholder="Entrez le prénom">
                </div>
                <div class="input-group">
                    <label>Matricule</label>
                    <input type="text" id="matricule" placeholder="Entrez le matricule">
                </div>
                <div class="input-group">
                    <label>Classe</label>
                    <select id="classe">
                        <option value="">Sélectionnez la classe</option>
                        <option value="6ème">6ème</option>
                        <option value="5ème">5ème</option>
                        <option value="4ème">4ème</option>
                        <option value="3ème">3ème</option>
                        <option value="2nde">2nde</option>
                        <option value="1ère">1ère</option>
                        <option value="Tle">Terminale</option>
                    </select>
                </div>
                <div class="input-group">
                    <label>Année Scolaire</label>
                    <input type="text" id="annee" placeholder="2024-2025" value="2024-2025">
                </div>
                <div class="input-group">
                    <label>Date de Naissance</label>
                    <input type="date" id="dateNaissance">
                </div>
            </div>
        </div>

        <div class="card">
            <h2 class="card-title">
                <i class="fas fa-book-open"></i>
                Notes par Matière
            </h2>
            <div class="grades-section">
                <table class="grades-table">
                    <thead>
                        <tr>
                            <th>Matière</th>
                            <th>Note (/20)</th>
                            <th>Coefficient</th>
                            <th>Note × Coef</th>
                            <th>Appréciation</th>
                        </tr>
                    </thead>
                    <tbody id="matieresBody">
                        <!-- Les matières seront générées dynamiquement -->
                    </tbody>
                </table>
                
                <div class="quick-stats">
                    <h3 style="color: var(--text-dark); margin-bottom: 20px; text-align: center;">
                        <i class="fas fa-chart-pie"></i> Statistiques Rapides
                    </h3>
                    <div class="stat-item">
                        <span class="stat-label">Matières saisies</span>
                        <span class="stat-value" id="matieresSaisies">0</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">Moyenne provisoire</span>
                        <span class="stat-value" id="moyenneProvisoire">-</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">Meilleure note</span>
                        <span class="stat-value" id="meilleureNote">-</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-label">Plus faible</span>
                        <span class="stat-value" id="plusFaibleNote">-</span>
                    </div>
                    <button class="btn-secondary" onclick="ajouterMatiere()" style="width: 100%; margin-top: 15px;">
                        <i class="fas fa-plus"></i> Ajouter Matière
                    </button>
                </div>
            </div>
        </div>

        <div class="card">
            <h2 class="card-title">
                <i class="fas fa-trophy"></i>
                Résultats Finaux
            </h2>
            
            <div class="results-grid">
                <div class="result-card">
                    <div class="progress-ring">
                        <div class="progress-bg"></div>
                        <div class="progress-fill" id="progressFill"></div>
                        <div class="progress-text" id="moyenneFinale">-</div>
                    </div>
                    <div class="result-label">Moyenne Générale</div>
                    <div class="result-subtext">sur 20 points</div>
                </div>

                <div class="result-card">
                    <div class="result-icon">📊</div>
                    <div class="result-value" id="totalPoints">-</div>
                    <div class="result-label">Total Points</div>
                    <div class="result-subtext">Somme notes × coefficients</div>
                </div>

                <div class="result-card">
                    <div class="result-icon">⭐</div>
                    <div class="result-value" id="mention">-</div>
                    <div class="result-label">Mention</div>
                    <div class="appreciation-badge" id="mentionBadge" style="background: var(--text-light);">-</div>
                </div>

                <div class="result-card">
                    <div class="result-icon">🎯</div>
                    <div class="result-value" id="decision">-</div>
                    <div class="result-label">Décision</div>
                    <div class="result-subtext" id="decisionSubtext">-</div>
                </div>
            </div>

            <div class="history-section">
                <h3 style="color: var(--text-dark); margin-bottom: 15px;">
                    <i class="fas fa-history"></i> Historique des Calculs
                </h3>
                <div class="history-list" id="historyList">
                    <!-- L'historique sera généré ici -->
                </div>
            </div>

            <div class="action-buttons">
                <button class="btn-primary" onclick="calculerResultats()">
                    <i class="fas fa-calculator"></i>
                    Calculer les Résultats
                </button>
                <button class="btn-secondary" onclick="reinitialiserTout()">
                    <i class="fas fa-redo"></i>
                    Tout Réinitialiser
                </button>
                <button class="btn-secondary" onclick="imprimerBulletin()">
                    <i class="fas fa-print"></i>
                    Imprimer le Bulletin
                </button>
                <button class="btn-secondary" onclick="sauvegarderDonnees()">
                    <i class="fas fa-save"></i>
                    Sauvegarder
                </button>
            </div>
        </div>

        <div class="footer">
            <p><i class="fas fa-copyright"></i> 2025 - Système de Bulletin Moderne | Développé avec <i class="fas fa-heart" style="color: #ef4444;"></i></p>
        </div>
    </div>

    <script>
        // Configuration initiale
        const matieresParDefaut = [
            { nom: 'Mathématiques', coef: 4, note: '' },
            { nom: 'Physique', coef: 3, note: '' },
            { nom: 'Chimie', coef: 3, note: '' },
            { nom: 'Biologie', coef: 2, note: '' },
            { nom: 'Anglais', coef: 2, note: '' },
            { nom: 'Français', coef: 3, note: '' },
            { nom: 'Histoire-Géo', coef: 2, note: '' },
            { nom: 'Philosophie', coef: 2, note: '' }
        ];

        let matieres = JSON.parse(localStorage.getItem('matieres')) || [...matieresParDefaut];
        let historique = JSON.parse(localStorage.getItem('historique')) || [];

        // Initialisation
        document.addEventListener('DOMContentLoaded', function() {
            initialiserMatieres();
            mettreAJourStatsRapides();
            chargerHistorique();
            chargerDonneesEtudiant();
        });

        function initialiserMatieres() {
            const tbody = document.getElementById('matieresBody');
            tbody.innerHTML = '';

            matieres.forEach((matiere, index) => {
                const appreciation = matiere.note ? getAppreciation(matiere.note) : '-';
                const row = `
                    <tr>
                        <td>
                            <i class="fas fa-book"></i>
                            <input type="text" value="${matiere.nom}" onchange="mettreAJourMatiere(${index}, 'nom', this.value)" style="border: none; background: transparent; font-weight: 600; color: var(--text-dark);">
                        </td>
                        <td><input type="number" value="${matiere.note}" min="0" max="20" step="0.25" onchange="mettreAJourMatiere(${index}, 'note', this.value)" oninput="mettreAJourStatsRapides()"></td>
                        <td><input type="number" value="${matiere.coef}" min="1" max="10" onchange="mettreAJourMatiere(${index}, 'coef', this.value)" oninput="mettreAJourStatsRapides()"></td>
                        <td><span class="total-matiere">${matiere.note ? (matiere.note * matiere.coef).toFixed(2) : '-'}</span></td>
                        <td><span class="appreciation" style="color: ${getAppreciationColor(matiere.note)}">${appreciation}</span></td>
                        <td><button onclick="supprimerMatiere(${index})" style="background: none; border: none; color: var(--danger); cursor: pointer;"><i class="fas fa-trash"></i></button></td>
                    </tr>
                `;
                tbody.innerHTML += row;
            });
        }

        function mettreAJourMatiere(index, champ, valeur) {
            matieres[index][champ] = champ === 'note' || champ === 'coef' ? parseFloat(valeur) || 0 : valeur;
            sauvegarderMatieres();
            mettreAJourStatsRapides();
        }

        function ajouterMatiere() {
            matieres.push({ nom: 'Nouvelle Matière', coef: 1, note: '' });
            initialiserMatieres();
            mettreAJourStatsRapides();
        }

        function supprimerMatiere(index) {
            if (matieres.length > 1) {
                matieres.splice(index, 1);
                initialiserMatieres();
                mettreAJourStatsRapides();
            } else {
                alert('Vous devez avoir au moins une matière !');
            }
        }

        function mettreAJourStatsRapides() {
            const notesSaisies = matieres.filter(m => m.note && m.note > 0).length;
            const notes = matieres.filter(m => m.note).map(m => parseFloat(m.note));
            
            document.getElementById('matieresSaisies').textContent = notesSaisies;

            if (notes.length > 0) {
                const moyenne = notes.reduce((a, b) => a + b, 0) / notes.length;
                document.getElementById('moyenneProvisoire').textContent = moyenne.toFixed(2);
                document.getElementById('meilleureNote').textContent = Math.max(...notes).toFixed(1);
                document.getElementById('plusFaibleNote').textContent = Math.min(...notes).toFixed(1);
            } else {
                document.getElementById('moyenneProvisoire').textContent = '-';
                document.getElementById('meilleureNote').textContent = '-';
                document.getElementById('plusFaibleNote').textContent = '-';
            }

            // Mettre à jour les totaux par matière
            document.querySelectorAll('.total-matiere').forEach((span, index) => {
                const matiere = matieres[index];
                span.textContent = matiere.note ? (matiere.note * matiere.coef).toFixed(2) : '-';
            });

            // Mettre à jour les appréciations
            document.querySelectorAll('.appreciation').forEach((span, index) => {
                const matiere = matieres[index];
                span.textContent = matiere.note ? getAppreciation(matiere.note) : '-';
                span.style.color = getAppreciationColor(matiere.note);
            });
        }

        function calculerResultats() {
            let totalPoints = 0;
            let totalCoef = 0;
            let notesValides = 0;

            matieres.forEach(matiere => {
                if (matiere.note && matiere.note > 0) {
                    totalPoints += matiere.note * matiere.coef;
                    totalCoef += matiere.coef;
                    notesValides++;
                }
            });

            const moyenne = totalCoef > 0 ? totalPoints / totalCoef : 0;

            // Mettre à jour l'interface
            document.getElementById('totalPoints').textContent = totalPoints.toFixed(2);
            document.getElementById('moyenneFinale').textContent = moyenne.toFixed(2);

            // Animation du cercle de progression
            const progressFill = document.getElementById('progressFill');
            const rotation = (moyenne / 20) * 360;
            progressFill.style.transform = `rotate(${rotation}deg)`;

            // Déterminer la mention
            let mention = '';
            let couleurMention = '';
            
            if (moyenne >= 18) {
                mention = 'Très Bien';
                couleurMention = '#10b981';
            } else if (moyenne >= 16) {
                mention = 'Bien';
                couleurMention = '#22c55e';
            } else if (moyenne >= 14) {
                mention = 'Assez Bien';
                couleurMention = '#f59e0b';
            } else if (moyenne >= 12) {
                mention = 'Passable';
                couleurMention = '#3b82f6';
            } else if (moyenne >= 10) {
                mention = 'Admis';
                couleurMention = '#6366f1';
            } else {
                mention = 'Insuffisant';
                couleurMention = '#ef4444';
            }

            document.getElementById('mention').textContent = mention;
            const mentionBadge = document.getElementById('mentionBadge');
            mentionBadge.textContent = mention;
            mentionBadge.style.background = couleurMention;

            // Décision finale
            const decision = moyenne >= 10 ? 'ADMIS(E)' : 'REDOUBLANT(E)';
            const decisionColor = moyenne >= 10 ? '#10b981' : '#ef4444';
            document.getElementById('decision').textContent = decision;
            document.getElementById('decision').style.color = decisionColor;
            document.getElementById('decisionSubtext').textContent = moyenne >= 10 ? 'Félicitations !' : 'Doit mieux travailler';

            // Ajouter à l'historique
            const now = new Date();
            const historiqueItem = {
                date: now.toLocaleString(),
                moyenne: moyenne.toFixed(2),
                mention: mention,
                decision: decision
            };
            historique.unshift(historiqueItem);
            if (historique.length > 5) historique.pop();
            
            sauvegarderHistorique();
            chargerHistorique();

            // Célébration si admis
            if (moyenne >= 10) {
                celebrerReussite();
            }

            // Sauvegarder les données
            sauvegarderDonneesEtudiant();
        }

        function getAppreciation(note) {
            if (!note) return '-';
            if (note >= 18) return 'Excellent';
            if (note >= 16) return 'Très Bien';
            if (note >= 14) return 'Bien';
            if (note >= 12) return 'Assez Bien';
            if (note >= 10) return 'Passable';
            if (note >= 8) return 'Insuffisant';
            if (note >= 6) return 'Faible';
            return 'Très Faible';
        }

        function getAppreciationColor(note) {
            if (!note) return 'var(--text-light)';
            if (note >= 16) return '#10b981';
            if (note >= 14) return '#22c55e';
            if (note >= 12) return '#f59e0b';
            if (note >= 10) return '#3b82f6';
            if (note >= 8) return '#ef4444';
            return '#dc2626';
        }

        function celebrerReussite() {
            // Animation des cartes de résultats
            const resultCards = document.querySelectorAll('.result-card');
            resultCards.forEach((card, index) => {
                setTimeout(() => {
                    card.style.transform = 'scale(1.1)';
                    setTimeout(() => {
                        card.style.transform = 'scale(1)';
                    }, 300);
                }, index * 100);
            });

            // Confettis simples
            for (let i = 0; i < 20; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    confetti.style.left = Math.random() * 100 + 'vw';
                    confetti.style.background = `hsl(${Math.random() * 360}, 70%, 60%)`;
                    confetti.style.opacity = '1';
                    document.body.appendChild(confetti);

                    setTimeout(() => {
                        confetti.style.transition = 'all 1s ease';
                        confetti.style.transform = `translateY(100vh) rotate(${Math.random() * 360}deg)`;
                        confetti.style.opacity = '0';
                        
                        setTimeout(() => {
                            document.body.removeChild(confetti);
                        }, 1000);
                    }, 100);
                }, i * 100);
            }
        }

        function chargerHistorique() {
            const historyList = document.getElementById('historyList');
            historyList.innerHTML = '';

            historique.forEach(item => {
                const historyItem = document.createElement('div');
                historyItem.className = 'history-item';
                historyItem.innerHTML = `
                    <div>
                        <strong>${item.date}</strong>
                        <div style="font-size: 12px; color: var(--text-light);">Moyenne: ${item.moyenne}</div>
                    </div>
                    <div style="color: ${item.decision.includes('ADMIS') ? '#10b981' : '#ef4444'}; font-weight: 600;">
                        ${item.decision}
                    </div>
                `;
                historyList.appendChild(historyItem);
            });
        }

        function toggleTheme() {
            const html = document.documentElement;
            const currentTheme = html.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            html.setAttribute('data-theme', newTheme);
            
            const icon = document.getElementById('themeIcon');
            const text = document.getElementById('themeText');
            
            if (newTheme === 'dark') {
                icon.className = 'fas fa-sun';
                text.textContent = 'Mode Clair';
            } else {
                icon.className = 'fas fa-moon';
                text.textContent = 'Mode Sombre';
            }
            
            localStorage.setItem('theme', newTheme);
        }

        function reinitialiserTout() {
            if (confirm('Êtes-vous sûr de vouloir tout réinitialiser ?')) {
                matieres = [...matieresParDefaut];
                historique = [];
                initialiserMatieres();
                mettreAJourStatsRapides();
                chargerHistorique();
                
                // Réinitialiser les champs étudiant
                document.getElementById('nom').value = '';
                document.getElementById('prenom').value = '';
                document.getElementById('matricule').value = '';
                document.getElementById('classe').value = '';
                document.getElementById('dateNaissance').value = '';
                
                localStorage.removeItem('matieres');
                localStorage.removeItem('historique');
                localStorage.removeItem('etudiant');
            }
        }

        function imprimerBulletin() {
            window.print();
        }

        function exporterPDF() {
            alert('Fonctionnalité PDF à implémenter - Export des données en cours...');
            // Ici, vous pourriez intégrer une bibliothèque comme jsPDF
        }

        function sauvegarderDonnees() {
            sauvegarderMatieres();
            sauvegarderHistorique();
            sauvegarderDonneesEtudiant();
            alert('Données sauvegardées avec succès !');
        }

        function sauvegarderMatieres() {
            localStorage.setItem('matieres', JSON.stringify(matieres));
        }

        function sauvegarderHistorique() {
            localStorage.setItem('historique', JSON.stringify(historique));
        }

        function sauvegarderDonneesEtudiant() {
            const etudiant = {
                nom: document.getElementById('nom').value,
                prenom: document.getElementById('prenom').value,
                matricule: document.getElementById('matricule').value,
                classe: document.getElementById('classe').value,
                annee: document.getElementById('annee').value,
                dateNaissance: document.getElementById('dateNaissance').value
            };
            localStorage.setItem('etudiant', JSON.stringify(etudiant));
        }

        function chargerDonneesEtudiant() {
            const etudiant = JSON.parse(localStorage.getItem('etudiant'));
            if (etudiant) {
                document.getElementById('nom').value = etudiant.nom || '';
                document.getElementById('prenom').value = etudiant.prenom || '';
                document.getElementById('matricule').value = etudiant.matricule || '';
                document.getElementById('classe').value = etudiant.classe || '';
                document.getElementById('annee').value = etudiant.annee || '2024-2025';
                document.getElementById('dateNaissance').value = etudiant.dateNaissance || '';
            }

            // Charger le thème sauvegardé
            const savedTheme = localStorage.getItem('theme') || 'light';
            document.documentElement.setAttribute('data-theme', savedTheme);
            if (savedTheme === 'dark') {
                document.getElementById('themeIcon').className = 'fas fa-sun';
                document.getElementById('themeText').textContent = 'Mode Clair';
            }
        }

        // Raccourci clavier
        document.addEventListener('keydown', function(e) {
            if (e.ctrlKey && e.key === 'Enter') {
                calculerResultats();
            }
        });
    </script>
</body>
