# Mobile-Optimized Sites
  * 1 in 4 mobile users access websites in mobile devices at least once a day 
  * boosts user engagement (more visits per user)
  * boosts sales



## Responsive Design
  * same URL, same HTML, different CSS
  * recommended by Google

### Implementation

 1. **Liquid Layouts** 
  * layout expands to fill the entire available area as the browser window is resized
  * use of % widths, min/max-width
  * poor handling of extreme window sizes
  

 2. **CSS @media Queries**
  * used to alter page rendering
  * allows developers to check CAPABILITY (rather than TYPE) of device used
  
  * **Syntax**:
  ```css
  @media type and (feature: value)
  @media (feature: value) and (feature: value)
  ```

  * **Types**:
   * `all`
   * Common: `screen`, `print`
   * Others: `braille`, `tv`, `projection`
 

  * **Features**:
   * `width` and `height` (window)
   * `device-width` and `device-height`
   * `orientation` - landscape or portrait
   * `resolution`
   * `color`, `monochrome`, `aspect-ratio`, etc
   * 
   
  * **Usage**:
   1. Separate stylesheet loading




```css
@media only screen and (max-width: 640px) {...}
```


##Dynamic Serving
  * same URL, different HTML, different CSS



##Dedicated Mobile Site
  * diff URL (mobile.site.com, m.site.com), different HTML, different CSS
  * same database




---




### Sources
  * [Mobile Mania: The Growing Importance of Mobile Optimization](http://blog.kissmetrics.com/mobile-mania/)
  * [Building Smartphone-Optimized Websites](https://developers.google.com/webmasters/smartphone-sites/) by Google Developers
  * [CSS Media queries](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries) by Mozilla Developer Network

### Useful Links
  * [CSS Media Queries for iPads & iPhones](http://stephen.io/mediaqueries/) by Stephen Gilbert
