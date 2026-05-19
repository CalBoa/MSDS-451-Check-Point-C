# Checkpoint C Research Report  
## QuantaFlex ETF Performance Evaluation

### Abstract

QuantaFlex ETF is a proposed rules-based, actively managed multi-asset ETF designed to allocate across equities, bonds, commodities, and cash using systematic signals and risk controls. This checkpoint evaluates the expected performance of the strategy through backtesting, benchmark comparison, Monte Carlo simulation, and fee analysis. The baseline equal-weight buy-and-hold portfolio from Checkpoint B is used as the starting point, with SPY as the benchmark. Results indicate that QuantaFlex produces lower raw return than SPY but also lower volatility, lower drawdown, and a slightly higher Sharpe ratio. Monte Carlo testing suggests positive expected growth over a five-year horizon. After considering management and trading fees, the strategy remains potentially attractive as a lower-risk multi-asset ETF concept.

**Keywords**: ETF, backtesting, performance evaluation, Monte Carlo simulation, Sharpe ratio, fees

### Introduction

This research is being conducted to evaluate whether QuantaFlex ETF can deliver attractive investor outcomes when tested using historical data and simulated market conditions. The problem is that investors often seek diversified active management and downside protection, but many actively managed funds lack transparency and may not justify their fees. QuantaFlex is intended to address this problem through a transparent, algorithmic, multi-asset framework.

The intended users of this work are retail investors, financial advisors, and institutional allocators interested in a disciplined, diversified ETF with systematic risk controls. The application being developed is an investment analytics and trading framework that can backtest portfolio rules, simulate market scenarios, evaluate expected returns after fees, and support future automation.

The main research question for this checkpoint is: Can QuantaFlex ETF generate competitive risk-adjusted performance relative to the market after accounting for fees and market uncertainty?

### Literature Review

Research on performance evaluation in quantitative investing supports the use of benchmark-relative and risk-adjusted measures. Sharpe (1964) introduced the framework that underlies the Sharpe ratio, alpha, and beta, which remain central to portfolio evaluation. Markowitz (1952) established the importance of diversification, which is fundamental to QuantaFlex’s multi-asset design.

Momentum and trend-following research suggests that systematic trading rules can generate excess returns across different asset classes (Jegadeesh and Titman 1993; Moskowitz, Ooi, and Pedersen 2012; Asness, Moskowitz, and Pedersen 2014). Mean reversion strategies are also widely studied in technical trading literature and may complement momentum under some market regimes. This supports the idea that QuantaFlex may eventually combine multiple signal types rather than relying only on passive allocation.

For evaluating strategies, López de Prado (2018) stresses that historical backtests must be interpreted carefully because overfitting can make a strategy appear stronger than it really is. Walk-forward testing and Monte Carlo simulation help reduce this risk by testing strategies across many possible market paths rather than just one realized history. Trivedi and Kyal (2021) also emphasize the importance of realistic backtesting, transaction costs, and validation procedures.

Together, this literature supports the use of backtesting, benchmark comparison, Monte Carlo simulation, and fee sensitivity analysis as the main tools for evaluating QuantaFlex ETF.

### Methods

This checkpoint evaluates QuantaFlex’s expected performance using the historical data prepared in Checkpoint B and a baseline portfolio design. The current implementation uses a long-only equal-weight buy-and-hold portfolio across NVDA, AGG, ACWI, GLD, DBC, and BIL. SPY is used as the benchmark representing the broad U.S. equity market.

Daily adjusted close prices from Yahoo Finance were used for the common period 2008–2024. Daily log returns were calculated from adjusted prices so that dividends and splits were reflected in the return series. The portfolio return series was constructed as the equal-weight average of the six selected assets.

Performance was evaluated using the following metrics:

- **Return**: annualized portfolio return
- **Risk**: annualized volatility and maximum drawdown
- **Risk-adjusted performance**: Sharpe ratio
- **Benchmark comparison**: alpha and beta relative to SPY

The backtest compared cumulative portfolio growth to SPY over the sample period. This provided a practical baseline before introducing more advanced trend, momentum, or volatility-managed trading rules.

Monte Carlo simulation was used to test the portfolio under uncertainty. A multivariate normal return model was calibrated from historical mean returns and covariance across the selected assets. Five hundred simulated five-year paths were generated, and the ending portfolio value for each simulation was recorded. This provided a distribution of possible outcomes rather than relying only on one realized market history.

Fees were considered conceptually as part of expected investor returns. Management fees in the range of 0% to 4% annually and brokerage or trading costs were identified as relevant to fund design. Because the current portfolio is buy-and-hold with low turnover, trading costs are expected to be relatively small at this stage. However, once more active rules are added, fee and turnover impacts will become more important and should be incorporated directly into the code.

### Results

The historical backtest showed that the QuantaFlex buy-and-hold portfolio produced lower total return than SPY, but with meaningfully lower volatility and shallower drawdowns. The approximate performance results were:

- **QuantaFlex Annualized Return**: 8.03%
- **QuantaFlex Annualized Volatility**: 12.92%
- **QuantaFlex Sharpe Ratio**: 0.62
- **QuantaFlex Maximum Drawdown**: -39.54%
- **QuantaFlex Alpha**: 2.64%
- **QuantaFlex Beta**: 0.50

For comparison, SPY produced:

- **SPY Annualized Return**: 10.85%
- **SPY Annualized Volatility**: 19.95%
- **SPY Sharpe Ratio**: 0.54
- **SPY Maximum Drawdown**: -51.48%

These results suggest that QuantaFlex did not outperform SPY on raw return, but it did provide a more defensive profile. Its volatility and drawdown were substantially lower, and its Sharpe ratio was slightly better. The beta of about 0.50 suggests that the portfolio moved with the market but with much lower overall sensitivity. This is consistent with the intended role of a diversified multi-asset ETF rather than a pure equity product.

The Monte Carlo simulation also produced encouraging results. Starting from an initial value of 1.00, the mean simulated five-year ending portfolio value was approximately 1.55 and the median ending value was approximately 1.50. This implies positive expected growth across simulated scenarios, although the distribution also showed downside risk and variation in outcomes.

Regarding fees, the current buy-and-hold version of QuantaFlex would likely remain viable under modest management fees because of its low turnover. However, higher fees would reduce net investor returns and could weaken the value proposition if the strategy remains only moderately differentiated from a passive benchmark. This means that future active versions of QuantaFlex will need to show either improved alpha, stronger downside protection, or both in order to justify management fees.

### Conclusions

Checkpoint C shows that QuantaFlex has potential as a lower-risk multi-asset ETF strategy, but its current baseline form is best viewed as a foundation rather than a finished product. The backtest results indicate that the portfolio provides meaningful diversification benefits relative to SPY, especially through lower volatility, lower drawdown, and a slightly better Sharpe ratio. Monte Carlo testing also suggests that the strategy can generate positive expected growth across a range of simulated market scenarios.

At the same time, the lower raw return relative to SPY shows that the current equal-weight buy-and-hold version is not yet strong enough to stand out as a complete actively managed ETF. The project therefore still depends on successfully adding and testing the active QuantaFlex trading rules introduced in earlier checkpoints, such as trend-following, momentum tilts, and volatility-aware allocation.

The main concerns at this point are the limited common data window, the risk of overcomplicating the strategy with too many signals, and the need to incorporate realistic fees and turnover costs once active trading begins. Even so, the project appears feasible and represents a credible business opportunity if later testing shows that the active strategy can improve alpha or downside protection after fees. The next steps are to implement the active rules, conduct walk-forward testing, include explicit fee sensitivity in the code, and evaluate whether QuantaFlex can consistently justify its management structure relative to simpler passive alternatives.

### References

Asness, Clifford S., Tobias J. Moskowitz, and Lasse Heje Pedersen. 2014. “Value and Momentum Everywhere.” *Journal of Finance* 68 (3): 929–985.

Jegadeesh, Narasimhan, and Sheridan Titman. 1993. “Returns to Buying Winners and Selling Losers: Implications for Stock Market Efficiency.” *Journal of Finance* 48 (1): 65–91.

López de Prado, Marcos. 2018. *Advances in Financial Machine Learning*. Hoboken, NJ: Wiley.

Markowitz, Harry. 1952. “Portfolio Selection.” *Journal of Finance* 7 (1): 77–91.

Moskowitz, Tobias J., Yao Hua Ooi, and Lasse Heje Pedersen. 2012. “Time Series Momentum.” *Journal of Financial Economics* 104 (2): 228–250.

Sharpe, William F. 1964. “Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk.” *Journal of Finance* 19 (3): 425–442.

Trivedi, K. S., and Kishor S. Trivedi. 2021. *Probability and Statistics with Reliability, Queueing, and Computer Science Applications*. Hoboken, NJ: Wiley.
