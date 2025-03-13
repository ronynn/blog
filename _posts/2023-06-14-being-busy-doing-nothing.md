---
layout: post
title: Being busy doing nothing
categories: [Philosophy, Learning, Inspiration, Chart]
author: ronynn
image: assets/images/lao.jpg
---

You know that quote from Lao Tzu, “Doing nothing is better than being busy doing nothing”? It’s been bugging me. I thought I agreed with it, but now I’m not so sure. I mean, a lot of the stuff we keep ourselves busy with feels like nothing—either foolish or just ways to pass the time.

So, what kind of work are we supposed to avoid? Is it the stuff that drains our spirit or the mindless tasks everyone else does? Is it work we choose for ourselves or work we feel we have to do? Is it work that inspires us or just tires us out? Any project, whether it’s art, science, or whatever, can feel like a waste if it doesn’t succeed. It feels like time lost, like it adds up to nothing.

And if we really take Lao Tzu’s idea to heart, wouldn’t that mean we’d never work on anything unless we were sure it’d pay off? That’s a dangerous way to think. It could stop all scientific discoveries in their tracks. Most breakthroughs start with chasing an idea, often without a clear path to success or reward.

True, but there’s a catch. When it comes to trivial stuff that people waste time on, Lao Tzu’s rule makes sense. Don’t busy yourself with nonsense. But also, don’t follow any idea blindly. It’s all about finding that balance.

So, what do we do? Don’t avoid work just because there’s no guaranteed payoff. Progress happens through exploration and sometimes failure. But also, don’t fill your time with empty tasks just to feel busy. Focus on what matters, what fuels your spirit, and what has the potential to lead to something meaningful. That’s where the real value lies.

I guess it’s about choosing your battles wisely, avoiding pointless busyness, and diving into work that truly matters, even if there’s no immediate payoff. It’s a balance we all have to find.

> “To be idle is a short road to death and to be diligent is a way of life; foolish people are idle, wise people are diligent.” – Buddha

But I am not one to just sit with it so I kept some data on my activities diving them into 3 categories to see the balance between meaningful work and pointless busyness.

### Step-by-Step Explanation

1. **Define the Data**: We'll categorize activities into "Meaningful Work," "Mindless Tasks," and "Rest/Reflection."

2. **Create the Chart**: We’ll use a pie chart to visualize how much time is spent on each category.

3. **Interpret the Chart**: We’ll try to guess the ideal balance, emphasizing the importance of minimizing "Mindless Tasks" and maximizing "Meaningful Work" and "Rest/Reflection."

 <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<body>
    <canvas id="myChart" width="400" height="400"></canvas>
    <script>
        var ctx = document.getElementById('myChart').getContext('2d');
        var myChart = new Chart(ctx, {
            type: 'pie',
            data: {
                labels: ['Meaningful Work', 'Mindless Tasks', 'Rest/Reflection'],
                datasets: [{
                    label: 'Time Allocation',
                    data: [50, 30, 20], // Example data
                    backgroundColor: [
                        'rgba(75, 192, 192, 0.2)',
                        'rgba(255, 99, 132, 0.2)',
                        'rgba(153, 102, 255, 0.2)'
                    ],
                    borderColor: [
                        'rgba(75, 192, 192, 1)',
                        'rgba(255, 99, 132, 1)',
                        'rgba(153, 102, 255, 1)'
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                plugins: {
                    legend: {
                        position: 'top',
                    },
                    tooltip: {
                        callbacks: {
                            label: function(tooltipItem) {
                                return tooltipItem.label + ': ' + tooltipItem.raw + '%';
                            }
                        }
                    }
                }
            }
        });
    </script>

### Explanation of the Chart

1. **Categories**:

    - **Meaningful Work**: This includes activities that are fulfilling and lead to personal growth, like working on projects I'm passionate about or learning new skills.
    - **Mindless Tasks**: These are activities that don't contribute significantly to my goals or well-being, such as excessive social media use or unnecessary chitchat.
    - **Rest/Reflection**: Time spent relaxing, meditating, or reflecting, which is crucial for mental health and productivity.

2. **Data Interpretation**:
    - **Meaningful Work (50%)**: Ideally, a significant portion of my time should be spent on activities that matter and bring me closer to my goals.
    - **Mindless Tasks (30%)**: I'll try to minimize time spent on these activities. They keep me busy but don't add real value.
    - **Rest/Reflection (20%)**: Essential for recharging and maintaining a high level of productivity and creativity.

Perhaps it was useful to me, perhaps it wasn't but by visualizing it this way, I could better understand where my time goes and hopefully in future I'll make conscious decisions to align my activities with my values and goals.
