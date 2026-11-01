---
layout: post
title: The Doomsday Programmer
author: ronynn
---

2026 update: My opinions have some changes, additions and clarifications: 

1. In a doomsday scenario, you might be reliant on programming languages found pre-installed in consumer computers, which as of present will likely be the browser, then python2, ruby if you find a mac. And if you are proficient, use powershell, bash, perl as they will also be present depending on the computer.
2. You should probably not be using a system level programming language anyway in a doomsday scenario, if you leave memory leaks among other bugs you can end up damaging the hardware in some cases.
3. If you have the luxury to store software and can run it on the computers available, rely on those that don't completely rely on online package managers, and are easy enough for you that you can build most things from scratch using the stdlib (python3, bun, [odin compiler](https://www.gingerbill.org/article/2025/09/08/package-managers-are-evil/)). I for example am keeping termux apk on my phones, and copy of some js files from cdn for local projects: petite-vue, chart.js (I imagine I might need charts for anything I might build and they should look good from the beginning). Just vendoring your dependencies is enough.
4. Debugging without gdb is a nice to have skill but you should ideally learn to debug all available tools properly.
5. Maybe keep a local llm model if your device can run it, and if you do have your programming language of choice installed, then for the most part you are done. The journey of learning the basics can still happen but you don't have to lose sleep over it.

---

Programming is a craft that can create wonders, machines, games, art, but too many of us have gotten lazy. We've fallen into the trap of relying on crutches, libraries, frameworks, fancy editors that promise to make our lives easier but end up weighing us down.

What happens if the internet is out? How would you fare as a programmer? You would not know how to run code without installing dependencies, or how to debug code without using tools. But if you've been honing your doomsday skills, you'd be ready to roll. You'd know how to write code from scratch, run it with minimal resources, and debug it using nothing but your wits.

The beauty of doomsday programming lies in its simplicity and self-reliance. By ditching the crutches, you sidestep all the headaches that come with modern programming. No more bugs from dodgy dependencies, no more bloat from unnecessary features, no more reliance on external services or proprietary libraries. Your code becomes leaner and more resilient. It's code that you own, control, and can trust to work anywhere, anytime.

I keep a termux apk on my phone and a folder of JavaScript files I downloaded from CDNs. It's a response to a specific failure I've hit maybe a dozen times: I open an old project, run `npm install`, and it doesn't work. Not because I wrote bad code. Because a package I depended on is gone, or its version constraint conflicts with something else I've since installed, or the CDN is down, or the registry is unreachable from whatever machine I'm on.

The apocalypse framing is a metaphor. The skills are not. Debugging without gdb, building without a package manager, reading a dependency's source instead of its documentation — these are the same skills you need when a build breaks at 2am and the maintainer has stopped responding. So I'll make the case for what I've been calling doomsday programming: knowing what your language can do without `install`, and knowing how to carry the parts you actually need.

## The failure is concrete, not hypothetical

In March 2016 the dev unpublished `left-pad` from npm. It was eleven lines of code. Thousands of builds broke within the hour because packages three levels up depended on it. Here's the whole thing:

```js
// left-pad@1.3.0, before it was taken down
module.exports = function leftPad(str, len, ch) {
  str = String(str);
  var i = -1;
  if (!ch && ch !== 0) ch = " ";
  len = len - str.length;
  while (++i < len) {
    str = ch + str;
  }
  return str;
};
```

That is the entire package. If you'd written it yourself, the outage would have been a Tuesday.

The modern version of this is a peer-dependency conflict, which is where I usually lose an afternoon:

```
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR!
npm ERR! While resolving: dashboard@0.4.0
npm ERR! Found: react@18.2.0
npm ERR! node_modules/react
npm ERR!   react@"^18.2.0" from the root project
npm ERR!
npm ERR! Could not resolve dependency:
npm ERR! peer react@"^16.8.0 || ^17.0.0" from react-dnd@15.1.2
npm ERR! node_modules/react-dnd
npm ERR!   react-dnd@"*" from the root project
```

The fix is usually `--legacy-peer-deps`, which means "pretend the conflict isn't happening." That's not a fix. That's a deferral.

And even when the build works, the footprint is absurd. A blank `create-react-app` in 2020 pulled in 1,300 packages. `node_modules` was larger than the Linux kernel. This is what the "convenience" costs.

## What the tutorials install vs. what the language already has

Most of the dependency lists I see in beginner tutorials were written in a different era of the language. The classic one:

```json
{
  "dependencies": {
    "axios": "^1.6.0",
    "moment": "^2.29.4",
    "fs-extra": "^11.1.1",
    "lodash": "^4.17.21",
    "dotenv": "^16.3.1"
  }
}
```

Here's the same job in current Node, with zero dependencies:

```js
// Node 18+
import { readFile, writeFile } from "node:fs/promises";

const res = await fetch("https://api.example.com/items");
const items = await res.json();

const stamp = new Intl.DateTimeFormat("en-CA", {
  dateStyle: "long",
  timeStyle: "short",
}).format(new Date());

const report = items
  .map(({ id, name }) => `${id}\t${name}\t${stamp}`)
  .join("\n");

await writeFile("report.tsv", report, "utf8");
```

Line by line:

- `axios` → `fetch`, global since Node 21 and stable since 18.
- `moment` → `Intl.DateTimeFormat`. `moment` is 70kb minified; `Intl` is in the runtime.
- `fs-extra` → `node:fs/promises`. The `promises` API has been stable for years, and `mkdir` with `recursive: true` covers what `fs-extra` was mostly used for.
- `lodash` → native array methods. `_.map`, `_.filter`, `_.find`, `_.reduce`, `_.groupBy` (via `Object.groupBy` in Node 21+) all have direct equivalents. The rest of lodash is mostly `_.get`, which you can write in six lines.
- `dotenv` → `node --env-file=.env app.js`, available since Node 20.6.

None of this is exotic. It's just newer than the tutorial. If a beginner learns the stdlib first, they never install the thing that later becomes redundant.

## The stdlib does more than people assume

The assumption that "real" programs need packages is mostly a JavaScript habit, and mostly because early Node had a thin stdlib. Python and Ruby don't have that problem, and neither does Nim.

Python 3 ships with enough to build a working service without `pip install`:

```python
import json
import sqlite3
import urllib.request
from http.server import ThreadingHTTPServer, SimpleHTTPRequestHandler

# HTTP client, no requests
with urllib.request.urlopen("https://api.example.com/items") as r:
    items = json.load(r)

# database, no SQLAlchemy
conn = sqlite3.connect("app.db")
conn.execute("""
    CREATE TABLE IF NOT EXISTS items (
        id   INTEGER PRIMARY KEY,
        name TEXT NOT NULL
    )
""")
conn.executemany(
    "INSERT OR REPLACE INTO items (id, name) VALUES (?, ?)",
    [(i["id"], i["name"]) for i in items],
)
conn.commit()

# static file server, no Flask
ThreadingHTTPServer(("127.0.0.1", 8000), SimpleHTTPRequestHandler).serve_forever()
```

That is a fetcher, a database, and a server in under twenty lines, using nothing outside the standard library. It is not what you'd ship at scale. It is absolutely what you'd ship for a personal project, a prototype, or a script that needs to keep working in five years.

The Nim equivalent, for the JSON-parsing case I used to reach for `axios` and `fs-extra`:

```nim
# nimble file: empty
# nim.cfg: empty

import std/[json, httpclient, os]

let client = newHttpClient()
let items  = parseJson(client.getContent("https://api.example.com/items"))

for item in items:
  echo item["id"].getInt(), "\t", item["name"].getStr()
```

No `package.json`, no `node_modules`, no lockfile. `nim c -d:release app.nim` produces one binary, and that binary works on any machine with the same OS and architecture. That is what "self-contained" actually looks like, and it's why I keep coming back to languages that ship their batteries.

## If you do need a dependency, vendor it

There are things you should not write yourself. A TLS stack. A JSON parser, probably. An HTTP server, if you're handling untrusted input. The doomsday position isn't "never install anything." It's "know what you installed, and be able to keep it."

Vendoring means copying the dependency into your repo and pointing at the local copy. For a JS project:

```bash
curl -fsSL https://unpkg.com/petite-vue@0.4.1/dist/petite-vue.iife.js \
     -o vendor/petite-vue.js
sha256sum vendor/petite-vue.js > vendor/petite-vue.js.sha256
```

Then reference it locally:

```html
<!-- works offline, works in ten years, works from a USB stick, browsers are available on all devices-->
<script src="./vendor/petite-vue.js"></script>
<script>
  const { createApp, reactive } = PetiteVue;
  createApp({ state: reactive({ n: 0 }) }).mount("#app");
</script>
```

The checksum file is the part people skip. It costs nothing and it means that if the file is ever modified — by you, by a bad merge, by a supply-chain attack — you can tell:

```bash
sha256sum -c vendor/petite-vue.js.sha256
```

For larger projects, a lockfile does the same job for the registry. `Gemfile.lock`, `package-lock.json`, `poetry.lock`, and `Cargo.lock` all pin exact versions and hashes. The rule is simple: commit the lockfile, pin the version, and prefer dependencies whose source you could read in an afternoon if you had to.

## The apocalypse scenario is a teaching tool

The reason I frame this as doomsday programming is that the framing forces a question that "best practices" doesn't: what would I do if the network were gone tomorrow? The answer is usually more interesting than the tutorial.

If you can't `pip install`, you learn what's in `http.server`. If you can't `npm install`, you learn that `fetch` and `Intl` exist. If you can't pull a base image, you learn what a binary actually links against. None of these are parlor tricks. They are the layer underneath the one you normally work at, and knowing the layer underneath is what lets you debug the layer above when it breaks.

There's a second reason: the doomsday framing makes the cost of dependencies visible. A `package.json` with thirty entries is thirty maintainers you're trusting, thirty release schedules you're exposed to, thirty sets of transitive dependencies you didn't audit. Most of the time that trust is fine. Occasionally it isn't, and the difference between a bad afternoon and a dead project is whether you can replace the dependency with something you wrote.

The article may have been insistent, but there's a kernel of truth in the doomsday programming ideology. While it's not a call to abandon all modern conveniences, it is a reminder of the serious benefits that come from embracing simplicity and self-reliance in programming. Going forward, I expect just as much from other programming environments too. 

Not everything should be written from scratch. Cryptography, parsing untrusted input, anything touching the network stack, and anything with a security surface should use a maintained library, and the maintainers should be paid. Vendoring a TLS implementation you found on GitHub is how you get CVEs.

And package managers exist for a reason. `cargo`, `go mod`, and `mix` are all good — they pin versions, verify checksums, and make the dependency graph legible. The problem is not package managers. The problem is package managers that fetch from a mutable registry at build time, with no lockfile, on a machine that might not have network access.

So the position I actually hold is narrower than "don't use dependencies." It's: know the stdlib before you reach for a package, vendor the things you can't avoid, pin the versions you do use, and keep a copy of the tools you'd need if the registry went away. The apocalypse is a metaphor. The habits are not.

> May your code be clean, your logic sound, and your resolve unshakeable.

Also: May your lockfile be committed and your stdlib be sufficient.

Edit: Previously the article went on and on about Nim but I don't find any use cases for it anymore, and in a real doomsday scenario, as I said in the beginning, the most installed yet versatile language being Python is the best thing to focus on.