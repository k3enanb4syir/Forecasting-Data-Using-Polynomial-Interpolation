# Weather Forecasting using Polynomial Interpolation

This project, created by Muhammad Keenan Basyir and Keita Kawabata, explores the use of polynomial interpolation (specifically **Newton's Divided Difference method**) to forecast weather temperatures.

Using real-world data from Yogyakarta, we build a polynomial model based on past temperature data to predict the next day's temperature. The notebook also serves as a case study on the significant limitations of using high-degree polynomial extrapolation for time-series forecasting.

## 💡 Key Concepts

* **Polynomial Interpolation:** A method of finding a unique polynomial function that passes exactly through a given set of data points.
* **Newton's Divided Difference:** An algorithm used to construct the interpolating polynomial.
* **Extrapolation:** Using the interpolating polynomial to estimate values *outside* the range of the original data points (i.e., forecasting).
* **Runge's Phenomenon:** A critical problem in numerical analysis where high-degree polynomials used for interpolation can oscillate wildly near the endpoints, leading to highly inaccurate extrapolations.

## 📊 Data Source

The temperature data used in this project was fetched from the **[Visual Crossing Weather API](https://www.visualcrossing.com/)**. The notebook includes the Python code to fetch the average temperature for the past 7 days in Yogyakarta.

## 📈 Methodology and Analysis

The notebook implements Newton's Divided Difference method in Python and runs three experiments to test its forecasting accuracy.

### 1. Code 1 (Low-Degree Polynomial)

* **Data:** 3 days of temperature data (index 0-2).
* **Goal:** Forecast the 4th day (index 3).
* **Result:** The model produced a reasonable forecast (`24.8°C`) with a relatively low **3.125% error** compared to the actual data (`25.6°C`).

### 2. Code 2 (High-Degree Polynomial)

* **Data:** 8 days of temperature data (index 0-7).
* **Goal:** Forecast the 9th day (index 8).
* **Result:** The model failed catastrophically, predicting a temperature of **43.50°C**—a clear outlier. This resulted in a massive **73.3% error** compared to the actual value (`25.1°C`). This is a textbook example of **Runge's phenomenon**.

### 3. Code 3 (Medium-Degree Polynomial)

* **Data:** 5 days of temperature data (index 0-4).
* **Goal:** Forecast the 6th day (index 5).
* **Result:** The forecast (`21.7°C`) was better than the high-degree model but still had a significant **14.9% error** (`vs. 25.5°C`), showing that instability can appear even with medium-degree polynomials.

## 🏁 Conclusion

This project demonstrates that while polynomial interpolation is a powerful mathematical tool for fitting known data, it is an **unreliable and erratic method for extrapolation (forecasting)**, especially when using a high degree.

The key takeaway is that forcing a single, high-degree polynomial to fit all data points makes it highly sensitive and prone to wild oscillations. A more robust approach for forecasting is to use **low-degree polynomials** (like linear or quadratic) on a small, recent subset of the data to capture the *local trend*.

## 🚀 How to Run

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git)
    cd your-repository-name
    ```

2.  **Install dependencies:**
    The only external library used is `requests`.
    ```bash
    pip install requests
    ```

3.  **Get an API Key:**
    * Sign up for a free account at [Visual Crossing Weather](https://www.visualcrossing.com/).
    * Get your API key.

4.  **Update the notebook:**
    * Open `forecasting-data-using-polynomial-interpolation.ipynb`.
    * In the first code cell, replace the placeholder `API_KEY` with your own key:
      ```python
      API_KEY = 'YOUR_OWN_API_KEY_HERE'
      ```

5.  **Run the cells:**
    You can now run the cells in the notebook (e.g., in VS Code, Jupyter Lab, or Google Colab) to fetch live data and see the interpolation results.

    **Note:** Your results will differ from the notebook's static data as you will be fetching current weather data.

## 👥 Authors

* Muhammad Keenan Basyir
* Keita Kawabata
