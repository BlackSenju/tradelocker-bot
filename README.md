# WSA Confluence Strategy - Forex Trading Bot

A sophisticated automated trading bot built with **Backtrader** and optimized for **TradeLocker**, implementing the WSA (Wyckoff Structure & Analysis) Confluence Strategy for forex trading.

## 🎯 Strategy Overview

The WSA Confluence Strategy identifies high-probability trading setups by combining multiple technical analysis confluences:

### Key Components

- **Swing Detection**: Identifies swing highs and lows to detect market structure
- - **Moving Averages**: Fast (10), Slow (30), and Trend (100) MAs for directional bias
  - - **Support & Resistance**: Dynamic S/R levels from recent swing points
    - - **Fibonacci Levels**: Key retracement levels (23.6%, 38.2%, 50%, 61.8%, 78.6%)
      - - **Chart Patterns**: Double tops/bottoms, higher lows, lower highs detection
        - - **RSI Indicator**: Overbought/oversold conditions for entry confirmation
          - - **ATR-Based Risk Management**: Intelligent stop losses and take profits
           
            - ### Confluence Scoring
           
            - Trades are only entered when multiple factors align. The strategy requires a minimum confluence score of 2+ (configurable) from the following factors:
           
            - 1. Market Structure (bullish/bearish)
              2. 2. Moving Average Alignment
                 3. 3. RSI Extremes
                    4. 4. Support/Resistance Levels
                       5. 5. Fibonacci Retracements
                          6. 6. Chart Patterns
                            
                             7. ## 📊 Optimized for
                            
                             8. - **Currency Pairs**: GBP/JPY, USD/JPY, AUD/USD (H4 timeframe recommended)
                                - - **Timeframe**: H4 (4-hour candles)
                                  - - **Trading Style**: Swing trading
                                   
                                    - ## ⚙️ Risk Management
                                   
                                    - - **Position Sizing**: Configurable lot size (default: 0.01 lots)
                                      - - **Stop Loss**: ATR-based (default: 1.5x ATR)
                                        - - **Take Profit Levels**:
                                          -   - TP1: 1.5x ATR (close 50% of position)
                                              -   - TP2: 3.0x ATR (close remaining position)
                                                  - - **Trailing Stop**: Optional trailing stop after partial close
                                                    - - **Daily Trade Limit**: Max 5 trades per day (configurable)
                                                      - - **Move SL to Breakeven**: Automatically move stop loss after TP1
                                                       
                                                        - ## 🚀 Getting Started
                                                       
                                                        - ### Prerequisites
                                                       
                                                        - - Python 3.8+
                                                          - - TradeLocker account
                                                            - - Backtrader library
                                                             
                                                              - ### Installation
                                                             
                                                              - ```bash
                                                                # Clone the repository
                                                                git clone https://github.com/BlackSenju/tradelocker-bot.git
                                                                cd tradelocker-bot

                                                                # Create virtual environment
                                                                python -m venv venv
                                                                source venv/bin/activate  # On Windows: venv\Scripts\activate

                                                                # Install dependencies
                                                                pip install backtrader
                                                                pip install python-dotenv  # For environment variables
                                                                ```

                                                                ### Configuration

                                                                1. Copy `.env.example` to `.env` and add your credentials:
                                                               
                                                                2. ```bash
                                                                   TRADELOCKER_API_KEY=your_api_key_here
                                                                   TRADELOCKER_SECRET=your_secret_here
                                                                   TRADELOCKER_ACCOUNT_ID=your_account_id_here
                                                                   ```

                                                                   2. Adjust strategy parameters in the `params` dictionary:
                                                                  
                                                                   3. ```python
                                                                      params = {
                                                                          "min_confluence": 2,      # Minimum confluence score for entry
                                                                          "ma_fast": 10,            # Fast moving average period
                                                                          "ma_slow": 30,            # Slow moving average period
                                                                          "ma_trend": 100,          # Trend moving average period
                                                                          "swing_lookback": 8,      # Bars to look back for swing detection
                                                                          "lots_per_trade": 0.01,   # Position size in lots
                                                                          "max_daily_trades": 5,    # Maximum trades per day
                                                                          # ... additional parameters
                                                                      }
                                                                      ```

                                                                      ### Running the Bot

                                                                      ```bash
                                                                      python backtest.py  # Run backtest
                                                                      python live_trade.py  # Run live trading (use with caution!)
                                                                      ```

                                                                      ## 📈 Parameters Reference

                                                                      | Parameter | Default | Description |
                                                                      |-----------|---------|-------------|
                                                                      | `min_confluence` | 2 | Minimum confluence score for entry |
                                                                      | `ma_fast` | 10 | Fast MA period |
                                                                      | `ma_slow` | 30 | Slow MA period |
                                                                      | `ma_trend` | 100 | Trend MA period |
                                                                      | `swing_lookback` | 8 | Bars for swing detection |
                                                                      | `lots_per_trade` | 0.01 | Position size |
                                                                      | `stop_atr_mult` | 1.5 | Stop loss multiplier |
                                                                      | `tp1_atr_mult` | 1.5 | First target multiplier |
                                                                      | `tp2_atr_mult` | 3.0 | Second target multiplier |
                                                                      | `partial_close_pct` | 50 | % to close at TP1 |
                                                                      | `use_trailing` | True | Enable trailing stop |
                                                                      | `max_daily_trades` | 5 | Daily trade limit |

                                                                      ## ⚠️ Disclaimer

                                                                      **This bot is provided for educational purposes only.** Forex trading carries significant risk. Always:

                                                                      - Test thoroughly on demo accounts before live trading
                                                                      - - Start with small position sizes
                                                                        - - Monitor bot performance regularly
                                                                          - - Use proper risk management
                                                                            - - Never invest more than you can afford to lose
                                                                             
                                                                              - ## 🔒 Security Notes
                                                                             
                                                                              - - **Never commit API keys or secrets** - Use `.env` files and `.gitignore`
                                                                                - - Always use strong passwords for trading accounts
                                                                                  - - Enable two-factor authentication on TradeLocker
                                                                                    - - Run bot in a secure environment
                                                                                      - - Monitor trading activity continuously
                                                                                       
                                                                                        - ## 📝 License
                                                                                       
                                                                                        - This project is licensed under the MIT License - see LICENSE file for details.
                                                                                       
                                                                                        - ## 🤝 Contributing
                                                                                       
                                                                                        - Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.
                                                                                       
                                                                                        - ## 📧 Support
                                                                                       
                                                                                        - For issues, questions, or improvements, please open an issue on GitHub or contact the repository owner.
                                                                                       
                                                                                        - ---

                                                                                        **Last Updated**: January 2026
                                                                                        **Status**: Active Development
