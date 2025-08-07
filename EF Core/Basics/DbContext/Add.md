Here’s a **beautiful and clear summary** of the page [“Adding Data via the DbContext”](https://www.learnentityframeworkcore.com/dbcontext/adding-data) from LearnEntityFrameworkCore.com:

---

## ➕ Adding Data with `DbContext` in EF Core

Entity Framework Core allows you to add data to the database using the `DbContext` class. This is done through methods like `Add`, `AddRange`, and their generic counterparts.

---

### 🧱 Core Methods for Adding Data

|**Method**|**Purpose**|
|---|---|
|`Add<TEntity>(entity)`|Adds a single entity of a specific type.|
|`Add(object entity)`|Adds a single entity (non-generic).|
|`AddRange(params object[])`|Adds multiple entities at once.|
|`AddRange(IEnumerable<object>)`|Adds a collection of entities.|

These methods mark the entity (and any related entities not already tracked) with the `EntityState.Added` state.

---

### 🧠 How EF Core Tracks Entities

When you use `Add()`:

- The entity is tracked with `EntityState.Added`.
- Any **related entities** (e.g., child objects in a navigation property) that are not already tracked will also be marked as `Added`.

---

### 📚 Example: Adding an Author with Books

```CSharp
var author = new Author {
    FirstName = "William",
    LastName = "Shakespeare",
    Books = new List<Book> {
        new Book { Title = "Hamlet" },
        new Book { Title = "Othello" },
        new Book { Title = "MacBeth" }
    }
};

context.Add(author);
context.SaveChanges();
```

✅ All books are added because they are part of the `Books` collection on the `Author`.

---

### ⚠️ Important Caveat

If you create books and assign the `Author` to them, but **don’t add them to the `Author.Books` collection**, EF Core won’t track them:

```CSharp
var author = new Author { FirstName = "William", LastName = "Shakespeare" };
var hamlet = new Book { Title = "Hamlet", Author = author };
context.Add(author);
context.SaveChanges();
```

❌ In this case, only the `Author` is added — the `Books` are ignored because the `Author` doesn’t reference them directly.

---

### 📦 Adding Multiple Records

Use `AddRange()` to add multiple entities efficiently:

```CSharp
context.AddRange(author, hamlet, othello, macbeth);
context.SaveChanges();
```

---

Would you like a visual diagram of how EF Core tracks related entities during `Add()`?