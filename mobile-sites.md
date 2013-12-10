# Mobile-Optimized Sites
  * By 2014, mobile internet usage will overtake desktop internet usage
  * 99% of smartphone users use the mobile browser once a day


##Dedicated Mobile Site
  * different URL, different HTML, different CSS, same data source
  * mobile.site.com, m.site.com
  * app-level device detection, **REDIRECT** to proper url
  * **Rails**
    * one app, use of namespace (easiest)
      * different controllers, routes
      * different views
    * multiple apps, one database?
  
```ruby
request.user_agent =~ /Mobile|webOS/
```
  * Example: https://m.facebook.com, https://mobile.twitter.com/

  
##Dynamic Serving
  * same URL, different HTML, different CSS
  * app-level device detection, **RENDER** proper views
  * **Rails**: For full details: [Railscast #199: Mobile Devices](http://railscasts.com/episodes/199-mobile-devices?view=asciicast)
    * same controllers, routes
    * separate views files (e.g. index.haml, index._mobile_.haml)

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
  * same URL, same HTML, CSS-level optimization
  * recommended by Google

### Implementation

 1. **Liquid Layouts** (same CSS for desktop/mobile)
  * layout expands to fill the entire available area as the browser window is resized
  * use of % widths, min/max-width
  * awkward handling of extreme window sizes
  
 2. **JS and Width-specific CSS Classes**
  * `window.width()` - returns width of browser viewport 
  * change `body` class based on width
  * Example: http://www.asylummarketing.com/


 3. **CSS @media Queries**
  * allows developers to check CAPABILITY (rather than TYPE) of device used

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


  * **Syntax**
  ```css
  @media type and (feature: value)
  @media (feature: value) and (feature: value)
  ```


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
    
  * Example: http://www.andremaurice.it/  

---

### [Gotcha]: Desktop Pixel vs Mobile Pixel
 * mobile browsers **_pretend_** to be hi-res desktop browsers
 * Android: 800px, iOS: 980px
 
 **Fix**:
 ```html
 <meta name="viewport" content="width=device-width, initial-scale=1">
 ```

---


### Sources
  * [Infographic: 2013 Mobile Growth Statistics](http://www.digitalbuzzblog.com/infographic-2013-mobile-growth-statistics/)
  * [INFOGRAPHIC -- Is Your Website Mobile Optimized?](http://www.prnewswire.com/news-releases/infographic----is-your-website-mobile-optimized-225437782.html)
  * [Building Smartphone-Optimized Websites](https://developers.google.com/webmasters/smartphone-sites/) by Google Developers
  * [Responsive design - harnessing the power of media queries](http://googlewebmastercentral.blogspot.com/2012/04/responsive-design-harnessing-power-of.html) by Google Webmaster Central
  * [How To Use CSS3 Media Queries To Create a Mobile Version of Your Website](http://mobile.smashingmagazine.com/2010/07/19/how-to-use-css3-media-queries-to-create-a-mobile-version-of-your-website/)
  * [CSS Media queries](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries) by Mozilla Developer Network
  * [Railscast #199: Mobile Devices](http://railscasts.com/episodes/199-mobile-devices?view=asciicast) by Ryan Bates
  * [StackOverflow: Multiple Rails app, single MySQL database](http://stackoverflow.com/questions/2690546/multiple-rails-app-single-mysql-database)


### Useful Links
  * [Protofluid: Effortless Responsive Design Testing](http://protofluid.com/)
  * [CSS Media Queries for iPads & iPhones](http://stephen.io/mediaqueries/) by Stephen Gilbert
