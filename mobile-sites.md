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
  
 2. **jQuery and Mobile-specific CSS Classes**
  * `window.width()` - returns width of browser viewport 
  * change `body` class based on width
  * Example: http://www.asylummarketing.com/


 3. **CSS @media Queries**
  * used to alter page rendering
  * allows developers to check CAPABILITY (rather than TYPE) of device used
  
  * **Syntax**
  ```css
  @media type and (feature: value)
  @media (feature: value) and (feature: value)
  ```

  * **Types**
    * `all`
    * Common: `screen`, `print`
    * Others: `braille`, `tv`, `projection`
 

  * **Features**
    * `width` and `height` (window)
    * `device-width` and `device-height`
    * `orientation` - landscape or portrait
    * `resolution`
    * `color`, `monochrome`, `aspect-ratio`, etc
    * 
   
  * **Usage**
    * separate stylesheet loading

    ```ruby
    stylesheet_link_tag 'application', :media => 'all'
    stylesheet_link_tag 'mobile', :media => 'only screen and (max-width: 640px)'
    ``` 

    * in css file
 
    ```css
    @media only screen and (max-width: 640px) {
      /* mobile-specific classes here */
    }
    ```
    
  * **Gotcha**: Desktop Pixel vs Mobile Pixel
    * mobile browsers **_pretend_** to be hi-res desktop browsers
    * Android: 800px, iOS: 980px
    
    **Fix**:
    ```html
    <meta name="viewport" content="width=device-width, initial-scale=1">
    ```

  * Example: http://www.andremaurice.it/

##Dynamic Serving
  * same URL, different HTML, different CSS



##Dedicated Mobile Site
  * diff URL (mobile.site.com, m.site.com), different HTML, different CSS
  * same database




---




### Sources
  * [Mobile Mania: The Growing Importance of Mobile Optimization](http://blog.kissmetrics.com/mobile-mania/)
  * [Building Smartphone-Optimized Websites](https://developers.google.com/webmasters/smartphone-sites/) by Google Developers
  * [Responsive design - harnessing the power of media queries](http://googlewebmastercentral.blogspot.com/2012/04/responsive-design-harnessing-power-of.html) by Google Webmaster Central
  * [CSS Media queries](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries) by Mozilla Developer Network

### Useful Links
  * [CSS Media Queries for iPads & iPhones](http://stephen.io/mediaqueries/) by Stephen Gilbert
