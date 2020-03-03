_[Home](../../) / [Conferences](../../) / [Frontend Love - 2020](../) / Day 3_
# Day 3

Key Notes:
- check out FormVueLatte - schema generated forms, where you pick the components
- check out vue mastery's conference page
- take a look at laravel, SaaS framework
- take a look at bootstrap vue open issues
- look into vonage APIs
- curated packages at https://awesomejs.dev

## Validations in composition age
Validation libraries in Vue.js 2.x
- vee-validate
- vuelidate
	- model based validations

Current problems:
- no lazy validation features
- no built in support for error messages
- requires validation rules for whole data model at once
- hard to share the validation results between components, especially from a child to a parent

Vuelidate v2.0:
- complete rewrite
- built for Vue 3.0
- half the code, quarter the complexity
- mostly backwards compatible

Similar to Vuelidate 1, the rules must map one to one to the state.

Vuelidate validators is a package of error messages for strings.

Common issues with schema form libraries:
- only supports predefined input components
- cant be used with existing UI component libraries
- limited possibilities when it comes to more complex data structures
- not compatible with external validation libaries

**FormVueLatte** provides lightweight schema generated forms:
- "bring your own components" idea
- no built in UI input components
- works with all v-model compatible components
- super lightweight

Roadmap for FormVueLatte:
- adaptors for popular UI libraries like Vuetify
- parsers for popular schema formats like JSON schema

Demo: github.com/shentao/fvlidate

## Authentication from scratch

Current Authentication providers:
- Auth0
- Firebase
- 0auth

JWT: Json Web Tokens, consist of three parts
- header: what type of encryption function
- payload: who the user is
- signature: hash of header + payload + secret

We are going to peresist a token in local storage to allow us to store authentication information.

Example Application consists of three compontns:
- RegisterUser
- LoginUser
- Dashboard (locked)

Registration logic:
1. check if user already exists
2. add the user to our database
3. create a JWT token
4. send a response back that includes that JWT token
5. persist this token in local storage and use it to validate future requests

Login Logic:
1. check user does already exist
2. generate their JWT token
3. send the JWT back ot the user
4. the token is persisted on the user and and used for future requests

Logout Logic:
1. clear the token from local storage

Additional Tips:
- implement route guards for pages that require auth
- catch and display register and login errors
- use localstorage to perform automatic login

## Test Driven Development with Vue.js
Testing is one of the pillars of writing robust software. They should give you confidence that you are not shipping broken software. But testing can be hard!

Works well with vue-test-utils, jest.

## Vuetify 2+

What is Vuetify?
- UI library build on Google's material design specification
- goal is to simplify development process
- make apps look good without having to be a designer
- big improvements in version 2

Updates and changes:
- a11y improvements
- complete RTL support
- conversion to typescript and sass
- massive performance improvements for inputs
- a revamped style variable customization process
- over 10 new components
- new observer API directives

A11y:
- ongoing process with constant improvements
- dedicated a11y contributor
- detailed overview on component doc pages

Internationalization:
- at over 30 languages in the default components currently
- can dynamically update all translations with `this.$vuetify.lang.current = 'it';`
- integrates with `vue-i18n`


Bidirectionality (RTL):
- can be set on an app level on conversion level
- simple as adding a class to change the visual appearance

_VSCode plugin coming soon!_

Improved styling:
- easy to opt-in at any time to modify root SASS variables
- thousands of variables available
- however does increase compilation time

What about when our designers still hate Material Design?
_Now vuetify is so configurable there is no reason it has to look like material whatsoever._

Quality of life changes:
- `v-img` now has deferred or lazy loading built in
- new lazy set of components, `v-dialog`, `v-menu`, `v-tooltip`
- the new default is to lazy load most things, however anything can still be set ot eager load

Long term support:
- 18 months for previous major release
- critical bugs and security vulnerability fixies
- backported fixes
- extensive upgrade guides
- migration help channels

Ecosystem Development: _Improving Productivity_
- new tooling and plugins coming soon
- images are 'progressive' (have lazy loading animation) out of the box

Vuetify 3.0 - Titan:
- rebuild with the composition API
- replace mixins with effects
- improve component structure
- improve development process

Effects to replace Mixin madness:
- uses Vue 3 composition API
- improved readability and process
- no obfuscation

## New Vue. New Compiler.

There are two compilers inside the new Vue library:
- the Template compiler: takes the template block and converts it to a reander function
- SFC compiler: compiler for single file components

_The compiler and differences between them is very interesting. Worth further investigation._

## You might not need Vuex

Do I need a shared stared at all?
- independent components
- different routes
- deep routing

With the vue composition API we can now use a shared reactive object as a form of store, potentially removing the need for vuex.

Apollo client and GraphQL plug in very nicely with these simplfications.

See here for the repo: https://gitlab.com/ntepluhina/vuex-presentation

## Vuex ORM - Relational data management in Vue
What is vuex ORM?
- it "normalizes" the data
- it provides ORM like access to Vuex store

Issues with related data:
- duplicated data is very messy
- it can be a pain to update

Vuex ORM treats vuex as a database. The redux documentation also recommends treating part of your store as a relational database.

By default all Vuex ORM data is going to be stored under `entities` namespace. This means vuex-orm won't interfere with any existing vuex store in your application.

Lookup the documentation for defining models.

There's a slack channel and many useful addons including search, worth checking out!

## Bootstrap Vue: The Road to 2.0 and Beyond
_Jacob Muller, core team member of BootstrapVue_

What is Bootstrap Vue?
The most comprehensive implementation of bootstrap in vue.js, built with accessibility in mind.

History
1. Creator of Nuxt.js came up with bootstrap vue back in 2016
2. Version 1.0.0 was released in november 2017
3. After 28 release candidates, version 2.0.0 was released in december 2019

Bootstrap Icons are now included in bootstrap, it also comes with the concept of icon stacking.

New form tags and calendar components are pretty great.

Current state:
- v2.5.0
- 75 Open issues

What's next in 3.0:
- vue.js v3
	- the composition api
	- portals
- bootstrap v5
	- new grid system
	- component improvements
- popper v2

## Micro Frontends: composing a greater whole

Problems with using the microservice pattern in the Frontend:
- we need a unified user experience
- we need a small bundle size
- in the server world everything is autonomous
- there is no standard library for micro frontends

What are micro front ends?
"Independent, self deployed components that in the whole, makes its own build component."

Benefits of Microfont ends?
- maintainability
- tech freedom
- independent deployment
- customizable

What's the best way to integrate a micro frontend framework?
- Single Framework:
	- build-time integration with npm
	- server side template composition becomes possible
- Multiple Frameworks:
	- less dependencies

Build-time integration:
- independent repos
- easy versionaing
- sharing dependencies
- used by top brands
- easiest to test
- requires rebuild for changes
- not customisable either

Alternative is Run time integration:
- technology agnostic
- works with the shadow DOM
- not used with many brands

or Run time integration using Iframes:
- absolute isolation
- widely supported
- easy to integrate
- used by top brands
- old frashion
- no shared dependencies

or Run time integration using JS and SPA
- highly flexible
- simple to conver existing applications
- easily send data
- no isolation

Whats the best way?
"All of the above". You want to enable as many of these methods as possible to make it as easy as possible for brands to integrate.

What about the unified user experience?
- shared CSS libraries
- shared components libraries

Communication?
- shared lifecycle events
- solve with @vonage/micro-frontends, with the MicroFrontendsOrchestrator

## High Level Introduction to Composition API

What's best about Vue.js?
- easy to learn
- easy to use
- Vue is options based (this isn't going away)

Vue 3:
- smaller and faster
- new features
- better typescript support
- more maintainable codebase
- in alpha, coming out in a few months, user code likely won't change

Currently we have reactivity caveats, however in Vue 3 there is no longer any need for `Vue.set` or `Vue.delete`

Portals allow us to 'teleport' an element. They are similar to routers in that regards however is built in to vue. This could mean we don't have a dependency on vue-router for much longer. They are already available in Vue-2 with the `vue-portal-plugin`

Vue 3 no longer requires a wrapper component. Multiple nodes can go in a single template.

The V-model api will update to support adding multiple models to a single component.

Composition API Benefits:
- extremely flexible
- clear source of properties
- performance
- no namespace collision

Composition API is a great fit for:
- when components grow too long
- multiple stakeholders in one big component
- when typescript support is important

Drawbacks of Composition API:
- overhead of introducing refs
- no shared template
- learning curve

Consider:
- no need to rewrite your Vue 2 app
- no need to use it in a simple component
- keep the junior devs in mind
(Vue.js team member's opinion

Suspense: new component that loads default components
```
<Suspense>
	<template #default>
	...
	</template>
	<template #fallback>
	...
	</template>
</Suspence>
```
This can help remove a lot of loading code!

Filters are also being removed in Vue 3.

## Performant Components through Customization

What is a component library?
- reusable
- stylable, and follow a style guideline
	- visual consistency
	- functional consistency
- customizable
- responsive and mobile friendly

_It's not just a component library, it has theming, styles and more. It's really a whole design system._

How to make a good library:
- define the goals of your component library, perhaps decide a reference style guide
- good planning === less breaking changes
- define component needs
- consider the DX of library consumers, not just props but also external dependencies etc
- consider the total build size, to ensure things are small and good for the planet!
- ease of use, you have 5 minutes to make me happy when trying

Best way to style components:

_We should use CSS variables instead of scss to set up the core of our styles. Variables can be modified within a block without effecting other parts of the page._

Storefront UI is a pretty good implementation of a framework. Inspired by atomic design.

## Vue Router

Vue router has some major limitations such as a lack of adding routes dynamically during your code.

It is improved by vue-router-next with:
- dynamic routing
- custom hisotry
- better envoding defaults for internationalisation
- to work with the composition api
- navigation direction
- better TS support
- easier to contribute
- more per-case documentation

## Building Blaze, Fast Sites with Gridsome

Gridsome is a tool to render pages built with Vue components to HTML and CSS at run time. It also provides a centralized GraphQL store for any data you will utilize in Vue templates. It even provides some features outside of Vue's scope.

It excels in DX:
- plugin ecosystem, including source plugins
- automatic code splitting

Uses the PRPL Pattern:
- push critical resources from initial URL route
- render initial route
- pre-cache remaining routes
- lazy load and fetch additional routes on demand

Gridsome doesn't sacrifice user experience for developer experience. It leverages DX to promote good UX by making the "right" choices easy.