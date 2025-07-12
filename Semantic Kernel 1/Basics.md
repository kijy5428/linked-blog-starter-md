
## System structure
![](../../Pasted%20image%2020250712110355.png)


### 🧠 Components in the Ecosystem

|Component|Role & Function|
|---|---|
|**Other AI Apps**|These are external AI services or tools (like ChatGPT, Copilot, etc.) that may integrate with your application for additional functionality.|
|**Plugins**|Serve as connectors or modular features that extend what AI apps can do. They act as intermediaries to interpret requests and interface with various systems or data sources.|
|**Semantic Kernel**|A Microsoft framework that orchestrates AI and traditional code together. It enables complex reasoning, memory handling, and workflow execution using AI in your app.|
|**Your App**|The main application you're building or using—this is where user interactions happen and where everything comes together.|

### 🔄 Interaction Flow

- **"Other AI Apps" ↔ Plugins ↔ Your App**: AI tools communicate with your app through plugins, which manage and translate requests or responses.
- **Semantic Kernel ↔ Plugins ↔ Your App**: SK runs logic, connects to plugins, and guides the flow of actions or knowledge within your app.

### 💡 Why This Matters

This architecture encourages:

- **Modular design**: Each piece works independently but can be swapped or upgraded easily.
- **Scalability**: You can integrate more plugins or AI tools as your needs evolve.
- **Interoperability**: Semantic Kernel acts as a brain coordinating traditional app logic with modern AI services.

Let me know if you'd like help mapping out a similar structure for one of your own projects—I know you're into system design and tracking systems! 🛠️

--- 
## Topics
 
- Telemetry support
- Hooks
- Filters
- OpenAPI

## Others
 - Personas
 - Memory
 - Planner
 - 
Managing Personas

Semantic kernel build up the flows

- Create embedding first

Kernel functions

Kernel memory

Micron shared semantic kernel

## References
- https://learn.microsoft.com/en-us/semantic-kernel/overview/
- 