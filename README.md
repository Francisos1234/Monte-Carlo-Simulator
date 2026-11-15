# Monte Carlo Trading Simulator

Explore how a trading strategy's historical outcomes could unfold across many hypothetical trading sequences.

**Live application:** [Open the Monte Carlo Trading Simulator](https://script.google.com/macros/s/AKfycbzR7RuM7IsYdzRFrOE_peBkDIjyL7Cr9Y_QYdZ8s69bHIu-R3LzBOcDfGvGGGIQ-LY7/exec)

**Repository:** [Francisos1234/Monte-Carlo-Simulator](https://github.com/Francisos1234/Monte-Carlo-Simulator)

An independent project by **Francis Chizurumoke**, developed with coding assistance from Claude.

---

## The idea behind the project

A trading strategy can have positive expectancy and still experience losing streaks, extended periods of weak performance and significant drawdowns. A single backtest or average-return figure does not show the full range of paths that might occur.

I wanted to build a practical way to explore that uncertainty. The idea was to use hypothetical simulations to examine how trading results could be arranged into different sequences and how those sequences might affect an account over time.

The central question is:

> If a strategy continues to produce outcomes resembling the results or assumptions being analysed, what range of trading journeys could occur?

The simulator is intended to help traders think beyond one expected outcome and pay closer attention to variability, drawdowns and risk.

## What Monte Carlo analysis means in trading

Monte Carlo simulation uses repeated random sampling to generate many hypothetical outcomes.

In a trading context, a simulation can construct a sequence of trades, update a hypothetical equity curve as each trade occurs, and repeat the process many times. Each run can produce a different sequence and therefore a different path.

For example, different runs might show:

- A relatively smooth upward equity curve.
- A profitable result after a substantial drawdown.
- A long period of sideways performance.
- Several losses occurring close together.
- A weak final result despite positive assumed expectancy.

The value is in examining a distribution of possible outcomes rather than treating one path as the only possible future.

## How it can help traders

The simulator is intended to support questions such as:

- How variable could the outcomes of this strategy be?
- What might a difficult sequence of trades look like?
- How sensitive are results to the assumptions being used?
- What kinds of drawdowns could occur along the way?
- Is the strategy's average result hiding a wide range of possible experiences?
- How should I think about risk before trading the strategy with real capital?

It is a planning and analytical aid, not a signal generator or a market prediction tool.

## The development story

The project began with my interest in evaluating trading performance through hypothetical simulations. I wanted to move beyond looking only at realised results and explore how different sequences could affect performance.

I approached the build as a practical problem-solving process:

1. **Define the question.** Identify what a trader might want to understand about possible future paths, not just average performance.
2. **Plan the calculation workflow.** Work out the information the model needs and the types of results that would make the analysis useful.
3. **Build the spreadsheet backend.** Use Google Sheets to organise the supporting data and calculations.
4. **Create the interactive application.** Use Google Apps Script to provide a web-based interface to the tool.
5. **Develop with AI assistance.** Use Claude as a coding assistant during implementation, while I directed the concept, requirements, workflow and testing.
6. **Manually stress-test the system.** Run a series of hypothetical scenarios, change assumptions and inspect whether the system responds as expected.

I ran multiple simulations manually to test the system. The results have been encouraging in my own testing so far. This is a description of my testing experience, not a claim of independent statistical validation.

## Technology and structure

| Component | Role |
| --- | --- |
| Google Sheets | Spreadsheet backend for supporting data and calculations |
| Google Apps Script | Application logic and interactive web interface |
| Claude | AI coding assistance during development |

The Apps Script deployment is the public entry point. Google Sheets supports the calculation workflow behind the application.

## Important distinction: simulation method matters

Not all Monte Carlo trading models represent trading results in the same way.

A simplified model may represent every win using one average winning outcome and every loss using one average losing outcome. This is easier to model, but it can hide the range of actual trade results.

An empirical resampling approach instead samples from a collection of historical R-multiples. For example, a historical sample might contain +3R, -1R, +2R, 0R and +4R. Sampling individual observations can preserve the variation in win sizes, losses and breakeven outcomes represented in that sample.

The supporting analysis for this project identified the difference between fixed average outcomes and resampling individual historical R results as an important methodological consideration. The exact method and available inputs in the deployed version should be confirmed against the implementation before assuming that a particular approach is currently used.

## Reading simulation results responsibly

Simulation results are conditional on the model and its assumptions. They are not predictions.

When reviewing an output, consider:

- The source and quality of the trading data.
- Whether the model uses fixed average outcomes or samples individual historical results.
- Whether breakeven trades are represented.
- The number of trades in each simulated sequence.
- The number of simulation runs.
- How drawdown is calculated.
- Whether risk is fixed or changes with account equity.
- Whether the model accounts for fees, slippage or other execution effects.

Percentiles can often describe a distribution more usefully than simply reporting the single best and worst run. For example, the 5th, 50th and 95th percentiles can help show adverse, middle and favourable portions of a simulated distribution. These should only be documented as actual application outputs if confirmed in the live version.

## Limitations

- Historical results may not represent future market conditions.
- Trade outcomes may be correlated rather than independent.
- A sample may be too small or unrepresentative.
- A model may omit changing market regimes, execution costs, slippage or position-sizing effects.
- A simulation does not guarantee that future results will fall within the range observed in the runs.
- A model that does not explicitly implement a risk rule cannot be assumed to account for it.

Use the simulator alongside a broader review of trading records and a risk-management plan.

## Screenshots

Screenshots will be added after the initial repository setup.

Suggested files:

- `screenshots/simulator-overview.png` — main interface.
- `screenshots/simulation-settings.png` — available inputs and settings.
- `screenshots/equity-curves.png` — example simulated paths.
- `screenshots/results-summary.png` — results and summary metrics.

## Related project

The companion [Prop Firm Challenge Calculator](https://github.com/Francisos1234/Prop-Firm-Challenge-Calculator) focuses on the relationship between challenge targets, drawdown boundaries and trading assumptions.

My broader [Trading Performance Journal project](https://github.com/Francisos1234/Trading-performance-journal) documents a separate trading-performance analysis workflow.

## Disclaimer

This project is for educational and analytical purposes only. It is not financial advice, an investment recommendation or a guarantee of future trading performance. All simulated results depend on the model, data and assumptions used.
