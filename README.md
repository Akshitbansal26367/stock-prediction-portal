# Stock Prediction Portal

A full-stack web application for stock analysis and prediction using a Django REST API backend, TensorFlow/Keras model inference, and a React frontend.

## Features

- Fetch historical stock data using `yfinance`
- Plot:
- Closing price
- 100-day moving average (DMA)
- 200-day moving average (DMA)
- Run model-based price prediction from a pretrained `.keras` model
- Return plot image URLs and evaluation metrics from the backend API
- JWT-based authentication endpoints (register, login token, refresh token, protected route)

## Tech Stack

### Backend

- Django
- Django REST Framework
- TensorFlow / Keras
- Pandas, NumPy, Matplotlib, scikit-learn
- yfinance

### Frontend

- React
- Axios

## Project Structure

```text
stock-prediction-portal/
|-- backend-drf/
|   |-- accounts/
|   |-- api/
|   |-- stock_prediction_main/
|   |-- manage.py
|   `-- stock_prediction_model.keras
|-- frontend-react/
|-- Resources/
|-- requirements.txt
|-- .gitignore
`-- README.md
```

## Setup

### 1. Clone repository

```bash
git clone https://github.com/Akshitbansal26367/stock-prediction-portal.git
cd stock-prediction-portal
```

### 2. Backend setup

Create and activate environment:

```bash
conda create -n tfenv python=3.10
conda activate tfenv
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create `.env` at `backend-drf/.env`:

```env
SECRET_KEY=your_secret_key
DEBUG=True
```

Run backend:

```bash
cd backend-drf
python manage.py migrate
python manage.py runserver
```

### 3. Frontend setup

```bash
cd frontend-react
npm install
npm start
```

## API

Base path: `/api/v1/`

### Prediction

Endpoint: `POST /api/v1/predict/`

Request body:

```json
{
  "ticker": "AAPL"
}
```

Sample success response:

```json
{
  "status": "success",
  "plot_img": "/media/AAPL_plot.png",
  "plot_100_dma": "/media/AAPL_100_dma.png",
  "plot_200_dma": "/media/AAPL_200_dma.png",
  "plot_prediction": "/media/AAPL_final_prediction.png",
  "mse": 0.0,
  "rmse": 0.0,
  "r2": 0.0
}
```

### Authentication

- `POST /api/v1/register/`
- `POST /api/v1/token/`
- `POST /api/v1/token/refresh/`
- `GET /api/v1/protected-view/`

## Model Details

- Model framework: TensorFlow/Keras
- Model file path: `backend-drf/stock_prediction_model.keras`
- Input source: Historical close-price data fetched via `yfinance`

## Notes

- Use Python 3.10 for TensorFlow compatibility.
- Ensure `stock_prediction_model.keras` exists before running prediction API.
- Start backend before using the frontend.

## Contributing

Contributions are welcome. Fork the repository and open a pull request.

## 📄 License

This project is open-source and available under the MIT License.

---

## 👨‍💻 Author

**Akshit Bansal**

---

## ⭐ Support

If you like this project, consider giving it a ⭐ on GitHub!