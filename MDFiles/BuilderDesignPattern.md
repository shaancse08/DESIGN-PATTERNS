## Builder Design Pattern

**Builder** is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.

The Builder Pattern is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types or representations of an object while avoiding “constructor pollution”: a situation where you have too many constructor parameters, which can lead to confusion.

Suppose you’re creating a character for a video game. This character has several attributes like name, class, armor, weapon, and many more. Instead of creating complex, multi-parameter constructors, you can use the Builder Pattern to set these attributes step by step.

##### Builder Pattern: Why and When?

The Builder Pattern serves several purposes:

- Flexibility: It allows for the construction of complex objects in a step-by-step fashion, giving you a great deal of control over the object’s creation.
  Clear and Readable Code: By avoiding constructor overloading, your code becomes more maintainable and less error-prone.
- Variety: It allows the construction of different representations of an object from the same construction code.

##### You should use the Builder Pattern when:

- The object has complex, multi-step construction.
- You want to avoid “constructor pollution,” where a constructor has too many parameters.
- You need to create different representations of an object, which would be impractical with a constructor.

##### Step by step build the pattern

- **Step 1: Create the Product Class**: First, we define our “product,” which in this case is the GameCharacter:

```javascript
class GameCharacter {
  name?: string;
  class?: string;
  weapon?: string;
  armor?: string;
  // ... any other game character attributes

  describe() {
    console.log(`Character: ${this.name}, Class: ${this.class}, Weapon: ${this.weapon}, Armor: ${this.armor}`);
  }
}
```

- **Step 2: Create the Builder Interface and Class**: Next, we create a CharacterBuilder interface and a GameCharacterBuilder class that implements this interface:

```javascript
interface CharacterBuilder {
  setName(name: string): void;
  setClass(className: string): void;
  setWeapon(weapon: string): void;
  setArmor(armor: string): void;
  // ... other setter methods
  build(): GameCharacter;
}

class GameCharacterBuilder implements CharacterBuilder {
  private character: GameCharacter;

  constructor() {
    this.character = new GameCharacter();
  }

  setName(name: string): void {
    this.character.name = name;
  }

  setClass(className: string): void {
    this.character.class = className;
  }

  setWeapon(weapon: string): void {
    this.character.weapon = weapon;
  }

  setArmor(armor: string): void {
    this.character.armor = armor;
  }

  // ... other setter methods

  build(): GameCharacter {
    return this.character;
  }
}
```

- **Step 3: Use the Builder**: Finally, we can use the builder to create a new game character:

```javascript
let characterBuilder = new GameCharacterBuilder();
characterBuilder.setName("Archer");
characterBuilder.setClass("Elf");
characterBuilder.setWeapon("Bow");
characterBuilder.setArmor("Leather armor");

let character = characterBuilder.build();
character.describe(); // Outputs: Character: Archer, Class: Elf, Weapon: Bow, Armor: Leather armor
```
