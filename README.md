⭐ Stock Star — Stock Market Simulator

Stock Star is a web-based stock market simulation application designed to help users explore stock prices, practise buying and selling stocks, and monitor a virtual investment portfolio without using real money.

The project combines a React.js frontend with a Python Flask backend and uses Yahoo Finance data through the `yfinance` library to retrieve stock prices.

Disclaimer: Stock Star is an educational project. It does not execute real stock market transactions or connect to a brokerage account.

🚀 Features

- Stock Watchlist: Displays a predefined list of 12 Indian stocks.
- Stock Price Retrieval: Fetches stock-price data using Yahoo Finance through `yfinance`.
- Virtual Trading: Simulates stock purchases and sales using virtual money.
- Virtual Balance: Starts with a simulated balance of ₹100,000.
- Portfolio Management: Tracks stock symbols, quantities and average purchase prices.
- Profit and Loss Tracking: Calculates unrealized profit or loss using the latest retrieved stock prices.
- Dynamic Interface: Uses React state to update the displayed balance and holdings following simulated trades.
- Flask REST API: Provides endpoints for retrieving prices and managing a separate in-memory portfolio.

🛠️ Technology Stack
| Technology | Purpose |
|---|---|
| React.js | Frontend user interface |
| JavaScript | Application logic |
| HTML5 and CSS3 | Structure and styling |
| Python | Backend programming |
| Flask | Backend REST API |
| Flask-CORS | Cross-origin communication |
| yfinance | Stock-price data retrieval |
| Node.js and npm | Frontend runtime and package management |
| Git and GitHub | Version control and source-code hosting |

📂 Project Structure

stock-star/
├── backend/
│   ├── app.py
│   └── requirements.txt
│
├── frontend/
│   ├── public/
│   │   ├── index.html
│   │   ├── logo.png
│   │   └── manifest.json
│   │
│   ├── src/
│   │   ├── App.js
│   │   ├── App.css
│   │   ├── api.js
│   │   ├── index.js
│   │   ├── index.css
│   │   ├── assets/
│   │   │   └── logo.png
│   │   ├── components/
│   │   │   └── Navbar.js
│   │   ├── context/
│   │   │   └── PortfolioContext.js
│   │   └── pages/
│   │       ├── Home.js
│   │       ├── Stocks.js
│   │       └── Portfolio.js
│   │
│   ├── package.json
│   └── package-lock.json
│
└── README.md
```

⚙️ Getting Started

Follow these steps to run Stock Star locally.
Prerequisites
Install the following software:
- [Python](https://www.python.org/downloads/)
- [Node.js and npm](https://nodejs.org/)
- [Visual Studio Code](https://code.visualstudio.com/) (recommended)
Git is optional if you download the repository as a ZIP file.

1. Clone the Repository
Open a terminal and run:
```bash
git clone https://github.com/sagargowda321/stock-star.git
cd stock-star
```
Alternatively, download the repository ZIP from GitHub and extract it.

2. Set Up the Backend
Open a terminal in the project root and navigate to the backend directory:
```bash
cd backend
```
Create a Python virtual environment:
```bash
python -m venv venv
```
Activate it on Windows Command Prompt:
```cmd
venv\Scripts\activate.bat
```
On Windows PowerShell:
```powershell
.\venv\Scripts\Activate.ps1
```
Install the backend dependencies:
```bash
python -m pip install -r requirements.txt
```
Start the Flask server:
```bash
python app.py
```
The backend should start at:
`http://127.0.0.1:5000`
Keep this terminal running.

3. Set Up the Frontend
Open a second terminal and navigate to the frontend directory from the project root:
```bash
cd frontend
```
Install the Node.js dependencies:
```bash
npm install
```
Start the React development server:
```bash
npm start
```

The application should open at:
`http://localhost:3000`
Keep both terminals running while using the application.

📈 Default Stock Watchlist
The Stocks page includes the following Indian stock symbols:
| Company | Yahoo Finance Symbol |
|---|---|
| Tata Consultancy Services | `TCS.NS` |
| Infosys | `INFY.NS` |
| Reliance Industries | `RELIANCE.NS` |
| HDFC Bank | `HDFCBANK.NS` |
| ICICI Bank | `ICICIBANK.NS` |
| Larsen & Toubro | `LT.NS` |
| State Bank of India | `SBIN.NS` |
| HCL Technologies | `HCLTECH.NS` |
| Kotak Mahindra Bank | `KOTAKBANK.NS` |
| Maruti Suzuki | `MARUTI.NS` |
| HDFC Ltd. | `HDFC.NS` |
| Axis Bank | `AXISBANK.NS` |
Note: The symbols are hardcoded in the application. Some symbols may be outdated or unavailable, and price retrieval depends on Yahoo Finance data availability.

🔄 How It Works
Frontend
The React application provides three main pages:

- Home: Displays the Stock Star welcome screen.
- Stocks: Displays the predefined watchlist, retrieved prices, virtual balance and buy/sell controls.
- Portfolio: Displays simulated holdings, average purchase prices and calculated profit/loss.

React Context manages the frontend's virtual balance and portfolio state.

 Backend
The Flask application retrieves stock prices and exposes REST API endpoints.
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/stocks/<symbol>` | Retrieves the latest available closing price for a stock symbol |
| POST | `/buy` | Simulates purchasing shares in the backend portfolio |
| POST | `/sell` | Simulates selling shares from the backend portfolio |
| GET | `/portfolio` | Returns the backend virtual balance and portfolio with price-based calculations |

Example price request:

```http
GET /stocks/RELIANCE.NS
```

Example successful response:

```json
{
  "symbol": "RELIANCE.NS",
  "price": 1400.00
}
```

The price shown is illustrative and is not a live quote.

Example purchase request:

```http
POST /buy
Content-Type: application/json
```

```json
{
  "symbol": "TCS.NS",
  "quantity": 2
}
```
The backend calculates the purchase cost, checks the virtual balance and updates its in-memory portfolio.

 Data Flow
User
  |
  v
React Frontend
  |
  v
Stock Watchlist and Portfolio UI
  |
  +----> Flask API ----> Yahoo Finance (yfinance)
  |           |
  |           v
  |      Backend Portfolio
  |
  +----> React Context
              |
              v
       Frontend Virtual Portfolio
```

Implementation note: The current frontend trading actions update React Context directly. They are not yet integrated with the Flask `/buy` and `/sell` endpoints. The backend and frontend therefore maintain separate in-memory trading states.

🧮 Virtual Trading Calculations
The simulator uses the following calculations:

Purchase cost
`Purchase Cost = Stock Price × Quantity`

Average purchase price
`Average Price = Total Purchase Cost ÷ Total Shares Held`

Unrealized profit or loss
`P/L = (Current Price − Average Purchase Price) × Quantity Held`
These calculations are intended for educational simulation and do not include brokerage fees, taxes, slippage or other transaction costs.

⚠️ Current Limitations
- No authentication: Login and signup functionality are not implemented.
- No persistent database: Virtual balances and holdings are stored in memory or React state and reset when the relevant application state is recreated.
- Separate trading states: Frontend trades do not update the Flask backend portfolio.
- Local API configuration: The frontend currently requests data from `http://127.0.0.1:5000`, so it is not configured for remote production use.
- Market-data dependency: Price retrieval depends on Yahoo Finance availability and may return errors or delayed data.
- Basic validation: The trading logic needs stronger input validation and error handling before wider use.
- Deployment: Production hosting and deployment have not been verified.

🔮 Future Improvements
- Integrate frontend trading actions with Flask API endpoints.
- Add a persistent database such as PostgreSQL or SQLite.
- Implement user registration, login and individual portfolios.
- Improve order validation, error handling and transaction consistency.
- Add stock search, customizable watchlists and historical price charts.
- Improve price caching and API request efficiency.
- Configure environment variables and production API URLs.
- Add automated testing and deploy the frontend and backend.

🎯 Project Objective
The objective of Stock Star is to provide a practical learning environment for understanding stock prices, simulated trading, portfolio tracking and profit/loss calculations while applying full-stack web development concepts.

👨‍💻 Author
Sagar S
Computer Science Engineering Student | Interested in Software Development, Financial Markets and FinTech.

📄 License
No license has been specified for this repository yet. If you intend to make the project open source, choose an appropriate license and add a `LICENSE` file.
Built with React.js, Python, Flask and yfinance.
