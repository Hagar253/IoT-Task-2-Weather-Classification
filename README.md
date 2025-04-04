# TinyML-Based Weather Classification Using DHT Sensor

## Project Overview
This project demonstrates a lightweight machine learning solution that classifies weather conditions as 'Sunny' or 'Cold' using real-time temperature and humidity data from a DHT22 sensor. The model is optimized for resource-constrained devices using TinyML and deployed on an ESP32 microcontroller. Predictions can also be visualized on a Node-RED dashboard via MQTT.

---

## Requirements

### Hardware
- ESP32 Microcontroller
- DHT22 Sensor

### Software
- Arduino IDE or PlatformIO
- TensorFlow Lite
- Node-RED (optional for visualization)

### Libraries
- `DHT.h` for sensor readings
- `EloquentTinyML.h` for machine learning operations

---

## Data Preparation

1. **Weather Dataset**: Weather data (temperature, humidity, and labels) is loaded from a CSV file (`Weather_Data.csv`).
2. **Data Processing**: 
   - Missing values were handled.
   - Features were scaled using `StandardScaler`.
   - Labels (Sunny/Cold) were encoded numerically.
   - Data was split into training and test sets.

---

## Model Training

1. **Model Architecture**: A lightweight neural network with 3 layers:
   - Input layer with 16 neurons (ReLU activation)
   - Hidden layer with 8 neurons (ReLU activation)
   - Output layer with 1 neuron (Sigmoid activation)
   
2. **Compilation**: 
   - Adam optimizer
   - Binary cross-entropy loss
   - Accuracy metric
   
3. **Training**: The model was trained for up to 30 epochs with early stopping to prevent overfitting.

---

## Model Evaluation

1. **Test Set Evaluation**: The trained model's performance was evaluated using the test set, generating loss and accuracy metrics.
2. **Classification Report**: Precision, recall, F1-score, and support for each class (Sunny/Cold).
3. **Confusion Matrix**: Visualized the model's predictions against actual labels.

---

## Model Quantization and Deployment

1. **Optimization**: The model was optimized for size and latency using representative data.
2. **TFLite Conversion**: The trained model was converted to a TensorFlow Lite (TFLite) format.
3. **C Array Conversion**: The TFLite model was converted to a C array for embedding into the ESP32 application.

---

## ESP32 Deployment

1. **Sensor Setup**: DHT22 sensor is connected to GPIO 4 on the ESP32.
2. **Model Loading**: The optimized TFLite model is loaded and initialized using the `EloquentTinyML` library.
3. **Real-Time Prediction**: The model classifies the weather as 'Sunny' or 'Cold' based on the temperature and humidity values read from the sensor.
4. **Error Handling**: If the sensor fails to provide valid data, an error message is shown.

---

## Result Visualization (Optional)

- **Node-RED Dashboard**: Visualize the predicted weather data (Sunny/Cold) via MQTT on a Node-RED dashboard.

---

## Running the Project

1. Connect the DHT22 sensor to your ESP32.
2. Upload the code to the ESP32 using Arduino IDE or PlatformIO.
3. Monitor the serial output to see real-time weather predictions based on temperature and humidity.

---

## License

This project is licensed under the MIT License.

---

## Contributions

Feel free to contribute, and let me know if you have any questions!
