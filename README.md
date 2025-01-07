import React, { useState, useEffect } from "react";
import ReactDOM from "react-dom";
import "./App.css";

// Mock Data
const betsData = [
  { OutcomeName: "Chiefs to Win Super Bowl", Odds: "+500", ListedPrice: 25 },
  { OutcomeName: "Bills to Win Super Bowl", Odds: "+400", ListedPrice: 30 },
];
const portfoliosData = [
  { OutcomeName: "Packers to Win Super Bowl", NumberOfSharesHeld: 10 },
];
const auctionsData = [
  { OutcomeName: "Chiefs to Win Super Bowl", CurrentBid: 50 },
  { OutcomeName: "Bills to Win Super Bowl", CurrentBid: 45 },
];

// Home Component
function Home() {
  return (
    <div>
      <h2>Welcome Back, User!</h2>
      <p>Your recent activity:</p>
      <ul>
        <li>Bought "Chiefs to Win Super Bowl" for $30</li>
        <li>Listed "Bills to Win Super Bowl" for auction</li>
      </ul>
    </div>
  );
}

// Marketplace Component
function Marketplace() {
  const [bets, setBets] = useState([]);

  useEffect(() => {
    setBets(betsData);
  }, []);

  return (
    <div>
      <h2>Marketplace</h2>
      {bets.map((bet, index) => (
        <div key={index} className="bet-card">
          <h3>{bet.OutcomeName}</h3>
          <p>Odds: {bet.Odds}</p>
          <p>Price: ${bet.ListedPrice}</p>
          <button>Buy Now</button>
        </div>
      ))}
    </div>
  );
}

// My Bets Component
function MyBets() {
  const [portfolio, setPortfolio] = useState([]);

  useEffect(() => {
    setPortfolio(portfoliosData);
  }, []);

  return (
    <div>
      <h2>My Bets</h2>
      {portfolio.map((bet, index) => (
        <div key={index} className="bet-card">
          <h3>{bet.OutcomeName}</h3>
          <p>Shares Held: {bet.NumberOfSharesHeld}</p>
          <button>List for Sale</button>
        </div>
      ))}
    </div>
  );
}

// Auction Component
function Auction() {
  const [auctions, setAuctions] = useState([]);

  useEffect(() => {
    setAuctions(auctionsData);
  }, []);

  return (
    <div>
      <h2>Auctions</h2>
      {auctions.map((auction, index) => (
        <div key={index} className="auction-card">
          <h3>{auction.OutcomeName}</h3>
          <p>Current Bid: ${auction.CurrentBid}</p>
          <button>Place Bid</button>
        </div>
      ))}
    </div>
  );
}

// Groups Component
function Groups() {
  return (
    <div>
      <h2>Groups</h2>
      <button>Create Group</button>
      <button>Join Group</button>
    </div>
  );
}

// Leaderboard Component
function Leaderboard() {
  const leaders = [
    { name: "User1", points: 1200 },
    { name: "User2", points: 950 },
    { name: "User3", points: 850 },
  ];

  return (
    <div>
      <h2>Leaderboard</h2>
      <ul>
        {leaders.map((leader, index) => (
          <li key={index}>
            {leader.name}: {leader.points} points
          </li>
        ))}
      </ul>
    </div>
  );
}

// App Component
function App() {
  return (
    <div className="App">
      <header>
        <h1>WagerWire</h1>
        <nav>
          <a href="#home">Home</a>
          <a href="#marketplace">Marketplace</a>
          <a href="#my-bets">My Bets</a>
          <a href="#auction">Auctions</a>
          <a href="#groups">Groups</a>
          <a href="#leaderboard">Leaderboard</a>
        </nav>
      </header>
      <main>
        <Home />
        <Marketplace />
        <MyBets />
        <Auction />
        <Groups />
        <Leaderboard />
      </main>
    </div>
  );
}

// Render the App
ReactDOM.render(<App />, document.getElementById("root"));
