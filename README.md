# 💻 L'Incident du Serveur Zéro

Un jeu d'aventure textuel interactif développé en HTML et CSS dans le cadre du TP "Initiation Web" (Plateforme YQuest).

Le joueur incarne un technicien réseau confronté à une IA rebelle dans un data center. À travers une série de choix, l'histoire se ramifie vers 6 fins différentes (victoires, fuites ou game over).

## 🚀 Fonctionnalités
- **13 pages interconnectées** avec une arborescence complexe et aucun "faux choix".
- **6 fins distinctes** selon les décisions prises.
- **Design immersif** inspiré des terminaux informatiques de type UNIX (mode sombre, texte vert, curseur clignotant).
- **Design Responsive** qui s'adapte à la taille de l'écran.

## 🛠️ Technologies et Bibliothèques utilisées
Ce projet est réalisé en HTML5 et CSS3 pur, sans JavaScript.

Pour renforcer l'immersion, j'ai utilisé deux ressources externes :
- **Google Fonts (Fira Code)** : Une police d'écriture monospace spécialement conçue pour le code, qui donne l'aspect "console de commandes" aux textes du jeu.
- **FontAwesome (v6.4.0)** : Une bibliothèque d'icônes intégrée via CDN. Elle me permet d'ajouter facilement des icônes vectorielles (`<i class="fa-solid..."></i>`) dans les titres et les boutons de choix sans avoir à charger de multiples images lourdes.

## 📁 Structure du projet
```text
guery-tp-web/
├── index.html              # Point de départ du jeu
├── style.css               # Feuille de style principale
├── README.md               # Documentation du projet
├── arbre-navigation.pdf    # Schéma des choix et des fins
├── pages/                  # Dossier contenant les 12 scènes du jeu
│   ├── scene01.html
│   ├── scene02.html
│   └── ...
└── assets/
    └── backgrounds/
        └── background.gif  # Image de fond animée
```

## 🔍 Focus sur le code CSS

Pour créer l'ambiance "Hacking / Serveur", j'ai utilisé quelques techniques CSS intéressantes :

**1. L'assombrissement du fond animé (GIF)**
Pour utiliser un GIF en arrière-plan sans qu'il ne gêne la lecture du texte, j'ai superposé un fond noir semi-transparent (à 85%) directement dans la propriété `background-image` grâce à `linear-gradient` :
```css
body {
    background-image: 
        linear-gradient(rgba(0, 0, 0, 0.85), rgba(0, 0, 0, 0.85)),
        url('assets/backgrounds/background.gif');
}
```

**2. L'animation d'allumage du terminal**
Pour donner l'impression qu'un vieil écran s'allume au chargement de chaque page, j'ai créé une animation `bootUp`. Elle joue sur l'opacité, l'échelle (`scale`) et la position (`translateY`) :
```css
.terminal-container {
    animation: bootUp 1.2s cubic-bezier(0.1, 0.8, 0.2, 1);
}

@keyframes bootUp {
    0% { opacity: 0; transform: scale(0.95) translateY(20px); }
    100% { opacity: 1; transform: scale(1) translateY(0); }
}
```

**3. L'effet de curseur clignotant**
Sur le titre principal, un faux curseur `_` clignote pour simuler une invite de commande en attente de saisie. L'animation utilise `step-end` pour un effet "on/off" net, sans transition douce :
```css
.cursor {
    animation: blink 1s step-end infinite;
}
@keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
}
```

## 🕹️ Comment jouer ?
Aucune installation de serveur n'est requise.
Il suffit de cloner ou télécharger ce dossier, puis d'ouvrir le fichier `index.html` dans n'importe quel navigateur web moderne (Chrome, Firefox, Safari...).