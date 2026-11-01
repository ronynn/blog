---
layout: post
title: Markdown is better than powerpoint for making presentations
---

I make presentations every year. Sometimes it's a lecture I give to the same class, sometimes it's a talk I've given before and need to update. And every time, I run into the same problem: the slides are a pain to change. Not because the content is hard, but because the format fights me. I spend more time nudging text boxes and re-aligning bullet points than I do thinking about what I actually want to say.

That's why I've moved to writing my presentations in Markdown. It lets me treat my slides like text — which means I can version control them and keep the content separate from how they look. That one change makes updating the same deck over years almost trivial.

## Slides are a bad default

PowerPoint (and its clones) became the default for presentations decades ago, and we stopped questioning it. But slides as a format have real problems. They need specific software to open. They break on older machines. They encourage you to waste time on animations and transitions that distract from what you're saying. And the files themselves are binary blobs — you can't diff them, you can't easily search them, and you can't track how they changed over time.

Worse, a PowerPoint file mixes two things that should be separate: the content of your presentation and the way it looks. If you want to change the colour scheme or the font next year, you have to go through every slide and adjust it. If you want to update a single fact, you might accidentally break the layout. The two layers are tangled together, and untangling them is tedious.

## Markdown separates the data from the presentation

Markdown is just plain text. You write your content — headings, bullet points, images, whatever — using simple syntax. That's the data layer. Then you use a separate tool to convert that Markdown into slides, applying a theme or a CSS file or a template. That's the presentation layer.

Because those two layers are separate, you can change one without touching the other. Want to update the content for this year's version of a talk? Edit the Markdown file. Want to switch to a new slide theme because your institution changed its branding? Change the template, re-render, done. Your content stays exactly as it was. No copying and pasting, no re-formatting, no accidental deletions.

![](https://ronynn.github.io/blog/assets/images/markdown.jpg)

This also means your presentations become searchable and portable. A Markdown file is just text, so it works with any editor, any operating system, and any note-taking app that indexes plain text. You can read it in a terminal, open it on your phone, or convert it to HTML, PDF, or DOCX with a single command. No PowerPoint required.

## Version control is the real win

Here's the part that changed how I work: because Markdown files are plain text, I can put them in Git. That means every change I make to my slides is tracked. I can see exactly what I added, removed, or reworded between last year's lecture and this year's. I can revert a bad edit. I can branch a version for a different audience. I can collaborate with a co-presenter without emailing files back and forth and guessing which version is current.

Try doing that with a `.pptx` file. You can't diff a binary. You can't merge two versions cleanly. You just save a new copy with a date in the filename and hope for the best.

With Markdown, the history of my presentation is just a `git log` away. And because the presentation layer is separate, changing the theme doesn't pollute that history with hundreds of layout changes. The commit log stays clean: content changes look like content changes, and style changes happen in a different file entirely.

## What about the slides themselves?

You still get slides. You just write them in Markdown and render them with a tool like Pandoc, Marp, or Reveal.js (I made a custom tool for displaying the slide content from a .txt file which is the only thing I edit). The output can look as polished as anything you'd make in PowerPoint. You can add speaker notes, images, code blocks, tables. You can choose a theme. But you're not locked in. If you decide next year that you want a different look, you change the theme and re-render — your content doesn't move.

I'm not saying PowerPoint is evil or that nobody should ever use it. If you need complex animations or your organisation mandates it, fine. But for the kind of presentation that gets reused, updated, and shared — the kind most of us actually make — Markdown is a better default. It respects your time, it plays nicely with version control, and it keeps your content and your design from getting in each other's way.

Once you've updated the same talk three years in a row by editing a single text file and re-rendering, you won't want to go back.

