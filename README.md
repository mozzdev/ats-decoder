# 🔍 Décodeur ASN.1 pour fichiers ATS/IMS CDR

> **Interface web moderne pour décoder et analyser les fichiers CDR (Call Detail Records) au format ASN.1 IMS/ATS selon la grammaire IMS-R8-2009-03**

## 🚀 Accès direct

### 🌐 Version en ligne
👉 **[Utilisez le décodeur maintenant](https://mozzdev.github.io/ats-decoder)**

*Aucune installation requise - Fonctionne directement dans votre navigateur*

---

## 📋 Table des matières

- [Aperçu](#-aperçu)
- [Fonctionnalités](#-fonctionnalités)
- [Utilisation](#-utilisation)
- [Format supporté](#-format-supporté)
- [Installation locale](#-installation-locale)
- [Technologies](#-technologies)
- [Structure du projet](#-structure-du-projet)
- [Contribution](#-contribution)
- [Licence](#-licence)
- [Support](#-support)

---

## 🎯 Aperçu

Ce projet fournit un **décodeur ASN.1 complet** pour analyser les fichiers CDR (Call Detail Records) générés par les équipements IMS/ATS dans les réseaux de télécommunications. L'outil permet de :

- 📁 **Décoder** les fichiers binaires `.dat`, `.bin`, `.asn1`
- 🔍 **Analyser** la structure des enregistrements ATS
- 📊 **Visualiser** les informations d'appel de manière claire
- ⏱️ **Calculer** les durées et statistiques d'appel
- 💾 **Exporter** les résultats décodés

### Capture d'écran

```
┌─────────────────────────────────────────────────────────────┐
│ 🔍 Décodeur ASN.1                                          │
│ Analyseur de fichiers CDR IMS/ATS selon ASN.1 IMS-R8-2009 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  📁 Sélectionner un fichier CDR                           │
│     Cliquez ici ou glissez-déposez votre fichier .dat     │
│                   [Choisir un fichier]                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## ✨ Fonctionnalités

### 🔧 Décodage ASN.1
- ✅ **Support complet** de la grammaire IMS-R8-2009-03
- ✅ **Décodage automatique** des tags et structures ASN.1
- ✅ **Gestion des timestamps** BCD et formats spéciaux
- ✅ **Extraction intelligente** des champs complexes
- ✅ **Validation** de l'intégrité des données

### 📊 Analyse des CDR
- 📞 **Informations d'appel** : Appelant, appelé, durée
- 🌐 **Données réseau** : Node address, GGSN, S-CSCF
- ⏰ **Timestamps précis** : Début, fin, ouverture, fermeture
- 🔗 **Sessions SIP** : Méthodes, identifiants, états
- 📍 **Géolocalisation** : Informations de cellule, réseau d'accès

### 💻 Interface utilisateur
- 🎨 **Design moderne** et responsive
- 🖱️ **Drag & Drop** pour l'upload de fichiers
- 📈 **Statistiques en temps réel** : Nombre d'enregistrements, taille, durées
- 🔍 **Vue détaillée** expandable par enregistrement
- 🎯 **Recherche et filtrage** des données décodées
- 📱 **Compatible mobile** et tablette

### 🛡️ Sécurité et performance
- 🔒 **Traitement local** : Vos fichiers ne quittent jamais votre navigateur
- ⚡ **Performance optimisée** pour les gros fichiers (jusqu'à 50MB)
- 🛡️ **Validation des entrées** et gestion d'erreurs robuste
- 💾 **Gestion mémoire** efficace pour éviter les fuites

---

## 📖 Utilisation

### 1. Accès rapide (Recommandé)
1. 🌐 Allez sur [https://VOTRENOM.github.io/ats-decoder](https://VOTRENOM.github.io/ats-decoder)
2. 📁 Glissez-déposez votre fichier CDR ou cliquez sur "Choisir un fichier"
3. ⏳ Attendez le décodage automatique
4. 📊 Explorez les résultats dans l'interface

### 2. Types de fichiers supportés
```
✅ .dat   - Fichiers CDR binaires standards
✅ .bin   - Fichiers binaires ASN.1
✅ .asn1  - Fichiers ASN.1 encodés
✅ .cdr   - Call Detail Records
```

### 3. Exemple d'analyse
Après upload d'un fichier ATS, vous obtiendrez :

```
📊 Résultats de l'analyse
├── 3 Enregistrements trouvés
├── 2.2 KB Taille du fichier  
├── 2 Appels identifiés
└── 15 Timestamps décodés

📞 Enregistrement 1 - ATSRecord
├── Appelant: tel:+224613345579
├── Appelé: tel:00224625682811
├── Début: 2025-07-28 09:08:03
├── Fin: 2025-07-28 09:08:05
├── Durée: 0m 2s
├── Node: camats01.ims.mnc001.mcc611.3gppnetwork.org
├── GGSN: 10.75.4.2
└── Session: asbcJNdcbLyXh@10.25.14.169
```

---

## 📘 Format supporté

### Standard ASN.1 IMS-R8-2009-03

Le décodeur supporte les enregistrements suivants :

| Type | Code | Description |
|------|------|-------------|
| **ATSRecord** | 69 | Enregistrements ATS (Application Telephony Server) |
| sCSCFRecord | 63 | Serving Call Session Control Function |
| pCSCFRecord | 64 | Proxy Call Session Control Function |
| iCSCFRecord | 65 | Interrogating Call Session Control Function |
| mGCFRecord | 67 | Media Gateway Control Function |
| iBCFRecord | 82 | Interconnection Border Control Function |

### Champs décodés

#### 📞 Informations d'appel
- `callingParty` - Numéro appelant (tel:+XXXX)
- `calledParty` - Numéro appelé (tel:+XXXX)
- `sipMethod` - Méthode SIP (INVITE, BYE, ACK)
- `duration` - Durée de l'appel
- `causeForRecordClosing` - Raison de fermeture

#### 🌐 Informations réseau
- `nodeAddress` - Adresse du nœud IMS
- `gGSNAddress` - Adresse GGSN/P-GW
- `accessNetworkInformation` - Info réseau d'accès (LTE, 5G)
- `servedPartyIPAddress` - Adresse IP du terminal

#### ⏰ Timestamps
- `serviceRequestTimeStamp` - Demande de service
- `serviceDeliveryStartTimeStamp` - Début de service
- `serviceDeliveryEndTimeStamp` - Fin de service
- `recordOpeningTime` - Ouverture d'enregistrement
- `recordClosureTime` - Fermeture d'enregistrement

#### 🔗 Identifiants de session
- `sessionId` - Identifiant de session SIP
- `imsChargingIdentifier` - Identifiant de facturation IMS
- `privateUserID` - IMPI (Private User Identity)
- `subscriptionID` - Identifiant d'abonnement

---

## 💻 Installation locale

### Méthode 1 : HTML simple

```bash
# 1. Cloner le repository
git clone https://github.com/VOTRENOM/ats-decoder.git
cd ats-decoder

# 2. Démarrer un serveur local
python3 -m http.server 8000

# 3. Ouvrir le navigateur
open http://localhost:8000
```

### Méthode 2 : Node.js (pour développement)

```bash
# 1. Cloner et installer
git clone https://github.com/VOTRENOM/ats-decoder.git
cd ats-decoder
npm install

# 2. Démarrer le serveur de développement
npm start

# 3. Ouvrir le navigateur
open http://localhost:3000
```

### Méthode 3 : Docker

```bash
# 1. Construire l'image
docker build -t ats-decoder .

# 2. Lancer le conteneur
docker run -p 8080:80 ats-decoder

# 3. Accéder à l'application
open http://localhost:8080
```

---

## 🛠️ Technologies

### Frontend
- **HTML5** - Structure sémantique
- **CSS3** - Styling moderne avec Grid/Flexbox
- **Vanilla JavaScript** - Logique métier sans framework
- **Web APIs** - FileReader, Drag & Drop, TextDecoder

### Décodage ASN.1
- **Parsing binaire** - Lecture directe des octets
- **BCD decoding** - Décodage Binary Coded Decimal
- **UTF-8 support** - Gestion des chaînes internationales
- **Validation** - Vérification d'intégrité des données

### Outils de développement
- **Git** - Contrôle de version
- **GitHub Pages** - Hébergement statique
- **ESLint** - Qualité du code JavaScript
- **Prettier** - Formatage automatique

---

## 📁 Structure du projet

```
ats-decoder/
├── 📄 index.html              # Interface principale
├── 🎨 assets/
│   ├── css/
│   │   └── styles.css         # Styles CSS
│   ├── js/
│   │   ├── decoder.js         # Classe de décodage ASN.1
│   │   ├── ui.js             # Interface utilisateur
│   │   └── utils.js          # Utilitaires
│   └── images/
│       └── logo.png          # Logo du projet
├── 📖 docs/
│   ├── API.md                # Documentation API
│   ├── ASN1-Grammar.md       # Grammaire ASN.1 complète
│   └── examples/             # Exemples de fichiers CDR
├── 🧪 test/
│   ├── test-files/           # Fichiers de test
│   └── decoder.test.js       # Tests unitaires
├── 🐳 docker/
│   ├── Dockerfile            # Configuration Docker
│   └── docker-compose.yml    # Services Docker
├── 📋 README.md              # Ce fichier
├── 📜 LICENSE                # Licence MIT
├── 🔧 package.json           # Configuration Node.js
└── ⚙️ .github/
    └── workflows/
        └── deploy.yml        # CI/CD GitHub Actions
```

---

## 🧪 Tests et validation

### Fichiers de test inclus
- `sample-ats-record.dat` - Enregistrement ATS simple
- `multiple-records.dat` - Fichier multi-enregistrements
- `large-file.dat` - Test de performance (5MB)
- `malformed.dat` - Test de robustesse

### Exécution des tests
```bash
# Tests unitaires
npm test

# Tests d'intégration
npm run test:integration

# Tests de performance
npm run test:performance

# Validation ASN.1
npm run validate:asn1
```

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Voici comment participer :

### 1. Fork du projet
```bash
# 1. Fork sur GitHub (bouton Fork)
# 2. Cloner votre fork
git clone https://github.com/VOTRE_USERNAME/ats-decoder.git
cd ats-decoder

# 3. Ajouter le repository original
git remote add upstream https://github.com/VOTRENOM/ats-decoder.git
```

### 2. Créer une branche
```bash
git checkout -b feature/nouvelle-fonctionnalite
```

### 3. Développer et tester
```bash
# Développer votre fonctionnalité
# Ajouter des tests
npm test

# Vérifier le code
npm run lint
npm run format
```

### 4. Soumettre une Pull Request
```bash
git add .
git commit -m "feat: Ajout de la nouvelle fonctionnalité"
git push origin feature/nouvelle-fonctionnalite

# Créer une Pull Request sur GitHub
```

### Guidelines de contribution
- ✅ **Code style** : Suivre les conventions ESLint/Prettier
- ✅ **Tests** : Ajouter des tests pour toute nouvelle fonctionnalité
- ✅ **Documentation** : Mettre à jour la documentation
- ✅ **Commits** : Messages descriptifs (format conventional)

---

## 🐛 Signalement de bugs

Trouvé un bug ? Aidez-nous à l'améliorer !

### 1. Vérifier les issues existantes
Consultez les [issues GitHub](https://github.com/VOTRENOM/ats-decoder/issues) pour voir si le problème a déjà été signalé.

### 2. Créer une nouvelle issue
```markdown
## 🐛 Description du bug
Description claire et concise du problème.

## 🔄 Étapes pour reproduire
1. Aller sur '...'
2. Cliquer sur '...'
3. Voir l'erreur

## ✅ Comportement attendu
Ce qui devrait se passer.

## 📸 Captures d'écran
Si applicable, ajoutez des captures d'écran.

## 🖥️ Environnement
- OS: [ex: Windows 10]
- Navigateur: [ex: Chrome 91]
- Version: [ex: 1.0.0]
```

---

## 📋 Roadmap

### Version 1.1 (Q4 2025)
- [ ] Support de nouveaux types d'enregistrements IMS
- [ ] Export en JSON/CSV/XML
- [ ] Recherche et filtrage avancés
- [ ] Mode batch pour multiple fichiers

### Version 1.2 (Q1 2026)
- [ ] API REST pour intégration
- [ ] Analyse statistique avancée
- [ ] Graphiques et visualisations
- [ ] Plugin pour Wireshark

### Version 2.0 (Q2 2026)
- [ ] Support temps réel (streaming)
- [ ] Machine learning pour détection d'anomalies
- [ ] Interface multi-langues
- [ ] Mode entreprise avec authentification

---

## 📚 Ressources

### Documentation technique
- 📖 [Spécification ASN.1 (ITU-T X.680)](https://www.itu.int/rec/T-REC-X.680/)
- 📖 [IMS Architecture 3GPP TS 23.228](https://www.3gpp.org/ftp/Specs/archive/23_series/23.228/)
- 📖 [CDR Format 3GPP TS 32.260](https://www.3gpp.org/ftp/Specs/archive/32_series/32.260/)

### Outils connexes
- 🔧 [ASN.1 Compiler](https://www.oss.com/asn1/products/asn1-tools/overview.html)
- 🔧 [Wireshark ASN.1 Dissector](https://www.wireshark.org/)
- 🔧 [OpenASN1](https://github.com/openasn1/)

### Communauté
- 💬 [Forum 3GPP](https://www.3gpp.org/)
- 💬 [Stack Overflow - ASN.1](https://stackoverflow.com/questions/tagged/asn.1)
- 💬 [Reddit - Telecom](https://www.reddit.com/r/telecom/)

---

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

```
MIT License

Copyright (c) 2025 Votre Nom

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software...
```

---

## 👨‍💻 Auteur

**Votre Nom**
- 📧 Email: [locsenmam@gmail.com](mailto:votre.email@example.com)
- 🐙 GitHub: [@mozzdev](https://github.com/VOTRENOM)

---

## 🙏 Remerciements

- 📚 **3GPP** pour les spécifications IMS
- 🏢 **ITU-T** pour les standards ASN.1
- 🌐 **GitHub** pour l'hébergement gratuit
- 👥 **Communauté open source** pour les retours et contributions
- 🛠️ **Contributeurs** qui ont aidé à améliorer ce projet

---

## 📊 Statistiques du projet

![GitHub Stars](https://img.shields.io/github/stars/VOTRENOM/ats-decoder?style=social)
![GitHub Forks](https://img.shields.io/github/forks/VOTRENOM/ats-decoder?style=social)
![GitHub Issues](https://img.shields.io/github/issues/VOTRENOM/ats-decoder)
![GitHub Pull Requests](https://img.shields.io/github/issues-pr/VOTRENOM/ats-decoder)
![Last Commit](https://img.shields.io/github/last-commit/VOTRENOM/ats-decoder)

---

<div align="center">

**⭐ Si ce projet vous aide, n'hésitez pas à lui donner une étoile sur GitHub ! ⭐**

[🚀 Utiliser le décodeur](https://VOTRENOM.github.io/ats-decoder) | [📖 Documentation](docs/) | [🐛 Signaler un bug](https://github.com/VOTRENOM/ats-decoder/issues) | [💡 Suggérer une amélioration](https://github.com/VOTRENOM/ats-decoder/discussions)

---

*Fait avec ❤️ pour la communauté télécom*

</div>
