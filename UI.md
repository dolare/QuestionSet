##1. How to make a css rule with the highest priority?

##2. what is strict mode in JavaScript?

Strict mode is a way to change both syntax and runtime behavior in javascript by use "use strict".

First, strict mode makes it impossible to accidentally create global variables.

mistypedVaraible = 17;

Second, strict mode makes assignments which would otherwise silently fail throw an exception.

// Assignment to a non-writable property
var obj1 = {};
Object.defineProperty(obj1, "x", { value: 42, writable: false });
obj1.x = 9; // throws a TypeError

Third, strict mode makes attempts to delete undeletable properties throw (where before the attempt would simply have no effect):
delete Object.prototype; // throws a TypeError

Fourth, strict mode prior to Gecko 34 requires that all properties named in an object literal be unique.
"use strict";
var o = { p: 1, p: 2 }; // !!! syntax error

Fifth, strict mode requires that function parameter names be unique.
function sum(a, a, c){ // !!! syntax error
  "use strict";
  return a + b + c; // wrong if this code ran
}

Sixth, strict mode in ECMAScript 5 forbids octal syntax.
var a = 0o10; // ES6: Octal

##3. css box model?
margin> border > padding > content

##4. CSS selector: How to change the color of the last div in a group of divs?
div:last-child{
  //do something
}

##5. the difference between div and span?
div is a block element, span is inline element.
This means that to use them semantically, divs should be used to wrap sections of a document, while spans should be
used to wrap small portions of text, images.

##6. how to select all elements in Jquery?
$("*"):

##7. In CSS, how to make 3 blocks display in one line?
method1:make the parent position as relative, and use float:left style in this block
method2:just use display:inline;

##8. in css, how to change the color of the 3rd column of a table?

use  nth-child(n) selector ,like this:

p:nth-child(odd){} p:nth-child(even){}  

solution:table td:nth-child(2){}

##9. what is z-index in css?
The z-index property specifies the z-order of an element and its descendants. When elements overlap, z-order determines 
which one covers the other. An element with a larger z-index generally covers an element with a lower one.

##10. what is css inheritance?
Inheritance is the process by which properties are passed from parent to child elements even though those properties
have not been explicitly defined by other means. Certain properties are inherited automatically, and as the name implies, 
a child element will take on the characteristics of its parent with regards to these properties.

For example, if a div element has a font-size of 20px then, assuming that no other font-size declarations have been
explicitly defined, any children will also inherit that font-size value


##11. css different type of font-size?
em
px
pt
%

##12. how to select the first 3 divs in a single line code?
div:nth-child(-n+4)


##13. create a singleton in javascript?

      var Singleton = (function () {
          var instance;
       
          function createInstance() {
              var object = new Object("I am the instance");
              return object;
          }
       
          return {
              getInstance: function () {
                  if (!instance) {
                      instance = createInstance();
                  }
                  return instance;
              }
          };
      })();
       
      function run() {
       
          var instance1 = Singleton.getInstance();
          var instance2 = Singleton.getInstance();
       
          alert("Same instance? " + (instance1 === instance2));  
      }
      
##14. how to detect os and browser version in web application by javascript?
  
    var OSName="Unknown OS";
    if (navigator.appVersion.indexOf("Win")!=-1) OSName="Windows";
    if (navigator.appVersion.indexOf("Mac")!=-1) OSName="MacOS";
    if (navigator.appVersion.indexOf("X11")!=-1) OSName="UNIX";
    if (navigator.appVersion.indexOf("Linux")!=-1) OSName="Linux";
    
    <div id="example"></div>

  <script type="text/javascript">

      txt = "<p>Browser CodeName: " + navigator.appCodeName + "</p>";
      txt+= "<p>Browser Name: " + navigator.appName + "</p>";
      txt+= "<p>Browser Version: " + navigator.appVersion + "</p>";
      txt+= "<p>Cookies Enabled: " + navigator.cookieEnabled + "</p>";
      txt+= "<p>Platform: " + navigator.platform + "</p>";
      txt+= "<p>User-agent header: " + navigator.userAgent + "</p>";
      
      document.getElementById("example").innerHTML=txt;
    
    </script>
    
    Browser CodeName: Mozilla
    
    Browser Name: Netscape
    
    Browser Version: 5.0 (Windows)
    
    Cookies Enabled: true
    
    Platform: Win32
    
    User-agent header: Mozilla/5.0 (Windows NT 5.1; rv:12.0) Gecko/20100101 Firefox/12.0
    
##15. what is idempotence in rest api?
    The PUT method is idempotent. An idempotent method means that the result of a successful performed request
    is independent of the number of times it is executed.
    
 ##16. how to reverse a string in javascript?
    
    1. decrementing for-loop with concatenation
    
      function reverse(s) {
        var o = '';
        for (var i = s.length - 1; i >= 0; i--)
          o += s[i];
        return o;
      }
  
    2. incrementing for-loop with array pushing and charAt
    
      function reverse(s) {
        var o = [];
        for (var i = 0, len = s.length; i <= len; i++)
          o.push(s.charAt(len - i));
        return o.join('');
     }
     
    3. in-built functions:
    
    function reverse(s){
      return s.split('').reverse().join('');
    }
    
##17. what is the pseudo-class in css?
    
    a pseudo-class is used to define a special state of an element.
    
example:
Style an element when a user mouses over it
Style visited and unvisited links differently
Style an element when it gets focus
a:link{}  a:visited{}  a:hover{} a:active{}

##18. how to handle security issue when using rest?
jsonp

##19. how to make ajax synchronous?
just set the attribute async false in ajax call.
$.ajax({async:false)}

##20. how to find out whether a variable is declared or not in javascript?
if (typeof variable === 'undefined') {
    // variable is undefined
}

##21. difference between local storage and session storage?

sessionStorage, localStorage and cookie all are used to store data on the client side.

LocalStorage:stores data with no expiration data, and get cleared only througn javascript or clearing the browser cache/locally 
stored data.

sessionStorage:similar to localStorage but expires when the brwoser closed.

cookie:store data that has to be sent back to the server with subsequent request.

Cookies are primarily for reading server-side, localStorage and sessionStorage can only be read client-side.

##22. what is jquery chain?

jquery chain is a technique that allows us to run multiple jquery commands, one after the other, on the same element.

such as: $('#p1').css('color','red').slideUp(2000).slideDown(2000);

##23. 
  
