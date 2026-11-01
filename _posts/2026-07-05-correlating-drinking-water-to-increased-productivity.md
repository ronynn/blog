

---

layout: post
title: Correlating drinking water to increase in productivity
---

I noticed I wrote better code on days I drank more water. On its own that’s a weak observation — it could have been sleep, or coffee, or whether the codebase was behaving that week. It could also be that I am working on different subjects so the active work never feels stale. So I tracked it for seven days to see if the pattern held up.

Staying hydrated is crucial for overall health, but emerging research also suggests that water intake can significantly affect cognitive performance and productivity, even slight dehydration can impair brain function, reducing focus, memory, and mental clarity. 

The research on this is real but softer than the way it gets repeated. The figure people cite is that a 2% drop in body weight from water loss is enough to impair attention and mood. I haven’t read the primary papers closely enough to defend the exact number, but it matches what I notice: on days I forget to drink, I get foggy around 3pm and start making careless mistakes. The “brain is 75% water” line gets repeated everywhere and I don’t think it explains much — the useful part is simpler. Dehydration feels like tiredness, and tiredness makes me worse at programming and reading.

To understand how hydration impacts productivity, I conducted a simple self-assessment experiment over a span of 7 days. During this period, I systematically tracked two variables:

1. Water Intake: The amount of water consumed per day (measured in liters).
2. Productivity: The efficiency and focus in various activities, specifically programming and reading non-fiction books.

So: seven days, two things logged. Liters of water. And a 1–10 score for how each day went on programming, creativity/writing tasks and on reading non fiction.

This score was influenced by subjective factors such as:
- Focus and energy levels during the task.
- Time spent on task without distractions.
- The quality of output in terms of problem-solving, reading comprehension, and coding productivity.

The score was subjective. I gave it based on focus, how long I went before checking my phone, and whether the code worked the first time. 

Here’s the chart:

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <canvas id="productivityChart" width="400" height="200"></canvas>

  <script>
    var ctx = document.getElementById('productivityChart').getContext('2d');
    var productivityChart = new Chart(ctx, {
      type: 'line',
      data: {
        labels: ['Day 1', 'Day 2', 'Day 3', 'Day 4', 'Day 5', 'Day 6', 'Day 7'],
        datasets: [{
          label: 'Programming Productivity',
          data: [6, 7, 8, 6, 9, 9, 7],  // productivity scores for programming
          borderColor: 'rgba(75, 192, 192, 1)',
          backgroundColor: 'rgba(75, 192, 192, 0.2)',
          fill: false,
          tension: 0.1
        },
        {
          label: 'Reading Non-Fiction Productivity',
          data: [5, 6, 7, 5, 8, 9, 6],  // productivity scores for reading
          borderColor: 'rgba(255, 159, 64, 1)',
          backgroundColor: 'rgba(255, 159, 64, 0.2)',
          fill: false,
          tension: 0.1
        },
        {
          label: 'Water Intake (Liters)',
          data: [1.5, 2.0, 2.3, 1.8, 2.5, 3.0, 2.0],  // water intake in liters
          borderColor: 'rgba(153, 102, 255, 1)',
          backgroundColor: 'rgba(153, 102, 255, 0.2)',
          fill: false,
          type: 'bar',  // Using bar chart for water intake
          tension: 0.1
        }]
      },
      options: {
        scales: {
          y: {
            beginAtZero: true
          }
        },
        responsive: true,
        plugins: {
          legend: {
            position: 'top',
          },
        }
      }
    });
  </script>


- X-axis: Represents the days of the week, with the data points corresponding to each day of the experiment.
- Y-axis: The scale on the left represents the productivity score (1-10), and the scale on the right shows water intake in liters.
- Lines and Bars: The chart contains three datasets:
  - A line chart for programming productivity and reading productivity, showing the changes in focus and output across the seven days.
  - A bar chart for water intake, which highlights how much water was consumed on each day.
  
From this chart, we can visually assess whether there is a noticeable correlation between the amount of water consumed and productivity levels for both programming and reading.

What the data actually says is less clean than I expected. The two best days for both programming and reading were Day 5 and Day 6, which were also the two highest water days (2.5 and 3.0 liters). Day 1 was the lowest water (1.5) and the lowest scores. That part looks like a correlation.

But Day 4 had 1.8 liters and scored 6 and 5, which is close to Day 1. And Day 7 had 2.0 liters and scored 7 and 6 — the same scores as Day 2 at the same intake, but lower than Day 3 at 2.3 liters. So the line isn’t clean. A week of data from one person isn’t going to settle anything, and I’d need a lot more days before I trusted the trend.

The thing I didn’t expect: tracking water made me drink more water. The measurement changed the behaviour. That might be the real finding here — not that hydration causes productivity, but that paying attention to hydration for a week made the afternoons less foggy, and the foggy afternoons were the ones I was trying to explain in the first place.
