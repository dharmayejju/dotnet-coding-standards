# SnapShot Interactive DotNET Coding Standards

  * [Default Platforms and Frameworks](#default-platforms-and-frameworks)
  * [Web Coding Standards](#web-coding-standards)
  * [Tooling Preferences](#tooling-preferences)
  * [Responsive Design](#responsive-design)
  * [Accessibility](#accessibility)
      * [ARIA](#aria)
  * [Internationalization](#internationalization)
  * [Hosting and Deployment](#hosting-and-deployment)
  * [Credits](#credits)
  * [Contributing](#contributing)

  
## Default Platforms and Frameworks

* Visual Studio 2015
* ASP.NET MVC 5 (Razor) 
* HTML5
* CSS 3 
* Entity Framework 6
* MS SQL 2016
* IIS 9+ 
* Foundation 6.x
* Sitefinity 10.x
* TeamCity / Octopus
* Kendo UI
* OWIN
* Browser Support (required)
    * IE 10+
    * Firefox
    * Chrome
    * iPhone / Android
    * iPad / Android Tablet

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Web Coding Standards

We really just want to use the strongest best-practices that are most widely used in the industry for any new projects. That’s not always possible when building off of client-created code, so “Rule 0” is always to just match the coding style of the project you’re working on. 

**Framework Design Guidelines:** For naming conventions and Design Pattern guidance in .NET
* https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/

**C# Coding Standards:** Use the MS coding standards whenever possible for C# code
* https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions

**JS Coding Standards:** Use these standards as a baseline that will work everywhere
* https://standardjs.com/rules.html

**HTML Coding Standards:** Follow the WC3 best practices where possible
* https://www.w3schools.com/html/html5_syntax.asp

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Tooling Preferences

These are areas we’re not exactly standardized on yet, but we have some strong opinions.

* Avoid .NET Web Forms, WCF, SOAP
* Use REST when creating APIs; distinguish between GET and POST, at least
* Avoid Bootstrap, JSX, RequireJS
* Use FontAwesome
* Prefer SVG to PNG; inline them when possible

* Prefer WebPack over grunt/gulp/etc.
* Prefer Sass over Less
* Prefer browser-based JS, not sever-based, translated TypeScript or ES6
* Prefer jQuery (or other standardized helpers) over vanilla JS
* In general, only use JS tooling for “bigger” projects

* Prefer simpler DI/IoC containers (Autofac, Ninject)
* Prefer NuGet for package management (unless using .NET Core)
* Use a standard unit testing framework (nUnit, xUnit) and mocking library (Moq, Fakes)
* In general, skip unit testing for “smaller” projects and Sitefinity builds
 
[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Responsive Design

All development should be considered “mobile-first” in that every part of the functionality needs to be considered for mobile sizes, as well as for touch devices in general. We use frameworks like Foundation as much as possible for this to create reasonable grid layouts built for whatever target browsers the client needs. If they’re IE8+, we use Float-based grids. If they’re 10+ we can use Flex grids, etc.

Any time you’d use `:hover`, you should also use `:focus`; any time you’d bind a `click` handler, bind it for `touch` also.

In general, try to think in terms of "graceful degredation" so that functionality works across all platforms by default and platform-specific effects can be layered on top of that. 

We use `modernizr.js` for polyfills for older browsers.

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Accessibility

For the smaller applications we usually build in .NET, the main points are to:
1.	Use semantic HTML5 tags, semantic headings, and ARIA roles where needed
2.	Use alt tags on images with visual descriptions of what’s in the image along with any text
3.	Make sure forms have appropriate tab indexes and labels with `label-for` (even if hidden)
4.	Make sure every link is accessible with the keyboard, in a reasonable order

For larger projects, aim to follow WCAG 2.0 standards:
* https://www.w3.org/WAI/intro/wcag

## ARIA

ARIA (Assistive Rich Internet Applications) is a spec from the W3C. It was created to improve accessibility of applications by providing extra information to screen readers via HTML attributes. Screen readers can already read HTML, but ARIA can help add context to content and make it easier for screen readers to interact with content.

ARIA is a descriptive layer on top of HTML to be used by screen readers. It has no effect on how elements are displayed or behave in browsers. We use these ARIA Landmark Roles (banner, navigation, main, etc.) to provide a better experience to users with disabilities.

That being said: let's not abuse ARIA. A pure semantic HTML5 solution without ARIA is always preferred. This way all devices interacting with the web page or app understand the meaning of this element.

```html
// Bad:
<div role="button" tabindex="0">text</div>

// Redundant:
<button role="button">text</button>

// Good:
<button>text</button>
```

The following HTML5 elements do not require their most-used ARIA roles in most cases:

```html
// Old:
<article role="article">
<aside role="complementary">
<footer role="contentinfo">
<header role="banner">
<main role="main">
<nav role="navigation">
<section role="region">

// New:
<article>
<aside>
<footer> (if not within an article or section element)
<header> (if not within an article or section element)
<main>
<nav>
<section>
```

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Internationalization

When developing custom .NET applications and APIs, use Resource Files (`.resx`) where appropriate to allow for internationalization, as well as to cleanly separate concerns of what text shows in the app and where it can be edited. If there’s a need for text translations that can’t be compiled into a Resource, try to find a pre-built solution online or use an existing package relevent to the platform instead of creating one from scratch.

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Hosting and Deployment

`TODO`

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)


## Credits

Created based on SnapShot's existing WordPress standards: https://github.com/snapshotinteractive/wp-coding-standards

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)

## Contributing

Please contribute via pull requests on [GitHub](https://github.com/snapshotinteractive/dotnet-coding-standards).

[**BACK TO TOP**](#snapshot-interactive-dotnet-coding-standards)