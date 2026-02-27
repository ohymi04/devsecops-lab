# 🚀 DevSecOps Lab

![Security](https://github.com/ohymi04/devsecops-lab/workflows/DevSecOps%20Pipeline/badge.svg)

## 📝 Description

Ce projet est un **laboratoire DevSecOps** avec une API Node.js sécurisée et une CI/CD complète :

- Backend : Node.js + Express  
- Sécurité : JWT, Helmet, rate limiting, validation des entrées  
- CI/CD : GitHub Actions avec SAST, SCA, CodeQL, container scan et security gate  
- Frontend : statique (déployé sur GitHub Pages)  

L'objectif est de démontrer les bonnes pratiques DevSecOps avec **analyse automatique de la sécurité**.

---

## 🏗️ Installation

Clonez le projet :

```bash
git clone https://github.com/ohymi04/devsecops-lab.git
cd devsecops-lab
````

Installez les dépendances Node.js :

```bash
cd src
npm install
```

Créez le fichier `.env` :

```env
JWT_SECRET=une_clé_super_secrète_de_32_caractères_min
ADMIN_USER=admin
ADMIN_PASS=adminpassword
```

---

## 🚀 Lancement de l'application

```bash
cd devsecops-lab
docker build -t vuln-app:latest .
docker run -p 3000:3000 vuln-app:latest
```

Testez l'API :

```bash
curl http://localhost:3000/health
# Réponse : { "status": "OK" }
```

---

## 🔒 CI/CD & Sécurité

La pipeline GitHub Actions inclut :

### 1. SAST (Static Application Security Testing)

* Outil : [Semgrep](https://semgrep.dev/)
* Détecte injections SQL, XSS, failles OWASP Top 10 et secrets accidentels

### 2. SCA (Software Composition Analysis)

* Outil : `npm audit`
* Analyse les dépendances Node.js pour détecter les vulnérabilités connues (CVE)

### 3. Secret Detection

* Outil : [Gitleaks](https://github.com/zricethezav/gitleaks)
* Détecte les clés API et tokens accidentellement committés

### 4. Container Scan

* Outil : [Trivy](https://aquasec.com/trivy)
* Scanne l'image Docker pour vulnérabilités dans OS et packages système

### 5. CodeQL

* Analyse avancée du code pour détecter des vulnérabilités complexes
* Intégré dans GitHub Actions

### 6. Security Gate

* Bloque le merge si des vulnérabilités critiques sont détectées
* Garantit que seules les branches sécurisées peuvent être fusionnées

### 7. Rapport final

* Génère un fichier `security-report.json`
* Résume le statut de tous les jobs (SAST, SCA, Secrets, Container Scan, CodeQL, Security Gate)
* Téléchargeable depuis les artifacts GitHub Actions

---

## 🌍 Déploiement Frontend (GitHub Pages)

Le frontend statique est déployé automatiquement :

* Source : `frontend/`
* URL : [https://ohymi04.github.io/devsecops-lab/](https://ohymi04.github.io/devsecops-lab/)

Exemple minimal de `index.html` :

```html
<!DOCTYPE html>
<html>
<head>
  <title>DevSecOps Lab</title>
</head>
<body>
  <h1>🚀 DevSecOps Lab</h1>
  <p>Application sécurisée avec CI/CD</p>
</body>
</html>
```

---

## 📊 Badge de sécurité

![Security](https://github.com/ohymi04/devsecops-lab/workflows/DevSecOps%20Pipeline/badge.svg)

* Vert : tous les scans sont passés
* Rouge : une ou plusieurs vulnérabilités critiques détectées

---

## 🧰 Technologies utilisées

* Node.js & Express
* Docker
* GitHub Actions
* Semgrep, CodeQL, Gitleaks, Trivy
* GitHub Pages (frontend statique)

---

## 💡 Notes

* L’API est containerisée et scannée en CI/CD
* Le frontend statique est déployé automatiquement sur GitHub Pages
* Toutes les vulnérabilités critiques bloquent la fusion via **Security Gate**

```
