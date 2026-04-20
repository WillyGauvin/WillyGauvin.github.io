---
permalink: /Drippin-Jack/
layout: single
author_profile: false
title: "Drippin' Jack"

sidebar:
  nav: "willyiam"

toc: true
toc_sticky: true

Initial:
  - url: Gifs/DrippinJack/1f.gif
    image_path: Gifs/DrippinJack/1f.gif
    alt: "Initial Front fall"
    title: "Initial Front fall"

  - url: Gifs/DrippinJack/1b.gif
    image_path: Gifs/DrippinJack/1b.gif
    alt: "Initial Back fall"
    title: "Initial Back fall"

Orientation:
  - url: Gifs/DrippinJack/2f.gif
    image_path: Gifs/DrippinJack/2f.gif
    alt: "Oriented Front fall"
    title: "Oriented Front fall"

  - url: Gifs/DrippinJack/2b.gif
    image_path: Gifs/DrippinJack/2b.gif
    alt: "Oriented Back fall"
    title: "Oriented Back fall"

Interpolation:
  - url: Gifs/DrippinJack/3f.gif
    image_path: Gifs/DrippinJack/3f.gif
    alt: "Interpolated Front fall"
    title: "Interpolated Front fall"

  - url: Gifs/DrippinJack/3b.gif
    image_path: Gifs/DrippinJack/3b.gif
    alt: "Interpolated Back fall"
    title: "Interpolated Back fall"

BeforeAfterFront:
  - url: Gifs/DrippinJack/BeforeForwards.gif
    image_path: Gifs/DrippinJack/BeforeForwards.gif
    alt: "Third Person Before forward fall"
    title: "Third Person Before forward fall"

  - url: Gifs/DrippinJack/AfterForwards.gif
    image_path: Gifs/DrippinJack/AfterForwards.gif
    alt: "Third Person After forwards fall"
    title: "Third Person After forwards fall"

BeforeAfterBack:
  - url: Gifs/DrippinJack/BeforeBackwards.gif
    image_path: Gifs/DrippinJack/BeforeBackwards.gif
    alt: "Third Person Before backwards fall"
    title: "Third Person Before backwards fall"

  - url: Gifs/DrippinJack/AfterBackwards.gif
    image_path: Gifs/DrippinJack/AfterBackwards.gif
    alt: "Third Person After backwards fall"
    title: "Third Person After backwards fall"
---

![image-center](/Photos/GameScreenShots/DrippinJack.png){: .align-center}

**[Play the game on itch!](https://willygauvin.itch.io/drippinjack){:target="_blank"}**

# About the game
Drippin' Jack was my teams submission for the 2026 Bigmode Game Jam. For ten days, I led a team of four to create this game based on the theme "Slick".

Drippin’ Jack is a chaotic third-person heist game where speed and control are constantly at odds. You play as Jack, a nervous thief attempting to steal as many fragile vases as possible before the museum’s security system comes back online.

There’s just one problem...Jack can’t stop sweating.

His slippery hands make it harder to hold onto stolen loot, while sweat pooling beneath his feet turns every step into a hazard. Move too fast, and you might wipe out. Crash into walls or obstacles, and Jack ragdolls, sending both him and any vases flying.

Navigate tight areas, avoid disaster, and push your luck: how much can you steal before everything falls apart?


- **Release**: February 8th 2026
- **Skill Focus**: Team Lead, Gameplay Systems Programming.
- **Made in**: Unity  
- **Development Time**: 10 Days

# Ragdoll To Animation Blending
One of the biggest hurdles I faced during this project was making the transition from a full physics ragdoll back to a controlled animation feel natural.
Usually, if you just toggle the Animator back on, the character teleports into the first frame of the stand-up animation, which looks... not so good.

{% include gallery id="Initial" caption="You can see we're snapping to that first frame... and the same animation is played no matter the orientation of Jack." %}

I wanted something that felt like like our character was actually regaining their footing after taking a fall.

## Orientation and Grounding
I implemented a system to determine the characters physical state on the ground. The script checks the hips' orientation to determine if Jack is laying on his stomach or back.
Based on that, we can determine which getup animation to play.

Additionally, I rotate the animator before triggering the animation to match the orientation of the ragdoll.

{% include gallery id="Orientation" caption="Correct animation and orientation" %}

We've solved which animation to use, and what orientation to set the player at. But we're still snapping to that first frame.

## Bone-Space Interpolation
This is the secret sauce, the Resetting Bone state. I need to interpolate the position and rotation of every single bone to the first frame of my animations.
To save on performance, I pre sampled these values and store them in the project to be easily accessed when needed.
When it's time to get up, I run a manual loop that linearly interpolates every single bone from its chaotic ragdoll position to that saved Frame 1 pose.
It happens in a fraction of a second, so you see the limbs physically pull themselves into a coherent starting pose.

{% include gallery id="Interpolation" caption="Interpolation from last ragdoll position to first frame position" %}


## Handoff to the Animator
Once the bones are aligned with the target pose, I perform the switch. I set the rigidbodies responsible for the ragdoll physics back to kinematic, re-enable the Animator, and trigger the stand-up state.
Because I've already manually moved the bones to that frame 1 position, the handoff is invisible. The result is a smooth recovery that maintains the physical presence of the character throughout the whole loop

{% include gallery id="BeforeAfterFront" caption="Falling forward, before and after." %}
{% include gallery id="BeforeAfterBack" caption="Falling backward, before and after" %}


---




