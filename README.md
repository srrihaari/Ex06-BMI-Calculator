# Ex06 BMI Calculator
## Date:

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
app.jsx
~~~
import { Routes, Route, Link } from 'react-router-dom';
import BMICalculator from './BMICalculator';

function App() {
  return (
    <div>
      <BMICalculator/>
    </div>
  );
}
export default App;
~~~
BMI calculator.jsx
~~~

import React, { useState } from 'react';

const BMICalculator = () => {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (!weight || !height) return;

    const heightInMeters = height / 100;
    const bmiValue = weight / (heightInMeters * heightInMeters);
    setBmi(bmiValue.toFixed(2));

    if (bmiValue < 18.5) setCategory('Underweight');
    else if (bmiValue < 24.9) setCategory('Normal weight');
    else if (bmiValue < 29.9) setCategory('Overweight');
    else setCategory('Obesity');
  };

  return (
    <div className="bmi-container">
      <h2>BMI Calculator</h2>
      <div className="bmi-form">
        <input
          type="number"
          placeholder="Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
        <input
          type="number"
          placeholder="Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
        <button onClick={calculateBMI}>Calculate BMI</button>
      </div>

      {bmi && (
        <div className="bmi-result">
          <p>Your BMI: <strong>{bmi}</strong></p>
          <p>Category: <strong>{category}</strong></p>
        </div>
      )}
    </div>
  );
};
export default BMICalculator;
~~~
index.css
~~~
.bmi-container {
  max-width: 400px;
  margin: 40px auto;
  background: #ffffff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  font-family: 'Segoe UI', sans-serif;
}

.bmi-container h2 {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

.bmi-form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.bmi-form input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-size: 1rem;
}

.bmi-form button {
  padding: 12px;
  background-color: #007bff;
  border: none;
  border-radius: 6px;
  color: white;
  font-size: 1rem;
  cursor: pointer;
  transition: background 0.3s;
}

.bmi-form button:hover {
  background-color: #0056b3;
}

.bmi-result {
  margin-top: 20px;
  padding: 15px;
  background-color: #f9f9f9;
  border-left: 4px solid #007bff;
  border-radius: 6px;
  font-size: 1.1rem;
}
~~~
## OUTPUT
<img width="1902" height="1018" alt="439818656-8f45954a-45f6-4c83-80f5-3729b2203a82" src="https://github.com/user-attachments/assets/4a8bfc86-5c7e-43fe-aa54-c90441266894" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
