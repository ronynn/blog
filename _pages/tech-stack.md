---
layout: page
title: TechStack
permalink: /tech-stack/
---

In recent times, choice of tech stack globally is shifting towards React just because AI knows it best, while I agree I'd still argue that simplicity, packet-size and closeness to native are still more important considerations for extensibility, specially for software that people will depend on. While one must be picking the right tool for the job, building skills to be confident in the tool takes time.

I often don't code for months only to get back look at my projects clueless how my js code looks like perl. A main reason for this page to exist is to keep my observations and tools of choice in place, and avoid wasting time reading online framework wars and debates or start hunting for the best tool for the latest job.

I'm pretty much only focussed on javascript. I think kotlin might be the best language, but I don't [use](github.com/ronynn/shintaku) it often. 

## Go to Stack (Opinionated)

- UI: petite-vue -> vue, preact+signals (+HTM) with Twind
- Server: Flask/Sanic
- Canvas API + Matter.js (for physics) or Konva.js (for scene graph/events), ZDog (pseudo-3d), p5.js (has webgl mode), W by xem for sizecoding webgl projects


### Tools specific to when they are required

- Data visualization: D3.js, Chart.js, µplot.js
- Analytics: Goatcounter (privacy friendly)
- Fast server: FastAPI, Hono + Wouter with Pocketbase
- SSG: Astro, Vuepress, Zola, Hugo, Pelican
- Vite with Deno for all sorts of testing and optimizations


- Aframe-Three.js, Godot: great DX, still very slow for simulations that are to run on web
- Ogl: Writing shaders is difficult
- React-Three-Fiber, React-Native
- Svelte, Threlte, Svelte-Native
- Marcoquad: When showing off using Rust skills
- Littlejs by Frank Force (has box2d and threejs plugin): Epic, but I'm not making any traditional full fledged games
- Kaplay: ECS based API
- Phaser4: has box 2d plugin, has MCP servers that can help using AI to make full commercial games, not immediate goal (my ideas are more DOM focussed)
- Pixijs, great api for webgl


### Reasoning behind tool ranks

Anytime I look up best tools, the most commonly hyped ones are suggested, but I'm not looking for the most tutorial focussed tools these days, just the lightest ones for my niche that provide quick/fast interactive dev and user experiences

For picking/updating the rank of choices in my techstack list, I consider some criterias

- Should give me useful skills in a world without internet, I can build with it with just the docs: That includes only the browser and python (that would be python2 tbh). I'm not very good with dom manipulation for big projects and the canvas api or webgl shaders but probably can build with it if I have a book in hand.
- Should be useful in limited internet connectivity and compute: I want to avoid build step, dependency on npm for frontend and I must build skills to quickly rewrite basic tools, an important aspect to keep in mind is that the target audience may always be in limited connectivity with weak phones so design should keep that in mind, petite-vue expertise for all projects is my goal
- Should provide great support even with cheap AI use: Either be react or vue or be close to vanillajs (also jquery if it's being used). Problem is that when it comes to canvas or threejs that's when either you need the top tier models or personal expertise, I depend on Aframejs for this as it's comparatively easier.
- Should be expandable with maybe a team: Preact is thus in my list, petite-vue to full vuejs route is clean enough as well.

> "And when implementation labor stops being scarce, the rational bet moves back down the abstraction ladder"
> - rwieruch

### Experiences

My techstack choice back in the days heavily relied on how many examples a library provides and if I can make do by their help for my own project ideas, these days I'm more into assembling microframeworks for specific tasks to keep code closed to metal/target.

I must focus on learning the standards and then easy additions. Even though I'm aware of how great they are, I gotta specialize instead of generalizing on most advertised good features, but will use them when I have a relevant project at hand.

#### Frontend

- [Karui](github.com/ronynn/karui) started as a Alpinejs app which I started by extending and adding features to a todolist tutorial code, but at a point (I believe when adding tabs), console errors were no longer helping me (because all the code was wrapped in a single #app just like the tutorial which was limited in scope). I also feel that alpine.cdn.min.js being bigger than jquery.slim.min.js is making me avoid it for future projects, petite-vue is better alternative considering its limits and simplicity.
- Svelte: Lovely simplicity, after alpine.js I moved Karui to svelte and it was delightful. I have to avoid this for now as I code on android and no matter the app vite always turns off and doesn't do HMR properly. Vitest is simply remarkable
- Took some time to get better at Preact with htm and twind, with signals it simply is the best at what it does, though I am not proficient at it yet
- Using W by xem feel lightweight and simple, littlejs might be better option if webgl is goal, p5.js webgl is not that performant
- d3js is difficult but useful if data to show is complex, chartjs is very easy and gorgeous, uplot is very light


#### Backend

- Used Mesa for a simulation, that runs on a server, used Flask for showing the result in a webview, it was complex but enjoyable. Tried several libraries to pack it into an exe, didn't work. Flask is delightful to use and I want to make something with Sanic, maybe turn the multiplayer interactive fiction game tutorials into full playable web games
- Wordpress with it's security vulnerabilities is not something I can recommend anymore, lots of other cms exist. As for php I do hear good things about laravel, for a project that really needs what it provides and when FastAPI is not the best option, there's Frankenphp now too
- Hono + Wouter + Pocketbase, I hear great things but I've never used these, closest thing I remember is the express js tutorial from freecodecamp.
- Astro has impressed me, Vuepress has nice themes, but if I was building something quick, given my focus on size and maintainability I'd pick Hugo or Zola, a single binary to install and start editing
- Jekyll: My blog uses it, but that's coz github only supported it back when I started, it's known to be slow for big sites



## Text editors

My Laptop, from what I've read online, is one of those with locked bootloaders, so linux couldn't be installed, currently it doesn't turns on.

- Acode editor on my phone, lets be honest this is my daily driver, runs alpine linux terminal, but due to android limitations I can't make good use of Vite
- Notepad++: It's simple and it works great, most of my pre-2023 projects were written with it
- VSCode: was way too slow on my pc, and on google's idx, but github codespaces editor works fine
- Termux/Cmder: 
  - Helix Editor: It's simple, it works and looks great
  - Vim: I am not proficient at using this, but introduced me to mode based editors, copying down lines and finding functions were very quick, ideas that got me looking into Helix



## Have used previously but not proficient

- React (Freecodecamp](https://github.com/freecodecamp-front-end)
- Alpinejs (Nice, not scalable)
- Svelte (Demos only, a version of karui, no complaints)
- Typescript (outside vscode/any IDE it isn't of much help except for type errors, which I don't face given I only work on niche projects and made nothing over 10k loc)
- Nim (used for Nim to js, didn't make anything its made for)
- C# (Freecodecamp, MSLearn Certificate)
- Pyscript (it wasnt slow on my phone)
- SCSS (CSS today can do most of the things that it couldn't when SCSS was popular, I've used it with jekyll for an older version of my blog that tried to look like medium)
- Ruby on Rails (nice but I only did odin project tutorial)
- Jekyll Pages: [Current Blog](https://github.com/ronynn/blog)
- GLSL Shaders in shader editor
- Processing, P5js, Q5js
- Tic80 with Lua, want to learn python with it
- Threejs, aframejs: [prototypes](https://github.com/ronynn/prototypes)
- Livescript, Coffeescript, Pugjs (dead tech but is very clean)
- Sugarcube-2, Gruescript, Inkle's Ink, Inform6
- JQuery in Twine Snowman


## Interested in using for full projects someday

- Macroquad (Rust): The Rust Programming language book was delightful to read, previoualy wrote a small compiler for the inkle format as a learning demo
- Tailwind with Daisy UI (too mainstream though, also npm installation gets stuck at postcss install step on all my devices)
- Beercss (For material design UI)
- Hugo, Zola
- Solidjs
- Phoenix web framework with Elixir, Gleam (Beam VM)
- Moonscript with love2d (Cart Life Clone)
- WASM4 with Assemblyscript (chrome dino clone)
- F#, Julia, Q#, Qiskit(tutorials were nice, even played an android game that trains to think in qbits)
- GDScript Godot with point and click framework
- Zed Editor on PC
- Blender + Unreal Engine + Motion Capture
- UPBGE (Python) or Armort Engine (Haxe)
- OpenTTD Multiplayer automated with lua