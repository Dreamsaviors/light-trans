# light-trans
A light weight multilingual & localization framework for your web application.

Light-trans is zero dependency multilingual & localization framework for vanilla javaScript. It is worked for any web based app build on Cordova, Node Webkit, Electron, etc. It is also great for normal websites.

# Installation
With NPM :

    npm i light-trans

# How to use

## Step 1. Installation

Include light-trans into your application.

NW (Node Webkit) and other Node embedded engine
```javascript
// create a new instance of Light Trans
const LT = require("light-trans");
```
Browser 
```html
<script type="text/javascript" src="light-trans.js"></script>
```

## Step 2. Initialization

Initialization
```javascript
// create a new instance of Light Trans
// run this at the top most of your code. You want to run light-trans before all of your code
const lt = new LT();
```
Light-trans will load the last selected language by user. Rest assured, no cookie are involved.

## Step 3. Marking for translation

**Marking your JavaScript code :**
```javascript
// instead of writing your codes directly like this :
alert("Hello world");
document.getElementById('text').innerHTML = "some string"

// wrap all your translatable string with the listener you defined before (by default the listener is "_t" function)
alert(_t("Hello world"));
document.getElementById('text').innerHTML = _t("some string")
// notice the "_t" function that encapsulate the texts that marked for translation.
// you can change the listener function as you like.
```

**Marking your HTML code :**
To mark inner html for translation, use "**data-tran**" attribute to the target element :
```html
<p data-tran="">This text between p tags will be subject for translation</p>
```

To mark attributes for translation, add **"data-tranattr"** attributes into target elements referring to the attribute name. Separate attribute name with spaces for multiple attributes.
```html
<input type="button" title="this is a very cool button" data-tranattr="title" />
<img src="coolimg.png" title="a very cool image" alt="cool image" data-tranattr="title alt" />
<input type="text" value="search" title="search" placeholder="Start searching" data-tranattr="title value placeholder" />
```

## Step 4. Create a translation table

There is several way to create translation table.
The most straight forward way is to define **translationPair** in the instance of light-trans.
```javascript
lt.set('translationPair', {
	"text to be translated" : "translation result",
	"hello" : "こんにちは",
	"this is a very cool button" : "これはとてもクールなボタンです",
	"This text between p tags will be subject for translation" : "pタグ間のこのテキストは翻訳されます"
})
```

Or, you can import from external .trans format.
```javascript
lt.from("lang/jp.trans");
```
You can use [Translator++](http://dreamsavior.net/download), [a free GUI editor to create and edit .trans document.](http://dreamsavior.net)

