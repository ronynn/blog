---
layout: post
title: A big limitation in understanding data sets is that we think with the hypothesis first
categories: [Organising, Chart]
tags: [sticky]
image: assets/images/zsh.jpg
author: ronynn
---

Being a thinker isn't just about having a brain; it's about flexing those observational muscles and soaking up knowledge like a sponge in a library. Thinkers, the good ones at least, have seen some stuff and learned a thing or two. And based on all that observation and learning, they cook up a hypothesis. But hold your horses, what's the deal with this "careful observation is the same thing as data" spiel?

Sure, you can drown yourself in data, but be prepared to swim in a sea of confusion and manipulation. Trusting data alone is like navigating a ship without a compass; you'll likely end up lost at sea. Because let's face it, data isn't some unbiased oracle of truth. It's influenced by its sources, collection methods, and the shiny tools used to process it. And don't even get me started on how data can be molded and twisted to fit a particular narrative or agenda.

So here's the scoop: thinking kicks off with a hypothesis - a hunch, a wild guess, a spark of curiosity. It's like throwing spaghetti at the wall to see what sticks. And this hypothesis isn't just a placeholder; it's the guiding star in the data universe. It tells us what data matters, what's just noise, and how to wrangle it all into something meaningful.

But hold onto your hats, folks, because I'm not saying data is useless. It's got its perks, as long as you keep it on a tight leash. Data can be the wingman to our hypotheses, helping us test and refine our wild theories. But let's not confuse correlation with causation or treat data like the gospel truth. It's a tool, not a crystal ball.


In the labyrinth of thought, hypotheses and data are like two sides of the same coin - they dance together in a delicate tango, but sometimes they step on each other's toes. But where does this dance find its groove?

Athena, goddess of wisdom, prided herself on her strategic prowess and calculated decisions. By relying on her keen intellect and meticulous planning, she would always emerge victorious in the games of war and diplomacy. Armed with her wisdom and a treasure trove of data from the Oracle of Delphi, she set out to shape the destiny of mortals and immortals alike.

But alas, even Athena, with all her wisdom, was not immune to misleading data. At times she failed to see the subtle nuances of human emotion and the unpredictable whims of fate. And so, in her quest for victory, she found herself ensnared in a web of deceit and misdirection, her carefully laid plans unraveling before her eyes.

For her data never ended up as a substitute for her intuition and empathy. In the ever-shifting sands of time, it is our ability to adapt and understand the human heart that truly determines our fate.

Ah, the plot thickens! Let's dive into my own data keeping experiment, I am on a quest for self-improvement, determined to conquer the beast known as procrastination. My hypothesis? By diligently tracking my daily study hours, I'll unlock the secrets to productivity paradise. With spreadsheets and timers, I march forth into battle, ready to slay the dragon of distraction.

Now, let me tell you, keeping track of time is no walk in the park, especially when your mind has a penchant for wandering off into the wild unknown.

With a press of a button, I set the stopwatch ticking at the corner of my screen, each passing second a reminder of the precious moments slipping through my fingers. But here's the kicker - I wasn't just watching the clock; I was waging a war against procrastination itself.

```typescript
import * as usage from "usage";
import * as os from "os";
import * as fs from "fs";

// Function to measure CPU usage
function measureCpuUsage() {
    const pid = process.pid;
    usage.lookup(pid, (err, result) => {
        if (err) {
            console.error(err);
            return;
        }
        console.log("CPU Usage:", result.cpu);
    });
}

// Function to measure memory usage
function measureMemoryUsage() {
    const freeMemory = os.freemem();
    const totalMemory = os.totalmem();
    const usedMemory = totalMemory - freeMemory;
    console.log("Memory Usage:", usedMemory / 1024 / 1024, "MB");
}

// Function to get active processes
function getActiveProcesses() {
    const processes = os.cpus().map(cpu => cpu.model);
    console.log("Active Processes:", processes);
    return processes;
}

// Function to write data to CSV file
function writeToCSV(data: string[][]) {
    const csvData = data.map(row => row.join(",")).join("\n");
    fs.writeFile("app_usage.csv", csvData, err => {
        if (err) {
            console.error("Error writing to CSV:", err);
        } else {
            console.log("CSV file created successfully");
        }
    });
}

// Interval to measure CPU and memory usage every 5 seconds
setInterval(() => {
    measureCpuUsage();
    measureMemoryUsage();
    const activeProcesses = getActiveProcesses();
    const currentTime = new Date().toLocaleString();
    const data = activeProcesses.map(process => [currentTime, process]);
    writeToCSV(data);
}, 5000);

// Your logic to track which apps are in use and calculate studying hours
```

Every time my thoughts strayed from the task at hand, I slammed on the brakes. Whether it was a quick scroll through social media or a sudden urge to rearrange my drawer, nothing escaped my vigilant eye.

But you know me, always one step ahead of the game. Inspired by a stroke of brilliance (or perhaps sheer desperation), I whipped up a quick TypeScript code to keep tabs on my digital dalliances. Using the mystical powers of Node.js, I crafted a script that prowled the digital landscape like a silent sentinel, sniffing out the culprits of distraction with ruthless efficiency.

And wouldn't you know it, the results were eye-opening. Whenever the clock was ticking, but the brain was snoozing, my code would be watching like a hawk - Steam, YouTube, and the treacherous depths of online shopping, beware.

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<canvas id="studyHoursChart" width="400" height="200"></canvas>

  <script>
    // Sample data
    const studyHoursSelf = [4.6, 5.6, 3.4, 5.8, 4.4]; // Self-calculated study hours
    const studyHoursActual = [3.1, 3.3, 2.2, 2.8, 3.5]; // Actual studying hours measured by Node.js

    // Chart.js configuration
    const ctx = document.getElementById('studyHoursChart').getContext('2d');
    const myChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['Day 1', 'Day 2', 'Day 3', 'Day 4', 'Day 5'],
        datasets: [
          {
            label: 'Self-calculated Study Hours',
            data: studyHoursSelf,
            backgroundColor: 'rgba(255, 99, 132, 0.5)', // Red
            borderColor: 'rgba(255, 99, 132, 1)',
            borderWidth: 1
          },
          {
            label: 'Actual Studying Hours (Measured)',
            data: studyHoursActual,
            backgroundColor: 'rgba(54, 162, 235, 0.5)', // Blue
            borderColor: 'rgba(54, 162, 235, 1)',
            borderWidth: 1
          }
        ]
      },
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    });
  </script>

As a result, I came to a startling realization: despite my valiant efforts to stay focused, I was prone to frequent distractions that I hadn't even considered distractions at all. It was as if I had been wandering through a dense fog, unaware of the pitfalls lurking just beyond my field of vision.

But let me tell you, my friend, facing the truth head-on is never easy. It's like staring into the abyss and realizing that the abyss is staring right back at you. I had to confront the fact that my study time wasn't as pristine and uninterrupted as I had imagined.

And yet, there was a certain beauty in this revelation, a raw honesty that cut through the clutter of my illusions. It was like peeling back the layers of an onion, each tearful moment bringing me closer to the core of my existence.

Imagine you're at a dinner party, engaging in a spirited debate about the meaning of life. Your hypothesis waltzes onto the stage, setting the tone with its bold assertions and thought-provoking questions. But lurking in the shadows is the skeptic, armed with doubts and skepticism, ready to rain on your parade. Beware the sirens of bias, singing sweetly in your ear, leading you astray with their seductive lies. Enter data, the beacon of objectivity that cuts through the fog of subjectivity, illuminating the path to truth and enlightenment.

So, whether you're debating life's big questions or unraveling the mysteries of the universe, remember this: hypotheses and data may be unlikely partners, but together they form a formidable team. So, keep your hypotheses sharp and your data sharper, and you'll be ready to take on whatever challenges come your way.
