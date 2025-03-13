---
layout: post
title: Would you use a desktop wallpaper which is a cat generator
categories: [Writing, Game Development]
author: ronynn
image: assets/images/cat.jpg
---

As a developer with a passion for blending design aesthetics and functional user experiences, I recently embarked on creating a web app that leverages the **glassmorphism** design trend. The app’s primary function is simple: fetch and display random cat pictures from an API with the press of a button. However, beyond its simple premise, my goal was to explore how the app could transcend its role as a mere novelty and become a viable **live wallpaper** for both mobile phones and desktop computers. In this essay, I will walk through the thought process behind the app’s design, usability considerations, and the reactions I hoped to receive from the audience. The core objective is to determine how effectively the app could function as a live wallpaper, considering elements like user interaction, performance, and the overall experience.

### Understanding the Glassmorphism Aesthetic

Before diving into usability, it’s important to understand the design trend I chose: **glassmorphism**. Glassmorphism is a design style that emulates the frosted glass effect, creating a translucent and blurred background with layered elements. This aesthetic can evoke a sense of depth and sophistication while maintaining a minimalist feel. It gained significant traction in UI/UX design, especially for mobile apps and web interfaces, thanks to its futuristic, "light" appearance. 

For my cat-pic-fetching web app, I chose to incorporate glassmorphism to create an elegant, modern interface that not only allows users to view cat pictures but also provides a visually engaging experience that could sit comfortably as a live wallpaper. This decision was motivated by the desire to make the app not just functional, but beautiful and pleasing to use over extended periods, something that a live wallpaper demands.

### Initial Design and Functionality

At its core, the app operates by fetching a new cat picture from a public API (such as **TheCatAPI**) with each button press. While the functionality is straightforward, my main concern was ensuring that the app didn’t become an eyesore when used as a live wallpaper. When transitioning the app from a web-based interface to a live wallpaper, several design principles had to be kept in mind to maintain usability and appeal.

1. **Minimalist Interaction**: Unlike traditional apps where user interaction is paramount, a live wallpaper app needs to provide minimal interruption. Users expect wallpapers to be **passive** rather than **active**. The cat picture-fetching button is central to the design but needs to be unobtrusive when the app is used as wallpaper. I made the button semi-transparent and positioned it in a way that it wouldn’t distract from the overall wallpaper aesthetic unless the user actively wanted to interact with it.

2. **Performance Considerations**: Live wallpapers are typically expected to consume as little system resources as possible. While the app doesn’t do anything computationally intensive (just fetching images from the API), the key challenge here was ensuring that the app doesn’t slow down the performance of the device, particularly when used as a background on mobile phones or desktops. I made sure that the image-fetching process was optimized: using caching to avoid redundant API calls and implementing lazy loading for images.

3. **Subtle Animations**: Another important aspect of the design was integrating **subtle animations** that wouldn’t distract from the overall aesthetic but would still provide a sense of life to the wallpaper. I added a soft fade-in effect for new images, ensuring that the transition between pictures felt smooth and didn’t jolt the user. This was crucial because a live wallpaper needs to feel fluid and continuous, rather than abruptly changing with every new image fetch.

4. **Screen Adaptability**: Given the variation in screen sizes, especially between mobile phones and desktops, I had to design the wallpaper to be adaptable. For desktop screens, the image would need to scale appropriately, while on mobile devices, I needed to ensure the wallpaper didn’t consume too much battery power or significantly impact performance.

### Usability Considerations for Live Wallpapers

To test the app’s viability as a live wallpaper, I considered several usability factors that would affect the user experience:

1. **Non-Intrusive Design**: A live wallpaper needs to be unobtrusive. While I wanted the cat pictures to be a fun and lighthearted addition to a user’s desktop or phone, it should not disrupt the normal use of the device. To achieve this, the web app had to function with minimal user interaction. For mobile phones, this meant that the button to fetch new pictures had to be hidden unless explicitly activated by the user. For desktop users, the button could remain somewhat visible but not so prominent that it interfered with everyday activities, such as typing or working on other apps.

2. **Personalization and Frequency of Change**: Users may not want the cat picture to change constantly. I implemented an option to allow the user to control how frequently the image refreshes—perhaps every 30 minutes or once a day. Additionally, users could opt for specific categories of cats (e.g., kittens, fluffy cats, etc.), allowing for more personalization. This was an important feature, as not every user would want a new cat image every time they glance at their device. 

3. **Interaction with the Wallpaper**: While the core of the app’s purpose is to act as a background, the option to interact with it by fetching a new image is an important element. However, this button couldn’t dominate the screen. I used **subtle animations** and minimal opacity effects to allow the button to exist as a small icon on the screen, accessible to the user but unobtrusive to the overall aesthetic of the wallpaper. For example, on mobile, the button would be visible when swiping down on the home screen, but otherwise, it would fade into the background. 

4. **Consistency and Design Integrity**: For a live wallpaper to be compelling, the images need to be of high quality and consistent with the app’s aesthetic. This is where I paid particular attention to how the **glassmorphism** design worked with the cat pictures. I ensured that the images blended well with the frosted background, neither too sharp nor too blurry. A high-quality image API (like TheCatAPI) ensured that the photos of the cats were always engaging, with no image feeling out of place.

5. **Device Performance**: Mobile devices and desktops have different performance characteristics. On mobile, battery life is a concern. To address this, I minimized resource usage by limiting image refreshes and utilizing the built-in **lazy loading** techniques. On desktops, performance is less of an issue, but I was still cautious about using unnecessary animations or effects that could slow down older machines. Additionally, I ensured that image caching worked across both platforms, preventing the app from repeatedly fetching the same images.

### Testing and Audience Reactions

After developing the app, I conducted several rounds of testing with users across multiple platforms—both mobile (Android and iOS) and desktop (Windows and Mac). The goal was to gather reactions and observe how the app performed as a live wallpaper.

**Initial Reactions**: Users were generally excited about the novelty of having cat images as live wallpapers, and many appreciated the clean and modern look of the glassmorphism design. However, several users pointed out that the button to fetch new images was often **too subtle** on mobile devices, especially when used as a background. This was an intentional design choice to avoid intrusiveness, but I considered adding a gesture-based mechanism, such as double-tapping the screen to refresh the wallpaper.

**Performance Feedback**: One common concern raised by desktop users was the occasional lag when fetching new images on lower-end machines. This was an important lesson in optimizing image handling for different systems, and I am now working on further performance enhancements, such as reducing the resolution of images when they are used as backgrounds and only fetching high-resolution images when the user actively requests a change.

**User Preferences**: Many users appreciated the ability to **personalize** the app, especially the feature to control how often the images change. For those who wanted a more static wallpaper, a "freeze" option was well received, allowing them to lock in their favorite cat image for a period of time before it updates again.


### Concluding thoughts

Creating a glassmorphism-inspired web app that fetches cat pictures and functions as a live wallpaper proved to be an intriguing experiment in blending aesthetics with usability. Through user testing, I learned the importance of **subtle interactions**, **personalization options**, and **performance optimization** when designing for live wallpaper use. Audience reactions ranged from excitement at the novelty of the concept to constructive feedback on improving the user interface for better accessibility and interactivity.

By considering these factors, the app not only provides an enjoyable experience as a background but also demonstrates how even the simplest applications, when designed with care, can elevate the user experience and provide delightful moments throughout the day. As I continue refining the app, it is clear that there’s great potential for simple yet engaging live wallpaper applications that offer both aesthetic appeal and functional value.