# Language Translator App

A simple and interactive language translation web application built using **HTML**, **CSS**, and **JavaScript**.  
This project uses the **MyMemory Translation API** to translate text between multiple languages and includes text-to-speech functionality.

---

## Features

- Translate text between dozens of world languages  
- Swap languages instantly  
- Two-way text input/output areas  
- Text-to-speech for both source and translated text  
- Beautiful and clean UI  
- Powered by MyMemory translation API  
- Fast and responsive interface  

---

## Project Structure
```
translator-app/
│
├── index.html
├── style.css
├── script.js
└── languages.js
```

---

## How It Works

### **1. Language Loading**
The `languages.js` file contains a large list of language codes and names.  
These values automatically populate both dropdown menus (`fromLang` and `toLang`).

### **2. Translation**
When the user clicks the **Translate** button, JavaScript sends a GET request to:

https://api.mymemory.translated.net/get?q=YOUR_TEXT&langpair=FROM|TO

The translated text is retrieved and displayed in the output textarea.

### **3. Language Swap**
Clicking the swap icon exchanges:
- The selected languages  
- The text in both textareas  

### **4. Text-to-Speech**
Each side has a sound icon.  
Clicking it triggers the browser’s `SpeechSynthesis` API to read the text aloud.

---

## Example Code Snippets

### **Fetch Translation**

let url = `https://api.mymemory.translated.net/get?q=${fromText.value}&langpair=${fromLang.value}|${toLang.value}`;

fetch(url)
    .then(res => res.json())
    .then(data => {
        toText.value = data.responseData.translatedText;
    });
    
### **Text-to-Speech**
let speech = new SpeechSynthesisUtterance(fromText.value);
speech.lang = fromLang.value;
speechSynthesis.speak(speech);

### **Swap Logic**
let temp = fromLang.value;
fromLang.value = toLang.value;
toLang.value = temp;

## How to Run
1. Clone or download the project

git clone https://github.com/your-username/translator-app.git

2. Open the project folder

3. Open index.html in any modern browser

4. Start typing text and translate instantly

No installations or dependencies required.

## Requirements
A modern browser (Chrome, Firefox, Edge, Safari)

Internet connection (for API requests & speech synthesis voices)

## Possible Improvements
Add auto-detection of input language

Add history or saved translations

Add dark/light themes

Improve mobile responsiveness

Add translation copy button

## License
This project currently has no license.

## Acknowledgements
Translation API: MyMemory Translated

Icons: Font Awesome

Uses native browser SpeechSynthesis API

