# new
[
  {
    "name": "Northeast Distributors",
    "shipped_last_month": 1200,
    "forecast_next_month": 1350,
    "avg_ytd": 1150,
    "health_status": "Healthy",
    "last_shipment_days": 4
  },
  {
    "name": "Midwest Logistics",
    "shipped_last_month": 980,
    "forecast_next_month": 1100,
    "avg_ytd": 1020,
    "health_status": "Warning",
    "last_shipment_days": 6
  }
]

import React from 'react';

interface DistributorProps {
  data: {
    name: string;
    shipped_last_month: number;
    forecast_next_month: number;
    avg_ytd: number;
    health_status: string;
    last_shipment_days: number;
  };
}

const DistributorCard: React.FC<DistributorProps> = ({ data }) => (
  <div className="card">
    <h2>{data.name}</h2>
    <p>Shipped Last Month: {data.shipped_last_month}</p>
    <p>Forecast Next Month: {data.forecast_next_month}</p>
    <p>YTD Avg/Month: {data.avg_ytd}</p>
    <p>Status: {data.health_status}</p>
    <p>Days Since Last Shipment: {data.last_shipment_days}</p>
  </div>
);

export default DistributorCard;

import React from 'react';
import distributors from './data/mockDistributors.json';
import DistributorCard from './components/DistributorCard';
import './App.css';

const App = () => {
  return (
    <div className="app">
      <h1>PepsiCo Augur – Predictive Supply Chain Dashboard</h1>
      <div className="grid">
        {distributors.map((d, index) => (
          <DistributorCard key={index} data={d} />
        ))}
      </div>
    </div>
  );
};

export default App;

.app {
  font-family: sans-serif;
  padding: 2rem;
  background-color: #f7f8fc;
}

h1 {
  text-align: center;
  color: #1b365d;
}

.grid {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 2rem;
}

.card {
  background-color: #fff;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.08);
  width: 280px;
  transition: transform 0.2s ease;
}

.card:hover {
  transform: translateY(-4px);
}

.card h2 {
  margin-bottom: 0.5rem;
  color: #0366d6;
}

import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
