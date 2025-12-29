Market Making System: Component List
Component 1: Market Data Engine
Ingests and processes market data from historical files or live feeds

Sub-components:
1.1 Data Source Abstraction Layer - Unified interface for historical files vs live WebSocket feeds
1.2 Order Book Reconstructor - Maintains real-time order book state (bids/asks/depth) from raw messages
1.3 Event Stream Manager - Queues and dispatches market events with proper timestamp ordering
Component 2: Market Making Strategy Engine
Calculates fair value and generates optimal bid/ask quotes

Sub-components:
2.1 Fair Value Calculator - Computes current "true" price from market data (mid-price, microprice)
2.2 Avellaneda-Stoikov Model - Implements the optimal market making algorithm with inventory risk management
2.3 Quote Generator - Produces actual bid/ask prices with spread adjustments and tick rounding
2.4 Quote Manager - Tracks active quotes and determines when to cancel/update them
Component 3: Position & Risk Management
Tracks positions, calculates P&L, and enforces risk limits

Sub-components:
3.1 Position Tracker - Maintains current inventory, average entry price, and position history
3.2 Risk Limits Engine - Enforces hard stops on position size, losses, and exposure
3.3 P&L Calculator - Computes realized/unrealized P&L, transaction costs, and attribution
3.4 Risk Reactions - Auto-adjusts or cancels quotes when approaching risk limits
Component 4: Execution Simulator / Paper Trading Engine
Simulates fills in historical mode or tracks paper fills in live mode

Sub-components:
4.1 Fill Simulator (Historical) - Determines if your quotes would have been filled based on market trades
4.2 Paper Trading Engine (Live) - Monitors live trades and simulates fills against your quotes
4.3 Market Impact Model - Models slippage, adverse selection, and fill probability
4.4 Transaction Cost Model - Applies maker/taker fees, rebates, and clearing costs
Component 5: Quote Comparison & Analytics Engine
Compares your quotes to actual market quotes and measures competitiveness

Sub-components:
5.1 Real-time Quote Comparator - Tracks your bid/ask vs market bid/ask, spread differences, price improvement
5.2 Competitiveness Scorer - Estimates market share, quote quality, and profitability vs market makers
5.3 Microstructure Analytics - Analyzes order book patterns, spread dynamics, and volume relationships
5.4 Adverse Selection Analyzer - Measures post-fill price drift and detects toxic flow
Component 6: Backtesting Framework & Visualization
Orchestrates experiments, calculates performance metrics, and generates reports

Sub-components:
6.1 Backtest Runner - Coordinates all components and loops through historical data
6.2 Performance Calculator - Computes Sharpe ratio, max drawdown, VaR, and other risk-adjusted metrics
6.3 Parameter Optimization - Runs grid searches and cross-validation to tune strategy parameters
6.4 Reporting Engine - Generates automated HTML/PDF reports with executive summaries
6.5 Visualization Suite - Creates P&L curves, position plots, heatmaps, and live dashboards
