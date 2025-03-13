---
layout: post
title: Picking the best design system for my apps
categories: [Design, Javascript]
author: ronynn
image: assets/images/laptopcalc.jpg
tags: [featured]
---

"Design is not just what it looks like and feels like. Design is how it works,” said Steve Jobs, and he was onto something.

I've been tinkering with web apps for years now. It's not some grand career or anything; it's just a hobby that keeps me out of trouble. I whip up all sorts of things – games, calculators, quizzes – you name it, I've probably had a crack at it. But here's the rub: my themes are as stale as last week’s bread. I’ve been recycling the same look for ages, and frankly, it's making me want to gag.

I’m itching for a change, a total overhaul that screams of my current tastes. The problem? I’m stuck in a design quagmire. You see, a design system is this rigid framework that tells you what colors to use, what fonts to choose, where to plop your icons, how to lay things out, and even how things should move on the screen. It's like a recipe for your web app’s visual identity, but I’m standing in the kitchen with no idea which cookbook to follow.

So here I am, trapped between the devil and the deep blue sea, knowing my old themes need a Viking funeral but unsure what new design system to anoint as the savior of my projects. It's a conundrum, I can tell you that.

Alright, so imagine this: you're scrolling through the vast wilderness of web design, hoping to find that elusive spark that'll make your app stand out. But, alas, you're met with the same old song and dance of design systems, each promising the moon but delivering just a sliver of satisfaction.

Enter Metro, with its bright colors and minimalistic charm, trying to convince you that less is more. But let's face it, it's like trying to find depth in a puddle - simple, but hardly captivating.

Then there's Neumorphism, with its soft edges and subtle shades, trying desperately to be the cool at the party. But underneath that trendy facade lies a tangled mess of shadows and highlights, leaving you wondering if it's worth the headache.

Let's delve into a scenario where Neumorphism can pose coding problems:

```css
.neumorphic-button {
    background-color: #f0f2f5;
    border-radius: 10px;
    box-shadow:
        5px 5px 10px #c4c9d2,
        -5px -5px 10px #ffffff;
    padding: 10px 20px;
    transition: all 0.3s ease;
}

.neumorphic-button:hover {
    box-shadow:
        inset 5px 5px 10px #c4c9d2,
        inset -5px -5px 10px #ffffff;
}
```

In the above CSS code snippet, we have a Neumorphic button style defined with a box shadow that creates the characteristic soft, raised effect. However, when the button is hovered over, we attempt to change the box shadow to create an inset effect. This transition from an outer shadow to an inset shadow can lead to a jarring visual experience for users, as the button's appearance abruptly shifts from a raised Neumorphic style to an inset one.

This sudden change in shadow direction not only disrupts the visual continuity but also contradicts the intended tactile feel of Neumorphism. It highlights a key challenge in implementing Neumorphic designs seamlessly, where transitions between different states can sometimes clash with the overall aesthetic and user experience.

And who could forget Material, Google's brainchild, with its paper-like elements and vibrant hues, trying to be both functional and expressive. But like a complicated puzzle, it's easy to get lost in its inconsistencies.

Imagine a scenario where the elevation of elements behaves unexpectedly, causing shadows to appear inconsistent across different components. For instance, a card may cast a shadow that seems out of sync with the rest of the interface, disrupting the visual harmony.

Consider the following code snippet showcasing a Material Design card:

```html
<div class="md-card">
    <p>This is a Material Design card.</p>
</div>
```

While the card may look visually appealing, issues may arise when applying elevation styles that result in inconsistent shadow effects across various elements. This inconsistency can lead to a disjointed user experience, where elements appear to float at different levels, creating a sense of disarray within the design.

In navigating the realm of Material Design, one must tread carefully to address these inconsistencies and maintain a cohesive visual language throughout the interface.

So, here I am, stuck in this existential crisis of web design, wondering if there's a light at the end of this CSS tunnel. Do I stick with the status quo, or do I dare to venture into uncharted territory and create my own design system?

As I ponder this conundrum, I can't help but think of Leonardo da Vinci's timeless words: "Simplicity is the ultimate sophistication." But let's be real, simplicity can sometimes be mistaken for mediocrity. After all, who wants an app that's as exciting as watching paint dry?

So, I've decided to spice things up a bit by dabbling in the art of glassmorphism. Picture this: glossy blur effects, vibrant colors, and a hint of mystery - it's like peeking through a frosted window on a snowy day.

And oh, the reactions from my friends! Gone are the days of "meh" and "okay, it does a thing." Because let's face it, in the world of web apps, it's not just about functionality anymore. It's about leaving a lasting impression, about making users stop and say, "Wow, this is something special."

So, as I embark on this journey of visual enchantment, I raise my glass (pun intended) to the importance of being visually pleasing and eye-catching. Here's to simplicity with a splash of pizzazz, to keeping things simple enough tounderstand but interesting enough to keep looking at. And who knows, maybe oneday, my web apps will be the talk of the town, leaving everyone in awe of their sheer brilliance. But for now, I'll settle for a few admiring glances. Cheers to the art of design!
