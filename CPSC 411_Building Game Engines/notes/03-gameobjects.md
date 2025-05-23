# GameObjects
- A GameObject represents an entity in our scene
- We can create a `GameObject` struct to keep track of these entities

## Common Properties
- ID (int/long instead of string for $O(1)$ comparions)

Some game engines like to put core attributes on the GameObject itself
- Position
- Name

## Design Patterns
### Inheritance
- Often, each type of GameObject (like Player, Enemy, CPU) can be sub-classes of GameObject

### Monolithic GameObject
- The GameObject class can have every single behavior, including Texture, CollisionBox, Transform, AIBehavior, Input, etc. Then, you can set the ones you don't use to `null`.

### Components
- A GameObject could have a collection of Components
- A Component implements a shared interface (i.e. `IComponent`)
- Each Component overrides the Update function, and the GameObject calls Update on each of its components
