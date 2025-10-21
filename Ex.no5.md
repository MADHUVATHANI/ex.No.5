# Ex05 Image Carousel
## Date:21-11-2025
## Name:MADHUVATHANI V
## Reg.no: 212223040107

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
App.js
```
import React, { useState } from 'react'; 
import './App.css';
import { evaluate } from 'mathjs';

function App() {
  const [input, setInput] = useState('');

  const handleClick = (value) => {
    if (value === 'AC') {
      setInput('');
    } else if (value === '⌫') {
      setInput(input.slice(0, -1));
    } else if (value === '=') {
      try {
        setInput(evaluate(input).toString());
      } catch {
        setInput('Error');
      }
    } else {
      setInput((prev) => prev + value);
    }
  };

  const buttons = [
    'AC', '⌫', '%', '/',
    '7', '8', '9', '*',
    '4', '5', '6', '-',
    '1', '2', '3', '+',
    '00', '0', '.', '='
  ];

  return (
    <div className="calculator">
      <div className="display">{input || '0'}</div>
      <div className="buttons">
        {buttons.map((btn, i) => (
          <button
            key={i}
            className={`button 
              ${btn === '=' ? 'equal' : ''} 
              ${btn === 'AC' || btn === '⌫' ? 'special' : ''}`}
            onClick={() => handleClick(btn)}
          >
            {btn}
          </button>
        ))}
      </div>
    </div>
  );
}

export default App;
```
App.css
```
.calculator {
  max-width: 320px;
  margin: 50px auto;
  border-radius: 20px;
  box-shadow: 0px 10px 25px rgba(0, 0, 0, 0.2);
  overflow: hidden;
  background-color: #1c1c1c;
  color: white;
  font-family: 'Arial', sans-serif;
}

.display {
  background-color: #1c1c1c;
  padding: 20px;
  font-size: 2.5em;
  text-align: right;
  color: white;
  min-height: 80px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

.button {
  padding: 25px;
  font-size: 1.5em;
  border: 1px solid #333;
  background-color: #505050;
  color: white;
  cursor: pointer;
}

.button:nth-child(4n) {
  background-color: #ff9500;
  color: white;
}

.button.equal {
  background-color: #28a745;
  color: white;
}

.button:nth-child(-n+3) {
  background-color: #d4d4d2;
  color: black;
}

.button:active {
  opacity: 0.8;
}
```


## OUTPUT

<img width="1427" height="701" alt="image" src="https://github.com/user-attachments/assets/ef4ab193-5fa3-4b7d-bd8e-605d7d16ce50" />

<img width="1424" height="728" alt="image" src="https://github.com/user-attachments/assets/e4f87454-fd46-4864-a121-31346b5d44cd" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
