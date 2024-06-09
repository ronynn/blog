# Overthinking Analytically - Blog Repository

Welcome to the repository for "Overthinking Analytically," a blog dedicated to detailed, humorous, and insightful explorations of everyday activities. Here, I document my focused study hours, casual reading habits, gaming versus social media usage, and more—all with the help of stats and charts. Additionally, this blog serves as a chronicle of my app and game development journey.

## Table of Contents

- [About the Blog](#about-the-blog)
- [Technology Stack](#technology-stack)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About the Blog

"Overthinking Analytically" is a Jekyll-based blog hosted on GitHub Pages. It features a mobile-friendly, simple design that will evolve as I develop my design language. The blog aims to provide insightful and entertaining content, blending data-driven analysis with a touch of humor in the style of Oscar Wilde.

## Technology Stack

- **Jekyll**: A static site generator used to create this blog.
- **GitHub Pages**: Hosting platform for the blog.
- **HTML/CSS**: Core technologies for structuring and styling the blog.
- **Responsive Design**: Ensuring the blog is accessible and readable on all devices.

## Installation and Setup

To set up this project locally, follow these steps:

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/ronynn/blog.git
    cd blog
    ```

2. **Install Jekyll and Bundler**:
    Ensure you have [Jekyll](https://jekyllrb.com/docs/installation/) and [Bundler](https://bundler.io/) installed.

    ```bash
    gem install jekyll bundler
    ```

3. **Install Dependencies**:
    ```bash
    bundle install
    ```

4. **Serve the Site Locally**:
    ```bash
    bundle exec jekyll serve
    ```

5. **View the Site**:
    Open your browser and go to `http://localhost:4000` to see the blog in action.

## Usage

### Creating a New Post

1. Navigate to the `_posts` directory.
2. Create a new markdown file with the naming convention `YYYY-MM-DD-title.md`.
3. Add your content using Markdown format. Here's an example template:

    ```markdown
    ---
    layout: post
    title: "Your Post Title"
    date: YYYY-MM-DD HH:MM:SS -0000
    categories: [category1, category2]
    tags: [tag1, tag2]
    ---
    
    Your post content goes here.
    ```

### Customizing the Design

Feel free to modify the HTML/CSS files in the `_layouts`, `_includes`, and `assets/css` directories to customize the blog's design. As I continue to work on developing my design language, expect frequent updates and improvements.

## Contributing

I welcome contributions to improve the blog! To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bugfix.
    ```bash
    git checkout -b feature-or-bugfix-name
    ```
3. Make your changes.
4. Commit your changes with a descriptive message.
    ```bash
    git commit -m "Description of the changes made"
    ```
5. Push to your fork.
    ```bash
    git push origin feature-or-bugfix-name
    ```
6. Open a pull request describing your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

If you have any questions, suggestions, or just want to say hello, feel free to reach out:

- **Mastodon**: @overlyanalytic@mastodon.social

Thank you for visiting "Overthing Analytically" blog's repo! Happy reading and analyzing!