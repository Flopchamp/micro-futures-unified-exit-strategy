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

### Trading Approach
- **Ultra-high frequency**: Designed for maximum signal generation
- **Micro patterns**: Sub-bar price action and instant turns
- **Session-aware**: Optimized for different trading sessions
- **Regime-adaptive**: Adjusts to trending vs ranging markets

### Risk Management
- **Dynamic Stops**: 1.2-1.8x ATR based on timeframe
- **Progressive Exits**: 60% quick, 40% runners
- **Daily Loss Protection**: 5% maximum daily drawdown
- **Position Limits**: 12% max per trade, 2 concurrent positions max

### Signal Quality
- **Multiple Confirmations**: Requires trend + momentum + price action alignment
- **Stronger Filters**: Hull MA slope + SuperTrend + envelope breakout
- **Quality Over Quantity**: Balanced approach to reduce overtrading

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

#### Ultra Trading Mode
```pine
ultraMode = true                    // Enable ultra trading
microScalping = true                // Enable micro scalping
instantSignals = true               // Enable instant signals
minimalFilters = true               // Reduce entry friction
```

#### Instrument Multipliers
```pine
// Trade Frequency
M2K: 1.8x base multiplier
MYM: 1.6x base multiplier
MES: 1.4x base multiplier

// Scalping Multipliers
M2K: 2.2x scalping multiplier
MYM: 1.8x scalping multiplier
MES: 1.6x scalping multiplier
```

#### Hull Moving Averages
```pine
// Base Periods (auto-adjusted per timeframe)
Main Hull: 25 periods
Fast Hull: 9 periods
Signal Hull: 14 periods

// M2K gets 70-80% of base
// MYM gets 90% of base
// MES uses base periods
```

#### Envelope Settings
```pine
// Base Settings
Length: 12 periods
Deviation: 0.8%

// Instrument-specific
M2K: 0.9x length, 0.85x deviation
MYM: Base settings
MES: 1.1x length, 0.95x deviation
```

#### SuperTrend Configuration
```pine
Pivot Period: 2
ATR Factor: 2.2
ATR Period: 8

// Instrument adjustments
M2K: 0.95x ATR factor
MYM: 1.05x ATR factor
MES: Base ATR factor
```

#### Risk Management
```pine
Base Risk: 0.6% per trade
Max Position: 12% of equity
Max Daily Loss: 5%
Max Concurrent: 1-2 trades

// Instrument Risk Multipliers
M2K: 1.3x risk
MYM: 1.1x risk
MES: 1.0x risk
```

#### Session Settings
```pine
Pre-Market: 1800 (6:00 PM ET)
Regular Hours: 0930-1600 (9:30 AM - 4:00 PM ET)
After Hours: 1600-1700

// Session Multipliers
Regular: 1.1x frequency
Extended: 0.7x frequency
Closed: 0.5x frequency
```

#### Timeframe Multipliers
```pine
1-minute: 1.8x base
2-minute: 1.6x base
3-minute: 1.4x base
5-minute: 1.2x base
```

#### Take Profit Levels
```pine
TP1: 60% at 0.4x ultra-quick (ATR * tpMultiplier * 0.5 * 0.4)
TP2: 25% at 0.3x quick (ATR * tpMultiplier * 0.3)
TP3: 10% at 0.6x medium (ATR * tpMultiplier * 0.6)
TP4: 5% at 1.0x extended (ATR * tpMultiplier * 1.0)
```

#### Stop Loss & Trailing
```pine
// Initial Stop
1-minute: 1.2x ATR
2-minute: 1.3x ATR
3-minute: 1.4x ATR
5-minute: 1.6x ATR

// Trailing Stop
Activation: After 0.7x ATR profit
Trail Distance: 0.6x ATR
```

### Customization Tips

1. **For Lower Frequency Trading**
   - Reduce trade multipliers (1.0-1.2x range)
   - Reduce scalping multipliers (1.2-1.5x)
   - Disable instant signals
   - Enable stricter filters

2. **For Higher Frequency Trading**
   - Increase trade multipliers (2.0-3.0x range)
   - Increase scalping multipliers (2.5-3.5x)
   - Enable all signal types
   - Use minimal filters

3. **For Different Market Conditions**
   - **Trending Markets**: Increase volatility multiplier, use wider trailing
   - **Ranging Markets**: Tighter stops, quicker profit taking
   - **High Volatility**: Reduce position size, wider stops
   - **Low Volatility**: Can increase size, tighter stops

4. **Session-Specific Optimization**
   - **Regular Hours**: Can increase frequency multiplier (1.2-1.5x)
   - **Pre-Market**: More conservative (0.5-0.7x)
   - **After Hours**: Reduced activity (0.5-0.8x)

## 📈 Testing Recommendations

### Backtesting Setup
1. **Data Quality**: Use minimum 6 months historical data with tick precision
2. **Recommended Timeframes**: 1-minute, 3-minute, or 5-minute charts
3. **Initial Capital**: $25,000 (strategy default for futures margin)
4. **Commission**: Include realistic futures commission ($0.62/contract typical)
5. **Slippage**: Account for 1 tick slippage minimum

### Performance Metrics to Monitor
- **Total Trades**: High frequency expected (watch for overtrading >1000/month)
- **Win Rate**: Secondary metric (60-75% typical with good filters)
- **Profit Factor**: Target 1.3+ (critical for high-frequency strategies)
- **Average Trade**: Should exceed commission + slippage costs
- **Max Drawdown**: Should be <15-20%
- **Average Win vs Average Loss**: Monitor R/R balance
- **Trades Per Session**: Check session distribution

### Instrument-Specific Testing
- **M2K**: Expect highest trade frequency, shorter holding periods
- **MYM**: Moderate frequency, balanced holding times
- **MES**: Lower frequency, potentially longer holds

### Debug Features
Monitor via Data Window:
- `Total Positions`: Current concurrent position count
- `Effective Risk %`: Actual risk being taken per trade
- `TF Multiplier`: Active timeframe multiplier
- `Holding Period`: Bars since entry
- `Position Size`: Dollar value of current position
- `Trade Frequency`: Active frequency boost
- `Session Multiplier`: Current session adjustment
- `Instrument`: 1=MYM, 2=M2K, 3=MES

## 🔧 Troubleshooting

### Too Many Trades (>1000/month)
- **Reduce trade multipliers**: Lower M2K/MYM/MES base multipliers to 1.0-1.2x
- **Reduce scalping multipliers**: Lower to 1.2-1.5x range
- **Disable instant signals**: Turn off `instantSignals` for fewer micro-turns
- **Increase base Hull periods**: Use 30-35 for main, 12-15 for fast
- **Stricter envelope**: Increase deviation to 1.0-1.2%
- **Disable micro scalping**: Turn off `microScalping` mode

### Too Few Trades (<50/month)
- **Increase trade multipliers**: Raise to 2.0-3.0x range
- **Increase scalping multipliers**: Raise to 2.5-3.5x range
- **Enable all signals**: Activate instant, micro, and scalp signals
- **Reduce Hull periods**: Lower to 15-20 main, 6-8 fast
- **Tighter envelope**: Reduce deviation to 0.5-0.6%
- **Enable minimal filters**: Activate `minimalFilters` mode

### Poor Win Rate (<50%)
- **Check stop placement**: May be too tight for volatility
- **Verify signal quality**: Ensure multiple confirmations required
- **Review timeframe**: Lower timeframes may have more noise
- **Check session filters**: Avoid low-liquidity sessions
- **Increase Hull periods**: Smoother signals with less whipsaws

### Poor Profit Factor (<1.2)
- **Widen TP targets**: Increase `tpMultiplier` to 1.2-1.5x
- **Review exit timing**: May be exiting too early
- **Check trailing stop**: Ensure activating at proper profit level
- **Reduce trade frequency**: Quality over quantity
- **Verify R/R balance**: Monitor avg win vs avg loss

### Stops Hit Too Frequently
- **Widen stops**: Increase ATR multiplier from 1.2 to 1.8-2.0x
- **Check volatility regime**: May be trading in high-volatility incorrectly
- **Review entry timing**: Entering too late in moves
- **Use smart trailing**: Enable with wider activation ratio (0.9-1.0x)

### Inconsistent Results Across Instruments
- **M2K volatile**: Reduce multipliers, tighten risk (0.8-1.0x)
- **MYM balanced**: Use standard settings
- **MES stable**: Can increase aggression slightly (1.1-1.2x)
- **Adjust individually**: Each instrument has unique characteristics

### Session-Specific Issues
- **Pre-market**: Lower frequency expected (0.5-0.7x normal)
- **Regular hours**: Should see most activity
- **After-hours**: Reduced but should still trade
- **Check session times**: Verify ET timezone alignment

### High Drawdowns (>20%)
- **Reduce position sizing**: Lower `maxPositionSize` to 8-10%
- **Reduce risk per trade**: Lower base risk to 0.3-0.4%
- **Enable daily loss limit**: Enforce max daily loss strictly
- **Reduce concurrent trades**: Limit to 1 position max
- **Check market conditions**: Strategy may not suit current regime

## 📝 Strategy Logic Flow

```
1. Instrument Detection & Optimization
   ├─ Auto-detect MYM/M2K/MES from ticker
   ├─ Load instrument-specific multipliers
   ├─ Adjust Hull/Envelope/SuperTrend parameters
   └─ Set risk and scalping multipliers

2. Session & Timeframe Analysis
   ├─ Determine current session (Pre/Regular/After)
   ├─ Detect chart timeframe (1m/2m/3m/5m)
   ├─ Calculate session multiplier
   └─ Calculate timeframe multiplier

3. Market Regime Detection
   ├─ Measure trend strength (strong/moderate/ranging)
   ├─ Assess volatility (high/normal)
   ├─ Calculate dynamic position size
   └─ Set effective risk percentage

4. Signal Generation (Multi-Source)
   ├─ Hull MA Analysis
   │  ├─ Calculate Main/Fast/Signal HMAs
   │  ├─ Detect micro-turns and slopes
   │  └─ Identify acceleration patterns
   ├─ Envelope Analysis
   │  ├─ Calculate upper/lower bands
   │  ├─ Detect micro-breakouts
   │  └─ Identify envelope touches
   ├─ SuperTrend Analysis
   │  ├─ Calculate pivot-based bands
   │  ├─ Determine trend direction
   │  └─ Detect trend changes
   └─ Momentum Analysis
      ├─ RSI and Stochastic calculation
      ├─ Micro momentum detection
      └─ Momentum acceleration

5. Signal Confirmation & Entry
   ├─ Combine micro/instant/scalp signals
   ├─ Require multiple confirmations:
   │  ├─ Hull slope alignment
   │  ├─ SuperTrend confirmation
   │  └─ Momentum/price action support
   ├─ Verify session allowance
   ├─ Check position limits
   ├─ Confirm daily loss not exceeded
   └─ Execute entry with dynamic size

6. Position Management (In Trade)
   ├─ Track holding period
   ├─ Monitor for TP1 hit (60% exit)
   ├─ Monitor for TP2 hit (25% exit)
   ├─ Monitor for TP3 hit (10% exit)
   ├─ Monitor for TP4 hit (5% exit)
   ├─ Activate trailing stop after profit threshold
   └─ Exit at max holding period if enabled

7. Risk Management (Continuous)
   ├─ Monitor daily P&L
   ├─ Track concurrent positions
   ├─ Enforce position size limits
   ├─ Apply stop loss protection
   └─ Execute smart trailing when activated

8. Exit Execution
   ├─ Partial exits at each TP level
   ├─ Stop loss if triggered
   ├─ Trailing stop if activated
   ├─ Time-based exit if holding limit reached
   └─ Update position counters
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
- **Type**: Strategy (backtestable with real-time alerts)
- **Initial Capital**: $25,000 (default for futures)
- **Order Type**: Cash-based with dynamic sizing
- **Execution**: On-close bar confirmation
- **Pyramiding**: Optional (configurable multi-position support)

### Key Calculations

#### Hull Moving Average
```pine
hma(src, len) => ta.wma(2 * ta.wma(src, len/2) - ta.wma(src, len), sqrt(len))
```

#### Dynamic Position Size
```pine
1. Calculate ATR-based stop distance
2. Apply timeframe multipliers (1.2-1.8x ATR)
3. Calculate risk in dollars (equity * effectiveRisk%)
4. Determine position size: risk$ / (stop distance * point value)
5. Apply position limits (12% max, $75 minimum)
6. Adjust for pyramid scaling if applicable
```

#### Effective Risk Calculation
```pine
effectiveRisk = baseRisk * instrumentMultiplier * riskMultiplier * tradeFrequency
Cap at 4.5% maximum
```

#### Trade Frequency Calculation
```pine
frequency = baseFrequency * instrumentMultiplier * timeframeMultiplier * sessionMultiplier
```

### Dependencies
- TradingView Pine Script v5 runtime
- Real-time or historical futures data feed
- No external indicators required (all built-in)

### Performance Characteristics
- **Execution Speed**: Fast (minimal calculations per bar)
- **Memory Usage**: Low (limited historical references)
- **Indicator Count**: 3 core (HMA, Envelope, SuperTrend)
- **Plot Count**: Multiple for visualization and debugging

## 📚 Version History

### Current Version: MJV6 Ultra
**Focus**: High-frequency ultra trading with intelligent signal generation

**Key Features**:
- Ultra trading mode with instant signals
- Micro scalping and pattern detection
- Instrument-specific optimization (M2K/MYM/MES)
- Session-based trading (Pre/Regular/After hours)
- Automatic timeframe adaptation (1m-5m)
- Market regime detection and adaptive sizing
- Multi-level progressive take profit (TP1-TP4)
- Smart trailing stop activation
- Comprehensive monitoring and debugging

**Optimizations**:
- Balanced signal generation (reduced overtrading)
- Stronger entry confirmations (multiple signals required)
- Adaptive Hull MA periods per instrument and timeframe
- Dynamic envelope sensitivity
- Session-aware frequency adjustments
- Regime-based position sizing (up to 3.5x in ideal conditions)

**Trade Management**:
- 4-level progressive exits (60%/25%/10%/5%)
- Ultra-quick TP1 at 0.4x target (60% position)
- Time-based holding limits (25-35 bars)
- Smart trailing after 0.7x ATR profit
- ATR-based stop loss (1.2-1.8x depending on timeframe)

### Previous Iterations
- **MJV5**: Initial ultra-trading implementation with micro signals
- **MJV4**: Advanced profit protection and multi-TP system
- **MJV3**: Basic timeframe optimization
- **MJV2**: Multi-instrument support (MYM/MES/M2K)
- **MJV1**: Single-instrument prototype with Hull MA

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
- Study Hull Moving Averages (HMA) for trend detection
- Learn about micro price action patterns
- Research futures contract specifications (tick size, point value)
- Understand session-based trading (Globex, RTH, extended hours)
- Study market regime classification (trending vs ranging)
- Learn about ATR (Average True Range) for dynamic stops

**Futures Trading Fundamentals:**
- Micro futures vs standard futures contracts
- Margin requirements and leverage
- Session trading hours for equity futures
- Commission structures and slippage
- Contract rollover dates
- Market depth and liquidity patterns

**Pine Script Resources:**
- [TradingView Pine Script Documentation](https://www.tradingview.com/pine-script-docs/)
- [Pine Script v5 User Manual](https://www.tradingview.com/pine-script-docs/en/v5/Introduction.html)
- [Pine Script v5 Migration Guide](https://www.tradingview.com/pine-script-docs/en/v5/migration_guides/v4_to_v5_migration_guide.html)
- TradingView Community Scripts for inspiration

**High-Frequency Trading Concepts:**
- Micro pattern recognition
- Ultra-short holding periods
- Progressive profit taking strategies
- Dynamic position sizing based on volatility
- Session-based optimization

---

**Disclaimer**: This strategy is provided as-is without any guarantees. Futures trading involves substantial risk of loss and is not suitable for all investors. Always conduct your own research and testing. Trade responsibly with money you can afford to lose.

*Last Updated: December 2025 - MJV6 Ultra Version*
