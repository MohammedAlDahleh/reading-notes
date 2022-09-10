## Things I want to know more about

# Redux-Toolkit

* The official, opinionated, batteries-included toolset for efficient Redux development

* Purpose
- The Redux Toolkit package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

1. "Configuring a Redux store is too complicated"
2. "I have to add a lot of packages to get Redux to do anything useful"
3. "Redux requires too much boilerplate code

* These tools should be beneficial to all Redux users. Whether you're a brand new Redux user setting up your first project, or an experienced user who wants to simplify an existing application, Redux Toolkit can help you make your Redux code better.

* Installation

- Using Create React App

- The recommended way to start new apps with React and Redux is by using the official Redux+JS template or Redux+TS template for Create React App, which takes advantage of Redux Toolkit and React Redux's integration with React component

```
# Redux + Plain JS template
npx create-react-app my-app --template redux

# Redux + TypeScript template
npx create-react-app my-app --template redux-typescript
```
* An Existing App
- Redux Toolkit is available as a package on NPM for use with a module bundler or in a Node application:

```
# NPM
npm install @reduxjs/toolkit
```
- It is also available as a precompiled UMD package that defines a window.RTK global variable. The UMD package can be used as a <script> tag directly.

* Redux Toolkit includes these APIs:

- configureStore(): wraps createStore to provide simplified configuration options and good defaults. It can automatically combine your slice reducers, adds whatever Redux middleware you supply, includes redux-thunk by default, and enables use of the Redux DevTools Extension.

- createReducer(): that lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements. In addition, it automatically uses the immer library to let you write simpler immutable updates with normal mutative code, like state.todos[3].completed = true.

- createAction(): generates an action creator function for the given action type string. The function itself has toString() defined, so that it can be used in place of the type constant.

- createSlice(): accepts an object of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.

- createAsyncThunk: accepts an action type string and a function that returns a promise, and generates a thunk that dispatches pending/fulfilled/rejected action types based on that promise

- createEntityAdapter: generates a set of reusable reducers and selectors to manage normalized data in the store

- The createSelector utility from the Reselect library, re-exported for ease of use.

# MobX

- MobX is a standalone library, but most people are using it with React


* Conceptually MobX treats your application like a spreadsheet.

1. First of all, there is the application state. Graphs of objects, arrays, primitives, references that forms the model of your application. These values are the “data cells” of your application.

2. Secondly there are derivations. Basically, any value that can be computed automatically from the state of your application. These derivations, or computed values, can range from simple values, like the number of unfinished todos, to complex stuff like a visual HTML representation of your todos. In spreadsheet terms: these are the formulas and charts of your application.

3. Reactions are very similar to derivations. The main difference is these functions don't produce a value. Instead, they run automatically to perform some task. Usually this is I/O related. They make sure that the DOM is updated or that network requests are made automatically at the right time.

4. Finally there are actions. Actions are all the things that alter the state. MobX will make sure that all changes to the application state caused by your actions are automatically processed by all derivations and reactions. Synchronously and glitch-free.


* A simple todo store...
 
 - For originality's sake let's start with a very simple ToDo store. 

```
class TodoStore {
  todos = [];

  get completedTodosCount() {
    return this.todos.filter(
      todo => todo.completed === true
    ).length;
  }

  report() {
    if (this.todos.length === 0)
      return "<none>";
    const nextTodo = this.todos.find(todo => todo.completed === false);
    return `Next todo: "${nextTodo ? nextTodo.task : "<none>"}". ` +
      `Progress: ${this.completedTodosCount}/${this.todos.length}`;
  }

  addTodo(task) {
    this.todos.push({
      task: task,
      completed: false,
      assignee: null
    });
  }
}

const todoStore = new TodoStore();
```

-   We just created a todoStore instance with a todos collection. Time to fill the todoStore with some objects. To make sure we see the effects of our changes we invoke todoStore.report after each change and log it. Note that the report intentionally always prints the first task only

```
todoStore.addTodo("read MobX tutorial");
console.log(todoStore.report());

todoStore.addTodo("try MobX");
console.log(todoStore.report());

todoStore.todos[0].completed = true;
console.log(todoStore.report());

todoStore.todos[1].task = "try MobX in own project";
console.log(todoStore.report());

todoStore.todos[0].task = "grok MobX tutorial";
console.log(todoStore.report());
```

# Hookstate
- Preface

- tuitive API. Most things will be self-explanatory. More in depth description will always be there.

- Code samples in each section are self-contained, complete and interactive. So, jump to the relevant section, copy-paste a sample to your app and extend it as needed.

- IntelliSense by IDE. If your project is in TypeScript, you will benefit a lot as type inference of the API functions supports any complexity of data structures of your states. Of course, you can also use it from plain JavaScript.

- Complete demo application. There is a Todo-list-like [complete demo application](https://github.com/avkonst/hookstate) built with Hookstate. It uses and demonstrates most of the core features of Hookstate. It gives an example of how to organise your project. You may follow the example or use any other module-composition structure.

- Installation and dependencies

- The library does not have external or peer dependencies, except React.

```
npm install --save @hookstate/core
```

- Hookstate consists of the core package @hookstate/core and optional plugins @hookstate/*, which you may include when needed. We have a goal of keeping the core library as small as possible but still feature-rich to address most of problems in state management and provide a good foundation for plugins. Plugins extend the library and address more specific needs. You can also write your own plugins: it is easy and gives a lot of power.

* Browser support

- Hookstate supports all recent browsers and works where React works, including mobile applications and server side rendering.

* IE11 support

- The library supports IE11 with a few exceptions for mutations of nested state, which has alternative working methods. The nested state section notes these exceptions.

- If you need to polyfill, for example for IE11, you need to make sure the following is supported by the target environment. You may checkout the existing IE11 demo project.

- ES5, Map and Set (All are available a long time ago, including for IE11)

-Symbol (You likely already have got one from the react-app-polyfill. If you do not import react-app-polyfill, you can get the standalone es6-symbol)

- Number.isInteger (Polyfill is available from core-js/features/number/is-integer)


[Redux Toolkit (RTK)](https://redux-toolkit.js.org/)<br/>
[MobX](https://mobx.js.org/getting-started.html)<br/>
[HookState](https://hookstate.js.org/)<br/>
[Tutorial](https://redux-toolkit.js.org/tutorials/intermediate-tutorial)<br/>