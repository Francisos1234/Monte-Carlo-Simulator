# Trading Equity Curve Simulator

A Monte Carlo trading simulator I built to explore how a trading strategy's performance could unfold across many different sequences of trades.

**Live application:** [Open the Trading Equity Curve Simulator](https://script.google.com/macros/s/AKfycbzR7RuM7IsYdzRFrOE_peBkDIjyL7Cr9Y_QYdZ8s69bHIu-R3LzBOcDfGvGGGIQ-LY7/exec)

**Repository:** [Francisos1234/Monte-Carlo-Simulator](https://github.com/Francisos1234/Monte-Carlo-Simulator)

Made by **Francis Chizurumoke**, with coding assistance from Claude.

---

## Project overview

I built this simulator to help traders visualise how a strategy's results might develop over a large number of trades, rather than judging the strategy by one equity curve or one average performance figure.

The application runs **1,000 simulations per run**. It uses the trading assumptions entered by the user, including win rate, break-even rate, average win and average loss in R, to generate different hypothetical trading outcomes.

Users can also choose between:

- **Fixed risk:** the amount risked per trade stays the same.
- **Compounding risk:** the risk amount is calculated as a percentage of the current account balance.

The simulator displays best, probable and worst result views, alongside equity curves and a probability analysis. It also reports metrics such as ending balance, return, expectancy per trade, maximum drawdown and maximum consecutive wins and losses.

I used statistics from my own trading journal as a reference for the simulator's starting assumptions. The journal and its supporting Excel analysis are documented in my [Trading Performance Analysis Portfolio](https://github.com/Francisos1234/Trading-performance-journal).

## The problem I wanted to explore

A trading strategy can have positive expectancy and still experience losing streaks, drawdowns and periods where performance is much weaker than expected.

Looking only at a win rate, average reward-to-risk ratio or one historical equity curve does not show the different sequences in which wins, losses and break-even trades could occur.

For example, two traders can have the same win rate and average reward-to-risk ratio but experience very different sequences of trades. One might have several wins early, while the other might experience a long losing streak before recovering.

I wanted to build a tool that could make this uncertainty easier to see.

The main question behind the project was:

> If I use the statistics from my trading journal as the basis for a strategy, how differently could the account perform across many hypothetical sequences of trades?

I also wanted to compare fixed risk with compounding risk and see how the choice could affect the equity curve and drawdown.

## Your contribution

This is my own project. I came up with the idea, planned the features and decided what I wanted the simulator to show.

My contribution included:

- Identifying the problem I wanted the simulator to address.
- Using statistics from my trading journal as a reference for the simulation inputs.
- Defining the inputs, including win rate, break-even rate, average win, average loss and risk per trade.
- Planning the fixed-risk and compounding-risk options.
- Deciding to run 1,000 simulations per run.
- Planning the best, probable and worst result views.
- Deciding which performance metrics and probability categories would help users interpret the results.
- Reviewing the interface and the way the equity curves and results are displayed.
- Running different scenarios manually and checking how the outputs responded to changes in the inputs.

I used Claude as a coding assistant during development. It helped with implementation, but the project idea, requirements, workflow and testing decisions came from me.

## Tools and technology

| Tool | How I used it |
| --- | --- |
| Notion | Recording my trades and their R-multiple results |
| Excel | Cleaning, organising and analysing the exported trading journal data |
| Google Sheets | Spreadsheet backend supporting the simulator |
| Google Apps Script | Application logic and web interface |
| Claude | AI coding assistance during development |
| GitHub | Source repository, project documentation and screenshots |
| Browser testing | Running the application and checking different scenarios |

The trading statistics used as a reference for the simulator come from a separate journal and analysis workflow. The simulator is a standalone application; this does not mean it automatically synchronises with Notion or Excel.

## Methodology

I approached the project by first looking at the statistics that describe a trading strategy, then deciding how those statistics could be used to explore different possible trading sequences.

### 1. Use trading journal statistics as a reference

I already had a trading journal where I recorded my trades in R-multiples.

The workflow is:

1. Trades are recorded manually in Notion.
2. The journal is exported to CSV.
3. The exported data is cleaned and summarised in Excel.
4. The Excel workbook checks the data, including trade count, sequence continuity, reconciliation to the journal's totals, group totals and drawdown.
5. The resulting statistics provide a reference for the assumptions entered into the simulator.

The journal and workbook are part of my [Trading Performance Analysis Portfolio](https://github.com/Francisos1234/Trading-performance-journal).

I used this approach because I wanted the simulator to be informed by actual recorded trading results rather than relying only on made-up example figures. The inputs can still be changed, so users can explore other hypothetical strategies and assumptions.

### 2. Define the strategy inputs

The simulator includes the following outcome inputs:

- **Win rate (%):** the percentage of trades that close as winners.
- **Break-even rate (%):** the percentage of trades that close at break-even.
- **Loss rate:** automatically derived from the win rate and break-even rate.
- **Average win (R):** the average result of winning trades, expressed in R.
- **Average loss (R):** the average loss, expressed in R.

The application also displays the expectancy per trade based on the entered outcome assumptions.

These values matter because a strategy's performance cannot be understood from win rate alone. The size of its wins and losses, as well as the proportion of break-even trades, also affect the overall result.

### 3. Set the simulation conditions

The user can then choose:

- Risk per trade (%).
- Fixed risk or compounding risk.
- Number of trades to simulate.
- Initial account capital.

These settings determine the conditions under which the hypothetical trading sequences are explored.

### 4. Run the simulations

The application runs 1,000 simulations per run. Each simulation produces a possible sequence of trading outcomes and an equity curve based on the selected inputs.

The purpose is to show that the same underlying assumptions can produce different paths. Some sequences can perform better than others, and some can experience larger drawdowns or longer losing streaks.

I have described the process at the level visible to the user. I have not presented it as a specific historical-trade resampling or bootstrap method, because that would require confirming the exact implementation.

### 5. Compare the results

The results area lets the user review three views:

- **Best:** the strongest result shown among the simulations.
- **Probable:** the result labelled as probable by the application.
- **Worst:** the weakest result shown among the simulations.

For each view, the application displays metrics including:

- Starting balance.
- Ending balance.
- Compounded return.
- Return in R.
- Expectancy per trade.
- Maximum drawdown.
- Maximum consecutive wins.
- Maximum consecutive losses.

The equity curve compares the three paths over the simulated trades.

### 6. Review the probability analysis

The application also displays a probability analysis with categories for:

- Probability of loss.
- Small gain (0–1,000%).
- Medium gain (1,000–2,000%).
- Large gain (2,000% and above).

These categories describe the outcome bands shown in the application. They should be read in the context of the selected assumptions and simulation settings, not as predictions of what a trader will earn.

## Validation

I tested the simulator manually by changing the inputs and running different scenarios.

My checks included:

- Changing the win rate and observing how the results responded.
- Changing the break-even rate and the average win and loss in R.
- Comparing fixed risk with compounding risk.
- Changing the risk-per-trade percentage.
- Changing the number of trades and initial capital.
- Reviewing the best, probable and worst result views.
- Comparing the equity curves and drawdown figures.
- Checking the probability analysis after changing the assumptions.

I also used the statistics from my trading journal as a practical reference for the inputs, rather than relying exclusively on arbitrary example values.

These checks helped me review the behaviour of the application and identify whether the displayed results changed when the assumptions changed. They are manual checks, not an independent audit of the simulation engine or proof that the model accurately predicts future trading performance.

## Limitations

There are important things this project does not establish.

1. **A simulation is not a prediction.** The results show hypothetical outcomes under selected assumptions. They cannot tell a trader what will happen in the future.
2. **Historical performance may not continue.** The statistics from my journal describe a recorded sample. Future market conditions and strategy performance can be different.
3. **The quality of the inputs matters.** An inaccurate win rate, break-even rate or average win and loss can make the outputs misleading.
4. **Trade outcomes may not be independent.** Market conditions can cause wins and losses to cluster. A model based on random sequences may not fully represent those relationships.
5. **A trading sample may be limited.** A small or unrepresentative sample may not capture the full range of outcomes a strategy can experience.
6. **Execution costs may not be fully represented.** Fees, spreads, slippage, missed trades and other real-world trading conditions can affect actual results. Do not assume they are included unless the application explicitly accounts for them.
7. **Risk settings change the outcome.** Fixed risk and compounding risk can produce very different equity curves. Neither setting makes a strategy profitable by itself.
8. **The best and worst paths are not forecasts.** They are outcomes displayed from the simulation runs, not guaranteed boundaries for future performance.
9. **The model has not been independently audited.** My manual testing is not a substitute for an independent review of the calculations or statistical assumptions.

The simulator is best used as a way to explore risk, variability and possible trading paths. It should be considered alongside a properly maintained trading journal and a realistic risk-management plan.

## Evidence and project links

The repository includes screenshots of the actual application, its inputs, result views, equity curves and built-in explanations. The live application is available separately.

- **[Open the live Trading Equity Curve Simulator](https://script.google.com/macros/s/AKfycbzR7RuM7IsYdzRFrOE_peBkDIjyL7Cr9Y_QYdZ8s69bHIu-R3LzBOcDfGvGGGIQ-LY7/exec)**
- **[View the GitHub repository](https://github.com/Francisos1234/Monte-Carlo-Simulator)**

### Screenshots

#### 1. Simulator overview

The main interface shows the outcome assumptions, R-multiple inputs, risk settings, number of trades and initial capital.

![Trading Equity Curve Simulator main interface](1-%20simulator%20overview.png)

#### 2. Probable simulation result

An example of the probable result view, including the account metrics, equity curve and probability analysis.

![Monte Carlo probable simulation result](2-%20simulation%20result.png)

#### 3. Best simulation result

An example of the best result view and its corresponding equity curve.

![Monte Carlo best simulation result](2-%20simulation%20result2.png)

#### 4. Worst simulation result

An example of the worst result view and its corresponding equity curve.

![Monte Carlo worst simulation result](2-%20simulation%20result3.png)

#### 5. Equity curve

A closer view of the three equity curves across the simulated trades.

![Example simulated trading equity curve](3-%20equity%20curve.jpg)

#### 6. Understanding the inputs and FAQs

The application includes explanations of the inputs and frequently asked questions to help users understand the assumptions and interpret the results.

![Simulator input explanations and frequently asked questions](4-%20Understading%20inputs%20and%20FAQs.png)

## Related portfolio pieces

These projects form part of my wider work around trading, performance analysis, risk and practical tools.

- **[Notion Trading Journal](https://keen-aphid-255.notion.site/1d6b72eefb448311bc0881252fd9eff1?v=351b72eefb448242bc4708990c24df04)** — where I manually record my trades and their R-multiple results.
- **[Excel Trading Analysis Workbook](https://docs.google.com/spreadsheets/d/1Zb0AqxhuoKOI4FfsY-HOJ8ML6g8eN37X/edit?usp=sharing)** — used to clean, summarise and validate the journal data.
- **[Trading Performance Analysis Portfolio](https://github.com/Francisos1234/Trading-performance-journal)** — an interactive dashboard built from the prepared journal data, with an R-multiple calendar, equity curve and performance analysis.
- **[Prop Firm Challenge Calculator](https://github.com/Francisos1234/Prop-Firm-Challenge-Calculator)** — explores challenge probability, drawdown limits, risk settings and the potential cost of repeated attempts.
- **[TradeDesk — Free Trading Journal](https://github.com/Francisos1234/Trade-desk-Free-Trading-Journal)** — a browser-based trading journal for recording trades and reviewing performance.

## Disclaimer

This project is for educational and analytical purposes only. It is not financial advice, an investment recommendation or a guarantee of future trading performance. The outputs depend on the inputs, model and simulation settings. The trading statistics used as a reference come from my own journal and are not audited brokerage statements. I have manually tested scenarios, but the simulator has not been independently audited or proven to predict real-world results.
