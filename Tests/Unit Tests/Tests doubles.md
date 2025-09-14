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

Here’s the updated **note-taking table** with **two more examples** added for each type of **test double**:

---

## 🧪 **Test Doubles – Extended Notes Table**

|**Type**|**Description**|**Examples**|
|---|---|---|
|**Fake**|Functional implementation not suitable for production.|1. In-memory SQLite DB  <br>2. Fake Email Service (logs instead of sending)  <br>3. In-memory Cache|
|**Dummy**|Placeholder object that is passed but never used.|1. Unused factory passed to constructor  <br>2. Empty config object  <br>3. Null logger instance|
|**Stub**|Provides predefined responses to method calls.|1. Stubbed user repository returning fixed user  <br>2. Stubbed API client with hardcoded JSON  <br>3. Stubbed product service returning fixed price|
|**Spy**|Records how it was used (calls, parameters, etc.).|1. Spy logger tracking error messages  <br>2. Spy payment processor tracking method calls  <br>3. Spy email sender recording recipients|
|**Mock**|Simulates behavior and verifies interactions.|1. Mock repository verifying `Add()` call  <br>2. Mock notification service checking trigger  <br>3. Mock file system verifying file write|

---

### 🧠 **Tip for Use**

- Combine different types of test doubles as needed.
- Choose based on **test isolation goals**, not just convenience.
- Use mocking frameworks to simplify creation of mocks, stubs, and dummies.

Would you like this exported as a Markdown file or PDF for your documentation?

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

Absolutely! Here's an enhanced and more **descriptive version** of the **Spy vs Mock comparison table**, with more precise language in the **Description** column:

---

## 🕵️‍♂️ **Spy vs Mock – Detailed Comparison**

|**Aspect**|**Spy**|**Mock**|
|---|---|---|
|**Purpose**|To **observe and record** how a dependency behaves during the test without enforcing behavior.|To **simulate and control** a dependency’s behavior and **verify** that specific interactions occur.|
|**Behavior**|Typically a **partial or real implementation** with added logic to track method calls and inputs.|A **fully simulated object** that mimics expected behavior and allows **predefined expectations**.|
|**Verification**|You **inspect the spy after the test** to see what methods were called and with what arguments.|You **define expectations before the test**, and the mock will **fail the test** if they’re not met.|
|**Usage Style**|**Passive**: Records what happened during the test for later inspection.|**Active**: Enforces specific behavior and validates interactions during the test.|
|**Common Tools**|Can be manually implemented or supported by some mocking libraries.|Typically created using mocking frameworks like **Moq**, **NSubstitute**, or **FakeItEasy**.|
|**Use Case**|Useful when you want to **track usage** (e.g., how many times a method was called).|Useful when you want to **ensure specific behavior** (e.g., a method must be called once).|

---

### 🔍 Quick Analogy

- **Spy** = Security camera: _Records what happened._
- **Mock** = Security guard: _Enforces rules and reports violations._

---

  

The terminology is not completely standardized. This is fine. What I mean by “not standardized” is that some people will use the words differently, and you will have to figure out what people mean. Here’s how I use them.

Let’s say you have an interface WidgetFooer.

- Dummy: Implements WidgetFooer with methods that that just panic or return zero.
    
- Stub: Implements WidgetFooer with dummy methods that just return values.
    
- Fake: Implements WidgetFooer with simple methods with not much logic.
    
- Spy: Implements WidgetFooer by forwarding method calls to a different WidgetFooer, and records which calls are made (spies on them).
    
- Mock: A stub or fake that records which calls are or verifies that the correct calls are made.