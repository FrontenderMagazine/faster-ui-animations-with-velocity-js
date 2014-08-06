<article class="post-195284 post type-post status-publish format-standard has-
post-thumbnail hentry category-coding tag-css tag-javascript tag-techniques tag-
tools post
">
From a motion design perspective, Facebook.com is phenomenally static. It’s
purposefully dumbed down for the broadest levels of compatibility and user 
comfort. Facebook’s iOS apps, on the other hand, are fluid. They prioritize the 
design of motion; they feel like living, breathing apps.

This article serves to demonstrate that this dichotomy does not need to exist
; websites can benefit from the same level of interactive and performant motion 
design found on mobile apps.

Before diving into examples, let’s first address why motion design is so
beneficial:

*   **Improved feedback loops**  
    As a UI and UX designer, you should use patterns as much as possible since
    users will be subconsciously looking for them. Responsive motion patterns, in 
    particular, are the key to pleasurable interactions: When a button has been 
    clicked, do you feel that it has reacted to the pressure of your mouse? When a 
    file has been saved, do you get the strong sense that your data has truly been 
    transferred and stored?
   
*   **Seamless content transitions**  
    Motion design allows you to avoid contextual breaks; modals fading in and
    out (as opposed to switching pages entirely) are a popular example of this.
   
*   **Filled dead spots**  
    When users are performing an unengaging task on your page, you can raise
    their level of arousal through sound, colors, and movement. Diverting a user’s 
    attention is a great way to make a pot boil faster.
   
*   **Aesthetic flourishes**  
    For the same aesthetic reasons that UI designers spend hours perfecting
    their pages’ color and font combinations, motion designers perfect their 
    animations’ transition and easing combinations: Refined products simply feel 
    superior.
   

In the examples below, we’ll be using [Velocity.js][1][1][2] — a popular
animation engine that drastically improves the speed of UI animation. (Velocity.
js behaves identically to jQuery’s`$.animate()` function, while outperforming
both jQuery animation and CSS animation libraries.) In particular, this article 
focuses on Velocity.js
’ [UI pack][3][2][4], which allows you to quickly inject motion design into
your pages. You may optionally watch this article’s[accompanying codecast][5]
[3][6] (5 minutes) for a preview of what we’ll cover.

### UI Pack Overview

After including the UI pack (only 1.8 KB ZIP’ed) on your page, you’ll gain
 access to UI effects that are organized into two categories:

#### Callouts

Callouts are effects that call attention to an element in order to heighten 
user experience, such as shaking an element to indicate an input error, flashing
an element to indicate that something has changed on the page, or bouncing an 
element to indicate that a message awaits the user.

See the Pen [Velocity.js – UI Pack: Callout][7][4][8] by Julian Shapiro (
[@julianshapiro][9][17][10][14][11][11][12][8][13][5][14]) on [CodePen][15]
[18][16][15][17][12][18][9][19][6][20].

#### Transitions

Transitions are effects that cause an element to appear in or out of view.
Every transition is associated with either an “in” or “out” direction. The value
of transitions is in revealing and hiding content in a way that’s visually 
richer than merely animating an element’s opacity. Here’s`slideUpIn`, a
transition that incorporates a subtle slide effect:

See the Pen [Velocity.js – UI Pack: Transition][21][7][22] by Julian Shapiro
([@julianshapiro][9][17][10][14][11][11][12][8][13][5][14]) on [CodePen][15]
[18][16][15][17][12][18][9][19][6][20].

If you’ve paid attention to the evolution of iOS’ UI motion design, you’
ll have noticed that over a dozen transition effects help make iOS’ interface 
pleasurable to interact with. This diversity of transitions is what Velocity.js
’ UI pack brings to everyday websites.

Note that, thanks to Velocity.js’ performance, as well as the optimizations
afforded by the UI pack, all of the pack’s effects are 100% ready for large-
scale production use.

Let’s dive into some simple code examples.

### Using The UI Pack

Callouts and transitions are referenced via Velocity’s first parameter: Pass
in an effect’s name instead of passing in a standard property map. For 
comparison, here’s the syntax of a*normal* Velocity.js call, which behaves
identically to jQuery’s`$.animate()`:

    $elements.velocity({ opacity: 0.5 });
    

In contrast, below are Velocity.js calls using effects from the UI pack:

    /* Shake an element. */
    $elements.velocity("callout.shake");
    
    /* Transition an element into view using slideUp. */
    $elements.velocity("transition.slideUpIn");
    

Just as with normal Velocity.js calls, UI effects may be chained onto each
other and may take options:

    /* Call the shake effect with a 2000ms duration, then slide the elements out of view. */
    $elements
    	.velocity("callout.shake", 2000)
    	.velocity("transition.slideDownOut");
    

Effects from the UI pack optionally take three unique options: `stagger`, 
`drag` and `backwards`.

#### Stagger

Specify `stagger` in milliseconds to successively delay the animation of each
element in a set by the specified amount. (Setting a`stagger` value prevents
elements from animating in parallel, which tends to lack elegance.
)

    /* Animate elements into view with intermittent delays of 250ms. */
    $divs.velocity("transition.slideLeftIn", { stagger: 250 });
    

See the Pen [Velocity.js – UI Pack: Stagger][23][10][24] by Julian Shapiro (
[@julianshapiro][9][17][10][14][11][11][12][8][13][5][14]) on [CodePen][15]
[18][16][15][17][12][18][9][19][6][20].

#### Drag

Set `drag` to `true` to successively increase the animation duration of each
element in a set. The last element will animate with a duration equal to the 
animation’s original value, whereas the elements prior to the last will have 
their duration values gradually approach the original value.

The result is a cross-element easing effect. (If you’ve ever been wowed by
motion typography demos made with After Effects, drag is a key yet subtle 
component behind their visual richness.
)

See the Pen [Velocity.js – UI Pack: Drag][25][13][26] by Julian Shapiro (
[@julianshapiro][9][17][10][14][11][11][12][8][13][5][14]) on [CodePen][15]
[18][16][15][17][12][18][9][19][6][20].

#### Backwards

Set `backwards` to `true` to animate starting with the last element in a set.
This option is ideal for an effect that transitions elements out of view, 
because the`backwards` option mirrors the behavior of elements transitioning
into view (which, by default, animate in a forward direction, from the first 
element to the last
).

See the Pen [Velocity.js – UI Pack: Backwards][27][16][28] by Julian Shapiro
([@julianshapiro][9][17][10][14][11][11][12][8][13][5][14]) on [CodePen][15]
[18][16][15][17][12][18][9][19][6][20].

Together, these three options bring the power of motion design suites to the
Web. When used sparingly, the results are beautiful — so long as you design with
 user experience in mind:

### Designing For UX

Spicing up a page with motion design can [escalate quickly][29][19][30]. Here
are a few considerations to keep in mind:

*   **Make them finish quickly**  
    When applying transitions, developers often make the mistake of letting
    them run too long, causing users to wait needlessly. Never let UI flourishes 
    slow down the apparent speed of your page. If you have a lot of content fading 
    in, keep the animation’s total duration short.
   
*   **Use an appropriate effect**  
    For example, don’t use a playful bounce effect on a page that features 
    formal content.
   
*   **Use them sparingly**  
    Having transitions in every corner of your page is overkill.
*   **Avoid extreme repetition**  
    Avoid transitions of medium-to-long duration in places where they’ll be
    repeatedly triggered.
   
*   **Experiment**  
    Find the right duration, stagger, drag and backwards combinations that will
    produce the right fit for each of your individual animations.
   

### Benefits Of JavaScript-Based Animation

Let’s step back and contextualize why powering these types of UI transitions
through JavaScript is a good idea in the first place. After all, up until now, 
these effects have been most commonly applied using pre-made CSS classes from 
libraries such as[Animate.css][31][20][32]:

*   Because the UI pack’s effects behave identically to standard animation
    calls in Velocity.js, they can be chained and take options. (Doing this with raw
    CSS can be cumbersome.
    )
*   The effects have all been optimized for performance (minimal DOM
    interaction
    ).
*   Elements animated via the UI pack automatically switch to `display: none`
    after transitioning out, and back to
   `display: block` or `inline` before transitioning in. (Doing this via CSS
    requires multiple calls and messy code.
    )
*   Velocity.js doesn’t leave your text blurry. If you’ve applied
    transition effects via CSS before, then you’ll know that text can look fuzzy 
    when you’re done animating and haven’t removed the associated class. This doesn’
    t happen in Velocity.js because its underlying engine completely clears unneeded
    transformation effects upon completion of an animation.
   
*   The effects work everywhere but Internet Explorer 8, where they gracefully
    fall back to simply fading in and out.
   

With all of these benefits, including the effects’ great performance across
all browsers and devices (including older mobile devices), you have no excuse to
not start experimenting with motion design on your sites. Enjoy!

**Note**: Look through [Velocity.js’ documentation][33][21][34] to play around
with all of the UI pack’s effects.

#### Links

*   [Download Velocity on GitHub][35][22][36] 
*   [Velocity demo gallery][37][23][38] 

*Front page image credits: [Unsplash.com][39][24][40]*

*(al, il)*

#### Footnotes

[↑ Back to top][41][Share on Twitter][42]</article>

 [1]: http://velocityjs.org "Velocity.js"

 [2]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#1
 [3]: http://velocityjs.org/#uiPack "UI Pack"

 [4]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#2
 [5]: https://www.youtube.com/watch?v=CdwvR6a39Tg&hd=1

 [6]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#3
 [7]: http://codepen.io/julianshapiro/pen/Fybjq/

 [8]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#4
 [9]: http://codepen.io/julianshapiro

 [10]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#17

 [11]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#14

 [12]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#11

 [13]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#8

 [14]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#5
 [15]: http://codepen.io

 [16]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#18

 [17]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#15

 [18]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#12

 [19]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#9

 [20]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#6
 [21]: http://codepen.io/julianshapiro/pen/aLhFC/

 [22]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#7
 [23]: http://codepen.io/julianshapiro/pen/mqsnk/

 [24]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#10
 [25]: http://codepen.io/julianshapiro/pen/lxfie/

 [26]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#13
 [27]: http://codepen.io/julianshapiro/pen/fEKsw/

 [28]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#16
 [29]: https://www.youtube.com/watch?v=FONN-0uoTHI

 [30]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#19
 [31]: https://github.com/daneden/animate.css

 [32]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#20
 [33]: http://velocityjs.org/#uiPack

 [34]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#21
 [35]: https://github.com/julianshapiro/velocity

 [36]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#22
 [37]: http://codepen.io/collection/tIjGb/

 [38]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#23
 [39]: http://unsplash.com/

 [40]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#24

 [41]: http://www.smashingmagazine.com/2014/06/18/faster-ui-animations-with-velocity-js/#top "Jump to the top of the page"

 [42]: https://twitter.com/intent/tweet?original_referer=http%3A%2F%2Fwww.smashingmagazine.com%2F2014%2F06%2F18%2Ffaster-ui-animations-with-velocity-js%2F&source=tweetbutton&text=Faster%20UI%20Animations%20With%20Velocity.js&url=http%3A%2F%2Fwww.smashingmagazine.com%2F2014%2F06%2F18%2Ffaster-ui-animations-with-velocity-js%2F&via=smashingmag "Share on Twitter!"