# MJV6 Micro Equity Futures Ultra Strategy

A high-frequency Pine Script v5 trading strategy designed specifically for micro equity futures contracts (MYM, MES, M2K) featuring ultra-responsive signal detection, dynamic timeframe optimization, and intelligent session-based trading.

## 🎯 Strategy Overview

This strategy implements an ultra-aggressive scalping and swing trading system with instant signal detection, micro pattern recognition, and adaptive position sizing. Built for TradingView with futures-specific optimizations, it provides professional-grade risk management tailored for high-frequency micro futures trading.

### Supported Instruments
- **MYM** (Micro E-mini Dow Jones) - Mid-volatility equity futures
- **MES** (Micro E-mini S&P 500) - Stable equity futures
- **M2K** (Micro E-mini Russell 2000) - High-volatility equity futures

## ✨ Key Features

### 1. **Ultra Trading Mode**
- **Instant Signals**: Micro-turn detection with real-time price action analysis
- **Micro Scalping**: Sub-minute pattern recognition and execution
- **Minimal Filters**: Reduced friction for maximum signal generation
- **Dynamic Frequency**: Adaptive trade generation based on market conditions

### 2. **Instrument-Specific Optimization**
- **M2K**: High-volatility optimization (1.8x trade multiplier, 2.2x scalp multiplier)
- **MYM**: Mid-volatility tuning (1.6x trade multiplier, 1.8x scalp multiplier)
- **MES**: Stable market approach (1.4x trade multiplier, 1.6x scalp multiplier)
- Auto-detection and parameter adjustment per instrument

### 3. **Advanced Signal Detection**
- **Hull Moving Averages**: Triple-HMA system (Main, Fast, Signal) with micro-slope detection
- **Envelope Breakouts**: Dynamic envelope with micro-breakout patterns
- **SuperTrend**: Pivot-based trend detection with micro-turn signals
- **Combined Signals**: Scalp, Instant, Micro, and Strong signal types

### 4. **Timeframe Optimization**
- **Auto-Adaptation**: Automatic parameter adjustment for 1m/2m/3m/5m charts
- **Reduced Periods**: Faster response on lower timeframes
- **Frequency Multipliers**: Timeframe-specific trade frequency boosting
  - 1-minute: 1.8x base multiplier
  - 2-minute: 1.6x base multiplier
  - 3-minute: 1.4x base multiplier
  - 5-minute: 1.2x base multiplier

### 5. **Session-Based Trading**
- **US Equity Sessions**: Pre-market (6PM ET), Regular (9:30AM-4PM), After-hours
- **Session Multipliers**: Higher frequency during regular hours (1.1x), lower in extended hours (0.7x)
- **Globex Support**: Extended pre-market from 6PM ET for overnight futures

### 6. **Market Regime Detection**
- **Trend Classification**: Strong trend, moderate trend, ranging market
- **Volatility Analysis**: High volatility vs normal conditions
- **Adaptive Sizing**: Position size adjustment based on regime
- **Regime-Specific Multipliers**: Up to 3.5x in ideal conditions

### 7. **Dynamic Position Sizing**
- **ATR-Based Stops**: 1.2-1.8x ATR depending on timeframe
- **Risk Multipliers**: Instrument-specific (M2K: 1.3x, MYM: 1.1x, MES: 1.0x)
- **Volatility Adjustment**: 2.2x base multiplier in trending markets
- **Maximum Limits**: 12% position size, 4.5% effective risk cap
- **Minimum Position**: $75 for futures margin efficiency

### 8. **Multi-Level Take Profit System**
- **4-Level Exits**: TP1-TP4 with progressive profit taking
  - TP1: 60% position at 0.4x ultra-quick target
  - TP2: 25% position at 0.3x quick target
  - TP3: 10% position at 0.6x medium target
  - TP4: 5% runners at 1.0x extended target
- **Adaptive Targets**: Adjusts to volatility and instrument characteristics
- **Smart Trailing**: Activates after 0.7x ATR profit with 0.6x ATR trail

### 9. **Time-Based Exit Management**
- **Max Holding Period**: 25 bars base (instrument-adjusted)
  - M2K: 25 bars
  - MYM: 30 bars
  - MES: 35 bars
- **Quick Exit Mode**: Automatic closure at holding limit
- **Session Close**: Optional end-of-day exit

### 10. **Comprehensive Monitoring**
- **Real-time Metrics**: Position count, effective risk, timeframe multiplier
- **Performance Tracking**: Holding period, position size, trade frequency
- **Session Indicators**: Visual session type and instrument identification
- **Signal Markers**: Different symbols for Scalp, Instant, and Micro signals

## 📊 Performance Characteristics

### Risk/Reward Focus
- Ultra-tight stops: 0.75-1.75x ATR
- Wide profit targets: 1.2-12.0x ATR
- Designed for high R/R ratios (1.5:1 minimum)
- Optimized to reduce overtrading

### Trade Management
- Partial position closing at each TP level
- Progressive profit protection
- Dynamic stop upgrading (never downgrading)
- Session-aware exit logic

## 🚀 Getting Started

### Prerequisites
- TradingView account (Pro+ recommended for multi-instrument testing)
- Access to micro futures data feed
- Understanding of futures trading risks

### Installation

1. **Copy the Strategy Code**
   - Open TradingView Pine Editor
   - Create new strategy
   - Paste code from `MJV6_MYM_MES_M2K_Strategy.pine`

2. **Load on Chart**
   - Apply to 5-minute chart (recommended starting timeframe)
   - Select your instrument (MYM, MES, or M2K)
   - Strategy will auto-detect instrument and apply optimized parameters

3. **Configure Settings** (Optional)
   - Adjust position sizing in strategy properties
   - Modify TP levels based on your risk tolerance
   - Enable/disable specific exit types
   - Configure alert messages

## ⚙️ Configuration

### Key Parameters

#### Entry Filters
```pine
// RSI Settings (instrument-specific)
M2K: 45-75 (long), 25-55 (short)
MYM: 40-80 (long), 20-60 (short)
MES: 35-85 (long), 15-65 (short)

// Volume Requirements
M2K: 1.2x average
MYM: 1.1x average
MES: 1.0x average
```

#### Stop Loss & Take Profit
```pine
// Stop Loss (ATR multipliers)
Scalp: 0.75-1.25x ATR
Swing: 1.25-1.75x ATR

// Take Profit Levels
Scalp TP1-TP4: 1.2x, 2.4x, 3.6x, 5.4x ATR
Swing TP1-TP4: 2.4x, 5.4x, 9.0x, 12.0x ATR
```

#### Risk Management
```pine
Position Size: 8% max equity per trade
Portfolio Risk: 2% total
Commission: $0.62 per contract
Slippage: 1 tick
```

### Customization Tips

1. **For More Conservative Trading**
   - Reduce position size multipliers
   - Tighten RSI filter bands
   - Increase volume requirements
   - Raise minimum R/R ratio

2. **For More Aggressive Trading**
   - Widen RSI bands slightly
   - Lower volume thresholds
   - Adjust TP levels closer

3. **For Different Timeframes**
   - Test on 3min, 5min, 15min charts
   - Adjust ATR period for longer timeframes
   - Modify session-based exits accordingly

## 📈 Testing Recommendations

### Backtesting Setup
1. **Data Quality**: Use minimum 6 months historical data
2. **Timeframe**: Start with 5-minute charts
3. **Commission/Slippage**: Keep realistic settings enabled
4. **Initial Capital**: $10,000-50,000 recommended

### Performance Metrics to Monitor
- **Profit Factor**: Target 1.5+ (indicates R/R balance)
- **Win Rate**: Secondary metric (can be 60-70% with good R/R)
- **Max Drawdown**: Should be <20%
- **Number of Trades**: Avoid overtrading (>500/month may indicate issues)
- **Average Win vs Average Loss**: Should favor wins 2:1+

### Debug Features
Enable debug plotting to monitor:
- Current R/R ratio calculations
- Stop distance in ticks
- TP distances for all levels
- Entry signal strength
- Active exit type

## 🔧 Troubleshooting

### No Trades Executing
- Check RSI filter bands (may be too tight)
- Verify volume requirements (lower thresholds)
- Ensure correct instrument symbol
- Check if R/R validation is too strict

### Too Many Trades
- Tighten RSI bands
- Increase volume multiplier requirements
- Enable stricter volatility filters
- Reduce position size multipliers

### Poor Profit Factor
- Widen TP targets (increase multipliers)
- Tighten stop loss (decrease multipliers)
- Enable profit lock system
- Review R/R validation settings

### Stops Hit Too Often
- Increase stop loss ATR multiplier
- Enable breakeven earlier
- Adjust profit lock percentages
- Review market volatility conditions

## 📝 Strategy Logic Flow

```
1. Entry Signal Detection
   ├─ RSI confirms oversold/overbought
   ├─ Volume surge detected
   ├─ Volatility within acceptable range
   └─ Trend alignment confirmed
   
2. Risk/Reward Validation
   ├─ Calculate stop loss distance
   ├─ Calculate TP1 distance
   ├─ Verify minimum R/R ratio
   └─ Approve/reject trade
   
3. Position Entry
   ├─ Calculate position size
   ├─ Set initial stop loss
   ├─ Set all TP levels
   └─ Initialize exit management
   
4. Trade Management (Continuous)
   ├─ Monitor for TP hits
   ├─ Upgrade stop loss (never downgrade)
   ├─ Activate profit locks
   ├─ Enable breakeven protection
   ├─ Trigger trailing stop
   └─ Check time/volatility exits
   
5. Exit Execution
   ├─ Partial closes at each TP
   ├─ Stop loss if triggered
   ├─ Session close if enabled
   └─ Emergency exits if needed
```

## ⚠️ Risk Disclosure

**Trading futures involves substantial risk of loss and is not suitable for all investors.**

- Past performance is not indicative of future results
- Leverage can work against you
- Markets can be volatile and unpredictable
- Always use proper risk management
- Never risk more than you can afford to lose
- Test thoroughly in simulation before live trading

## 🛠️ Technical Details

### Code Structure
- **Language**: Pine Script v5
- **Type**: Strategy (not indicator)
- **Execution**: On-close confirmation
- **Pyramiding**: Disabled (no position averaging)
- **Order Size**: Dynamic ATR-based calculation

### Dependencies
- TradingView Pine Script v5 runtime
- Real-time or historical futures data feed
- No external indicators required (all calculations built-in)

## 📚 Version History

### Current Version: MJV6
- Unified stop loss system implementation
- Optimized risk/reward ratios (50% tighter stops, 3x wider TPs)
- Instrument-specific parameter optimization
- Enhanced debugging and visualization
- Alert dedupe system
- Relaxed filter balance for trade generation

### Previous Iterations
- MJV5: Initial multi-exit implementation
- MJV4: Advanced profit protection
- MJV3: Basic exit management
- MJV2: Multi-instrument support
- MJV1: Single-instrument prototype

## 🤝 Contributing

This is a personal trading strategy. However, suggestions for improvements are welcome:
- Open issues for bugs or unexpected behavior
- Suggest optimizations via pull requests
- Share backtesting results for different timeframes/instruments

## 📄 License

This code is provided for educational and personal use. 

**Important**: 
- No warranty or guarantee of profitability
- Use at your own risk
- Not financial advice
- Recommended for experienced traders only

## 📞 Support

For questions or issues:
1. Review the troubleshooting section above
2. Check TradingView Pine Script documentation
3. Test in simulation mode before live trading
4. Consult with a licensed financial advisor

## 🎓 Learning Resources

**Understanding the Strategy:**
- Study ATR (Average True Range) for dynamic stops
- Learn about risk/reward ratios in trading
- Research proper position sizing methods
- Understand futures contract specifications

**Pine Script Resources:**
- [TradingView Pine Script Documentation](https://www.tradingview.com/pine-script-docs/)
- [Pine Script User Manual](https://www.tradingview.com/pine-script-docs/en/v5/Introduction.html)
- TradingView Community Scripts for inspiration

---

**Disclaimer**: This strategy is provided as-is without any guarantees. Always conduct your own research and testing. Trade responsibly.

*Last Updated: December 2025*
