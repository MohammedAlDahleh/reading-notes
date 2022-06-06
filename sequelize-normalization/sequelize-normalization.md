## Things I want to know more about

<h1>sequelize normalization</h1>

<h2>Associations</h2>

* Sequelize supports the standard associations:
 1. [One-To-One](https://en.wikipedia.org/wiki/One-to-one_%28data_model%29)
 2. [One-To-Many](https://en.wikipedia.org/wiki/One-to-many_%28data_model%29)
 3. [Many-To-Many](https://en.wikipedia.org/wiki/Many-to-many_%28data_model%29)

 * Sequelize provides four types of associations that should be combined to create them:
  1. The HasOne association
  2. The BelongsTo association
  3. The HasMany association
  4. The BelongsToMany association

  <h3>Defining the Sequelize associations</h3>
---
const A = sequelize.define('A', /* ... */);
const B = sequelize.define('B', /* ... */);

A.hasOne(B); // A HasOne B
A.belongsTo(B); // A BelongsTo B
A.hasMany(B); // A HasMany B
A.belongsToMany(B, { through: 'C' }); // A BelongsToMany B through the junction table C
---

* Mandatory for belongsToMany containing at least the through property):
---
A.hasOne(B, { /* options */ });
A.belongsTo(B, { /* options */ });
A.hasMany(B, { /* options */ });
A.belongsToMany(B, { through: 'C', /* options */ });
---

* onDelete and onUpdate
---
Foo.hasOne(Bar, {
  onDelete: 'RESTRICT',
  onUpdate: 'RESTRICT'
});
Bar.belongsTo(Foo);
---

* Customizing the foreign key
---
// Option 1
Foo.hasOne(Bar, {
  foreignKey: 'myFooId'
});
Bar.belongsTo(Foo);

// Option 2
Foo.hasOne(Bar, {
  foreignKey: {
    name: 'myFooId'
  }
});
Bar.belongsTo(Foo);

// Option 3
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: 'myFooId'
});

// Option 4
Foo.hasOne(Bar);
Bar.belongsTo(Foo, {
  foreignKey: {
    name: 'myFooId'
  }
});
---