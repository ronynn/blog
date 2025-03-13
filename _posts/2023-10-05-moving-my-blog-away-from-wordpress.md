---
layout: post
title: Moving my blog away from wordpress.com
categories: [Organising, Writing, Chart]
tags: [featured]
image: https://ronynn.github.io/assets/images/wordpress.jpg
author: ronynn
---

My tale begins with an earnest venture into the digital landscape, armed with nothing but a keyboard and an unquenchable thirst for storytelling. WordPress.com was my stage, my canvas, and for a time, my sanctuary.

### The Dawn of a Digital Dream

When I first stepped into the world of WordPress.com, it was with the innocence and enthusiasm of a novice writer. My inaugural project was a work of fiction—a mystery plot that unfolded over eight tantalizing chapters. Each post was a piece of a puzzle, a breadcrumb leading my readers through a labyrinth of intrigue and suspense. The platform provided me with a ready-made audience, an array of themes to dress my words, and an intuitive interface that made the act of publishing a delight.

From the shadows of mystery fiction, I wandered into the sunlit fields of poetry. Here, I dabbled in verse, experimenting with rhythm and rhyme, exploring the bounds of metaphor and meter. WordPress.com was a faithful companion in this artistic endeavor, offering me the tools to share my lyrical musings with the world. The thrill of seeing my thoughts, my very essence, published for all to see was a heady experience.

### The Strain of Growth

However, as with all things, the simplicity of those early days began to wane. As my blog grew, so did the complexity of my thoughts. I ventured into the realm of essays and reflections, writing about everything from the philosophical to the mundane. But as my writing evolved, so too did WordPress.com, and not always in ways that suited my needs.

The once-sleek editing interface began to bloat like a soufflé left in the oven too long. What was once a seamless experience became a cumbersome ordeal. I found myself wrestling with an editor that refused to load on any of my devices. The joy of spontaneous writing was marred by technical glitches and slow load times. Each attempt to post felt like preparing for battle, a battle I was increasingly losing.

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<canvas id="blogTimeChart" width="400" height="200"></canvas>

<script>
    var ctx = document.getElementById('blogTimeChart').getContext('2d');
    var blogTimeChart = new Chart(ctx, {
        type: 'line',
        data: {
            labels: ['Week 1', 'Week 2', 'Week 3', 'Week 4', 'Week 5', 'Week 6'],
            datasets: [
                {
                    label: 'Total Time Spent Writing/Editing (hours)',
                    data: [5, 6, 7, 8, 7, 9],
                    borderColor: '#2196F3',
                    backgroundColor: "rgba(33, 150, 243, 0.2)",
                    fill: true,
                    tension: 0.1
                },
                {
                    label: 'Time Spent on WordPress.com editing interface (hours)',
                    data: [2, 3, 4, 3, 4, 5],
                    borderColor: '#4CAF50',
                    backgroundColor: "rgba(76, 175, 80, 0.2)", 
                    fill: true,
                    tension: 0.1
                }
            ]
        },
        options: {
            scales: {
                y: {
                    beginAtZero: true
                }
            },
            plugins: {
                legend: {
                    display: true,
                    position: 'top'
                }
            }
        }
    });
</script>

### A Tale of Themes and Frustration

As if the editing woes were not enough, my favorite theme — the digital cloak that dressed my words so elegantly — ceased to function. The culprit? A PHP update, that mysterious and often malevolent force that lurks in the backend of web technology. Choosing a new theme was akin to navigating a maze blindfolded, each turn leading to frustration and confusion.

Gone were the days of effortless customization. I spent hours sifting through themes, only to find that none could capture the essence of my blog as the old one had. The process of personalizing my digital space, which had once been a source of pleasure, became a Sisyphean task.

### The Liberation of Simplicity

In the midst of this digital disarray, I found myself yearning for a simpler, more flexible solution. Enter Jekyll, a static site generator that promised freedom from the shackles of bloated interfaces and restrictive themes. Here was a platform that allowed me to design as elaborately or as simplistically as I desired. With the power of HTML, CSS, and JavaScript at my fingertips, the possibilities were endless.

Jekyll's beauty lies in its simplicity. Gone are the days of battling with an unruly editor. Instead, I write in markdown, each post is a file, neatly stored and easily accessible. The act of publishing has transformed from a dreaded chore into a delightful ritual.

### Embracing the Future

With Jekyll, I am no longer confined to the limitations of a single platform. I can craft interactive elements, embed dynamic content, and truly make my blog a reflection of my evolving design language. The freedom to experiment, to innovate, is exhilarating.

My journey from WordPress.com to Jekyll is not just a tale of technological transition, but a narrative of personal growth. It is a testament to the importance of finding the right tools to nurture one's creative spirit. WordPress.com served me well in my early days, but as my needs evolved, so too did my tools.

In leaving WordPress.com, I have not abandoned my roots but rather have built upon them. My new blog, "Overthinking Analytically," is a celebration of this evolution. It is a space where I can indulge in my penchant for over-analysis, where each post is a meticulous exploration of the everyday, rendered with data, and some wit.

Join me on this new adventure. Together, let us delve into the mysteries of the mundane, unravel the intricacies of the everyday, and find humor and wisdom in the act of over-analysis. For in the words of Oscar Wilde, “To live is the rarest thing in the world. Most people exist, that is all.” Here, we do not merely exist; we thrive, in the glorious pursuit of knowledge and creativity.
