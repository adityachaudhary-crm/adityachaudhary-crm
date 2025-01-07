### LWC is based on Web Component.  

In the below code, the HTML is attached inline. In LWC, the HTML is read from .html file - I belive the logic is in in the LightningElement. 

```
// 1. Define the custom class
class MyCustomDiv extends HTMLElement {
    constructor() {
        super(); // Always call `super()` in the constructor of a custom element
        const shadowRoot = this.attachShadow({ mode: 'open' });
        shadowRoot.innerHTML = `
            <style>
                h1 {
                    color: blue;
                    font-family: Arial, sans-serif;
                }
            </style>
            <h1>Hello from MyCustomDiv!</h1>
        `;
    }
}

// 2. Register the custom element
customElements.define('my-custom-div', MyCustomDiv);

// 3. Use the custom element in HTML
document.body.innerHTML = '<my-custom-div></my-custom-div>';
````

When the browser processes the <my-custom-div> tag, it:
	1.	Creates an instance of MyCustomDiv.
	2.	Calls its constructor(), attaching a shadow DOM and adding styles and content to it.
	3.	Displays the result.
