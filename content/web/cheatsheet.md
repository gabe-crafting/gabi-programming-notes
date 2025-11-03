---
title: Cheatsheet
links: []
---

# Testing

::card-group{.w-full}
  :::card
  ## Testing
  
  - Unit testing: Validate the behavior of function, classes, components, methods (Given an input, check if the output is expected)
  - Integration testing
  - End to end testing: Run your app in a simulated environment: Cypress
  - acceptance testing: tests that ensure the software meets all the clients requirement
  - system testing: Tests that work on required hardware/servers
  - smoke testing: Most important tests first before the rest of the suit
  - stress testing: capability of infrastructure
  :::

  :::card
  ## Test driven development
  
  - Have a pipeline that run the tests before making the commit
  - Write tests before start coding
  - Refactor -> Fail -> Pass -> Refactor (till all pass)
  - tool: jest
  :::

  :::card
  ## BDD (Behavior-Driven Development)
  
  Goal: Bridge the gap between business, development, and QA by using a common language.

  Focus: Define system behavior through examples (scenarios) written in natural language.

  1. Discovery: Collaborate with stakeholders to identify features and behaviors.

  2. Formulation: Write behaviors as scenarios (Gherkin syntax).

  3. Automation: Automate those scenarios as acceptance tests.
  :::

  :::card
  ## Integration testing
  
  - Testing multiple units of code together.
  - Not just input and output. See if a function has been called the right way, as many time as needed with the correct parameters, the component has been mounted and so on
  - Ex: Component that takes data from a hook. Check if it displayed properly in the component
  - Ex: API getters that integrates with the application. Proper errors are integrated, proper result display and so on.
  :::

  :::card
  ## Jest
  
  - [Mock functions](https://jestjs.io/docs/mock-function-api): function that you can pass as a callback to test other function. You can watch details about the callback. How many time it was run and what parameters where passed into it.
    - you can acces the watch method intel with `.mock` attribute ex `mockFn.mock.calls`, `mockFn.mock.results`
    - `spyOn` to also track the methods
  - Setup and Teardown: You can set prepearment methods: what will happen before/after testing, for everything or just scoped
  - The Jest Object: Automatically in scope in every test file. Provides the functionality, `test`, `it`, `describe`, etc.
  :::
::

# Data storage and manipulation

::card-group{.w-full}
  :::card
  ## [Rest](https://developer.mozilla.org/en-US/docs/Glossary/REST)
  
  Rest: A web arhitecture that is based on client sending a request and getting a response.Methods:
  
  - [GET](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET) retrieve data from server
  - [POST](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST) cause a change
  - [PUT](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT) replace all the target with the payload
  - [PATCH](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PATCH) apply partial modification
  - [DELETE](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/DELETE) deletes the specific resource
  :::

  :::card
  ## Browser user data storage & database
  
  - [sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage) ends when browser session ends
  - [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) no expiration time
  - [cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies) Any data about user that is stored in a session level (server side)
  
  Crud: all ways that you can operate a store data (used in databases): create, read, update, delete
  :::

  :::card
  ## [Webhook](https://www.getvero.com/resources/webhooks/)
  
  - [video reference](https://www.youtube.com/watch?v=Mfzucn4f9Xk)
  - your frontend uses a third party webhook service provider + the webhookEndpoint
    - by accessing it's frontend
    - by sending it a request for a service
  - the third webhook provider party executes the action then sends a payload (usually a 200) to the sended webhookEndpoint (your backend)
  - your backend notify your frontend that action is completed (most prob with a SSE / sockets)
  :::

  :::card
  [Server-Sent Events (SSE)](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events) is a web technology that pushes text event to the browser
  
  - Unidirectional communication: SSE allows the server to push data to the client (web browser) without the need for the client to make additional requests.
  - uses EventSource to declear the listened link
  - Automatic reconnection
  - Event-driven: Data sent through SSE is organized into named events
  - Text-based data transmission (including objects)
  :::

  :::card
  ## WebRTC (Web Real-Time Communication):
  
  Powerful set of APIs that enable real-time communication directly between web browsers without the need for plugins or intermediary servers. WebRTC is primarily used for peer-to-peer audio, video, and data sharing applications.
  :::

  :::card
  ## [WebSockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
  
  - Protocol: WebSocket operates over a single, full-duplex TCP connection.
  - Bidirectional Communication: Allows data to be sent and received simultaneously between client and server.
  - Real-time Updates: Ideal for applications requiring live updates and instant communication.
  - Efficiency: Reduces overhead by maintaining a persistent connection.
  - inspect them in networking by checking ws
  :::

  :::card
  ## GraphQl
  
  - Query language for APIs, Client's query for certain data, returns requested data in a JSON-like format
  - Allows clients to request specific data they need
  - Defined by a schema describing data types, fields, and relationships
  - Single endpoint for querying
  - Hierarchical queries mirror data structure
  - Supports mutations for creating, updating, or deleting data
  - Subscriptions for real-time updates
  - Optimizing data fetching in complex applications
  - Simplifies API interactions with a single endpoint
  - Type safety and validation of queries
  :::
::

# Optimization & Core web vitals

::card-group{.w-full}
  :::card
  ## Optimization tools
  
  [Reference](https://www.youtube.com/watch?v=0fONene3OIA)
  
  - [web vitals](https://chromewebstore.google.com/detail/web-vitals/ahfhijdlegdabablpippeagghigmibma?pli=1) made by google, hover over elements that need optimization, display measurements
  - [lighthouse](https://developer.chrome.com/docs/lighthouse/overview/) (integrated with devtools)
  - [unlighthouse](https://unlighthouse.dev/) - lighthouse report for each page (has an stk, can be integrated into the pipeline)
  
  ##### FID (First Input Delay)
  
  - The ammount of time the user interacts with the page (click button, process events)
  - Good 100ms < needs improvement 300ms < bad
  - reduce javascript execution time
  - use lazy loading
  - measure with web vitals plugin
  :::

  :::card
  ## LCP (Largest contentful paint)
  
  - loading performance: text -> css -> images & videos.
  - Good 2.5 sec < Needs improvement 4.0 < poor (impact on search engine optimization)
  - analyze open network -> analyze waterfall
  - reduce the resource load time (compress img use modern formats and fonts)
  - serves assets from CDN (content delivery network) server nearby good
  - blocking js (don't run js before loading the image), SSR > SPA
  - preload (modenr browser)
    - img fetchPriority (high/low) html tag
    - preload attribute in link
  :::

  :::card
  ## CLS (Comulative Layout Shift)
  
  Visual stability. All things load at once or pretty close to each other. No random renders apears on screen
  
  - good 0.1 < needs improvement 0.25 < bad
  - generate lighthouse report in dev tools
  - web vitals extension
  - don't use img without width / height tags or aspect-ratio: 4/9;
  - srcset tag different img different containers
  :::
::
