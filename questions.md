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
 
 Rule: div { color: blue; }
 - selector: div
 - declaration block: { color: blue; }

 Declaration block consists of property(color) and value(blue).


## 3. Variants to add CSS 

 - Inline:     Add style directly to the element via attribyte: 
 			   ```<div style="....">``` It can be ovverride only with !important

 - Internal:   Styling the entire webpage. Add ```<style>``` tag to the ```<head>```
	
 - Extrenal:   Styling in external *.css file.  Include it ```<link>``` tag inside ```<head>```
               ```<link href="...." rel="stylesheet" />```
 
 - @import:    Add style via import directive


## 4. How many types of levels in style sheets

 - Inline:              Specified for a specific occurrence of a tag and apply only to that tag. 
                        This is finegrain style, which defeats the purpose of style sheets - uniform style

 - Internal(Embedded):  Document-level css, apply to the whole document in which they appear, inside ```<head>``` element

 - External:            Can be applied to any number of documents

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

        Ex:

		    ```
            <li>
				<em><span> First </span></em>
            </li>
			<li>
				<span> Second </span>
			</li>
			````
	
	Will be applied ONLY to *Second* text: direct child(```<span>```) of the parent ```<li>```
	*First* has ```<em>``` element between.

 - Selector for NEXT CHILDREN: ```ul li + li { color:red; }```

        Ex: 

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

        Ex: 
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
