# CSS
 
## Common

###  What is CSS

 CSS(Cascading Style Sheet: add visal effects to the HTML page.
 Number of rules which tell browser how to display elements on the page, color, font.

 History:
  - CSS1 was developed in 1996
  - CSS2 was developed in 1998
  - CSS3 was published as a W3C Recommendation in 2011.
    CSS3 is divided into several separate documents called "modules". 

Superior styles to HTML − CSS has a much wider array of attributes than HTML, 
so CSS give a better look to HTML page in comparison to HTML attributes


###  What is CSS rule 

CSS rule consists of 2 elements:
 
 Rule: ```div { color: blue; }```
 - selector: div
 - declaration block: { color: blue; }

 Declaration block consists of property(color) and value(blue).


###  Variants to add CSS 

 - **Inline:**     Add style directly to the element via attribyte: 
 			   ```<div style="....">``` It can be ovverride only with !important

 - **Internal:**   Styling the entire webpage. Add ```<style>``` tag to the ```<head>```
	
 - **Extrenal:**   Styling in external *.css file.  Include it via  ```<link>``` tag inside ```<head>```
               ```<link href="...." rel="stylesheet" />```
 
 - **@import:**    Add style via import directive


###  How many types of levels in style sheets

 - **Inline:**              Specified for a specific occurrence of a tag and apply only to that tag. 
                        This is finegrain style, which defeats the purpose of style sheets - uniform style

 - **Internal(Embedded):**  Document-level css, apply to the whole document in which they appear, inside ```<head>``` element

 - **External:**            Can be applied to any number of documents

Priorites of these levels are: 
 - *inline* has the highest priority
 - *internal* and *external* has the same priority, it depends on which style was enabled later:
	
	a) Yellow will win:
	```
 	<style>
		.test-internal-external {
			color: blue;
		}
	</style>
	<link rel="stylesheet" href="../css/Lesson1-2.css">  => inside: ( .test-internal-external { color: yellow; } )
	```

	b) Blue will win:

	```
	<link rel="stylesheet" href="../css/Lesson1-2.css">  => inside: ( .test-internal-external { color: yellow; } )
 	<style>
		.test-internal-external {
			color: blue;
		}
	</style>
	```

###  Layout / painting / compositioning

These ae the pahes of the web page render:

 - Layout: calculate the postion of the element according to rules from CSS
 
 - Painting: draw pixels for showing the visual elements
 
 - Compositioning: rendering the layers in needed order (z-index)

https://developer.mozilla.org/ru/docs/Web/Performance/Critical_rendering_path
https://habr.com/ru/articles/224187/


###  What is BEM

The term BEM stands for Block-Element-Modifier, which is a naming convention for CSS class 

names that helps to maintain a clear and consistent structure in a project's styling.

Component approach for web development, of reusing the component



###  What is CSS sprite                   

CSS Sprites are a collection of images that are combined into a single file that an HTML document can access.
Mostlikely is used for icons.

Use: 
  - background-position

  - background-size

  - background-image


###  Whats is css preproperssing

Programm can generates css from its own syntax: SASS, LESS, STILYS.
Improve and simplify the use of common CSS:

  - SASS(Syntactically Awesome Style Sheets). Sass works Ruby and processed on server side. 

  - LESS(Leaner Style Sheets, developed in 2009) Is a backwards-compatible language extension for CSS. 
    Can run on the client side or server side. 
    It allows us to use features like variables, nesting, mixins, etc, all in a CSS-compatible syntax. 
    LESS is influenced by SASS and has influenced the newer “SCSS” syntax of SASS. 
    LESS was used in Bootstrap 3 but was replaced by SASS in Bootstrap 4.
    https://mrmlnc.gitbooks.io/less-guidebook-for-beginners/content/

  - Stylus, PostCSS

###  CSS stacking order 

  - background/borders
  - negative z-index       position: relative/absolute z-index <0
  - block level boxes      display: block
  - floating boxes         float: left
  - inline boxes           display: inline inline-block 
  - z-index = 0            position: relative/absolute z-index =0
  - positive z-index       position: relative/absolute z-index > 0

    https://habr.com/ru/articles/431046/


###  CSS Frameworks

#### Types of CSS Frameworks

   - CSS-in-JS
          With the rise of JavaScript libraries like React, CSS-in-JS frameworks were created to let 
          developers manipulate styles directly in JavaScript by including CSS in their JavaScript markup.

   - Component-Based Frameworks
          Offer a set of pre-built UI components that developers can plug into their applications to assemble 
          interfaces quickly. The goal is to provide a modular and reusable design system. 
          This is the origin of CSS frameworks.

   - Utility-First Frameworks
          The idea behind utility-first frameworks is that CSS should not be descriptive and should not heavily rely on your markup. 
          Set of CSS styles and classes that only do one thing: m-10, в котором margin=2.2 rem


#### Frameworks

- Bootstrap:  Ver 5: 2021
        Twitter introduced the framework in 2011 to make responsive web design easily accessible to developers.
        Contra: Overused, *all Bootstrap websites look the same*.  Component-Based
   
- Tailwind:
        Released 2021. it does not provide a series of predefined classes for elements such as buttons or tables. 
        Instead, it creates a collection of "utility" CSS classes that can be used to style each element by mixing and matching.
        The names of these classes are intutively understandable.
        Single class means single property:  mx-2 => margin-left: 0.5rem; margin-right: 0.5rem (mx: margin on axis X)
        Utility-first CSS framework for rapid UI development.
        
        For ex:  
        
        ```
      <div class="py-4 mx-2 overflow-y-auto whitespace-nowrap"></div>
        
        ```
	
 
- Foundation: 
        Released 2011. This responsive front-end framework provides a grid, HTML, SASS, and CSS UI elements, templates, 
        and code that covers navigation, buttons, typography, forms, etc. 
        It also comprises optional functionalities offered by JavaScript extensions
        Contra: 
            Relies on Javascript: Many of Foundation’s features rely on Javascript, using jQuery or Zepto.
            Hard to learn: Foundation comes with almost too many options.
            
- Bulma:
        Modern CSS framework based on Flexbox.

... to be continued


https://github.com/troxler/awesome-css-frameworks

## Style selectors and cascading

###  What is style selector 

Selector is a part of the css rule. It can help to choose the element and set style for it.
   

###  Simple selectors(containt single selector):                                               
   	
 - universal(*): For all child elements, can be use for reset(normalize) css rules

 - tagName: Selector by element tag name, ex: ```h1 { color: red; }```             
     
 - class: Selector by class name, ex: ```.myclass { color: red; }``` 

 - id: Selector by element *id* attribute, ex:  ```#main { color: red; }```
	   *Id* must be unique on the HTML page.

- tagName.class: More precise selector, combination of tag and class, ex: ```h1.myclass { color: red; }```
   
Use *id* selector if you want to add some logic for exact element.
Use *class* selector for styling the set of elements.


###  Complex selector(several)

 - Group selectors: Divided by comma, ex:  ```h1, h2, h3 { color: red; }```

 - Pseudo class, ex:  ```a:hover```

 - Pseudo element, ex:  ```li:first-child```
 
 - Selector of the element attribute, ex:  ```a[target]```:

      **Exact** attribute value: ```a[target="_blank"]```
 
      **Start** of the attribute substring: ```a[href^="http"]``` 
 
      **End** of the attribute substring: ```a[href$=".jpg"]```
 
      **Include** of the attribute substring:   ```a[href*="todo"]``` 

 - Selector of CHILD divided by space and applied only for LAST element in chain. 
   
   Ex: ```div p span  { color: red; }```, it will be applied only for *span*
	 
 - Selector only of DIRECT CHILD:  ```li > span { color: red; }```

		```
		<li>
			<em><span> First </span></em>
		</li>
		<li>
			<span> Second </span>
		</li>
		```
	
	Will be applied ONLY to *Second* text: direct child( ```<span>``` ) of the parent ```<li>```
	*First* has ```<em>``` element between.

 - Selector for NEXT CHILDREN: ```ul li + li { color:red; }```

		```
		<ul>
			<li> 1 </li>
			<li> 2 </li>                    
			<li> 3 </li>
			<li> <em>4 </em></li>
		</ul>
		```

	Will be applied for *2* and *3* - the next elements(on the same level for firts ```<li>```)


 - Selector for FOLOWING ELEMENTS: ```br ~ p { color:red; }```

		```
		<br>
			<p> Par3 </p>
			<p> Par4 </p> 
			<p> Par5 </p> 
		```

	Will be applied for *Par3* and *Par4* and *Par5*

Combinator explains the relationship between the selectors. There are four combinators in CSS:

 - child selector (>)

 - adjacent sibling selector (+)

 - general sibling selector (~)

 - descendent selector (space)


###  What is specificity of the selectors

Specificity is the algorithm used by browsers to determine the CSS declaration that is 
the most relevant to an element, which in turn, determines the property value to apply to the element.

Selector weight 

|   Selector                   |  Weight  
|------------------------------|:-----------:|
| Inline                       |   1-0-0-0   
| Id                           |   0-1-0-0   
| Class/Attr/Pseudo-class      |   0-0-1-0  
| Element(tag)/Pseudo-element  |   0-0-0-1   
| Universal(*)                 |   0-0-0-0
    


Need to summarize all selectors for the rule. Examples:  
                
|   Selector           |  Summa  
|----------------------|:-----------:|
| h1      			   |   1    
| .myclass       	   |   10    
| h1.myclass      	   |   11    
| #main     		   |   100   
| body h1.myclass  	   |   10+1+1-12    
| p:first-line    	   |   1+1=2  
| h2 strong    	       |   1+1=2  
| span.test ul li      |   10+1+1=13    
| a:hover              |  1+10=11      
| ul ol+li             |  1+1+1=3  
| ul li                |   1+1=2   
| ul ol li.item        |  1+1+1+10
| li.item.main         |  1+10+10=21   
| #test p              |  100+1  
| h1 + *[href="test"]  |  1+10=11
| #test:not(.main)     | 100+10=110


###  CSS Cascade

The cascade is an algorithm that defines how user agents combine property values originating from different sources.
When a selector matches an element, the property value from the origin with the highest precedence gets applied, 
even if the selector from a lower precedence origin or layer has greater specificity.

Brief

  Importance -> Specificity -> Source order

    
More details

|       Order                  |    			Description												 |
|  :---                        |  :---																	 |
| 1. Relevance                 | It first filters all the rules from the different sources to keep only the rules that apply to a given 
|                              | element. That means rules whose selector matches the given element and which are part
|                              | of an appropriate media at-rule
| 2. Origin and importance     | Then it sorts these rules according to their importance, that is, whether or not they are 
|                              | followed by *!important*, and by their origin. Ignoring layers for the moment, the cascade 
|                              | order is as follows
| 3. Specificity               | The specificity of the selectors are compared, and the declaration with the highest specificity wins
| 4. Scoping proximity         | When two selectors in the origin layer with precedence have the same specificity, the property value 
|                              | within scoped rules with the smallest number of hops up the DOM hierarchy to the scope root wins.
| 5. Order of appearance       | The last declaration in the style order is applied


###  Cascading inheritance

 - There are properties which can be inherit: font, color...

 - Which DO NOT inherite from the parent element: border, margins, padding...
   
 - Manual property inheritance can be applyed:   ```div { border: inherit; }```

Note: Each browser has its onw table of default styles for elements. 



## Cross browsers problems

###  Vender prefix and why do we need it 

  --webkit-opacity   
  --moz-opacity
  --o-opacity
  --ms-opacity
    
This css property is under construction or tesing in specific browser.
Or this property is not in standart yet.
    
Note: Resource for tesing vender properties: caniuse.com

###  Whats is cross browsing CSS compatibility

Browser has its own styling. Need to correct behaviour on different browsers in order
that your design looks the same on different browsers. Two main approaches:

 - Reset.css: erase to 0 all browser styles
    
 - Normilize.css: normalize default browser styling, make the same for all browsers [Preferable]
    
Inlcude reset/normilize.css as first css in you page.


###  How to detremine with the help of CSS that property is supported by browser

The @supports CSS at-rule lets you specify CSS declarations that depend on a browser's support for CSS features. 

Using this at-rule is commonly called a feature query. The rule must be placed at the top level of your code or nested 

inside any other conditional group at-rule.

    ```
    @supports (display: flex) {
        .flex-container > * {
          text-shadow: 0 0 2px blue;
          float: none;
        }
    }
    ```

###  How to fix specific problems in CSS for different browsers

- Use reset.css  or normilize.css

- Divide different styles for different browsers

- Use of Autoprefixer: is a PostCSS plugin which parses your CSS and adds vendor prefixes



## Common design practices and approaches

###  How to maintain common CSS coding style in big projects

  - style guids
  - vars and mixins
  - version control
  - Stylelint
  - CSS metodologies (BEM, SMACSS, OOCSS)


###  How to organize scalable CSS code

 - use css modules

 - use CSS preprocessors

 - use semantic classes

 - use methodolgies: SMACSS | OOCSS | BEM

https://habr.com/ru/articles/256109/ [2015]
https://medium.com/@companjero/%D0%BC%D0%B5%D1%82%D0%BE%D0%B4%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%8F-smacss-e601222cd4eb
https://medium.com/@stepanovv.ru/%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9-css-oocss-smacss-bem-%D0%B8-sass-49351a119283


###  ```@container```  queries

Container queries enable you to apply styles to an element based on the size of the element's container. 

If, for example, a container has less space available in the surrounding context, you can hide certain elements or use smaller fonts.

Container queries are an alternative to media queries, which apply styles to elements based on viewport size or other device characteristics.

    ```
    /* If the container is larger than 700px */
    @container (min-width: 700px) {
        .card h2 {
            font-size: 2em;
        }
    }
    ```

###  Responsive design and ```@media``` queries

Responsive web pages looks good on desktop monitors, laptops and on smartphones. 

There are some rules to make the page responsive:

 - use of media queries: @media.  Apply css rules depending on page size, orientation, min-width height, pixel depth.

	```
    @media screen and print {       all(default) | screen | print | speach 
        color: red;
    }
	```

    Rules separators:  and | , | not
    
    Media functions:  

    - width, height, min-width, max-width, min-height, max-height

	- orientation: portrait | landscape
    
	- device-aspect-ratio: 16/9 | 1336/768
    
	- min-resolution:  2dppx, 300dpi
    
	- monochrome
    
	- color
    
	- grid

	```
    @media screen and (max-width: 990px)  and (orientation: portrait)  { 
		color: red;
    }
    ```

###   *prefers-reduced-motion*  media feature

The prefers-reduced-motion CSS media feature is used to detect if a user has enabled a setting on their device to minimize the amount of non-essential motion. 

The setting is used to convey to the browser on the device that the user prefers an interface that removes, reduces, or replaces motion-based animations.


###  Tasks of responsive design 

 - Change number of columns depending on width
 
 - Flexible width
 
 - Decrease empty spaces
    
 - Size of the fonts
    
 - Hide some media content or simple content


###  What is the difference between adaptive and responsive design

  -- Adaptive: several versions of the same website which loaded depending on device its open.
	       Css/html will be loaded depending on user device

  -- Responsive: rebuild the screen depending on screen size and orientation.
	         One set of css/html files.


###  Difference between Progressive Enchancement and Graceful Degradation

These approaches are used for created cross-platform and cross-browser apps

  - GD: Create Web UI for complex solution, then try to test and fix for simplest(mobile) or out-of-date browsers.

  - PE: Create UI from simple to complex. In each phase the web ui is created as an enchancement from the previous phase. 



## Elements styling

###  Global css keywords initial/inherit/revert/unset

 - **initial** CSS keyword applies the initial (or default) value of a property to an element.

 - **inherit** CSS keyword causes the element to take the computed value of the property from its parent element(for inherited properties only)

 - **revert**  CSS keyword reverts the cascaded value of the property from its current value to the value the property would have had if no changes had been made by the current style origin to the current element of the current browser 

 - **unset** CSS keyword resets a property to its inherited value if the property naturally inherits from its parent, and to its initial value if not. 
 
     1) it behaves like the *inherit* keyword in the first case, when the property is an inherited property
    
     2) it behaves like the *initial* keyword in the second case, when the property is a non-inherited property.


###  Block/Inline model CSS, display property

*Block* element will take the whole line and *Inline* element take the inline place. 

The *display* CSS property sets whether an element is treated as a block or inline box.
  
  - **none:**  Remove element form the flow.

  - **block:** The element generates a block box, generating line breaks both before and after the element when in the normal flow

  - **inline:** The element generates one or more inline boxes that do not generate line breaks before or after themselves. 
            Any height and width properties will have no effect, in normal flow, the next element will be on the same line if there is space.

  - **inline-block:** Displays an element as an inline-level block container. 
                  The element itself is formatted as an inline element, but you can apply height and width values.

  - **flex:** Displays an element as a block-level flex container. Setup flexible layout

  - **grid:** Displays an element as a block-level grid container

  - **inline-flex** | **inline-grid** | **table** | **table-cell**

 #### Margin 

   Space between element and other element (between border and other element)
             
	- 10px              : all 10px
    - 1px 2px 3px 4px   : top-right-left-right
    - 10px 20px         : top-bottom  left-right
    
	More precise properties: margin-top, margin-right, margin-bottom , margin-left

   NOTE1:   margin-top-bottom does NOT work for *inline* elements

   NOTE2:   For boxing elements bottom and top margins can collapse

   NOTE3:   For *inline* elements  width and height does NOT work


 #### Padding 

   Space between content and border  (between content and border)
   Similar values to margin: padding, padding-top, padding-right, padding-bottom , padding-left


 #### Box model of the element

   L-margin <= border <= L-padding <= **CONTENT** => R-padding => border => R-margin
   
   Ex: If we set width=50px border=1px padding=10px margin=5px, 
   
   then total width will be: 50 + 1 + 10*2 + 5*2 = 82px.  Because box-sizing=content by default!

   NOTE4: If we want to width will be 50px set box-sizing: border-box;


###  What is margins collapse

Vertical margins (top-bottom) are collapsed for 2 blocked elements.


###  Positioning in CSS  

We get HTML document, browser start to parse it and build DOM tree. Interpretator finds CSS and starts 
to read it also. All elements are situated in the one main flow.

 #### Position

  - **static:**    Default value. We cannot move the element.   
	              
  - **relative:**  Can move element relatively its start position: top, right, bottom, left   
	           Element situated in the new flow, its prevoius position remains blank! 
			   The prevoius position names *shadow element*

  - **absolute:**  Element situated in the new flow and REMOVES from main flow. All its prevoius space will take other elements.
               Position relatively the first parent which has NON static position. Scroll make no sense.

  - **fixed:**     Deleted from the main flow. New position will be relative to the browser window. 
               Position of the parent make NO sense.

  - **sticky:**    The element is positioned according to the normal flow of the document 
  			   and then offset relative to its nearest scrolling ancestor

###  What is the difference between display: none and visibility: hidden

Both will hide the element
  - display:none  -> element will be removed from the flow. Content is hidden 
	                   for the search engines  
  
  - visibility: hidden -> just hide the element, but is still takes place, also
	                        avaliable for search engines


###  What is the difference between margin and padding
   
  - margin: outer space of the element, out of the border
  
  - padding: inner space of the element betweeb content and border 


###  Sizes of the element

  - width 
  - height
  - min-width
  - min-height
  - max-width
  - max-height


###  Units of sizes in CSS

  #### Absolute
	- px:  pixels 
    - cm:  centimeters
    - in:  inches
    - mm:  millimeters
    - pc:  picas
    - pt:  points


  #### Relative

  |  Type     |    Name 			 | Description										   
  |  :---     |  :---				 |  :---					    						   
  |   %       |  percentage          | From the size of the **parent** element
  |   em      | Font-sizes           | 1em=current font-size(16 by browser default) of the **parent**
  |  rem      | Font-sizes           | 1em=current font-size of the BROWSER, to override: increase font for html or :root
  | ex        | Character sizes      | x-height of the element's font.
  | ch        | Character sizes      | The advance measure (width) of the glyph "0" of the element's font.
  | vw/vh     | Viewpoint dimensions | visible part of the screen: 1% of the viewport's width/height
  | vmax      | Viewpoint max        | 1% of the viewport's larger  dimension.
  | vmin      | Viewpoint min        | 1% of the viewport's smaller dimension.
    
    function calc for with height =>  width: calc(100vh-100px) 


###  z-index                       

**z-index** determines the order of the element on the z-axis of the stacking context.
Otherwise: the order how they appear in HTML document.

**Only** for absolute and fixed positions.   
Max for z-index=9999, can be negative.

!!! MAKE NO SENSE FOR STATIC
    
https://habr.com/ru/articles/431046/
 

###  Overflow of the element content

 #### Overflow
 - auto:    scrollbar will appear IF overflow
 - scroll:  scrollbar will be shown ALWAYS
 - hidden:  do not show scrollbar, overflow content will be hidden

More precise: overflow-x, overflow-y


###  Floating elements (legacy => use flex)
    
  **float** 
   - REMOVES element from main flow: BUT *inline* elements still see it

   - width became the with of the content

   - can be set to inline elements, in this case their behaviour will be as block element

    float: left, right
    
    clear: both, left, right, none
    
RESUME: Its very complex with several nuances. USE FLEX!


###  Setup font, text styles  

*Safe fonts* - this font can be found on user computer. But it depends on OS.
    
 - font-weight:      100-900 (+100)   normal bold
 - font-style:       normal, italic, cursive
 - font-size:        40px
 - color:            red
 - text-decoration:  underline, overline, linethrew, none
 - letter-spacing:   distance betwween letters 
 - word-spacing:     distance between words
 - line-height:      
 - text-transform:   uppercase lowercase  capitilize none
 - text-align:       left center right justify
 - text-indent:      indent from left for the text
 - font-kerning:     defines how letters are spaced
 - font-synthesis:   property lets you specify whether or not the browser may synthesize 
                     the bold, italic, small-caps, and/or subscript and superscript 
                     typefaces when they are missing in the specified font-family.

- font-synthesis-small-caps: lets you specify whether or not the browser may synthesize 
                              small-caps typeface when it is missing in a font family.
        

  **font-family**
   - Serif:        шрифты с зачечками на буквах
   - Sans-serif:   без засечек на буквах
   - Monospace:    the same width of the letter
   - Cursive:
   - Fantasy:
    
  NOTE: to direct include the font to the page use **font-face**

	```
    @font-face {
		font-famile: "mefont";
		src:  url("....")  format(),
		src:  url("....")  format()
	}     
	```
    
The best browser compatibility is for TTF/OTF, WOFF, WOFF2

- TrueType Fonts(TTF):  Developed by Apple and Microsoft in the late 1980s 

- OpenType Fonts(OFF):  Scalable font by Microsoft in 1996
                        Scalable font can increase in size without causing any degradation in the quality.

- The Web Open Font Format (WOFF): Developed in 2009, recomended by W3C. WOFF is a font format for use in web pages.
								   WOFF is essentially OpenType or TrueType with compression and additional metadata. 
                                   The goal is to support font distribution from a server to a client over a network with bandwidth constraints.

- WOFF 2.0: Better compression than WOFF 1.0

- SVG Fonts/Shapes:  SVG fonts allow SVG to be used as glyphs when displaying text. 


###  border             

  - border-width:
  - border-style:  none, solid, dashed, dotted, double, groove, inset, upset   
  - border-color:  
  - border:        mix 3 upper properties, order doesn't matter

More precise: border-left, border-right, border-top, border-bottom
              border-left-color ......

###  outline

An outline is a line that is drawn around elements, OUTSIDE the borders.

It **don't change the size of the box element** and can be set only for **all four side**.
But it helps for accessibility: it is border for element on focus

  - outline-style
  - outline-color
  - outline-width
  - outline-offset
  - outline


###  Shadows 

#### On element:
  - box-shadow:  inset | length | length | color
                 inset: shadow will be shown inside element

 Several shadows can be set, separated by comma

 #### On text
 - text-shadow:  offset-x | offset-y | blur-radius | color
                 
 Several shadows can be set, separated by comma


###  Round corners


 - border-radius:    40px:  all  OR  
                     top-left top-right  bottom-right  bottom-left
                     20px/40px : horiz/vertic  => ellipse

More precise: border-top-left, border-top-right, border-bottom-left, border-bottom-right


###  Lists                                

 #### ol/ul

 - list-style-type:      none, disk(defalt), circle, square, upper-alfa, lower-alfa,  decimal, upper-roman 
 - list-style-position:  outside(default), inside
 - list-style-image:     url("...")   
 
 NOTE1: image size cannot be set in css


###  Colors                              

Note 1: **Specificationdefined named colors** (CSS 2.1): red, navy, white, yellow, red ....

Note 2: DEPRECATED BY CSS3: CSS **system colors** (introduced by CSS2): ActiveBorder, ButtonFace, InfoText... 

  - HEX: 00ff00, 6-Hex Color, some colors can be shorten to 3-hex color
    
  - RGB: (0, 255, 0)
    
  - HSL(0, 100%, 50%), hue(оттенок)-saturaton(насыщенность)-lighness(священность)
    
  - RGBA, HSLA  => (alpha channel ~ opacity)

  - transparent

  - currentColor


###  What is currentColor keyword

**currentColor** Keyword:  refers to the value of the color property of an element

	```
	.class {
		color: blue; 
		border: 10px solid currentcolor; /* will be Blue */
	}
	```

###  Hide elements    

  - display: none
    Totaly remove element from the flow and DOM and not visible for SEO

  - visibility: hidden
    Was **not deleted** from flow, its still visible for search engines.

  - opacity: 0
    Was **not deleted** from flow, its still visible for search engines.



###  Text effects                         

  - text-overflow:  ellipsis - ...
                    clip - text will be cuted
    
  - white-space:    nowrap - single line
    
  - word-wrap:      break-word - word will be wrap to next line
  
  - word-break:     normal(default) | break-all;

  - writing-mode:   vertical  vertical-lr

 Multicolumn  text can be divided to columns. Need to set in parent element (```<div>```)

  - column-count:  N
    
  - column-rule:   1px solid grey
    
  - column-width:  auto(default) | 300px
    
  - column-gap:    100px    space between columns


###  Background

  - background-color:      color
  - background-image:      url(...)
  - background-size:       contain, cover   (100px 200px)-it will duplicate by default
  - background-repeat:     no-repeat, repeat-x, repeat-y
  - background-position:   left, center, right, bottom
  - background-position-x:  %   or  px  => shift image horiz or verticaly
  - background-position-y:
  - background-attachment:  fixed  => image will be always visible, not depending on scroll
    
Summary:
  - background:  color | image | position | repeat | attachment 
    
Note: Separated by comma, we can add several background images


###  Gradient                              

  #### linear                               
    - background/background-image: linear-gradient(90dep,   black,   white..... other colors)
                                    to top right   can use px and there is 2nd parameter
                                    repeating-linear-gradient
  #### radial
    - background: radial-gradient([elipse/circle], startcolor, endcolor)
                  closest-side  closest-corner  farhtest-side  farthest-corner
				  repeating-radial-gradient

###  Filters                             

Add visual effects for elements. Filters can be combined.
    
  **filter** 
   - blur:         blur deapth   2px
   - drop-shadow:  horiz shift    vertic shift    blur  цвет 
                   NOTE: shadow will be applyed to *content* of the pseudo after/before also
                              useful for bottom triangle (like in tooltip)
   - greyscale:    (0-100%) 
   - brightness:   (-50 +150%)
   - contrast:     (-50 +150%)
   - hue-rotate:   (deg 0-360)  
   - invert:       (0-100%)
   - saturate:     (0-1000%)     aka contrast
   - sepia:        (0-100%)      old look
   - opacity:      (0-100%) 
   - url(file.svg#filter-element-id)    You can use url() to reference an SVG filter element. 
                                        For a reference to an SVG <filter> element, use the following syntax


###  Elements Transformations             

Transformed element will **not touch the rounded elements**. Transforms can be combined.
    
  **transform**

   - rotate         (deg)  can be negative-positive

   - scale          (number)  0-1: decrease  >1:increase     (x, y):  x-acis y-acis
                    scaleX, scaleY  the last in the code will be applyed
                    Note: *Loop* feature can be done with scale and parent div overflow:hidden

   - translate:     (horiz, vertic)  shift to right-bottom by default
                    translateX, translateY

   - skew:          (vertic, horiz) deg
                    skewX, skewY

**origin**: the basic point on which ol transformation occur, by default this is center of the image.
    
  - transform-origin:  right bottom left top  => change the basic point
                       pixels, procenteges

###  Transitions                           

  ####  transition

   - transition-duration:  (seconds)  1s  0.5s  500ms, can set each duration for each property, separated by comma

   - transition-property:  color | all   
                           transform => only size will be changed
                           can combine properties separated by comma

   - transition-delay:     1s  0.5s  500ms   DELAY in start of transition
                           can set each duration for each property, separated by comma

   - transition-timing-function   transition is changed during time
                                  ease | ease-in | ease-out | ease-in-out | linear | step-start
                                  step-end | steps(10, start)  | steps(10, end) | cubic-bezier(....) 

 Combined single rule:
   - transition:   properties |  duration  | function  |  delay 


###  Animations                          

Animation can do multiply transitions in many loops, also it can be stopped.

At the beginning key-frames should be deteremined.

  **Step 1:** Determine of the animation: with 3 frames(from, 50%, to)

              Other frames can be added:

			  ```
              @key-frames  myAnimation {
                  from {  background-color: red;   }
                  50%  {  background-color: blue;  }
                  to   {  background-color: green; }
              }
			  ```


   **Step 2:** Do this animation for the target element:

   			```
            <target>  div {
                anumation-name:             myAnimation;
                animation-duration:         5s;  (500ms);
                animation-timing-function:  linear ... (the same as transition)
                animation-iteration-count:  num (default =1)  infinity
                animation-direction:        normal | alternate | reverse | alternate-reverse 
                animation-play-state:       paused | running
                animation-fill-mode:        forwards
                animation-delay:            1s 500ms  
            }
			```

Combined single rule:
  - animation:   none | duration | function | delay |  iteration-count | direction | fill-mode
                (minimum 4 must be set)

Several animations can be set for single target element.


###  Tables                               

  - **border**:             1px soild red;

  - **border-collapse:**    separate(defalt) - will be double border
                            collapse         - single
    
  - **border-spacing:**     10px | (horiz, vert)  difference between borders

  - **caption-side:**       top(default) | bottom

  - **text-align:**         left | center | right
    
  - **vertical-align:**     baseline | bottom | middle | sub | super | text-bottom | text-top | top
    
  - **empty-cells:**        show(default) | hide 


###  Cursors                              

  - **pointer-events:**  Sets under what circumstances (if any) a particular graphic element can become the target 
  						 of pointer events. Can be used for disabled buttons or prohibit text selection. 
                         auto(default) | none
        
  - **pointer:**     hand | crosshair | copy | progress:   wait:

  - **url(...):** image for cursor


###  pointer-events property

Sets under what circumstances (if any) a particular graphic element can become the target of pointer events. 

Can be used for disabled buttons or prohibit text selection. 

  - auto(default) 

  - none

  - stroke (svg only)

  - fill (svg only)


###  Placeholders styling                 

Use **::placeholder**  pseudo-class for changing placeholder style.
    
It will not work for complex elements (date, or smth with dropdown)


###  Scrollbars styling                    

  - webkit-scrollbar:           the whole scrollbat itself
  
  - webkit-scrollbar-track:     space under the scroll, progress bar of the scrollbar.
  
  - webkit-scrollbar-thumb:     the draggable scrolling handle - сам ползунок
    
  - webkit-scrollbar-button:    the buttons on the scrollbar (arrows pointing upwards and downwards)


###  scrollbar-gutter property (limited functionality)

Solve the problem when the content fleshes after the scrollbar appear/disappear.
The scrollbar-gutter CSS property allows authors to reserve space for the scrollbar, preventing unwanted layout changes 
as the content grows while also avoiding unnecessary visuals when scrolling isn't needed.

 - auto
 - stable
 - stable both-edges


## Pseudo classes and elements

###  What is pseudo-class 

A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element

	:hover  
	:visited  
	:active 
	:focus
	:first-child 
	:not

Added in CSS3
	:nth-child(n)  
    :nth-last-child(n)  
    :last-child (n)
    :only-child
    :nth-of-type(n)
	:first-of-type  
	:last-of-type   
	:nth-child(even)  
	:nth-child(odd)  
	:nth-child(2n) 
	:nth-child(3n+1)


###  What is pseudo-element 

Added to css selector with :: and changed the element structure

	::first-line  
	::first-letter  
	::marker  
	::placeholder
    ::selection (only for color and background-color)
    ::after 
	::before (with content only)


###  Difference between pseudo-class and pseudo-element

  - class: specifies a special state of the selected element, which can be change after user action or smth else

  - element: change the element structure and add virtual elements

###  pseudo-elements for text selection

    ::selection (only for color and background-color)
    ::grammar-error  (experimental)
    ::spelling-error (experimental)
    ::target-text    (experimental)

###  :inavlid/valid pseudo-classes 

The :invalid CSS pseudo-class represents any *form*, *fieldset*, *input* or other *form* element whose contents fail to validate.
This pseudo-class is useful for highlighting field errors for the user.

The :valid CSS pseudo-class represents any *input* or other *form* element whose contents validate successfully. 
This allows to easily make valid fields adopt an appearance that helps the user confirm that their data is formatted properly.

###  :has() pseudo-class

The functional :has() CSS pseudo-class represents an element if any of the relative selectors that are passed as an 
argument match at least one element when anchored against this element. 
This pseudo-class presents a way of selecting a parent element or a previous sibling element with respect to a reference element
by taking a relative selector list as an argument.
It does NOT add any addiotional weight to selector specificity.

###  What is *attr*

The attr() CSS function is used to retrieve the value of an attribute of the selected element and use it in the stylesheet. 

It can also be used on **pseudo-elements**, in which case the value of the attribute on the pseudo-element's originating element is returned.

    ```
    html
    <blockquote cite="https://web.dev/about/">
        Google believes in an open, accessible, private, and secure web.
    </blockquote>

    css
    blockquote::after {
        display: block;
        content: ' (source: ' attr(cite) ') ';
        color: hotpink;
    }
    ```