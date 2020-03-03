_[Home](../../) / [Conferences](../../) / [Frontend Love - 2020](../) / Day 1_
# Day 1
Key Points:
- look into using lighthouse to audit for SEO and a11y
- look into playwright for testing
- use storybook to create documentation for component libraries
- check out Kitze's website: https://ok-google.io
- go and try out this dialogflow project further
- investigate AWS amplify

## How thinking small is changing software development big time
- Doing things in projects doesn't work
- Avoid monoliths and large changes
- Release small and often, multiple times a day
- We have sped up as programmers so much in the last 50 years, what's next?

## How to pack Webpack
- try using a typescript webpack configuration, powered by node-ts
- do as little at compilation time as possible
	- don't check types
	- don't lint, your IDE can do this at a different time
- use lighthouse to see how you're doing

## Svelte JS
- another framework
- pretty nifty and simple
- computed js variables are a neat touch

## Serverless
- still cheap
- still scalable
- works well with microservices
- less infrastructure overhead

## Browser Testing
- [Cypress](https://www.cypress.io) is a very powerful tool but not ideal for:
	- cross-browser testing (recent cross browser release())
	- cross-domains testing - it has some useful features but is best for testing during development
- [Webdriver](https://webdriver.io) is a pretty good alternative, along with [Testcafe](https://devexpress.github.io/testcafe).
- [Puppeteer](https://github.com/puppeteer/puppeteer) is another alternative, a tool focused on controlling browser actions. However for now it only works for chrome :( ([Taiko](https://github.com/getgauge/taiko) is similar)
- [Playwright](https://github.com/microsoft/playwright) might just do it right:
	- cross browser
	- built by the same team who built Puppeteer, but at microsoft
	- has a great jest preset
- Webdriver is still competetive but their is a new approach (using native browser protocols) that is planning to take the code

## Practical A11y for Web Apps
_Getting started with accessibility in SPAs_
- Why accessibility? It's the law, to make sure your app is usable by everyone, SEO, screen readers and IoT
- Everyone has times they have limited control of an app, i.e. using one in a car or with one hand full.
- The guidelines:
	- Perceivable
		- meaningful order of content
		- don't only use color to convey information
		- sufficient contract
		- do not restrict a single orientation
	- Operable
		- user interface components and navigation must be keyboard + tab operable
		- logical focus order
		- labels for user interface elements
	- Understable
		- language attribute present
		- don't randomly change context (i.e. change page based on dropdown choice)
	- Robust
		- use native HTML elements where possible
		- they provide accessible properties out of the box
- Client side routing:
	- you want to scroll to the top
	- you want it to focus on the first element in the body
- In chrome devtools there is an accessibility tab, it's pretty powerful (even includes a contrast check!)
- Look out for loops in tab index
- and turn off CSS to ensure visual order of components is following the DOM order
- Test your app with the screen readers, either Voice Over on mac or NVDA on windows, on desktop and mobile
- Landmarks are a powerful way to identify the structure of a page:
	- In voice over there is a shortcut for landmarks, which lists all that are on the page
	- examples: `<nav>`, `<main>`, `<search>`
	- Add 'skiplinks' to navigate directly to landmarks
- WAI-ARIA
	- rule #1 of ARIA, don't use ARIA, instead use plain HTML elements
	- ARIA is very powerful and therefore very dangerous / spooky
	- If you must create your own interface components then follow the ARIA w3 best practives
	- the exception to the rule: `aria-live`, i.e.:
		`<div aria-live="polite">Hi</div>`
		in JS we dynamically update parts of the screen, this will politely notify the user

## Micro-interactions
"I wish I knew how to add animations to my application." is a very common thought as CSS animations don't seem very robust.
- animations can illustrate a state change
- they are very effective at capturing a users attention
- custom progress bars convince users to wait for a little longer
- they build habits, facebook and instragram as simple examples
- micro-interactions have 3 core parts:
	- an interaction
	- a state
	- an animation
	- never make your users wait for an animation when the data is available
- React Spring is an example of a physics based animation framework

## But you're not Facebook
- Kitze on twitter, very entertaining guy
- we don't need to do things like facebook, because we aren't facebook
- sizzly is a neat (paid) browser that is very useful for testing on multiple devices
- spending months to save 14kb from a bundle is usually a waste of time
- https://ok-google.io/ is his site
- starting programming live streams on saturday, might be worth checking out
- He was mean about `eslint-config-airbnb` :(

## Beats, Rhymes and Unit Tests
_[Speech recognition and unit tests.](https://github.com/tonyedwardspz/beats-rhymes-and-unit-tests-demo)_
- There are 2 Billion speech to text devices out in the market currently.
- There are incredible tools for people looking for more accessible options.
- The Speech Recognition API:
	- only works with chromium based browsers at the moment
	- There is a web platform example provided by google
- Can you use the SpeechRecognitionAPI:
	- to parse spoken words?

In short, speech to text is a powerful tool, I should try and use it.

## GraphQL Without a Database
GraphQL allows you to 'join' data in a way that can allow data that would previously have taken multiple requests to load, can now be loaded in a single request.

It's also useful as it allows us to select which parts of data we want to load, and this is valuable when many people are on mobile data. These large JSONs also use memory resources that we don't need.

It's possible to create a wrapper for a REST api that can allow us to make GraphQL requests without a dedicated database.

Open API to graphQL is another useful tool to port an existing rest API to graphql.

## DX is the new black:
DX is developer experience, it covers things such as:
- enjoyment coming to work each day
- getting apps up and running on their machine seamlessly
- quick and reliable deployments
- CI/CD

Storybook is 'living' documentation in that it uses the latest build of your components. It's an example of visually driven developent. It's very powerful and provides documentation and a demo of components rolled into one.

It's also possible to add custom tools to Storybook, such as configuring breakpoints to show etc.

## What is WebAssembly (WASM)?
- Byte code format
- Compilation target for higher level languages
- It is much quicker to load into the browser and can be run right away
- It's a web standard, this means **no plugins!**
- Runs in the same sandbox as js applications, meaning we have the same in built security protecting local storage, webcams, etc.

What is Blazor?
- component based UI Framework for creating SPA's
- based on .NET core razor pages
- uses a virtual DOM (render tree)
- it can use webassembly!
- there are two flavours: server side rendering, and client side (allows you to write C# to run in browser!!)

What is Razor?
- template markup syntax based on C#
Optimized for HTML generation with minimal transition between HTML and code

Client side Blazor is still in preview but is very promising:

Pros:
- works offline
- runs directly in browser
- code execution faster than js
- reduces server-side load
- code sharing between client and server

Cons:
- still in Preview (release planned for May 2020)
- requires the entire runtime to be downloaded (for now, 3mb)
- restricted runtime as not the full .NET environment
- debugging is cumbersome because of tooling not being finished (for now)

## Audio Streaming - Using WebRTC for building your own Voice AIs
This talk isn't about google assistant, it's about streaming audio to a back end to apply machine learning.

Google assistant facts:
- publicly available
- runs on all assistant powered devices
- native google assistant features
- Invoke actions: "Hey Google, talk to \<my app>"
- customer Terms and conditions
- special technical requirements (max 30s recording)

You might want to build your own AI due to technical requirements, overkill or enterprise usage.

Short Utterance vs Streaming:
- short utterance: i.e. "turn on the lights" matches to one intent
- long utterances have many possible intent matches

**RecordRTC** is a javascript library to allow you to stream audio to a backend (and select number of channels). Audio should be sent to the backend as mono.

**Socket IO stream** with socket IO provides two way data streaming to stream the audio to and from the server and client.

**Google speech-to-text** enables developers to convert audio to text. We can use dialogflow for this directly with audio, but if we want to support multiple languages it is good to use text to speech and translate to a base language (i.e. English) before sending to dialogflow as text.

**Dialogflow** is a powerful ML tool from google to convert english sentences to functions (intents) with parameters. A good rule of thumb is to add ~15 or so examples to each intent. It offers powerful tools for speech synthethis

Check out github.com/dialogflow/selfservicekiosk-audio-streaming

## Offline First (Synchronising Data)
What does it mean?
- Data is written to and queried locally from the end user's device and periodically uploaded and replicated in the database.
- Provide a consitent user experience even with spotty internet connections

What is a real time application?
- an application that functions within a timeframe that seems immediate (i.e. google docs, chat apps)
- cohesive system where data is in sync across all connected devices

Client technnologies:
- AWS amplify - multi platform on-device persitant storage, this synchronises later when possible (powered by graphQL, much of this is open source)
- AWS appsync

Cache challenges:
- data synchronisation (conflict detection and resolution, clock based - can get very academic)
- complex querying
- additional complexity in your code

It is important to remember that we shouldn't be treating our typical cache as a database due to the above challenges.

"Optimistic responses" are a pattern where you assume there will be no issues synchronising with the database later and we give the user a seamless experience.

Maybe the solution is a _store_ instead of a _cache_?

Amplify Datastore:
- monotonic counters
- controlled by the system itself (AppSync)
- graphQL types with versions used for merged or rejected decision
- powered by base tables and change tables with graphQL types

AWS AppSync provides some nifty auto-merge functionality, for a price.

## The state of WebAssembly
Issues with javascript as is:
- no types
- polymorphism
- unpredictable behaviour
- runtime errors!

WebAssembly is not a language, it's a high level implentation of how to run native code inside the javascript engine.

Advantages of WebAssembly:
- near native performance (~30% faster than JS)
- secure
- uses a linear memory model, as a Shared Array Buffer
	_continous array where new information is simply added to the end of the list. Very quick to add new data, slow to update / remove._

It's important to remember that due to the above WebAssembly is not always a faster solution.

What languages support WASM?
- C / C++ (+it has a lot of options, +all batteries included, -verbose)
	_write normal C code and add a `WASM_EXPORT` notation to the top of your file_
- Rust (+less verbose, +small runtime, +inbuilt into the compiler, +best tooling support, -sometimes bigger binaries)
	_run `cargo install wasm-pack`_
- AssemblyScript (+closer to js community, +awesome tooling)
	_`npm i --save-dev assemblyscript`_
- GO - it can be done I guess...