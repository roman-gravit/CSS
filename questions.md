 # CSS
 

 ## 1. What is CSS

 CSS(Cascading Style Sheet: add visal effects to the HTML page.
 Number of rules which tell browser how to display elements on the page, color, font.

 History:
  - CSS1 was developed in 1996
  - CSS2 was developed in 1998
  - CSS3 was published as a W3C Recommendation in 2011.
    CSS3 is divided into several separate documents called "modules". 

Superior styles to HTML − CSS has a much wider array of attributes than HTML, 
so CSS give a better look to HTML page in comparison to HTML attributes


## 2. What is CSS rule 

CSS rule consists of 2 elements:
 
 Rule: ```div { color: blue; }```
 - selector: div
 - declaration block: { color: blue; }

 Declaration block consists of property(color) and value(blue).


## 3. Variants to add CSS 

 - **Inline:**     Add style directly to the element via attribyte: 
 			   ```<div style="....">``` It can be ovverride only with !important

 - **Internal:**   Styling the entire webpage. Add ```<style>``` tag to the ```<head>```
	
 - **Extrenal:**   Styling in external *.css file.  Include it via  ```<link>``` tag inside ```<head>```
               ```<link href="...." rel="stylesheet" />```
 
 - **@import:**    Add style via import directive


## 4. How many types of levels in style sheets

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

## 5. What is style selector 

Selector is a part of the css rule. It can help to choose the element and set style for it.
   
### Simple selectors(containt single selector):                                               
   	
 - universal(*): For all child elements, can be use for reset(normalize) css rules

 - tagName: Selector by element tag name, ex: ```h1 { color: red; }```             
     
 - class: Selector by class name, ex: ```.myclass { color: red; }``` 

 - id: Selector by element *id* attribute, ex:  ```#main { color: red; }```
	   *Id* must be unique on the HTML page.

- tagName.class: More precise selector, combination of tag and class, ex: ```h1.myclass { color: red; }```
   
Use *id* selector if you want to add some logic for exact element.
Use *class* selector for styling the set of elements.


### Complex selector(several)

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


## 6. What is specificity of the selectors

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


## 7. What is pseudo-class 

A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element:

	:hover  
	:visited  
	:active 
	:focus
	:first-child :last-child  
	:nth-child(even)  
	:nth-child(odd)  
	:nth-child(n)  
	:nth-child(2n) 
	:nth-child(3n+1)
	:first-of-type  
	:last-of-type   
	:nth-of-type
	:not


## 8. What is pseudo-element 

Added to css selector with :: and changed the element structure:

	::first-line  
	::first-letter  
	::marker  
	::placeholder
    ::selection (only for color and background-color)
    ::after 
	::before (with content only)


## 9. CSS Cascade

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


## 10. Cascading inheritance

 - There are properties which can be inherit: font, color...

 - Which DO NOT inherite from the parent element: border, margins, padding...
   
 - Manual property inheritance can be applyed:   ```div { border: inherit; }```

Note: Each browser has its onw table of default styles for elements. 


## 11. Whats is cross browsing CSS compatibility

Browser has its own styling. Need to correct behaviour on different browsers in order
that your design looks the same on different browsers. Two main approaches:

 - Reset.css: erase to 0 all browser styles
    
 - Normilize.css: normalize default browser styling, make the same for all browsers [Preferable]
    
Inlcude reset/normilize.css as first css in you page.


## 12. Block/Inline model CSS 

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


##  13. What is margins collapse

Vertical margins (top-bottom) are collapsed for 2 blocked elements.


##  14. Positioning in CSS  

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


##  15. Sizes of the element

  - width 
  - height
  - min-width
  - min-height
  - max-width
  - max-height


## 16. Units of sizes in CSS

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


## 17. z-index                       

**z-index** determines the order of the element on the z-axis of the stacking context.
Otherwise: the order how they appear in HTML document.

**Only** for absolute and fixed positions.   
Max for z-index=9999, can be negative.

!!! MAKE NO SENSE FOR STATIC
    
https://habr.com/ru/articles/431046/
 

## 18. Overflow of the element content

 #### Overflow
 - auto:    scrollbar will appear IF overflow
 - scroll:  scrollbar will be shown ALWAYS
 - hidden:  do not show scrollbar, overflow content will be hidden

More precise: overflow-x, overflow-y


## 19. Floating elements (legacy => use flex)
    
  **float** 
   - REMOVES element from main flow: BUT *inline* elements still see it

   - width became the with of the content

   - can be set to inline elements, in this case their behaviour will be as block element

    float: left, right
    
    clear: both, left, right, none
    
RESUME: Its very complex with several nuances. USE FLEX!


## 20. Setup font, text styles  

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


## 21. Border             

 #### Border 
  - border-width:
  - border-style:  none, solid, dashed, dotted, double, groove, inset, upset   
  - border-color:  
  - border:        mix 3 upper properties, order doesn't matter

More precise: border-left, border-right, border-top, border-bottom
              border-left-color ......

 #### Outline 

 An outline is a line drawn outside the element's border.
 An outline is a line that is drawn around elements, OUTSIDE the borders.
 It **don't change the size of the box element** and can be set only for **all four side**.
 But it helps for accessibility: it is border for element on focus

  - outline-style
  - outline-color
  - outline-width
  - outline-offset
  - outline


## 22. Shadows 

#### On element:
  - box-shadow:  inset | length | length | color
                 inset: shadow will be shown inside element

 Several shadows can be set, separated by comma

 #### On text
 - text-shadow:  offset-x | offset-y | blur-radius | color
                 
 Several shadows can be set, separated by comma


## 23. Round corners


 - border-radius:    40px:  all  OR  
                     top-left top-right  bottom-right  bottom-left
                     20px/40px : horiz/vertic  => ellipse

More precise: border-top-left, border-top-right, border-bottom-left, border-bottom-right


##  24. Lists                                

 #### ol/ul

 - list-style-type:      none, disk(defalt), circle, square, upper-alfa, lower-alfa,  decimal, upper-roman 
 - list-style-position:  outside(default), inside
 - list-style-image:     url("...")   
 
 NOTE1: image size cannot be set in css


##  25. Colors                                

Note 1: **Specificationdefined named colors** (CSS 2.1): red, navy, white, yellow, red ....

Note 2: DEPRECATED BY CSS3: CSS **system colors** (introduced by CSS2): ActiveBorder, ButtonFace, InfoText... 

  - HEX: 00ff00, 6-Hex Color, some colors can be shorten to 3-hex color
    
  - RGB: (0, 255, 0)
    
  - HSL(0, 100%, 50%), hue(оттенок)-saturaton(насыщенность)-lighness(священность)
    
  - RGBA, HSLA  => (alpha channel ~ opacity)
     

**currentcolor** Keyword:  refers to the value of the color property of an element

	```
	.class {
		color: blue; 
		border: 10px solid currentcolor; /* will be Blue */
	}
	```

##  26. Hide elements    

  - display: none
    Totaly remove element from the flow and DOM and not visible for SEO

  - visibility: hidden
    Was **not deleted** from flow, its still visible for search engines.

  - opacity: 0
    Was **not deleted** from flow, its still visible for search engines.


##  27. Vender prefix and why do we need it 

  --webkit-opacity   
  --moz-opacity
  --o-opacity
  --ms-opacity
    
This css property is under construction or tesing in specific browser.
Or this property is not in standart yet.
    
Note: Resource for tesing vender properties: caniuse.com
