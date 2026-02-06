# 360° example

Here is you find a code snippet for our 360° images to use as a spinner.

{% embed url="https://jsfiddle.net/edwardbrosens/dewf15ps/224/" %}

```html
<input type="range" min="0" value="0" class="slider" id="angleSlider" />
<div id="imagesContainer" />
```

```javascript
	// Setup
const customerId = "your-customer-id";

// Example url for the Abarth 124-spider
const cdnUrl = `https://cdn.imagin.studio/getImage?customer=${customerId}&make=abarth&modelFamily=124-spider&modelRange=124-spider&modelVariant=ca&bodySize=2&modelYear=2018`;
const angles = ["200", "201", "202", "203", "204", "205", "206", "207", "208", "209", "210", "211", "212", "213", "214", "215", "216", "217", "218", "219", "220", "221", "222", "223", "224", "225", "226", "227", "228", "229", "230", "231"];

// Select elements
const sliderElement = document.getElementById("angleSlider");
const imagesContainerElement = document.getElementById("imagesContainer");
const images = [];


// Initialization
const init = () => {
		
    // clear the images array
    images.length = 0;
    
    // create the images
    angles.reverse().forEach((angle, index) => {
      const img = document.createElement("img");
      img.src = `${cdnUrl}&angle=${angle}`;
      img.classList.add("image");
      if (index === 0) {
	      img.classList.add("current");
      }
      images.push(img);
    	imagesContainerElement.appendChild(img);
    });
    sliderElement.setAttribute("max", angles.length -1);
    sliderElement.oninput = (e) => {
    	handleUpdate(e.currentTarget.value);
    };
};

const handleUpdate = (value) => {
		const intValue = parseInt(value, 10);
		images.forEach((image, index) => {
    	if (index === intValue) {
      	image.classList.add("current");
      } else {
      	image.classList.remove("current");
      }
    });
};

init();
```

```css
#imagesContainer {
  position: relative;
}

img.image {
  position: absolute;
  visibility: hidden;
  max-width: 300px;
}
img.image.current {
  visibility: visible;
}
```
