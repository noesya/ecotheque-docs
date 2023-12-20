---
title: Structure
---

## Items

### Concept
Les objets ont des propriétés intrinsèques codées en dur, et un ensemble de propriétés éditables appuyées sur les `items`.
Un `Item` peut être un titre, un champ de texte, un sélecteur à choix multiple, une galerie de photos... Placés dans un ordre choisi, ils définissent la structure de la page des objets. Ainsi, un matériau a un certain nombre d'items, un projet en a d'autres. C'est éléments permettent à la fois l'édition en admin et l'affichage en front. 

### Diagramme entité relations

Dans le diagramme suivant, `Object` peut être un `Material`, un `Project`... Toutes les classes sont rangées dans un namespace `Structure::`, afin de ne pas polluer le niveau métier.

```mermaid
erDiagram
  Item {
    string name
    string slug
    int kind
    text hint
    int position
  }
  Value {
    text text
  }
  Option {
    string name
    string slug
    text hint
    int position
  }
  Item }o--|| Class : about
  Item ||--o{ Option : has
  Item ||--o{ Value : has
  Value }o--|| Object : polymorphic
  Value }o--o| Option : has
  Class ||--o{ Object : instanciates
```
