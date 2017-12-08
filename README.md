## SASS Project
### Continued exploration from [Epicodus 2-day SASS project](https://www.learnhowtoprogram.com/css/sass/integrating-sass-2-day-project).
_Amy Churchwell, December 8 2017._

---
### Approach

##### Philosophy
###### KISS - Keep it simple, stupid!
My ultimate goal for the day is to focus on creating code that is _not repetitive_, straight-forward, and clear. I want to use the most direct approach to solve a problem, only using mixins and functions that help me achieve simplicity.

(The irony is that this README is really verbose!)

##### Workflow
1. My intentions are to first build responsive templates from small to large (mobile > tablet > desktop). Focusing primarily on the main layout sections of the page.

2. File structure will follow the [7-1 architecture pattern](http://sass-guidelin.es/#architecture)

 * This student is utilizing Giraudel's [SASS boilerplate](https://github.com/HugoGiraudel/sass-boilerplate) as a beginner's tool for organization and following SASS guidelines.

3. Styles will be applied to the page from the outside in. Meaning, larger components of the site will be fleshed out before smaller content-oriented details are finessed.

4. Github commits will be made early and often.

---

### Two-Day Project Thoughts and Feedback

A large takeaway I have from researching SASS this week is that less is more. That at the end of the day, the idea is to write less code that does broad strokes.

Yesterday, my partner and I were researching possibles ways SASS can handle media queries. We originally used a couple of (albeit, very clever but overly complex) if statements to solve for this:

```
@mixin mQ($arg...){
  @if length($arg) == 1{
    @media screen and (max-width: nth($arg,1)){
      @content;
    }
  }
  @if length($arg) == 2{
    @media screen and (max-width: nth($arg,1)) and (min-width: nth($arg, 2)){
      @content;
    }
  }
}
```
-- source [Net Ninja, youtube](https://www.youtube.com/playlist?list=PL4cUxeGkcC9iEwigam3gTjU_7IA3W2WZA).

Now, this code is helpful if you need to solve for elements reacting in a *variety of ways* at a *variety of sizes.* For us, we really only needed things to behave at a couple of standard size ranges.

Variables.
```
$mobile-width: 767px;
$tablet-width: 768px;
$desktop-width: 1024px;
```
Media Query Mixins
```
@mixin mobile {
  @media (max-width: #{$mobile-width}) {
    @content;
  }
}

@mixin tablet {
  @media (min-width: #{$tablet-width}) and (max-width: #{$desktop-width - 1px}) {
    @content;
  }
}

@mixin desktop {
  @media (min-width: #{$desktop-width}) {
    @content;
  }
}
```
-- source [Landon Schropp](https://davidwalsh.name/write-media-queries-sass).

Less bells and whistles, but ultimately a better approach for us because it is more direct.

---
### SASS elements table


A table listing all of the Sass elements your original from Wednesday included (no fewer than five), with an explanation about how you used each element on your project from the week (not what you will be doing on your project moving forward).

This is similar to the table you were asked to created in class on Wednesday, and in your first CSS code review.

How is this table different?


| TERM  | DESCRIPTION  | IMPLEMENTATION |
|---|---|---|
|   MIXIN    | A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. | We utilized mixins to add media queries to any desired element. |
|  @CONTENT  | This makes it possible to define abstractions relating to the construction of selectors and directives. | Allowed us to write code where we could insert custom content depending on the situation. |
|   IF STATEMENT   | @if statements are tried in order until one succeeds or the @else is reached. | **See thoughts and feedback section** |
|   EACH LOOP   | The @each rule sets $var to each item in the list or map, then outputs the styles it contains using that value of $var. |  |
|   VARIABLES   | Variables are a way to store information that you want to reuse throughout your stylesheet. |   |
