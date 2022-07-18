# KhazarOwnsEverything

credit : Jonas Schmedtmann

## Table des matières

- [Bankist Flowchart](#bankist-flowchart)
- [Manipulation du DOM](#manipulation-du-dom)
  - [element.innerHTML](#elementinnerhtml)
  - [Array.prototype.forEach()](#arrayprototypeforeach)
  - [Littéraux de gabarits](#littéraux-de-gabarits)
  - [element.insertAdjacentHTML](#elementinsertadjacenthtml)
  - [Code complet](#code-complet)

## Bankist Flowchart

![Bankist Flowchart](Bankist-flowchart.png)

## Manipulation du DOM

### element.innerHTML

La propriété Element.innerHTML de Element récupère ou définit la syntaxe HTML décrivant les descendants de l'élément.

- On vide le contenu de initial de la div de class .movements.

```js
const displayMovements = function (movements) {
// Vide le contenu de la balise de class .movements.
containerMovements.innerHTML = '';
```

### Array.prototype.forEach()

La méthode forEach() permet d'exécuter une fonction donnée sur chaque élément du tableau.

- On vérifie pour chaque élément du tableau movements, s'il s'agit d'une valeur positive (dépôt) ou d'une valeur négative (retrait).

```js
movements.forEach(function (mov, index) {
// Vérifie s'il s'agit d'un dépôt ou d'un retrait
const type = mov > 0 ? 'deposit' : 'withdrawal';
```

### Littéraux de gabarits

Les littéraux de gabarits sont des littéraux de chaînes de caractères permettant d'intégrer des expressions.

- On insert des balises html dynamique grâce aux littéraux

```js
// Template Litteral pour intégrer chaque mouvement
const html = `

  <div class="movements__row">
    <div class="movements__type movements__type--${type}">${index + 1} ${type}</div>
    <div class="movements__value">${mov}€</div>
  </div>`;
```

### element.insertAdjacentHTML

insertAdjacentHTML() analyse le texte spécifié en tant que HTML ou XML et insère les noeuds résultants dans le DOM à la position spécifiée.

```js
// Insert le template litteral html
containerMovements.insertAdjacentHTML('afterbegin', html);
```

### Code complet

```js

const displayMovements = function (movements) {
  // Vide le contenu de la balise de class .movements.
  containerMovements.innerHTML = '';

  // Loop forEach sur le tableau movements
  movements.forEach(function (mov, index) {
    // Vérifie s'il s'agit d'un dépôt ou d'un retrait
    const type = mov > 0 ? 'deposit' : 'withdrawal';

    // Template Litteral pour intégrer chaque mouvement
    const html = `
  <div class="movements__row">
    <div class="movements__type movements__type--${type}">${index + 1} ${type}</div>
    <div class="movements__value">${mov}€</div>
  </div>`;

    // Insert le template litteral html
    containerMovements.insertAdjacentHTML('afterbegin', html);
  });
};
displayMovements(account1.movements);
```