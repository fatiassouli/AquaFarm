# 🌱 AquaFarm

> **AI-Powered Smart Irrigation & Agricultural Decision Support Platform**

**AquaFarm** is an intelligent irrigation decision-support application developed as part of a Master's degree in Artificial Intelligence. It leverages an **XGBoost classification model** to estimate the irrigation requirements of agricultural plots, categorizing them into three levels: **Low, Medium, or High**.

By combining agronomic parameters, environmental conditions, and real-time weather data, AquaFarm provides an interactive platform to support smarter and more informed irrigation decisions.

## ✨ Key Features

- 🔬 **Manual ML Prediction:** Estimate irrigation requirements using agronomic and environmental parameters.
- 🌦️ **Weather-Based Prediction:** Integrate real-time weather data through the OpenWeather API.
- 📂 **Batch Prediction:** Process multiple agricultural records using CSV file uploads.
- 📊 **Prediction Probabilities:** Visualize classification probabilities and irrigation risk levels with Plotly.
- 🏆 **Feature Importance:** Explore the most influential variables using XGBoost feature importance.
- 📜 **Prediction History:** Track predictions throughout the current session.
- 📥 **CSV Export:** Download prediction results for further analysis.
- 🛡️ **Input Validation & Security:** Validate user inputs and securely manage API credentials.
- 🎨 **Interactive Dashboard:** Responsive Streamlit interface with a dedicated agricultural theme.

## 🧠 Machine Learning

AquaFarm uses an **XGBoost classification model** trained to predict the irrigation requirements of agricultural plots.

The prediction pipeline reproduces the preprocessing steps applied during model training:

1. Ordinal encoding of crop growth stages.
2. Binary encoding of mulching.
3. One-hot encoding of categorical variables.
4. Boolean-to-integer conversion.
5. Feature alignment with the original training schema.
6. XGBoost model inference.
7. Custom decision rule: if the predicted probability of the High class exceeds 60% (`P(High) > 0.60`), the final prediction is set to High.

### Output Classes

| Class | Interpretation |
|---|---|
| 💧 Low | Low irrigation requirement |
| 🌿 Medium | Moderate irrigation requirement |
| 🔥 High | High irrigation requirement |

## 🏗️ Project Architecture

```text
aquafarm/
│
├── app.py                         # Streamlit application
├── prediction.py                  # ML preprocessing and inference
├── weather_service.py             # OpenWeather integration
├── cities.py                      # City list
├── config.py                      # Application and ML configuration
├── utils.py                       # Charts, history and exports
│
├── models/
│   ├── irrigation_model.pkl       # Trained XGBoost model
│   └── feature_names.pkl          # Training feature schema
│
├── .streamlit/
│   ├── config.toml                # Streamlit theme/server config
│   └── secrets.toml.example       # Secret configuration template
│
├── screenshots/                   # Application screenshots
├── .gitignore
├── requirements.txt
└── README.md
```

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/fatiassouli/aquafarm.git
cd aquafarm
```

### 2. Create a virtual environment

**Windows**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**Linux / macOS**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure OpenWeather

Create the following file:

```text
.streamlit/secrets.toml
```

Add your API key:

```toml
OPENWEATHER_API_KEY = "YOUR_OPENWEATHER_API_KEY"
```

The file is intentionally excluded from Git and must never be committed to the repository.

### 5. Launch the application

```bash
streamlit run app.py
```

Open your browser at:

```text
http://localhost:8501
```

## ☁️ Deployment

AquaFarm is designed to be deployed using **Streamlit Community Cloud**.

Typical deployment workflow:

```text
GitHub Repository
       ↓
Streamlit Community Cloud
       ↓
Install dependencies
       ↓
Configure application secrets
       ↓
Launch app.py
       ↓
AquaFarm Dashboard
```

For Streamlit Community Cloud, configure `OPENWEATHER_API_KEY` in the application's **Secrets** settings instead of committing `.streamlit/secrets.toml`.

## 🔐 Security

API credentials are deliberately excluded from version control.

- `.streamlit/secrets.toml` is ignored by Git.
- `secrets.toml.example` contains only a placeholder.
- OpenWeather credentials are stored as application secrets.
- API keys must never be hardcoded in Python source files.

> **Important:** If an API key has ever been committed to a public repository, revoke or rotate it through the provider dashboard and replace it with a new key.

## 📌 Project Status

**Status:** Academic & Portfolio Project — Functional Prototype.

AquaFarm demonstrates the practical integration of:

**Artificial Intelligence · Machine Learning · XGBoost · Python · Streamlit · Data Processing · Data Visualization · Weather API Integration**

## 👩‍💻 Author

**Fatima Zahraa Assouli**

Master's Student in Artificial Intelligence  
Faculté des Sciences Ben M'Sik — Casablanca, Morocco.

- **LinkedIn:** https://www.linkedin.com/in/fatima-zahraa-assouli-204008279/
- **GitHub:** https://github.com/fatiassouli

## 📄 License

This project is distributed under the MIT License.
