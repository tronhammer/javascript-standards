Javascript Standards
====================
This document uses our existing code conventions as a baseline and mixes in standards adapted from authoritative resources that are recognized by the Javascript community as a whole. Much of the content here has been lifted directly from those documents (listed in the resources section at the end) where relevant or applicable.

------------------
Yet to be defined
------------------
Items that are purely convention.

######Aligning assignments to furthest indentation

    var currentState    = "running",
        storage         = {},
        user            = new User("Tron");
        
        
    var ontraport = {
        currentState:   "running",
        storage:        {},
        user:           new User("Rambo");
    }

######Quoting All Property Keys

    var user = {
        "name": "Tron",
        "getContactList": function()
        {
            // logic...
        }
    };

----------
Whitespace
----------
 - Never mix spaces and tabs unless it is meant to be represented in a string.
 - Lines should not contain trailing spaces, even after binary operators, commas or semicolons.
 - Blank lines should not contain any whitespace.
 - For readability, I always recommend setting your editor's indent size to four characters — this means two spaces or two spaces representing a real tab.
 - If your editor supports it, always work with the "show invisibles" setting turned on. The benefits of this practice are:
  - Enforced consistency
  - Eliminating end of line whitespace
  - Eliminating blank line whitespace
  - Commits and diffs that are easier to read


###Boundaries

####Tabs
Use 4 spaces for tabs.

####Newlines
Try to keep lines to 120*(reference needed) characters or less. 

*Wrapped line indentation should align with the initial block statement argument list parentheses.*

######Example
    var controller = this.model.meta.typeSelection.options[type]
                                                    .controller;
                                                    
    if(user.hasPerms('edit_content') && space.isEditable
        && content.isEditable)
    {
        /* Block Logic */
    }

###Whitespace with Operators

Separate binary operators with spaces.

######Example
    var total = count + total;

Spaces after commas and semicolons, but not after keywords

######Example
    var perms = ["staff", "user", "reviewer"];


###Whitespace with Block Statements
No spaces before or after block statement keywords or their parentheses.
All block statement keywords will start on their own line unless being assigned.

######Example
    if(success)
    while(success)
    function(success)


------
Casing
------
####Public Variables/Properties
######camelCase
    var userContactList = [];

    var user = {
        contactList: []
    };


####"Private" Variables/Properties
######Underscored camelCase
    var _addContact = [];

####Class Names
######PascalCase
    var User = {};
    var ContactItem = {};

####Constants
######Capital Underscore
    var DB_USER = 'VladimirPutin';

####jQuery DOM Elements
######Dollar camelCase
    var $contactRow = $(".contacts-container").find(".selected");


----------------
Block Statements
----------------
All block statements will have curly braces and their logic will be encapsulated within respectively.
All opening curly braces will start on the newline by themselves in alignment with the block statement keyword.

###Conditionals

######Example
    if(success)
    {
        // logic...
    }
    else
    {
        // logic...
    }

###Loops
All `for` loops will instantiate variables with `var` in their expression.

######Example
    for(var error in errors)
    {
        // logic...
    }
    
    for(var a; a<total; a++)
    {
        // logic...
    }
    
######Identifiers
Utilize identifiers in nested loops if applicable.

######Example
    userloop:for(var user in contactList.getUser())
    {
        userpropertyloop:for(var userProp in user)
        {
            if (userProp == 'something_im_lookingfor')
            {
                break userloop;
            }
            else if (userProp == 'something_else_im_lookingfor')
            {
                continue userloop;
            }
        }
    }
    
######Watch Out! Extended Native Prototypes will cause `for in` to act unexpectedly
In the event of adding a library that extends the native prorotypes such as Array, beware of unexpected behavior in existing `for in` statements in the code base, as the intention of the `in` operator in this context is to enumerate over properties of an object and will thusly start providing keys to the extended properties and methods.

Known Offending Libraries:

- ember.js
- prototype.js

###Functions

######Example
    /* assigned functions */
    var callback = function(success, errors)
    {
            // logic...
    };
    
    /* auto invoking functions */
    var mappedList = (
        function(list)
        {
            // logic...
        }
    )();
    
    /* method */
    var user = {
        getUserContactList: function()
        {
            // logic...
        }
    };

####Named Function Expressions
Avoid named functions were possible as they clutter the scope and call stack. In general, they should only be used when creating a prototyped object with the intention having multiple instances.
    
######Example
    /* Not so great */
    function mapUsers()
    {
        // logic...
    }
    
    /* Good */
    var mapUsers = function()
    {
        // logic...
    }
    
    /* Better */
    var utils = {
        mapUsers: function()
        {
            // logic...
        }
    }

------
Quotes
------
Use double quotes for all `String` objects, except in in-line event handlers or when quoting double quotes.

######Example
    /* normal strings */
    var name = "Tron";
    
    /* quoting double quote strings */
    var userJSON = '{"name":"Tron"}';
    
    /* in-line event handler */
    <div onclick="javascript:clicked('this div was clicked');" />

---------
Operators / Tokens
---------
All logical blocks should be encapsulated in either `{}` or `()`.
Longer expressions, conditions or short circuits should provide extra clarity through parenthases and whitespace where logic is compact.

######Example
    /* Not Clear */
    var simplified = x + 1 / x - 1;
    
    /* Clear */
    var simplified = (x + 1) / (x - 1);
    
    /* Not Clear */
    if (true && true && true || true && false || false && true || false && true)
    
    /* Clear */
    if (true && true && (true || (true && false)) || (false && true || false && true))


###Strictness
Where possible, use equality without type coercion with `===` as opposed to the traditional `==`.

######Example
    if (list.length === max)
    {
        // logic...
    }

-------------------------
Terminators / Punctuators
-------------------------
All complete logical statements should always end with a `;`

--------
Keywords
--------
Do not use the following keywords for identifiers.

 - `new`
 
 - `var`

 - `throw`

 - `return`

 - `break`

 - `continue`

 - `try`

 - `catch`

-----------
Declaration
-----------
All new variables should be instantiated with a `var` keyword (unfortunately `let` is not yet supported) and declared at the head of the block its scope is first utilized in.

*This includes for loops.*

######Example
    function(status,user)
    {
        var userContactList = user.getContactList(),
            firstName = user.name.split(' ')[0],
            result;
            
        if (status)
        {
            for(var contact in  userContactList)
            {
                if (contact.isFriend())
                {
                    result = contact;
                    break;
                }
            }
        }
        
        // logic...
        
        return result;
    }

----------------------
Restricted Productions
----------------------
Restricted productions are those in which a __*line break cannot appear*__ in a particular position, specifically after in most cases. If a line break does appear there, it will prevent the program from parsing in the expected way, though it may still parse another way.

The following are restricted productions:

 - ++
 - \--
 - continue
 - break
 - return
 - throw

######Example
    var getUserInfo = function(user)
    {
        return                                  // Line break triggers semicolon insertion
        {
            fullName: user.firstName + " " + user.lastName
        };
    };
    
    var user = getUserInfo(someUser);           // returns undefined

------------
Mr. Cool Guy
------------

####Multiple Declaration
Attempt to utilize multiple declerations with a single `var` at the head of a block to denote expected variables local to that scope.

######Example
    var user = new User(),
        item = new Item(),
        $container = $('.container');


####Chaining
Use chaining where possible and use line breaks and indentation to represent context changes. Better yet, prep your functions to utilize chaining by always `return` an object.

######Example
    /* jQuery chaining */
    $('.container')
        .closest('.item')
            .find('.stub')
                .hide()
            .end()
            .addClass("selected")
        .end()
        addClass("updated");
    
    /* chaining function */
    var getContainer = function(){
        return $(".container");
    };
    
    getContainer().hide();

####Turnary
Use turnaries sparingly. They can often become logic that needs to be expanded out later by another developer. But otherwise they are a great means to provide fallbacks to assignments.

######Example
    var username = (user) ? user.username : "Tron";
    
######Indentation Example
    var x = a ? b : c;  // All on one line if it will fit.

    // Indentation +4 is OK.
    var y = a ?
        longButSimpleOperandB : longButSimpleOperandC;

    // Indenting to the line position of the first operand is also OK.
    var z = a ?
        moreComplicatedB :
        moreComplicatedC;

####Short Circuit
Use short circuit sparingly. They can often become logic that needs to be expanded out later by another developer. But otherwise they are a great means to provide fallbacks to assignments. 

######Example
    var username = user.getID() && user.username || "Tron";

####Assignments in Conditions
Use assignments in conditions sparingly, as they can lead to confusion or misinterpretation of intentions by another developer (did he really mean `=` or `==`).

######Example
    if (($ele = $(".container")).length)
    {
        $ele.remove();
    }

####Pre-emptive Type Casting
The unary + operator will convert its right side operand to a number.

######Example
    var rowID = +$(".selected").data('id');

-------
Caching
-------
Always cache results of any function that is going to be used multiple times in the same block, __especially jQuery DOM Objects__

######Example
    /* BAD */
    if ($(".container").length)
    {
        $(".container").find(".item").fadeIn();
        // logic ...
        $(".container").find(".item").addClass("selected");
    }
    
    /* GOOD */
    var $container = $(".container");
    if ($container.length)
    {
        var $item = $container.find(".item");
        $item.fadeIn();
        // logic ...
        $item.addClass("selected");
    }

-------------
Documentation
-------------
Adhere to the Documentation Standards! Always!

-----------
Namespacing
-----------
Avoid using global scope identifiers where possible. Consider namespacing in the `window` object in order to prevent unforeseen conflicts in the future.

######Example
    /* Non namespaced global variable decleration could have potential name conflicts */
    window.username = {};
    
    /* Namespaced property decleration */
    window.ontraport = {
        username: {}
    };

---------------------------
Specific Naming Conventions
---------------------------

 - The terms get/set SHOULD NOT used where a field is accessed, unless the variable being accessed is lexically private.
 - The "is" prefix SHOULD be used for boolean variables and methods. Alternatives include "has", "can" and "should"
 - The term "compute" CAN be used in methods where something is computed.
 - The term "find" CAN be used in methods where something is looked up.
 - The terms "initialize" or "init" CAN be used where an object or a concept is established.
 - UI Control variables SHOULD be suffixed by the control type. Examples: leftComboBox, topScrollPane
 - Plural form MUST be used to name collections.
 - A "num" prefix or "count" postfix SHOULD be used for variables representing a number of objects.
 - Iterator variables SHOULD be called "i", "j", "k", etc.
 - Complement names MUST be used for complement entities. Examples: get/set, add/remove, create/destroy, start/stop, insert/delete, begin/end, etc.
 - Abbreviations in names SHOULD be avoided.
 - Negated boolean variable names MUST be avoided:

        isNotError, isNotFound are unacceptable.
        Exception classes SHOULD be suffixed with "Exception" or "Error" .. FIXME (trt) not sure about this?
 - Methods returning an object MAY be named after what they return, and methods returning void after what they do.


------------------
Standards features
------------------
Use native built in functions over library functions where applicable.

######Example
    /* Works */
    var letter = string[3]
    
    /* Works Better */
    var letter = string.charAt(3);

-----------------------
General Recommendations
-----------------------
Listed here are things to take into consideration during development.

 - Only use `alert();`, `confirm();`, `prompt();` if you intend to block the javascript thread. Be cognizent of the effects on active or expected webservices.
 - Avoid global declarations were possible and always use intuitive namespacing. 


---------------------
Words Of The Wise
---------------------

> HTML that makes sense without JavaScript should not be created with JavaScript. HTML that *only* makes sense *with* Javascript should be created with JavaScript.
> - Chris Heilmann

---------
Resources
---------

 - [Google Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
 - [Idiomatic.js](https://github.com/rwldrn/idiomatic.js)
 - [jQuery Javascript Style Guide](http://contribute.jquery.org/style-guide/js/)
 - [Dojo Toolkit Javascript Style Guide](http://dojotoolkit.org/community/styleGuide)
 - [JavaScript Programming Guideline by Siemens Building Technologies](http://www.galasoft-lb.ch/myjavascript/Siemens_SBT_JavaScript_Coding_Guidelines.pdf)
 - [Javascript Code Convention by Douglas Crockford](http://javascript.crockford.com/code.html)
 - [Code Guidelines for Rich Internet Application Development](http://jibbering.com/faq/notes/code-guidelines/)
 - [A Baseline for Front End Developers by Rebecca Murphy](http://rmurphey.com/blog/2012/04/12/a-baseline-for-front-end-developers/)
 - [Scripting Maintainability by Chris Heilmann](http://www.slideshare.net/cheilmann/fronteers-maintainability-presentation)
 - [Javascript Style Guide by Neil Rashbrook](http://neil.rashbrook.org/Js.htm)
 - [JavaScript Semicolon Insertion](http://inimino.org/~inimino/blog/javascript_semicolons)
 - [Named Function Expressions and the IE dilemma](http://kiro.me/blog/nfe_dilemma.html)
 - [ECMA International](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf)
 - [Annotated ECMAScript 5.1](http://es5.github.io/)
