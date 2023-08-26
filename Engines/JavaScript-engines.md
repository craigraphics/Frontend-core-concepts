## JavaScript engines
JavaScript engines are specialized software interpreters that execute JavaScript code in web browsers or on servers. They essentially transform high-level JavaScript code into machine-level instructions that can be executed by a computer's CPU. Below, I'll provide a formal breakdown of some well-known JavaScript engines:

### V8
**Developer:** Google  
**Language:** C++  
**Used in:** Google Chrome, Node.js, Deno, etc.

**Description:**  
V8 is perhaps one of the most famous JavaScript engines and is developed by Google. It is employed in Google Chrome and is also the runtime for Node.js. V8 compiles JavaScript to native machine code before executing it, instead of employing an interpreter. It uses Just-In-Time (JIT) compilation for this purpose. V8 also includes a garbage collector and supports WebAssembly.

### JavaScriptCore (also known as Nitro)
**Developer:** Apple  
**Language:** C++  
**Used in:** Safari

**Description:**  
JavaScriptCore is the engine used in Apple's Safari browser. Like V8, it uses JIT compilation for performance optimization. The engine aims to be fast, efficient, and compliant with web standards. It has seen considerable optimization for mobile platforms, given Apple's ecosystem.

### SpiderMonkey
**Developer:** Mozilla  
**Language:** C/C++  
**Used in:** Firefox

**Description:**  
SpiderMonkey is the first JavaScript engine, developed by Brendan Eich, the creator of JavaScript. It is used in Mozilla Firefox. SpiderMonkey also compiles JavaScript into native machine code via JIT compilation. It includes a garbage collector and has undergone numerous performance improvements over the years.

### Chakra
**Developer:** Microsoft  
**Language:** C++  
**Used in:** Internet Explorer, Microsoft Edge (legacy)

**Description:**  
Chakra was developed by Microsoft for their Internet Explorer browser and was later used in the legacy version of Microsoft Edge (before it switched to Chromium and, consequently, V8). ChakraCore, the open-source core of the engine, is designed to be embedded in Microsoft products like Windows and is optimized for their ecosystem. It also uses JIT compilation and has a separate engine for interpreting JavaScript to balance performance and startup time.
