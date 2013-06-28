Javascript Standards
====================
This document uses our existing code conventions as a baseline and mix in standards adapted from authoritative resources that are recognized by the Javascript community as a whole. Much of the content here has been lifted directly from those documents (listed in the resources section at the end) where relevant or applicable.

------------------
Yet to be defined
------------------
Items that are purely convention.

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


----------
Whitespace
----------
 - Never mix spaces and tabs unless it is meant to be represented in a string.
 - Use 4 spaces for tabs.
 - Lines should not contain trailing spaces, even after binary operators, commas or semicolons.
 - Separate binary operators with spaces.
 - Spaces after commas and semicolons, but not before.
 - Spaces after keywords, e.g. if (x > 0).
 - For readability, I always recommend setting your editor's indent size to four characters — this means two spaces or two spaces representing a real tab.
 - If your editor supports it, always work with the "show invisibles" setting turned on. The benefits of this practice are:
  - Enforced consistency
  - Eliminating end of line whitespace
  - Eliminating blank line whitespace
  - Commits and diffs that are easier to read
 - Try to keep lines to 100 characters or less. When wrapping lines, try to indent to line up with a related item on the previous line.


------
Quotes
------
Prefer double quotes, except in in-line event handlers or when quoting double quotes.

---------
Operators / Tokens
---------

-------------------------
Terminators / Punctuators
-------------------------
```;```

--------
Keywords
--------
```new```
```var```

----------------------
Restricted Productions
----------------------
Restricted productions are those in which a __*line break cannot appear*__ in a particular position, so if a line break appears there, it will prevent the program from parsing in that way, though it may still parse another way.

 - ++
 - \--
 - continue
 - break
 - return
 - throw

------------
Mr. Cool Guy
------------

####Identifiers

    userloop:for( var user in contactList.getUser() )
    {
        propertyloop:for (var userProp in user)
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


####Chaining

    $('.container').closest('.item').find('.stub')
                                    .hide();

####Turnary

####Short Circuit
```-1 == resultOfOperation() || die();```

####Assignments in Conditions

####Switch vs Dictionary

-----------------------
General Recommendations
-----------------------
Listed here are things to take into consideration during development.

 - Only use alert(); confirm(); prompt(); if you intend to block the javascript thread. Be cognizent of the effects on active or expected webservices.
 - Avoid global declarations were possible and always use intuitive namespacing. 


---------------------
Wise Words To Live By
---------------------

> HTML that makes sense without JavaScript should not be created with JavaScript. HTML that *only* makes sense *with* Javascript should be created with JavaScript.
> - Chris Heilmann

Resources
---------
 - [Google Style Guide](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
 - [Idiomatic.js](https://github.com/rwldrn/idiomatic.js)
 - [Javascript Code Convention by Douglas Crockford](http://javascript.crockford.com/code.html)
 - [A Baseline for Front End Developers by Rebecca Murphy](http://rmurphey.com/blog/2012/04/12/a-baseline-for-front-end-developers/)
 - [Scripting Maintainability by Chris Heilmann](http://www.slideshare.net/cheilmann/fronteers-maintainability-presentation)
 - [JavaScript Semicolon Insertion](http://inimino.org/~inimino/blog/javascript_semicolons)
 - [ECMA International](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma-262.pdf)
