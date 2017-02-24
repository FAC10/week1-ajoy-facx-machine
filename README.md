# FACX Machine's [Nice Site](https://fac10.github.io/week1-ajoy-facx-machine/)

## Why
To create a place where prospective clients can see information about our team, our team members and our work.

## What

+ Navbar
+ Landing/about section
+ Team profiles section
+ Contact form section

## How

+ We began by sitting down as a group to discuss the user stories and design requirements.
+ Given the limited timespan to work on the project we chose a relatively simple layout that would let us focus on writing semantic HTML and ensuring the site is accessible.
+ We discussed CSS layout methods and decided to use flexbox as it allowed us to quickly build a simple responsive grid. Writing our code mobile first meant that we could progressively enhance for users with newer browsers — anyone with a browser without flexbox support would still be able to view the content in the mobile layout.
+ We developed the page by first talking through the layout with a rough sketch of the layout. We then divided the different sections between pairs, and began pair programming each section.

### Project set-up

+ We worked using Browser-sync to watch for changes on one laptop whilst working on the other together. This program also allowed us to monitor changes being made by the other pair, and live test on real mobile devices.
+ We also set up a pre-push git hook to prevent ourselves from pushing to master unwittingly and worked by opening issues for each bit/stage of work and worked on feature branches throughout.

### How we split up the work

+ We decided to break the work up into components so each pair could work on both HTML & CSS. We ensured that one member of each pair had a solid knowledge of flexbox so one pair didn't end up struggling with the layout method we'd chosen.

+ Each pair worked on the HTML structure and layout styles at first (one pair working on the navbar and contact form, and the other working on the About and Team sections).

+ Once the layout was built we switched and worked on the design/styling of the other team's components. This ensured we were all up-to-speed on the entire codebase.

## Stretch goals

- [x] Create a fully functional form with [Formspree](http://formspree.io).
- [x] Nice hover effects for profile links.
- [ ] Possibly some on-load CSS animations - Ran out out of time unfortunately
