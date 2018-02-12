## SASS Project
### Continued exploration from [Epicodus 2-day SASS project](https://www.learnhowtoprogram.com/css/sass/integrating-sass-2-day-project).
_Amy Churchwell, December 8 2017._

### A project to explore responsive design.

#### Mobile

![screen shot of mobile design](https://raw.githubusercontent.com/amychurchwell/sass/master/img/mobile.png)

#### Tablet

![screen shot of tablet design](https://raw.githubusercontent.com/amychurchwell/sass/master/img/tablet.png)

#### Desktop

![screen shot of desktop design](https://raw.githubusercontent.com/amychurchwell/sass/master/img/desktop.png)

---
### Setup Instructions

Clone from Github
```
$ git clone https://github.com/amychurchwell/SASS.git
```

Open index.html in browser of choice.
---
### Approach

##### Philosophy
###### KISS - Keep it simple, stupid!
My ultimate goal for the day is to focus on creating code that is _not repetitive_, straight-forward, and clear. I want to use the most direct approach to solve a problem, only using mixins and functions that help me achieve simplicity.


##### Workflow
1. My intentions are to first build responsive templates from small to large (mobile > tablet > desktop). Focusing primarily on the main layout sections of the page.

2. File structure will follow the [7-1 architecture pattern](http://sass-guidelin.es/#architecture)

 * This student is utilizing Giraudel's [SASS boilerplate](https://github.com/HugoGiraudel/sass-boilerplate) as a beginner's tool for organization and following SASS guidelines.

3. Styles will be applied to the page from the outside in. Meaning, larger components of the site will be fleshed out before smaller content-oriented details are finessed.

4. Github commits will be made early and often.

##### Hiccups
You cannot apply content to two mixins at once. Therefore, if you want to write styles for both @include tablet and @include desktop you have to write them out separately, causing some repetition in the code. Making mixins for content that has repeating styles in both sizes doesn't make sense to me.
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

#### Prompt:
"A table listing all of the Sass elements your original from Wednesday included (no fewer than five), with an explanation about how you used each element on your project from the week (not what you will be doing on your project moving forward).

_This is similar to the table you were asked to created in class on Wednesday, and in your first CSS code review._


 Considering that this table is supposed to have explanations from how we used the elements on our Wed-Thurs project: How is this table different from the table we created on Wednesday?

I mentioned briefly on Thursday that I think this table would be more helpful if it were broken down into the page's components. Then underneath each component a student could write out what methods/tools they planned to use to accomplish the desired result. That sort of table would be something useful to reference while working.

| TERM  | DESCRIPTION  | IMPLEMENTATION |
|---|---|---|
|   MIXIN    | A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. | We will be using a lot of mixins, but one example is for Media Queries. This will allow us to add the media specs to any desired page element. |
|  @CONTENT  | This makes it possible to define abstractions relating to the construction of selectors and directives. | We will also be using this in our media queries. This will allow us to customize some styles, element by element, instead of adding everything to one large media query. |
|   IF STATEMENT   | @if statements are tried in order until one succeeds or the @else is reached. | We will be using if statements for our min-width and max-width values in our dynamic media queries. |
|   EACH LOOP   | The @each rule sets $var to each item in the list or map, then outputs the styles it contains using that value of $var. | We will be using an each loop to assign hex values to color variables for easier naming. |
|   VARIABLES   | Variables are a way to store information that you want to reuse throughout your stylesheet. | We will be using lots of variables, as they make it possible to call a value by an easy to remember name. |
|   NESTING   | Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. | Nesting will be a common theme, it will help us to organize pseudo:classes along-side their parent-classes. |
|   MATH OPERATOR   | Sass has a handful of standard math operators like +, -, *, /, and %. |  We will be using a math operator to keep our grid responsive. |
|   COLOR FUNCTIONS   | Functions that alter the state of a color. |  We will use these (example compliment) to style our content in a cohesive way. |
|   7-1 PATTERN   | A standard file architecture. 7 organization folders and a single file at the root level. |  We will use this structure to organize and load our SASS files. |
|   PARTIALS   | If you have a SCSS or Sass file that you want to import but don't want to compile to a CSS file, you can add an underscore to the beginning of the filename. This will tell Sass not to compile it to a normal CSS file. | W will be importing partial files to the main.scss file to cut down on load time. |
