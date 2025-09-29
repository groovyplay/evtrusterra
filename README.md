Local directory structure matches this:/trusterra-prototype
├── main.py
├── requirements.txt
├── sample_input.json
└── src/
├── models.py
└── pipeline.py

Commands:

1. Create virtual env

"mkdir trusterra-prototype"
"python3 -m venv path/to/venv.py"
"source path/to/venv/bin/activate"


2. Setup and Installation Ensure Python (3.8+) is installed.Install dependencies using the provided requirements.

"pip install -r requirements.txt"

3. Running the Prototype

You have two primary ways to test the functionality: API Mode (recommended for testing the full interface) or CLI Mode (for quick logic testing).

Option A: Running the Lightweight API (Recommended)

This launches the FastAPI service, making the prediction endpoint available and exposing the interactive documentation.

1. Run the API Server:

"uvicorn main:app --reload"

(The --reload flag is useful during development.)

2. Access the Documentation:

Once the server starts (you should see the address in your terminal, e.g., http://127.0.0.1:8000),
open your web browser and navigate to:[http://127.0.0.1:8000/docs]

Use the interactive Swagger UI here to test the /v1/predict endpoint by providing the content of sample_input.json as the request body.

Option B: Run on CLI/terminal

"python main.py"                 

--- Running CLI Test with sample_input.json ---

Input Data:
{
  "vehicle_id": "KA-51LS-5486",
  "mileage_km": 110000.0,
  "current_soh": 0.72,
  "fast_charge_ratio": 0.45,
  "avg_temp_c": 35.5,
  "age_years": 4.5
}

Prediction Output:
{
  "predicted_rul_months": 63,
  "predicted_rv_usd": 27091,
  "explanation_text": "The predicted Remaining Useful Life (RUL) of **63 months** and Residual Value (RV) of **27,091** are primarily driven by a high ratio of DC fast charging events, the vehicle's relatively high mileage, the current State of Health (SOH) of the battery. Our model scientifically links these factors, especially battery SOH and charging habits, to market value, providing a transparent valuation.",
  "model_version": "v1.0.0-hybrid-sim"
}
