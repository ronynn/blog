---
layout: post
title: A personal experience involving Git in Game Developemnt
categories: [Writing, Game Development]
author: ronynn
image: assets/images/kanban.jpg
---

Participating in a game jam is always an exhilarating and chaotic experience. As a game developer, the pressure to create something playable within a short period, usually 48-72 hours, can be both thrilling and stressful. This year, I had the opportunity to work with a talented group of designers, developers, and artists. In the midst of the high-energy rush of prototyping and refining our game, one tool stood out: Git. In this essay, I’d like to reflect on how we set up Git for our game jam project, the challenges we faced, and how the tool ultimately proved indispensable despite some design-specific hurdles.

### Setting Up Git for Game Jam Success

When we first began the game jam, we knew the importance of effective collaboration, especially since our team consisted of members with different skill sets—programming, art, sound, and design. Given the time constraints, we also knew that managing versions of the game efficiently would be crucial. Enter Git, the version control system that we’ve all heard about, but only a few of us had used extensively in the past. The problem that was lingering in the back of my mind was that Git isn't really the right tool when it comes to blender and other UI design files.

We started by creating a central repository on GitHub. The decision to use GitHub for our project was straightforward: it provided a cloud-based backup for our files, allowing us to collaborate remotely (which was crucial since some team members couldn’t be physically present all the time). We also appreciated GitHub’s built-in issue tracker and project boards, which helped us manage tasks, bugs, and features quickly.

On the technical side, we initially set up a basic branching model: one main branch for the stable, playable version of the game, and separate feature branches for different aspects of the project (e.g., gameplay mechanics, art assets, sound implementation). We tried to keep commits small and meaningful, with frequent pushes to ensure that everyone’s work stayed synchronized. The developers primarily worked in Unity, while artists provided assets in formats like .png, .svg, and .psd. Sound designers worked with .wav and .mp3 files, and all of these had to be version-controlled and integrated seamlessly into the game.

Despite the seemingly simple setup, we quickly discovered that managing a game project in Git wasn’t as straightforward as it seemed. While Git is excellent for text-based files (like code or scripts), game assets present their own unique set of challenges.

### Challenges Faced: Game Assets and Design-Specific Issues

One of the first challenges we encountered was managing large binary files, particularly game assets like sprites, textures, and sound effects. Unlike text files, binary files (such as images and audio files) cannot be diffed or merged, which means that if two team members make changes to the same asset at the same time, you risk overwriting each other’s work or losing important updates. 

Our initial approach was to commit binary assets regularly, but we quickly realized this led to large repository sizes and slow performance when pulling or pushing updates. As the number of commits accumulated, the repository became unwieldy, and GitHub’s file size limitations became an issue. In particular, we ran into trouble when attempting to manage large sound files, which had to be frequently updated as we iterated on the game’s audio design.

To mitigate this, we eventually adopted Git LFS (Large File Storage), which is a Git extension designed to handle large binary files more efficiently. Git LFS stores large files separately from the main repository and keeps references to them in the Git history, which significantly improved our workflow. However, this also introduced a new problem: some team members weren’t familiar with Git LFS and ended up pushing files without realizing they were exceeding the storage limits, leading to occasional confusion and troubleshooting.

Another challenge related specifically to the design aspects of the game was maintaining consistent visual and sound asset versions. Our game’s art was constantly evolving as we iterated on the game’s look and feel, and this often led to conflicts between different versions of sprites or textures. Because we were working with a highly dynamic, evolving set of assets, there were several moments where changes made in parallel by multiple artists resulted in frustrating merge conflicts that required manual resolution. In one instance, a conflict over the resolution of a sprite sheet led to several hours of debugging and reworking the game’s graphics.

Additionally, there were issues around organizing assets and keeping track of changes to different elements of the game. Unlike code, which can be easily tracked and reviewed, asset-based changes in design aren’t always as visible. While we made use of GitHub’s project board to assign tasks and communicate about asset-related issues, there were often unclear handoffs between team members, especially when an asset was being updated while the game was in motion. This led to situations where updated art wasn’t properly integrated, or sound files weren’t linked to the correct events, resulting in last-minute scramble to get everything functioning together.

### The Bright Side: Git as a Lifeline in Crisis

Despite these challenges, Git ultimately proved to be an essential tool for our success during the game jam. Git allowed us to stay synchronized and contribute to the game without stepping on each other’s toes. Thanks to frequent commits, we could always roll back to a previous version if something went wrong, and we could experiment freely, knowing that we could revert to a known working state.

Moreover, Git’s branching capabilities were particularly helpful in managing multiple features in parallel. Developers could work on new gameplay mechanics or bug fixes in separate branches without disturbing the main build, and artists could continue updating assets in their own branches. In the final hours of the jam, when time was running out, we could combine our efforts and merge everything together without major disasters. We could integrate new art, implement new code, and patch up sound design bugs, all while maintaining a stable main branch.

In the end, Git became the backbone of our game jam project, enabling us to collaborate, track progress, and manage changes across a team with diverse skill sets. While we faced challenges in managing large binary assets and resolving conflicts in design elements, the flexibility and power of Git helped us navigate these obstacles. The tool’s ability to handle rapid iteration, versioning, and collaboration ultimately made our game jam experience smoother and more productive.

For future game jams, I would definitely recommend Git to any team, but with the caveat that the specific challenges of game design—particularly in terms of asset management—require careful planning and best practices. Tools like Git LFS are invaluable for managing large files, and a clear workflow for asset updates and version control will go a long way in ensuring a successful jam experience. Despite the inevitable hiccups, Git proved itself to be a game-changer, and I’m confident that its role in game jam development will only continue to grow.

We didn't win the jam though :(