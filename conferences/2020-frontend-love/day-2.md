_[Home](../../) / [Conferences](../../) / [Frontend Love - 2020](../) / Day 2_
# Day 2

Key points:
- dive into some of these SVG resources, apparently animating SVGs is fairly straightforward
- code `AMS2020` gives 30% off an annual subscription to Vue mastery (25% of revenue goes to Vue.js)
- try out vue composition api, it works with Vue 2
- try building a store front to sell SVGs!

## State of Vuenion - Evan You
- Summary of 2019 has been spent pushing Vue3 from research and prototyping into a reality.
- Vue.js devtools are currently at 1.1million active monthly users.

Stage 1 - late 2018 to early 2019:
_laying the foundation for experimentation_
- adopting typescript
- following a monorepo architecture
- new testing setup using Jest
- refined workflow scripts
- established RFC process

Stage 2 - early to mid 2019: _aligning and validating major new ideas_
- rethinking the runtime update strategy, ended up rewriting the renderer from scratch
- iterating on new api, with the class api being built on top of the composition api.

The bottleneck of a traditional virtual DOM update strategy is that it is very brute force. It effectively walks the entire tree of node and compares every single one, only when it detects a change does it perform an update.

The performance of traditional rendering is defined by the size of the template rather than the content within it.

Vue 3 Compiler:
- analyses the template and breaks it into blocks, by v-if and v-for. This gives a 'stable tree structure', i.e. one that cannot change.
- this gives us a "block tree" that contains a flat array of all dynamic bindings for each block.

Stage 3 - late 2019 to now: _pushing towards feature complete_
- finalising RFCs
- finishing the new compiler
- server-side rendering

Vue 3 current states: 3.0.0~alpha.5
- runtime / compiler feature parity with 2.x
- most active RFCs implemented
- basic SSR support
- close to beta

The new compiler:
- full source map support
- plugin based transform pipeline
- layered design for higher-order compilers

Advanced Optimisations:
- block based dynamic parts tracking
- more aggressive static tree hoisting
- event handler caching
- stable slots detection

A template explorer against the latest build can be seen here; https://vue-next-template-explorer.netlify.com/

SSR: The last piece of the puzzle, in 3.0 string contatenation as opposed to serlialisation is used wherever possible. This results in a three times improvement to performance.
- seamlessly supports mixing template and render based components
- async setup() serves as a generic hook for async work

Hydration:
- automatically skips static trees in the DOM
- tree shakeable for non SSR apps

This means that for many features, including `v-model`, if you don't use it - it won't be in your bundle!

Typescript:
- the first class type declarations included in vue 3 will provide intellisense even for those working in JS
- 95% of code should now be the same for typescript and javascript projects
- SVG logos allow us to animate our logos

## Scalable Vue Graphics for the Modern Web

We all know we can use SVG for scalable icons.
- Lottiefiles is a collection of animated SVG icons we might want
- Humaaans is a set of svg designs

Using SVG:
- we can copy svgs directly into our tempalte
- we can use vue-svg loader
- loading.io creates nice backgrounds
- emotivefeels.com has some examples of how designs can help animations
- third party plugins can allow SVGs to render 3d models
Everything that can be done with SVG can be created using HTML and CSS.
- SVGs support internal media queiries based on their own size
- you can change the colour of items of clothing with magic, by placing an svg layer on top of an image

To make SVGs:
- after effects
- figma
- svg-edit
- vue.js + GSAP

## The Future of Vue Test Utils
Vue Test Utils is a library of helper functions to assist developers with testing their vue components.

Helpful methods include:
- find()
- findAll()
- getByText()

These help provide unit tests in Vue applications in places where they may be needed.

Typescript support is coming soon to VTU.

shallowMount vs Mount:
- possible API changes in the future, potentially: `mount({ shallow: true })`
- it's really important to consider the responsibility that comes with the the power of shallowMount (it's often risky)

## Vue Composition API

The composition API is a more advanced optional syntax for Vue 3.

What are the limitations of Vue 2?
- large components can becomes hard to read and maintain
- no optimal way to reuse logic between components

When to use Composition API?
- typscript support
- component is too large and needs to be organized by features
- need to reuse code across other components (pagination!!)

Because is run before the component is created the new setup hook, like the `data()` block in the options API, does not have access to this.

Where data was used previously we can now use `ref` to extract just the pieces we need.
```
<template>
	<div>
		<span v-text="capacity"/>
		<button @click="increaseValue" v-text="'+'"/>
	</div>
</template>
<script>
import { ref } from 'vue';

export default {
	setup() {
		const capacity = ref(3);
		function increaseCapacity() {
			capacity.value++
		}
		return { capacity, increaseCapacity };
	}
}
</script>
```

_This syntax is already available to us in Vue 2 using the options api._

`toRefs()` is a newly provided method that maps a reactive object into a non reactive object where all its values are references to the matching property on the original reactive object.

## More Composition API: _Emerging best practices_

`Ref()` vs `Reactive()`:
- ref seems to be being used in 95% of use cases so far
- refs work consistently and can be used instead of reactive in most cases

`watch` becomes more useful in the composition API when working with elements that are not loaded during the `mounted hook` (i.e. behind a `v-if`). We can now simplfy watch the ref and add or remove then.

## Making eCommerce development sexy again with VueStorefront and Composition API

Storefront is a headless ecommerce solution that was originally a boilerplate that has developed into a framework. An issue they were seeing was that mixins were difficult to work with when importing business logic, fortunately the Composition API solves this completely.

Store6 and Shopware are interesting ecommerce solutions to consider.

This is much easier with the composition API:
- we know exactly what we have access to
- implementation details are hidden

Vue Store Front excels in how it allows us to select which ecommerce provider we are interested in without changing any code in our UI.

## Serverless with Vue and Node.js
- Firebase extensions are a powerful tool that offer prepublished functionality.
- Along with firebase Jexia is a neat alternative

Serverless with static sites is a fantastic way to quickly create high quality applications.

## Handling global events with renderless components
Renderless components are simply components that don't have a template, instead they have a `render()` function defined.

That means we can have a component like:
```
export default {
	render() {},
	props: {
		event: {
			type: String,
			required: true
		}
	},
	methods: {
		handle (e) {
			this.$emit('fired', e);
		}
	},
	mounted() {
		Object.keys(this.$listeners).forEach(event => {
			const handler = this.$listeners[event];
			window.addEventlistener(event, handler);
		});
	},
	onDestroy() {
		Object.keys(this.$listeners).forEach(event => {
			const handler = this.$listeners[event];
			window.removeEventlistener(event, handler);
		});
	}
}
```
Which allows us to encapsulate our shortcut logic into a component.

Like:
```
<event-listener event="offline" handle="showOfflinemessage"/>
```

We can also hook up to network events.

These notifcations combined with animations can provide a very smooth user experience.

Global event handlers are also useful in situations where you want a space bar to be able to play a video without having to focus the video.
companion repo: github.com/vueschool/application-shortcuts

`vue-global-packages`

`vueschool.io/love/vue-amsterdam`

## Content loading that isn't broken

There are different types of disabilities
- motor
- cognitive
- audio
- visual

Colourblindness is a serious issue, we should never use colour alone to signify the status of something.

Heading structure:
- keep them in order
- don't skip headings

Single page application issues:
- client side routing
- screen reader announcements
- focus managements

Single page solutions:
- aria live regions
- handling focus

Metadata can be added to routing information to mitigate this issue.

Aria live regions: used to announce non-interactive content changes
- `aria-live="assertive"` - updates announcement interrupts user flow
- `aria-live="polite"` - updates announcement, but waits and doesn't interrupt
	_this is the same as using `role="status"`
- `aria-live="off"` - the defau;t

Aria current: used to indicate a current item in a step
- page
- step
- location
- date
- time

Screen readers have different compatibilites with different browsers:
- NVDA: firefox
- JAWS: internet explorer
- VoiceOver: safari

Landmarks are a very useful way to set up a logic page.

Tabindex: indicates the order that items should be focused
- `tabIndex="0", focusable and added to dom in it's order in the tree
- `tabIndex="1", focusable and added to the top of the focus list (same for 2, 3 etc). We should avoid this as it jumps ahead of DOM order.
- `tabIndex="-1"`, allows an element to be focused programmatically

Accessible Names:
- aria-label: provides essential information about an object
- aria-labelledby: establishes relationships between objects (by ID)
- aria-describedby: provides additional information a user might need

This directive may be useful:
```
Vue.directive('focus', () => {
	// focus the element here (#TODO complete this)
});
```
^ repo github vue memory game accessibility #TODO

## Team Driven Development

A framework to lead a team to success in a high pressure environment.

The ability to produce good teach in a high-pressure enviornment is completely dependent on having a properly organised team.

Most projects face the following challenges:
- different client of PO **expectations** / potentially immature client
- **perceived** pressure from client or management
- **different** ways to measure quality
- **perceived** degree of autonomy / giving value

These issues make people unhappy and will cause low quality output.

Team First is split into three categories:

as a leader:
- a leader can also be a developer
- make the team feel responsible for their work
	- trust the team
	- give people the freedom to be responsible
	- give direction, do not micromanage
	- let people manage their own time
- teach everybody in the team what all disciplines do
- ask people what they want and guide them to what the collective needs
- explain **grind and glory** and give gloy when deserved
- let people **champion** subjects
- put people directly in front of the client. They will win or lose by themselves.

as a developer:
- a developer may also be a leader
- know yourself and have helicopter vue
- understand motivation and why you feel what you feel: **autonomy**, **mastery**, **purpose**.
- understand **agile** workflow processes and **weaponize** them.
- **champion** subjects you like
- failure is **iteration**. Fail forward. You are probably not coding heartrate monitors.
- take decisions on intuition, ask for forgiveness later
- make sure to have a **helicopter view** (step back and look at what's in front of you, it helps to make strategic decisions and helps with bug fixing)

as a team:
- be **one** team, even across offices
- go **low** context
- set up a **definition of ready** everybody agrees with
- agile teams make commitments. If a commitment cannot be made, say **NO**.
- make sure nobody influences the scrum team from the **outside** during a sprint.
- understand **cultural** differences
	- understand **low** context vs **high** context
	communication, go **low** context where we can
	- understand how people **persuade**, principles first vs application first.

Assumption is the mother of all fuck ups.

## What is Nuxt 2020?
- Nuxt is a JavaScript framework based on `Vue.js`, `vue-router`, `vue-meta`, and `vuex` (optional).
- It gives you a manageable directory structure and is perfomance oriented.
- It case cares about developer experience
	- loading screen / indicator in the browser
	- `nuxt build -a` to analyse your bundles
	- Write `.vue` files, CSS pre and post processors supported
- Nuxt does Server Side rendering, althought static generation and client side apps are also supported

Nuxt has powerful built in logic for pages and `fetch`, worth reading up on.