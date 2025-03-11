Here is the **README.md** file for your entire project, including **setup, deployment, API usage, and Docker instructions**.

---

### **README.md - House Price Prediction API**
```md
# 🏡 House Price Prediction API

This project is a **machine learning-powered API** that predicts **house prices** based on various features. It is built using **FastAPI** and trained on the **California Housing Dataset** with a **Random Forest Regressor**. The API allows users to send house data and receive a predicted price.

---

## 🚀 Features
✅ **Preprocessed dataset with feature scaling**  
✅ **Trained & optimized Random Forest model** using `GridSearchCV`  
✅ **REST API built with FastAPI**  
✅ **Supports Docker containerization** for easy deployment  
✅ **Cloud-Ready** (Can be deployed on AWS, Render, or Heroku)  

---

## 📂 Project Structure
```
├── app.py                    # FastAPI application
├── house_price_prediction.ipynb # Jupyter Notebook for training
├── house_price_model.pkl      # Trained ML model
├── scaler.pkl                 # Scaler for input data
├── requirements.txt           # List of required dependencies
├── Dockerfile                 # Docker configuration for deployment
└── README.md                  # Documentation (this file)
```

---

## 🛠️ Setup & Installation

### **1️⃣ Install Dependencies**
First, install the required Python libraries:
```bash
pip install -r requirements.txt
```

---

### **2️⃣ Train the Model**
Before running the API, you need to **train the model**.

#### **Run the Jupyter Notebook**
1. Open `house_price_prediction.ipynb` and execute all cells.
2. This will **train the Random Forest model** and **save it as `house_price_model.pkl`**.
3. The scaler used for feature transformation will also be saved as `scaler.pkl`.

---

### **3️⃣ Running the API Locally**
Start the FastAPI server:
```bash
uvicorn app:app --reload
```
Now, your API is running at **http://127.0.0.1:8000**.

#### **Test the API**
Use **Postman** or **cURL** to send a request:
```bash
curl -X 'POST' 'http://127.0.0.1:8000/predict' \
     -H 'Content-Type: application/json' \
     -d '{"MedInc": 3.5, "HouseAge": 20, "AveRooms": 5, "AveBedrms": 1, "Population": 500, "AveOccup": 3, "Latitude": 34.5, "Longitude": -118.3}'
```
Alternatively, open **http://127.0.0.1:8000/docs** in a browser to test via Swagger UI.

---

## 🐳 Deploy with Docker (Recommended)
To run the API inside a **Docker container**, follow these steps:

### **1️⃣ Build the Docker Image**
```bash
docker build -t house-price-api .
```

### **2️⃣ Run the Docker Container**
```bash
docker run -p 8000:8000 house-price-api
```
Now, your API is accessible at **http://127.0.0.1:8000**.

---

## ☁️ Deploying to the Cloud

### **Option 1: AWS EC2 Deployment**
1. **Launch an AWS EC2 instance** (Ubuntu recommended).
2. **Install Docker on EC2**:
   ```bash
   sudo apt update && sudo apt install -y docker.io
   ```
3. **Copy your project files to EC2** using SCP:
   ```bash
   scp -i your-key.pem -r /your-local-project-folder ubuntu@your-ec2-ip:/home/ubuntu/
   ```
4. **SSH into EC2**:
   ```bash
   ssh -i your-key.pem ubuntu@your-ec2-ip
   cd /home/ubuntu/your-local-project-folder
   ```
5. **Build and run Docker container**:
   ```bash
   docker build -t house-price-api .
   docker run -d -p 8000:8000 house-price-api
   ```
6. **Access your API** at:
   ```bash
   http://your-ec2-ip:8000
   ```

---

### **Option 2: Deploy to Render (Easiest)**
1. **Go to** [Render](https://dashboard.render.com/).
2. **Click "New Web Service"**.
3. **Connect your GitHub repository**.
4. **Set the runtime environment to** `Python 3.x`.
5. **Start command**:
   ```bash
   uvicorn app:app --host 0.0.0.0 --port 10000
   ```
6. **Deploy**, and Render will provide a public URL.

---

### **Option 3: Deploy to Heroku**
1. **Install the Heroku CLI** ([Download Here](https://devcenter.heroku.com/articles/heroku-cli)).
2. **Login to Heroku**:
   ```bash
   heroku login
   ```
3. **Create a new app**:
   ```bash
   heroku create house-price-api
   ```
4. **Deploy with Git**:
   ```bash
   git init
   git add .
   git commit -m "Deploy FastAPI app"
   git push heroku main
   ```
5. **Open the API**:
   ```bash
   heroku open
   ```

---

## 🎯 **API Endpoints**
### **1️⃣ Root Endpoint**
- **URL:** `GET /`
- **Response:**
  ```json
  { "message": "House Price Prediction API is running" }
  ```

### **2️⃣ House Price Prediction**
- **URL:** `POST /predict`
- **Request Body (JSON):**
  ```json
  {
    "MedInc": 3.5,
    "HouseAge": 20,
    "AveRooms": 5,
    "AveBedrms": 1,
    "Population": 500,
    "AveOccup": 3,
    "Latitude": 34.5,
    "Longitude": -118.3
  }
  ```
- **Response:**
  ```json
  { "predicted_price": 240000.0 }
  ```

---

## 📌 **Troubleshooting**
### **1️⃣ FastAPI Import Errors**
If you see:
```python
ImportError: cannot import name 'Doc' from 'typing_extensions'
```
Run:
```bash
pip install --upgrade typing_extensions
pip install --upgrade fastapi
```

### **2️⃣ Docker Port Issues**
If **Docker is not working**, make sure **port 8000** is available:
```bash
docker ps  # Check running containers
docker stop <container_id>  # Stop any process using port 8000
```

### **3️⃣ API Not Working on Cloud**
- For AWS EC2, check if your **Security Group** allows **port 8000**:
  ```bash
  sudo ufw allow 8000
  ```

---

## 🔥 **Project Summary**
- ✅ **Machine Learning**: RandomForestRegressor for house price prediction.
- ✅ **Model Optimization**: GridSearchCV for best hyperparameters.
- ✅ **API Deployment**: FastAPI for real-time predictions.
- ✅ **Docker & Cloud Ready**: Easily deployable to **AWS, Render, or Heroku**.

**Now, you have a fully functional API for house price prediction! 🚀🏡**

---
```

This **README.md** provides all the steps for **installation, training, running locally, Docker deployment, cloud deployment, API usage, and troubleshooting**.

Let me know if you need modifications! 🚀🎯
