[.header-strong: #1A99FC]

# [fit] **5 Minute**
# [fit] Introduction
# [fit] to **ASTs**
# [fit] in JavaScript

---

[.header: alignment(center), text-scale(2.0)]
[.header-strong: #1A99FC]

<br>

# Hello 👋

### **I'm Saugat Acharya**

<br>

#### Open Source Enthusiast **(@mesaugat)**
#### Lead Engineer, Leapfrog Technology

---

[.header: alignment(center), text-scale(3.5)]
[.header-strong: #1A99FC]

<br>
<br>

# **ASTs**

#### What are Abstract Syntax Trees?

---

> "Tree representation of the abstract syntactic structure of source code."
<br>
-- Wikipedia

---

[.header-strong: #1A99FC]
[.header: alignment(center), text-scale(1.8)]

# Example

<br>
<br>

## **1 + (2 * 3)**

![right fit](images/ast-example-1.png)

---

[.header: alignment(center), text-scale(1.8)]

# A **"Real"** Example

<br>
<br>

```javascript
function sum(a, b) {
    return a + b;
}

sum(5, 10)
```

![right fit](images/ast-example-2.png)

---

# AST **Parsers**

[.header: alignment(center), text-scale(1.5)]
[.header-strong: #1A99FC]

![inline](images/ast-parsers.png)

### **https://alligator.io/js/traversing-ast**

---

<br>
<br>
<br>

# AST **Object Representation**

[.header: alignment(center), text-scale(1.8)]

![right 100%](images/ast-preview.png)

---

<br>
<br>
<br>

# AST **JSON Representation**

[.header: alignment(center), text-scale(1.8)]
[.code: Dank Mono]

![right 110%](images/ast-json-preview.png)

---

[.header: alignment(center), text-scale(1.5)]

# Who uses ASTs?

![inline 80%](images/babel.png) ![inline 80%](images/eslint.png)
![inline 80%](images/prettier.png) ![inline 95%](images/webpack.png)

---

[.header: alignment(center), text-scale(1.5)]

# Transpilation / Transformation

![inline](images/babel-transformation.png)

#### Transforming **JSX and React** to **ES5** using Babel

---

# ES6 to ES5

[.header: alignment(center), text-scale(1.5)]

![inline 111%](images/react-es6.png)![inline 120%](images/react-es5.png)

#### Converting **one AST** to **another AST**

---

[.header: alignment(center), text-scale(1.5)]

# Linting / Static Code Analysis

![inline fit](images/eslint-analysis.png)

#### Applying **lint rules** using **ESLint**

---

# Formatting

[.header: alignment(center), text-scale(1.5)]

![inline](images/prettier-format.png)

#### **Format code** using Prettier
#### Works by compiling code to an AST, and then pretty-printing the AST

---

[.header: alignment(center), text-scale(1.5)]

# **What Can You Do** with ASTs?

| Examples                                             |
| ---------------------------------------------------- |
| 1. Create your own Babel plugin                      |
| 2. Write custom ESLint rules                         |
| 3. Generate codemods to refactor code quickly        |
| 4. Analyze your code by looking into AST parse times |
| 5. Build your own AST parser                         |

---

[.header: alignment(center), text-scale(1.5)]
[.header-strong: #1A99FC]

# Start Exploring ASTs

![inline](images/ast-explorer.png)

#### **https://astexplorer.net**

---

[.header: alignment(center), text-scale(1.5)]
[.header-strong: #1A99FC]

# Explore AST Parsers

![inline fit](images/ast-explorer-other.png)

#### **https://astexplorer.net**

---

> Thank You 🙏
