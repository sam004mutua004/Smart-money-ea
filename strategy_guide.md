# SmartMoney EA — Strategy Guide

## How the Robot Thinks

### Step 1: Identify Market Structure (BOS)
The robot scans the last N bars for swing highs and lows.
- If price **closes above** a previous swing high → **Bullish BOS**
- If price **closes below** a previous swing low → **Bearish BOS**
- If the bias **flips** (e.g., bearish structure breaks bullish) → **CHoCH** (Change of Character)

### Step 2: Map Liquidity Zones
Equal highs and swing highs = **Buy-Side Liquidity (BSL)**
Equal lows and swing lows = **Sell-Side Liquidity (SSL)**
Institutions target these zones to fill large orders.

### Step 3: Identify Fair Value Gaps (FVG)
A 3-candle pattern where the middle candle creates an imbalance:
- **Bullish FVG**: gap between high of candle[i+1] and low of candle[i-1]
- **Bearish FVG**: gap between low of candle[i+1] and high of candle[i-1]
Price often returns to fill these gaps.

### Step 4: Confluence = Signal
The robot only fires when ALL 3 conditions align:

**BUY:**  Bullish BOS + Price in Bullish FVG + Sell-side Liquidity nearby

**SELL:** Bearish BOS + Price in Bearish FVG + Buy-side Liquidity nearby

### Step 5: Trade Execution
- SL placed 1.5× ATR beyond the entry
- TP placed at 2× SL distance (configurable RR)
- Lot size calculated based on risk % of account
- Trailing stop moves with price (1× ATR)
