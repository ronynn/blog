
# Welcome

This repo is for my blog posts, its design is built from the ground up with simplicity at it's core. I am hoping it will be useful to others as a remote theme for their github pages.


A lightweight, customizable Jekyll blog with support for multiple themes, a Vanta.js animated background, and clean styling using Milligram CSS. Built with Liquid templates for flexibility and supports deployment on GitHub Pages.


---

✨ Features

Dynamic Theming: Choose from multiple pre-defined themes (e.g., Gruvbox, Dracula, Cupcake, etc.)

Persistent Preferences: Stores selected theme and Vanta background state in localStorage

Animated Background: Uses Three.js + Vanta.js for an interactive dots animation

Remote Theme Support: Can be used as a GitHub Pages remote theme

Simple & Minimal: Built with Jekyll, Liquid, and Markdown



---

🚀 How to Use This Theme

1️⃣ Using as a Remote Theme (for GitHub Pages)

You can use this Jekyll theme in your own GitHub Pages project without cloning the repository. Simply add this to your _config.yml:

remote_theme: ronynn/blog



<!--

2️⃣ Running Locally

If you want to test the theme locally before deploying:

🔹 Install Jekyll

Make sure you have Jekyll installed:

gem install jekyll

🔹 Clone the Repo

git clone https://github.com/username/my-jekyll-blog.git  
cd my-jekyll-blog

🔹 Install Dependencies

bundle install

🔹 Serve Locally

bundle exec jekyll serve

Your blog should now be running at: http://localhost:4000 -->


---

🛠️ Customization

🎨 Adding More Themes

You can define additional themes in assets/css/milligram.css. Example:

[data-theme="pastel"] {
   --bg: #fffbf2;
   --text: #ff7f50;
   --border: #ffb6c1;
   --button: #ff69b4;
   --button-hover: #ff1493;
   --input-bg: #fff;
   --input-border: #ffc0cb;
   --input-text: #ff7f50;
}

Then, add it to the theme selector in _layouts/default.html.


---

🖼️ Changing Favicon

Replace assets/images/favicon.png with your own favicon and update _layouts/default.html:

<link rel="icon" type="image/png" href="{{ '/assets/images/favicon.png' | relative_url }}">


---

🔧 Technologies Used

Jekyll – Static site generator

Liquid – Jekyll’s templating language

Three.js – Handles 3D graphics rendering

Vanta.js – Animated background effect

Milligram.css – Lightweight CSS framework



---

🌐 Live Demo

[View the demo here](https://ronynn.github.io/blog)


---

📜 License

This project is open-source and available under the GPLv3 License.


---

💡 Contributing

Feel free to submit issues or PRs if you want to improve the theme! 🚀

---

## Roadmap

- [ ] Fix the css for better accessibility scores on lighthouse.
- [ ] Canvas backgrounds
- [ ] Transitions on page switches
