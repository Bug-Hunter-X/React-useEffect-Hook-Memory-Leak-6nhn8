# React useEffect Hook Memory Leak

This repository demonstrates a common error in React applications involving the `useEffect` hook: forgetting to include a return statement for cleanup.  Failure to return a cleanup function can result in memory leaks and unexpected behavior, especially when dealing with subscriptions, timers, or event listeners.

## Bug Description

The `bug.js` file showcases a component that uses `useEffect` to log a message when the component mounts.  Crucially, it *omits* the return statement needed to clean up after the effect. This means that any resources allocated within the effect (though this example is minimal) remain active even after the component is unmounted, potentially leading to memory leaks and performance issues.

## Solution

The `bugSolution.js` file corrects this issue by including a return statement with a cleanup function. This function ensures that any necessary cleanup actions (in this case, there are none, but it would handle tasks like unsubscribing from event listeners or clearing timers) are performed before the component unmounts.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `npm install` to install dependencies.
4. Run `npm start` to start the development server.
5. Observe the behavior in both `bug.js` and `bugSolution.js` to see the difference.

## Key Learning

Always include a return statement with a cleanup function within `useEffect` hooks to manage resources efficiently and prevent memory leaks in your React applications.  Good coding practices dictate the use of these cleanup functions for any external actions done in useEffect.  This is best practice even if the effect seems simple.