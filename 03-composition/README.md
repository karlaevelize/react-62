---
title: "Thinking in Components"
tags:
  - React
---

# Thinking in Components

<Tagline>
  React apps are all about composing smaller components into larger components,
  building large UIs from small bits of UI
</Tagline>

In this chapter, we're going to break down a large UI into smaller bits: components. Breaking down a UI into reusable bits is one of the main techniques that React developers use to structure large applications: **composition**.

To get started:

1. Create a new react app using `create-react-app`
2. Copy the starter files below into `App.js` and `App.css`
3. In `public/index.html` add a Google webfont for styling purposes:

   ```html
   <!-- public/index.html -->
   <head>
     <!-- rest of the meta tags and link tags -->
     <!-- add the required google font here -->
     <link
       href="https://fonts.googleapis.com/css?family=Montserrat:400,500,700&display=swap"
       rel="stylesheet"
     />
   </head>
   ```

Now, for the exercise. Our App component is huge, and contains _a lot_ or duplication, so not keeping with the **DRY** principle! Your task is to break it up into smaller, reusable components.

- Just as our `Title` component in the previous section, we'll gather all the components together in a single folder: `src/components`. Write each component in a separate file though, for clarity. Note: we're chooing this file/directory structure not for technical reasons, but because it will be easier to understand the project structure, for your future colleagues and yourself.
- Remember: a component _is like a blue-print_. But the page will have many _instances of the same component_. To give each of these component instances their unique content, you'll want to use _props_.

<p style="font-size: 1.2em; text-align: center; font-weight: bold; font-family: 'Roboto Mono', monospace;">
  src/App.js
</p>

```tsx:collapse
// App.js
import "./App.css";

export default function App() {
  return (
    <div>
      <header id="header" className="section-header scroll">
        <a href="./">
          <img
            className="icon"
            src="https://learntocodetogether.nl/assets/icon.svg"
          />
        </a>
        <a href="https://www.meetup.com/Learning-to-Code-Amsterdam/">
          <img
            className="meetup-icon"
            src="https://learntocodetogether.nl/assets/meetup-icon.svg"
          />
        </a>
        <nav>
          <a href="/courses.html">Our Courses</a>
        </nav>
      </header>

      <div className="section-header-spacer"></div>

      <div className="content">
        <div className="section section-what-usp">
          <div className="component-section-header">
            <div className="title-badge">
              <div className="title-badge-title">Do you want to</div>
            </div>

            <h2>
              <div className="component-title ">Learn how to code</div>
            </h2>

            <div className="description">
              Awesome! Let’s do this together. We are here to support you in
              your coding journey.
            </div>
          </div>

          <div className="component-usp-row">
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/team.svg"
              />
              <div className="component-title title">
                Get help from experienced developers
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/community.svg"
              />
              <div className="component-title title">
                Learn &amp; share with our community
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/personal-speed.svg"
              />
              <div className="component-title title">
                Personal &amp; at your own speed
              </div>
            </div>
          </div>
        </div>

        <div className="section-line">
          <div className="line "></div>
        </div>

        <div className="section section-courses-usp">
          <div className="component-section-header">
            <div className="title-badge">
              <div className="title-badge-title">Courses</div>
            </div>

            <h2>
              <div className="component-title ">Our Courses</div>
            </h2>

            <div className="description">
              We have created courses to help you learn, with easy to follow
              steps and some sparks of fun!
            </div>
          </div>

          <div className="component-usp-row">
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/expand-horizon.svg"
              />
              <div className="component-title title">
                Learn new skills and expand your horizon
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/developers.svg"
              />
              <div className="component-title title">
                Follow courses created by experienced developers
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                style={{ width: "200px" }}
                src="https://learntocodetogether.nl/assets/step-by-step.svg"
              />
              <div className="component-title title">
                Fun, hands on and easy to follow
              </div>
            </div>
          </div>
        </div>

        <div className="section-line">
          <div className="line "></div>
        </div>

        <div className="section section-why-usp">
          <div className="component-section-header">
            <div className="title-badge">
              <div className="title-badge-title">Why?</div>
            </div>

            <h2>
              <div className="component-title ">Why do we do this</div>
            </h2>

            <div className="description">
              It’s really simple actually. We just love to combine our passion
              for code with our love for teaching. Coding is so much fun when
              doing it together.
            </div>
          </div>

          <div className="component-usp-row">
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/technology.svg"
              />
              <div className="component-title title">Technology</div>
              <div className="description">
                We love to experiment and create awesome stuff from the comfort
                of our couch.
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/community.svg"
              />
              <div className="component-title title">People</div>
              <div className="description">
                It’s always fun to do things together, the excitement and the
                collaborations.
              </div>
            </div>
            <div className="item team">
              <img
                className="image"
                src="https://learntocodetogether.nl/assets/personal-speed.svg"
              />
              <div className="component-title title">Teaching</div>
              <div className="description">
                We like to learn and to teach others the stuff we know.
              </div>
            </div>
          </div>
        </div>
      </div>

      <div className="section-line">
        <div className="line "></div>
      </div>

      <div className="section-footer">
        <img
          className="logo"
          src="https://learntocodetogether.nl/assets/logo.svg"
        />
        <div className="title">Created by</div>
        <div className="subtitle">
          Rein Op &#x27;t land &amp; Danny van der Jagt
        </div>
        <div className="team-container">
          <img
            className="team"
            src="https://learntocodetogether.nl/assets/danny&rein.svg"
          />
        </div>
      </div>
    </div>
  );
}
```

<p style="font-size: 1.2em; text-align: center; font-weight: bold; font-family: 'Roboto Mono', monospace;">
  src/App.css
</p>

```css:collapse
/* App.css */

/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/
html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}

body {
  line-height: 1;
}

ol,
ul {
  list-style: none;
}

blockquote,
q {
  quotes: none;
}

blockquote:before,
blockquote:after {
  content: "";
  content: none;
}

q:before,
q:after {
  content: "";
  content: none;
}

table {
  border-collapse: collapse;
}

body {
  font-family: "Montserrat", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow-x: hidden;
  font-size: 17px;
  line-height: 21px;
}

.font-weight-medium,
.title-badge-subtitle,
.section-header nav a {
  font-weight: 500;
}

.font-weight-bold,
h1,
h2,
.title-badge,
.section-courses .item-container .item .content .title,
.section-featured-resources > a > .button,
.section-featured-resources .item-container .item .title,
.section-footer .title {
  font-weight: 700;
}

a {
  color: inherit;
  text-decoration: inherit;
}

h1 {
  font-size: 45px;
  line-height: 47px;
}

h2 {
  font-size: 40px;
  line-height: 42px;
}

.section {
  padding: 100px 40px;
}

@media (max-width: 660px) {
  .section {
    padding: 40px 20px;
  }
}

.section-line {
  position: absolute;
  width: 100%;
}

.section-line .line {
  width: 100%;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  transform: rotate(-0.7deg);
}

.section-line .line.mask-top {
  height: 50px;
  background-color: white;
  margin-top: -40px;
}

.component-title {
  font-weight: normal;
}

.title-badge {
  background: #ffd240;
  padding: 8px 25px;
  color: white;
  display: inline-block;
  transform: rotate(-0.7deg);
}

.title-badge .title-badge-title {
  transform: rotate(0.7deg);
  font-size: 20px;
}

.title-badge-subtitle {
  margin-top: 15px;
  margin-bottom: 10px;
  font-size: 20px;
}

.component-page-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 40px 60px 40px;
}

.component-page-header h1 {
  text-align: center;
  margin: 15px 0px;
}

.component-page-header .text {
  text-align: center;
  max-width: 600px;
}

.component-section-header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.component-section-header h2 {
  margin-top: 15px;
  text-align: center;
}

.component-section-header .description {
  font-size: 17px;
  line-height: 20px;
  text-align: center;
  margin-top: 15px;
  max-width: 500px;
}

.component-usp-row {
  display: flex;
  justify-content: center;
  margin-top: 50px;
}

.component-usp-row .item {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-basis: 250px;
  min-width: 250px;
  padding: 0px 20px;
}

.component-usp-row .item img {
  height: 130px;
}

.component-usp-row .item .title {
  text-align: center;
  max-width: 250px;
  margin-top: 20px;
}

.component-usp-row .item .description {
  text-align: center;
  margin-top: 5px;
  max-width: 400px;
}

@media (max-width: 880px) {
  .component-usp-row {
    flex-direction: column;
  }

  .component-usp-row .item {
    margin-bottom: 20px;
  }
}

.section-courses {
  background: #fafafa;
  padding: 60px 40px;
}

.section-courses .category {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.section-courses .item-container {
  margin-top: 20px;
  margin-bottom: 50px;
  display: flex;
  flex-wrap: wrap;
  max-width: 1086px;
  width: 100%;
}

@media only screen and (max-width: 1165px) {
  .section-courses .item-container {
    max-width: 724px;
  }
}

@media only screen and (max-width: 803px) {
  .section-courses .item-container {
    justify-content: center;
  }
}

.section-courses .item-container .item {
  display: flex;
  flex-direction: column;
  width: 340px;
  height: 200px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  background: white;
  cursor: pointer;
  margin: 10px;
  overflow: hidden;
}

.section-courses .item-container .item .content {
  padding: 20px;
}

.section-courses .item-container .item .content .title {
  font-size: 25px;
  margin-bottom: 7px;
}

.section-courses .item-container .item .content .subTitle {
  font-size: 18px;
}

.section-courses .item-container .item .content .description {
  display: flex;
  flex: 1;
  font-size: 14px;
  line-height: 18px;
  margin-top: 15px;
}

.section-courses .item-container .item .bar {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0 15px;
  background: #fafafa;
  display: flex;
  height: 45px;
}

.section-courses .item-container .item .bar .time-icon {
  height: 20px;
  margin-right: 10px;
}

.section-courses .item-container .item .bar .time-text,
.section-courses .item-container .item .bar .type-text {
  font-size: 14px;
  padding-right: 5px;
}

.section-courses .item-container .item .bar .line {
  height: 20px;
  width: 1px;
  border-right: 1px solid rgba(0, 0, 0, 0.2);
  margin: 0 10px;
}

.section-courses .item-container .item .bar .button {
  height: 26px;
  width: 26px;
  background-color: #ffd240;
  border-radius: 4px;
  margin-top: -2px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.section-featured-resources {
  padding: 100px 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.section-featured-resources > a > .button {
  background: #ffd240;
  font-size: 16px;
  padding: 15px 20px;
  border-radius: 30px;
  margin-top: 40px;
}

.section-featured-resources .illustration {
  margin-bottom: -110px;
  height: 200px;
  width: 200px;
  margin-top: 20px;
}

.section-featured-resources .item-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  margin-top: 40px;
}

.section-featured-resources .item-container .item {
  display: flex;
  flex-direction: column;
  width: 280px;
  height: 100px;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 4px;
  margin: 0 10px;
  background: white;
  margin-top: 10px;
  padding: 20px;
}

.section-featured-resources .item-container .item .illustration {
  position: absolute;
  margin-top: -140px;
  margin-left: 55px;
  z-index: -10;
}

.section-featured-resources .item-container .item .title {
  font-size: 25px;
}

.section-featured-resources .item-container .item .description {
  margin-top: 5px;
  font-size: 17px;
  line-height: 21px;
}

.section-featured-resources .item-container .item .bar {
  display: flex;
  flex: 1;
  align-items: flex-end;
  justify-content: flex-end;
}

@media only screen and (max-width: 1129px) {
  .section-featured-resources .item-container {
    flex-direction: column;
  }

  .section-featured-resources .item-container .item {
    max-width: 400px;
  }
}

.section-footer {
  position: relative;
  display: flex;
  flex-direction: column;
  padding: 60px 40px 0px 40px;
  height: 390px;
  background: url("https://learntocodetogether.nl/assets/skyline.svg") no-repeat
    bottom center;
  overflow: hidden;
}

.section-footer .logo {
  margin-left: -14px;
}

.section-footer .team-container {
  width: 100%;
  position: absolute;
  bottom: -40px;
  text-align: center;
  margin-left: -40px;
}

.section-footer .team-container .team {
  display: inline-block;
}

.section-footer .title {
  font-size: 24px;
  text-align: center;
  margin-top: 50px;
}

.section-footer .subtitle {
  font-size: 17px;
  text-align: center;
  margin-top: 5px;
}

.section-header-spacer {
  height: 110px;
  width: 100%;
}

.section-header {
  position: fixed;
  height: 100px;
  width: 100%;
  border-top: 3px solid #ffd240;
  z-index: 99;
  display: flex;
  justify-content: center;
  background: url("https://learntocodetogether.nl/assets/skyline-upside-down.svg")
    top center no-repeat;
}

.section-header .skyline {
  position: absolute;
  height: 100px;
}

.section-header.scroll {
  height: 60px;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  background-color: white;
}

.section-header .icon {
  position: absolute;
  height: 30px;
  left: 20px;
  top: 15px;
}

.section-header .meetup-icon {
  position: absolute;
  height: 25px;
  right: 20px;
  top: 17.5px;
}

.section-header nav {
  height: 60px;
  display: flex;
  align-items: center;
}

.section-header nav a {
  margin-right: 20px;
  padding-bottom: 3px;
  border-bottom: 2px solid rgba(0, 0, 0, 0);
}

.section-header nav a:hover {
  border-bottom: 2px solid #ffd240;
}

.section-header nav a:last-child {
  margin-right: 0px;
}

@media only screen and (max-width: 600px) {
  .section-header-spacer {
    height: 200px;
  }

  .section-header nav {
    flex-direction: column;
    margin-top: 10px;
    height: 1000px;
  }
}

.section-home-header {
  display: flex;
  justify-content: center;
}

.section-home-header .header-desktop {
  width: 100%;
  min-width: 1250px;
}

.section-home-header .header-mobile {
  display: none;
  margin-bottom: 100px;
}

@media only screen and (max-width: 600px) {
  .section-home-header .header-mobile {
    display: inline-block;
  }

  .section-home-header .header-desktop {
    display: none;
  }
}

.section-why-usp .image {
  height: 100px;
}

.section-why-usp .title {
  font-size: 30px;
  margin-bottom: 10px;
}
```

Only once you've solved the exercise on your own, compare your solution with [our solution](https://github.com/Codaisseur/thinking-in-components/commits/main), although there isn't necessarily only one correct way of doing this!
