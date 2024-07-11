Adaptation of Craig Hockenberry’s 4 July 2024 article, [Dynamic Type on the Web](https://furbo.org/2024/07/04/dynamic-type-on-the-web/), into a test page for the CSS techniques described, to support: 

> Dynamic Type on iOS and iPadOS. If you go to System Settings on your iPhone or iPad, and change the setting for *Display &amp; Brightness &gt; Text Size*, you’ll see the change reflected on this website.

> This is a big win for accessibility: many folks make this adjustment on their device to match their abilities. Just because you can read a tiny font doesn’t mean that I can. It also is a win for consistency: my site’s font size matches the other text that a visitor sees on their device.

> The best part is that this improvement can be realized with only a few lines of CSS:

```css
html {
	font-size: 100%;
	font: -apple-system-body;
	font-family: system-ui;
}
```

Where `font-size` sets a text size for platforms that do not adapt to `-apple-system-body`, which I recommend setting to `100%`, that gets overridden in `font` for systems that do adapt to `-apple-system-body`, and `font-family` then overrides `-apple-system-body` to be whatever typeface you want, the simplest and most universally compatible option being [`system-ui`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family#system-ui) where: 

> Glyphs are taken from the default user interface font on a given platform. Because typographic traditions vary widely across the world, this generic is provided for typefaces that don't map cleanly into the other generics.

The [World Wide Web Consortium (W3C) Web Accessibility Initiative (WAI) Accessibility Guidelines Working Group (AGWG) Mobile Accessibility Task Force (MATF)](https://www.w3.org/WAI/about/groups/task-forces/matf/) covers the technical specifications in [Mobile Technique – Specifying a system font in web content to support platform text resize without browser or platform assistive technology zoom](https://www.w3.org/WAI/GL/mobile-a11y-tf/wiki/Specifying_a_system_font_in_web_content_to_support_platform_text_resize_without_browser_or_platform_assistive_technology_zoom.#User_Agent_and_Assistive_Technology_Support_Notes):

> This technique is to be used to support resize of web text content on iOS.

> The objective of this technique is to use the platform system font which takes into account the user’s text size settings of the platform in iOS via the dynamic text options. […] Use of the system fonts is designed to affect the font size and thus setting the CSS font-size on an element will override the font size applied by the platform. If units including em or rem are applied to descendant elements that inherit the system font then the text will scale by the units based on the default font text specified by the system font.

More resources: 

- [Text Resizing for Web Pages in iOS using Dynamic Type](https://www.tpgi.com/text-resizing-web-pages-ios-using-dynamic-type/) - TPGi (Previously known as The Paciello Group); November 17, 2015

- [How to support Apple's dynamic type in your web content with CSS](https://dev.to/colingourlay/how-to-support-apple-s-dynamic-text-in-your-web-content-with-css-40c0); Colin Gourlay; Posted on Aug 18, 2019; Updated on Dec 10, 2020

- [Can Safari on iOS be made to respect the “Text Size” control in Control Center? - Ask Different](https://apple.stackexchange.com/questions/460132/can-safari-on-ios-be-made-to-respect-the-text-size-control-in-control-center); asked May 21, 2023 at 14:10 by mhucka; answered May 21, 2023 at 17:00 by grg

- [Rethinking Text Resizing on Web - The Airbnb Tech Blog](https://medium.com/airbnb-engineering/rethinking-text-resizing-on-web-1047b12d2881); Steven Bassett; May 16, 2024
