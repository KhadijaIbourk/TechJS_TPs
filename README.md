# TechJS – TPs JavaScript

Ce dépôt contient mes exercices réalisés dans le cadre du module **TechJS**.  

## Exercice 1 : Pierre-Papier-Ciseaux

### Description
Un jeu classique jouable contre l’ordinateur.  
Le joueur utilise le clavier pour choisir un coup :  
- **r** pour Pierre  
- **p** pour Papier  
- **s** pour Ciseaux  

Le jeu compare le coup du joueur avec celui de l’ordinateur, affiche le résultat, met à jour le score et le sauvegarde dans le navigateur.

### Explication du code
- **`keydown`** : permet de détecter quand l’utilisateur appuie sur une touche du clavier.  
- **`if / else if / else`** : structure conditionnelle utilisée pour comparer le choix du joueur et exécuter la logique appropriée.  
  - `if` → vérifie une condition spécifique.  
  - `else if` → teste une autre condition si la première n’est pas vraie.  
  - `else` → exécute le code si aucune condition précédente n’est remplie.  

En résumé : le code écoute les touches du clavier et utilise `if / else if / else` pour déterminer l’action à effectuer selon la touche pressée.

### Code clé
```javascript
document.addEventListener('keydown', (event) => {
  if (event.key === 'r') {
    playGame('rock');
  } else if (event.key === 'p') {
    playGame('paper');
  } else if (event.key === 's') {
    playGame('scissors');
  }
});

function playGame(playerMove) {
  const computerMove = pickComputerMove();
  let result = '';

  if (playerMove === computerMove) {
    result = 'Tie';
    score.ties++;
  } else if (playerMove == 'paper' && computerMove == 'rock') {
    result = 'You win';
    score.wins++;
  } else if (playerMove == 'rock' && computerMove == 'scissors') {
    result = 'You win';
    score.wins++;
  } else {
    result = 'You lose';
    score.losses++;
  }

  updateScoreElement();
  localStorage.setItem('score', JSON.stringify(score));
  document.querySelector('.js-result').innerHTML = result;
}
