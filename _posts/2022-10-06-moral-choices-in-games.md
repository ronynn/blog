---
layout: post
title: Moral choices in games
categories: [Philosophy, Game Development, Chart]
---

Ever found yourself knee-deep in a video game, questioning every moral fiber of your being? It's like being tossed into a philosophical blender and forced to confront the consequences of your pixelated actions. These games don't just entertain; they provoke introspection. They thrust you into ethical maelstroms with no clear way out, leaving you to wrestle with your own moral compass.

But how do they pull off this mind-bending feat? How do video games morph into virtual morality labs, pushing players to ponder their choices? And what's the deal with the perks and pitfalls of adding morality into the mix?

One trick up their digital sleeves is the morality system—a set of virtual scales that weigh your every move. Some games lay it all out, slapping labels like "Paragon" or "Renegade" on your forehead. Others keep it sly, letting your deeds speak louder than any on-screen scorecard.

Then there's the whole binary vs. complex debate. Some games toss you into a black-and-white world of good versus evil, like a cosmic game of cops and robbers. Others dive into shades of gray, where every choice feels like a minefield of moral ambiguity.

But let's get real for a sec. In the world of espionage or contract killing, there's no room for moral hand-wringing. In Splinter Cell, you're just a pawn in the government's game, following orders without question (or so they want you to think). And in Hitman, you're not pondering the ethics of your hit list; you're just cashing in on contracts.

Sure, in some games, the "bad guys" might have a point. Zombies gotta eat, right? But when push comes to shove, it's survival of the fittest.

Alright, gather 'round, folks. I've got a tale to tell about an experiment that'll make your eyebrows shoot up.

So, picture this: a week of gaming, ten games lined up, and me, armed with a notepad and a mission to track every single choice that felt like a revelation versus those that had me yawning into my controller.

Now, I'm no stranger to the moral quandaries of gaming. But this time, I decided to get down and dirty with some hard data. I wanted to see just how often those game choices had me feeling like I'd stumbled upon the meaning of life versus feeling like I'd wasted precious moments of my gaming life.

So, for months straight, I dove headfirst into ten different games. Every time I hit a crossroads, every time the game threw a moral curveball my way, I made a mark in my trusty notebook—enlightening on one side, boring on the other.

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>


  <canvas id="gameChoicesChart"></canvas>


  <script>
    
        // Data for the chart
        const gameData = {
            labels: ["Game 1", "Game 2", "Game 3", "Game 4", "Game 5", "Game 6", "Game 7", "Game 8", "Game 9", "Game 10"],
            datasets: [
                {
                    label: 'Enlightening Choices',
                    backgroundColor: 'rgba(54, 162, 235, 0.5)',
                    borderColor: 'rgba(54, 162, 235, 1)',
                    borderWidth: 1,
                    data: [17, 16, 18, 15, 19, 7, 16, 8, 7, 16]
                },
                {
                    label: 'Boring Choices',
                    backgroundColor: 'rgba(255, 99, 132, 0.5)',
                    borderColor: 'rgba(255, 99, 132, 1)',
                    borderWidth: 1,
                    data: [13, 4, 12, 5, 11, 3, 4, 12, 13, 4]
                }
            ]
        };

        // Configuration options
        const options = {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
                x: {
                    stacked: true,
                    title: {
                        display: true,
                        text: 'Games'
                    }
                },
                y: {
                    stacked: true,
                    title: {
                        display: true,
                        text: 'Number of Choices'
                    }
                }
            }
        };

        // Create the chart
        const ctx = document.getElementById('gameChoicesChart').getContext('2d');
        const myChart = new Chart(ctx, {
            type: 'bar',
            data: gameData,
            options: options
        });
        
    </script>

Here's the rundown of the ten games that took me on a rollercoaster ride of moral introspection:

1. The Last of Us
2. Fallout 1
3. Fallout 76
4. Cart Life
5. Fable
6. Splinter Cell
7. Splinter Cell: Pandora Tomorrow
8. Splinter Cell: Chaos Theory
9. Hitman Blood Money
10. Bioshock

Each one brought its own flavor to the table, although I don't feel like mentioning which game any particular data belongs to. But when it came to making choices that left me scratching my head, they all delivered in their own unique way.

And let me tell you, the results were eye-opening. Turns out, some games are masterpieces of moral complexity, weaving narratives that make you question everything you thought you knew about right and wrong. Others? Well, let's just say they're about as thrilling as watching paint dry.

But hey, that's the beauty of experimentation, right? You never know what you'll uncover until you roll up your sleeves and dive in. And let me tell you, this little dive into the world of gaming morality left me with more questions than answers. But isn't that what makes life—and gaming—so darn interesting?

So here's the kicker: morality in games is a double-edged sword. It can leave you feeling enlightened one minute and infuriated the next. It's a wild rollercoaster ride, with no clear destination in sight. But hey, that's the beauty of it, right? It's a reflection of our own moral landscapes, a chance to question and maybe even change ourselves in the process.

So next time you're faced with a moral quandary in a game, tread carefully. Your choices aren't just pixels on a screen—they're reflections of who you are. And in the end, isn't that what gaming is all about?
