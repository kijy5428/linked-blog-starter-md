Here’s a structured and concise summary formatted for **note-taking** on the topic of **test isolation and test doubles** in unit testing:

---

## 🧪 **Test Isolation & Test Doubles in Unit Testing**

### 🔹 Why Avoid Real Repository in Unit Tests?

- Using real repositories/databases introduces **external dependencies**.
- This can lead to **integration tests**, not **unit tests**.
- External systems may **influence test outcomes**.
- Goal: **Isolate the unit** being tested.

---

### 🔹 What is a Test Double?

A **test double** is a substitute for a real object used in testing.

#### 🧩 **Types of Test Doubles**

|Type|Description|Example|
|---|---|---|
|**Fake**|Functional implementation not suitable for production|In-memory SQLite DB|
|**Dummy**|Placeholder object, never used|Passing unused factory to constructor|
|**Stub**|Provides predefined data|InternalEmployee with preset values|
|**Spy**|Captures indirect output/input|Subclass with added behavior (not used in this course)|
|**Mock**|Simulates behavior and verifies interactions|Used to test expected calls without real object|

> ✅ Most unit test projects use a **combination** of these.

---

### 🔹 Approaches to Test Isolation

#### 1. **Manual Creation**

- Write custom test versions of dependencies (e.g., fake repositories).
- ✅ Works well but ❌ **costly** and ❌ **hard to maintain**.

#### 2. **Built-in Framework Features**

- Use features from libraries like:
    - **Entity Framework Core**: In-memory DB for testing.
    - **HttpClient**: Message handler chain to avoid real API calls.

#### 3. **Mocking Frameworks**

- Tools that help create:
    - Mocks
    - Dummies
    - Stubs
- ✅ Efficient and flexible for test isolation.

---

### 🔹 Key Takeaways

- ✅ **Isolate tests** from external systems.
- ✅ Use appropriate **test doubles** based on context.
- ✅ Combine approaches as needed.
- ❌ Don’t rely on real implementations for unit tests.
- ✅ Focus on **behavior**, not infrastructure.

---

Would you like this turned into a printable checklist or a markdown file for your documentation?