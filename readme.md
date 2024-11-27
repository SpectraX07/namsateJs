## **1. Execution Context in JavaScript**

Everything in JavaScript happens inside an **Execution Context**.

### **Components of an Execution Context:**

1. **Memory Component** (also known as Variable Environment)
2. **Code Component** (also known as Thread of Execution)

| **Memory Component / Variable Environment** | **Code Component / Thread of Execution** |
| --- | --- |
| Stores key-value pairs, such as: | Executes the code line by line. |
| - **`a : 10`** |  |
| - **`fn : {……}`** |  |

### **JavaScript: A Synchronous, Single-Threaded Language**

JavaScript operates in a synchronous and single-threaded manner, meaning it executes one command at a time in a specific order. Even though it can handle asynchronous tasks like callbacks or promises, these are managed through the event loop and do not break its single-threaded nature.

## **2. What Happens When You Run JavaScript Code?**

### **Code Example**

```javascript
var n = 2;

const square = num => {
  var ans = num * num;
  return ans;
};

var square2 = square(n);
var square4 = square(4);
```

---

### **How These Functions Get Executed**

When the code runs, **Execution Contexts** and the **Call Stack** work together to manage the execution of functions. Below is a step-by-step explanation and a visualization of how this happens:

1. **Step 1: Global Execution Context**
    - Created when the script starts. Memory is allocated, and **`n`**, **`square2`**, and **`square4`** are set to **`undefined`**.
    - **`square`** is stored as a function in memory.
2. **Step 2: Function Execution**
    - When **`square(n)`** is called, a **Function Execution Context** is created for **`square`**. The **`num`** parameter is assigned the value of **`n`**, which is **`2`**.
    - The **`ans`** variable is calculated as **`2 * 2 = 4`**, and the result (**`4`**) is returned.
    - This function execution context is popped off the **Call Stack**.
3. **Step 3: Second Function Call**
    - When **`square(4)`** is called, another **Function Execution Context** is created. The **`num`** parameter is assigned **`4`**.
    - The **`ans`** variable is calculated as **`4 * 4 = 16`**, and the result (**`16`**) is returned.
    - This function execution context is also popped off the **Call Stack**.
4. **Step 4: End of Execution**
    - After both function calls are completed, the Global Execution Context is removed from the **Call Stack**, and the script finishes.

---

### **Call Stack Flow Diagram**

1. **Before Execution Starts**
    - Call Stack: **`[ Global Execution Context ]`**

2. **During Execution of `square(n)`**
    - Call Stack:

      ```css
      [ square Execution Context ]
      [ Global Execution Context ]
      ```

3. **After Returning from `square(n)`**
    - Call Stack: **`[ Global Execution Context ]`**

4. **During Execution of `square(4)`**
    - Call Stack:

      ```css
      [ square Execution Context ]
      [ Global Execution Context ]
      ```

5. **After Returning from `square(4)`**
    - Call Stack: **`[ Global Execution Context ]`**

6. **After Script Completes**
    - Call Stack: **`[]`**

---

### **Memory and Code Execution Table**

| **Memory Component / Variable Environment** | **Code Component / Thread of Execution** |
| --- | --- |
| **`n: undefined`** | Executes code line by line. |
| **`square: { … }`** |  |
| **`square2: undefined`** |  |
| **`square4: undefined`** |  |

---

### **Key Points**

1. The **Global Execution Context** manages the overall script.
2. Each function call creates a **new Function Execution Context**, which is pushed onto the **Call Stack**.
3. Once a function finishes, its execution context is removed from the stack.
4. The **Call Stack** maintains the order of execution of execution context.
5. Call stack is also known as Execution Context Stack, Program Stack, Control Stack, Runtime Stack, Machine Stack.
