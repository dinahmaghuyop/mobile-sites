# Mobile-Optimized Sites
  * 1 in 4 mobile users access websites in mobile devices at least once a day 
  * boosts user engagement (more visits per user)
  * boosts sales


##Dedicated Mobile Site
  * different URL, different HTML, different CSS, same data source
  * mobile.site.com, m.site.com
  * app-level device detection, **REDIRECT** to proper site
  
```ruby
request.user_agent =~ /Mobile|webOS/
```
  * Example: https://m.facebook.com, https://mobile.twitter.com/

  
##Dynamic Serving
  * same URL, different HTML, different CSS
  * app-level device detection, **RENDER** proper views
  * **Rails**: For full details: [Railscast #199: Mobile Devices](http://railscasts.com/episodes/199-mobile-devices?view=asciicast)
    * separate view files (e.g. index.haml, index._mobile_.haml)

```ruby
# mime_types.rb
Mime::Type.register_alias "text/html", :mobile


# before_filter in application_controller.rb
def set_mobile_request
  request.format = :mobile if mobile_device?
end


# sample controller
def index
  respond_to do |format|
    format.html
    format.mobile
  end
end
```

## Responsive Design
  * same URL, same HTML, different CSS
  * recommended by Google

### Implementation

 1. **Liquid Layouts** 
  * layout expands to fill the entire available area as the browser window is resized
  * use of % widths, min/max-width
  * awkward handling of extreme window sizes
  
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






---




### Sources
  * [Mobile Mania: The Growing Importance of Mobile Optimization](http://blog.kissmetrics.com/mobile-mania/)
  * [Building Smartphone-Optimized Websites](https://developers.google.com/webmasters/smartphone-sites/) by Google Developers
  * [Responsive design - harnessing the power of media queries](http://googlewebmastercentral.blogspot.com/2012/04/responsive-design-harnessing-power-of.html) by Google Webmaster Central
  * [How To Use CSS3 Media Queries To Create a Mobile Version of Your Website](http://mobile.smashingmagazine.com/2010/07/19/how-to-use-css3-media-queries-to-create-a-mobile-version-of-your-website/)
  * [CSS Media queries](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries) by Mozilla Developer Network
  * [Railscast #199: Mobile Devices](http://railscasts.com/episodes/199-mobile-devices?view=asciicast)

### Useful Links
  * [Protofluid: Effortless Responsive Design Testing](http://protofluid.com/)
  * [CSS Media Queries for iPads & iPhones](http://stephen.io/mediaqueries/) by Stephen Gilbert
