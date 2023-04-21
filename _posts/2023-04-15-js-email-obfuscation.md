---
title: "Email obfuscation using JavaScript"
date: 2023-04-15
categories: JavaScript
tags: snippets email
m: "mail address obfuscation"
published: yes
---

Email harvesters and other bots roam the Internet looking for email addresses to add to lists that target recipients for spam. This trend results in an increasing amount of unwanted email. Learn how to create a simple **{{page.m}}** using JavaScript. 

Check this step-by-step guide.

Let´s Start.

<details open>
  <summary>
    <h2>Background</h2>
  </summarry>
I like how Cloudflare obfuscate mails, googling around I found an [Andrew Lock](https://andrewlock.net/) article explaining how to use a simple bitwise XOR using a key, and as I knew the technique, I decided to adapt it and do my own implementation. 

If you want to skip the how-to and just use it you can visit my [encoder page](https://lucianofullstack.pages.dev/assets/encoder).

`XOR` stands for *exclusive OR*. It is a logical operation that returns a positive or true result when either but not both of its two inputs are true. In other words, the output is true if the inputs are not alike otherwise the output is false.

The `XOR` algorithm is basically a simple substitution cipher. In other words, it just replaces each alphanumeric in a string that is fed into it with another number. Crucially, the algorithm is reversible. So if you feed the output string back into the same algorithm, you end up with the original string with the cipher removed. This kind of cipher is also called an additive cipher, and is the simplest kind of cipher there is.
</details>

## Goal

Create a simple {{page.m}} using just JavaScript for encoding and decoding our address. In order to encode we will need a string representing a valid email address and a numerical key from `0` to `255` (`0` to `FF` in `hex`). Also we have to create a drop-in script that decode our emails, and a form to create the ciphered ones.

## Encoder

The function will receive two parameters `email` and `key` and returns a `string` containing the concatenation of the `key` in `hex` and  the result of applying `XOR` to every character of the mail address.

First, as `key` is a `decimal` number we have to convert it to `hex` and pad it with a zero in case is smaller than 10<sub>16</sub>

```js
let encodedString = key.toString(16).padStart(2,'0')
```

Then we iterate trough the whole mail address doing a `xor`, padding and concatenating to `encodedString`

```js
for ( let n=0; n < email.length ; n++ ) {
    encodedString += ( email.charCodeAt(n) ^ key ).toString(16).padStart(2,'0')
  }

```

The whole encoder code so far

```js
function encodeEmail(email, key) {
  let encodedString = 
      key
      .toString(16)
      .padStart(2,'0')
  for ( let n=0        ; 
            n < email.length ; 
            n++ 
      ) {
          encodedString += 
          ( email
           .charCodeAt(n) ^ key 
          ).toString(16)
           .padStart(2,'0')
  }
  return encodedString
}
```

## Decoder

As we can realize the new length will be `originalLenght*2+2` as every char and the key will be represented by their `hex value`, so we have to pick the first two characters of the encoded string and covert it to decimal. Then we will repeat the operation using that value as `key` and doing `xor` and concatenating the rest. 

```js
const decodeEmail = (encoded) => {
  let
  decEml   = '' ,
  keyInHex = encoded.substr (0, 2) ,
  key      = parseInt (keyInHex, 16)
  for (let n = 2;
           n < encoded.length;
           n += 2
  ) {
      let
      charInHex = encoded.substr (n, 2) ,
      char      = parseInt (charInHex, 16) ,
      output    = char ^ key
      decEml += String.fromCharCode (output)
    }
    return decEml
}
```

## Parser

In order to store our encoded address we will use the `data` attribute and we also will make a function to parse all of our encoded emails that have a certain class for instance `eml` .

Example Link:

```html
<a href="#" class="eml" data-encoded= "9c...">[contact]</a>
```

Parse Function:

```js
function parseEmail() {
  const
  eml =
  document.getElementsByClassName("eml")
  for (let i = 0; i < eml.length; i++) {
    let
    elEml = eml[i] ,
    encoded = elEml.dataset.encoded,
    decoded = decodeEmail(encoded)
    elEml.textContent = decoded
    elEml.href = 'mailto:' + decoded
  }
} parseEmail()
```

## The Form Encoder

We will create a very basic form in order to encode and create the links also it will have the instructions that allow users to add the script needed to decode mails.

The form need some validations as we need an email address and a key from 0 to 255. You can check the full source code below. 

In order to verify the address we use this function that returns `true` or `false` when an address is passed to it.

```js
function validEmail(email) {
    const 
    res = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
    return res.test(String(email).toLowerCase())
}

```

In terms of design we will use https://simplecss.org a minimal CSS semantic framework.

## The Result

### You can visit the page with the [final result](https://lucianofullstack.pages.dev/assets/encoder).

Or check this pen:

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="poxyVQb" data-user="lucianofullstack" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/lucianofullstack/pen/poxyVQb">
  Email Obfuscation</a> by Luciano Fullstack (<a href="https://codepen.io/lucianofullstack">@lucianofullstack</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p><script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
