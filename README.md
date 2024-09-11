---

# Bank Note Authentication - FastAPI Project

This project implements a **Bank Note Authentication** system using a **Random Forest Classifier**, achieving 98% accuracy on the provided dataset. The system classifies whether a bank note is authentic or fake based on features such as variance, skewness, curtosis, and entropy of the note.

## Features:
- **FastAPI** for high-performance API creation and deployment.
- **Pydantic** for data validation and model structuring.
- **Random Forest Classifier** model trained to classify bank notes with 98% accuracy.
- API interaction via **Swagger UI** (built-in with FastAPI) for testing endpoints without a front-end.

---

## File Structure:
```bash
├── BankNote_Authentication.csv   # Dataset used for model training
├── BankNotes.py                  # Pydantic model for request validation
├── ModelTraining.ipynb           # Jupyter notebook for model training
├── Procfile                      # For deployment, e.g., Heroku
├── README.md                     # Project documentation
├── app.py                        # FastAPI app with routes for predictions
├── classifier.pkl                # Trained Random Forest model
├── main.py                       # (Optional) Entry point for the app
├── requirements.txt              # Dependencies for the project
```

---

## Setup Instructions:

### Step 1: Clone the Repository
First, clone this repository to your local machine.
```bash
git clone https://github.com/your-username/bank-note-authentication.git
cd bank-note-authentication
```

### Step 2: Install Dependencies
Install the required libraries using the `requirements.txt` file.
```bash
pip install -r requirements.txt
```

Dependencies include:
- FastAPI
- Pydantic
- Uvicorn (for running the server)
- Scikit-learn (for the Random Forest Classifier)
- Pandas (for data manipulation)
- Numpy (for numerical operations)

### Step 3: Train the Model (Optional)
The pre-trained model `classifier.pkl` is provided. However, if you want to retrain the model, open the **`ModelTraining.ipynb`** file in Jupyter Notebook and execute the cells to train a new Random Forest Classifier.

### Step 4: Run the FastAPI Application
Run the FastAPI application using Uvicorn.
```bash
uvicorn app:app --reload
```
The server will start at **`http://127.0.0.1:8000`** by default.

### Step 5: Interact with the API using Swagger UI
FastAPI automatically generates an interactive API documentation using **Swagger UI**, where you can test the API endpoints without needing a front-end.

To access it:
1. Open your browser and go to: **`http://127.0.0.1:8000/docs`**.
2. Use the provided interface to interact with the API, test predictions, and view responses.

---

## API Endpoints:

### 1. Index Route
**GET /**

This route returns a simple welcome message.
```json
{
  "message": "Hello, World"
}
```

### 2. Name Route
**GET /{name}**

This route takes a name as a path parameter and returns a personalized message.
```json
{
  "Verify your Bank Note ": "John"
}
```

### 3. Prediction Route
**POST /predict**

This route accepts a JSON payload containing the features of the bank note (variance, skewness, curtosis, entropy) and returns whether the note is authentic or fake.

#### Request Body:
```json
{
  "variance": 2.3,
  "skewness": 4.5,
  "curtosis": -0.7,
  "entropy": 1.2
}
```

#### Response:
```json
{
  "prediction": "Fake note"
}
```

- The prediction is based on the **Random Forest Classifier**.
- If the result is positive (`> 0.5`), it will return `"Fake note"`, otherwise `"It's a Bank note"`.

---

## Model Details:
- The model used is a **Random Forest Classifier** trained on the Bank Note Authentication dataset.
- It achieves **98% accuracy** on the test data.
- The model is saved as `classifier.pkl` and loaded during API runtime for predictions.

---

## Deployment (Optional):

### Deploying on Heroku:
You can easily deploy this project to platforms like Heroku. The **`Procfile`** included in the repository defines the commands to run the app.

1. Login to Heroku and create a new application.
2. Push your code to Heroku by linking your GitHub repo.
3. Heroku will automatically detect the **`Procfile`** and set up the environment.

### Running Locally:
You can run the project locally using the instructions above, or use Docker for containerized deployment.

---

## Conclusion:
This **Bank Note Authentication** project is a simple and efficient solution for classifying banknotes using a machine learning model. By using **FastAPI**, it ensures a fast and scalable API, while **Pydantic** provides robust validation. The lack of a frontend is compensated by FastAPI's automatic **Swagger UI**, which allows for seamless interaction with the API endpoints.

Feel free to fork this project and contribute!

---
