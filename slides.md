---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-left
title: How React18 Importve Performance
---

# How React 18 Improves Application Performance

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Main thread and Long Tasks
<br/>
<div>
When we run JavaScript in the browser, the JavaScript engine executes code in a single-threaded environment, which is often referred to as the main thread.
</div>
<br/>
<br/>
<br/>

<div>
  <img src="/main.avif" />
</div>

<br>
<br>


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Main thread and Long Tasks
<br/>
<div>
Any task that takes more than 50 milliseconds to run is considered a "long task".
</div>
<br/>
<div>
This 50ms benchmark is based on the fact that devices must create a new frame every 16ms (60fps) to maintain a smooth visual experience.
</div>

<br/>

<div>
  <img src="/main2.avif" />
</div>
<div v-click class="w-full h-full absolute top-10 left-10">
  <img class="w-80%" src="/side1.png" />
</div>
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Total Blocking Time
<br/>
<div>
Total Blocking Time (TBT) is an important metric that measures the time between the First Contentful Paint (FCP) and Time to Interactive (TTI).
</div>

<br/>
<br/>
<div>
  <img src="/main3.avif" />
</div>

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Interaction to Next Paint
<br/>
<div>
The Interaction to Next Paint (INP), a new Core Web Vitals metric, measures the time from a user's first interaction with the page (e.g. clicking a button) to when this interaction is visible on-screen
</div>

<br/>
<br/>
<div>
  <img src="/main4.avif" />
</div>

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Traditional React Rendering 
<br/>
<div>
A visual update in React is divided into two phases: the render phase and the commit phase.
</div>
<br/>
<div>
The render phase in React is a pure computation phase where React elements are reconciled with (i.e. compared to) the existing DOM.
</div>
<br/>
<div>
The commit phase, React applies the updates calculated during the render phase to the actual DOM. This involves creating, updating, and deleting DOM nodes to mirror the new React component tree.
</div>

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
.slidev-vclick-hidden {
  display: none;
}
</style>

---

# Traditional React Rendering 
<br/>

<div class="mt-4">
  <img src="/main5.avif" />
</div>

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Traditional React Rendering 
<br/>
A synchronous render is an “all-or-nothing” operation, where it’s guaranteed that a component that starts rendering will always finish.

<div class="mt-4">
  <img src="/main6.avif" />
</div>
<br>
<br>
Poor in INP

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Concurrent Render 
<br/>
In that case, React will yield back to the main thread every 5 milliseconds to see if there are more important tasks to handle instead
<div class="mt-0">
  <img class="w-80%" src="/main7.avif" />
</div>
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Concurrent Render 
<br/>
<div class="mt-0">
  <img class="w-80%" src="/main8.avif" />
</div>
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Transitions
<br/>
We can mark an update as non-urgent by using the <b>startTransition</b> function made available by the <b>useTransition</b> hook. 

```ts {all|4|10-12}
import { useTransition } from "react";

function Button() {
  const [isPending, startTransition] = useTransition();

  return (
    <button 
      onClick={() => {
        urgentUpdate();
        startTransition(() => {
          nonUrgentUpdate()
        })
      }}
    >...</button>
  )
}
```
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# React Server Components
<br/>
React Server Components are an experimental feature in React 18, but ready for frameworks to adopt. This is important to know before we delve into Next.js.

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# React Server Components
<br/>

<div class="mt-0">
  <img class="w-60%" src="/main9.avif" />
</div>
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# React Server Components
<br/>
React Server Components allow React to send the actual serialized component tree to the client. The client-side React renderer understands this format and uses it to performantly reconstruct the React component tree without having to send the HTML file or JavaScript bundle.
<div class="mt-4">
  <img class="w-80%" src="/main10.avif" />
</div>
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# React Server Components
<br/>
We can use this new rendering pattern by combining react-server-dom-webpack/server's renderToPipeableStream method with react-dom/client's createRoot method.
<br/>
```ts {all|4}
// server/index.js
import App from '../src/App.js'
app.get('/rsc', async function(req, res) {  
  const {pipe} = renderToPipeableStream(React.createElement(App));
  return pipe(res);
});

---
// src/index.js
import { createRoot } from 'react-dom/client';
import { createFromFetch } from 'react-server-dom-webpack/client';
export function Index() {
  ...
  return createFromFetch(fetch('/rsc'));
}
const root = createRoot(document.getElementById('root'));
root.render(<Index />);
```

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# React Server Components
<br/>
By default, React won't hydrate React Server Components. The components aren't expected to use any client-side interactivity like accessing the window object or use hooks like useState or useEffect.
<br/>
<br/>
you can use the "use client" bundler directive on the top of the file. 
<br/>
<br/>
<div>
  <img src="/main11.avif" />
</div>

<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Suspense
<br/>
Using Suspense, we can delay the rendering of a component until certain conditions are met, such as data being loaded from a remote source. In the meantime, we can render a fallback component that indicates that this component is still loading.
<br/>
<br/>
```ts
async function BlogPosts() {
  const posts = await db.posts.findAll();
  return '...';
}
 
export default function Page() {
  return (
    <Suspense fallback={<Skeleton />}>
      <BlogPosts />
    </Suspense>
  )
}
```

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Conclusion
<br/>
- With Concurrent React, the rendering process can be paused and resumed later or even abandoned. This means the UI can respond immediately to user input even if a large rendering task is in progress.
<br/>
<br/>
- The Transitions API allows for smoother transitions during data fetches or screen changes without blocking user input.
<br/>
<br/>
- React Server Components lets developers build components that work on both the server and client, combining the interactivity of client-side apps with the performance of traditional server rendering without the cost of hydration.
<br>
<br>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Refernce
<br/>
<a target="_blank" src="https://vercel.com/blog/how-react-18-improves-application-performance">How React 18 Improves Application Performance</a>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>