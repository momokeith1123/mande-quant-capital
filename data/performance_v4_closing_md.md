# performance.html — CLOSING BLOCK
# Paste this immediately after the cut-off point in performance_v4_switcher.md
# The cut-off is mid-sentence inside the second .method-card of the Momentum methodology section.
# Replace the incomplete card and paste everything below.
#
# ─── WHERE TO PASTE ───────────────────────────────────────────────────────────
# Find this line in part 1:
#   <p>12-month return, skip 1 month — the
# Delete it and paste from <!-- RESUME --> below in its place.
# ──────────────────────────────────────────────────────────────────────────────

<!-- RESUME: second method-card, completing the momentum methodology section -->

        <div class="method-card">
          <div class="method-num">02 · Academic Signal</div>
          <h3>12-1 Momentum</h3>
          <p>
            12-month return, skip 1 month — the canonical specification from
            Jegadeesh &amp; Titman (1993), validated in decades of academic
            and practitioner research. No signal engineering or parameter tuning.
          </p>
        </div>
        <div class="method-card">
          <div class="method-num">03 · Realistic Costs</div>
          <h3>Net of All Transaction Costs</h3>
          <p>
            10 bps/side transaction cost applied at every monthly rebalance.
            Zero commission (Schwab). All return figures are net — the
            strategy must overcome real friction to show a positive Sharpe.
          </p>
        </div>
        <div class="method-card">
          <div class="method-num">04 · Cross-Sectional Ranking</div>
          <h3>Rank, Not Level</h3>
          <p>
            The signal ranks all stocks by past return each month and
            selects the top and bottom quintile. This removes market-wide
            beta — the portfolio profits from relative performance, not
            from a directional market bet.
          </p>
        </div>
        <div class="method-card">
          <div class="method-num">05 · Regime Coverage</div>
          <h3>Includes Momentum Crash Periods</h3>
          <p>
            The validation period deliberately includes known momentum
            crash environments (2020 reversal, 2022 growth-to-value
            rotation). The reported drawdown reflects these episodes in full —
            no cherry-picking of favourable windows.
          </p>
        </div>
        <div class="method-card">
          <div class="method-num">06 · LSEG Data</div>
          <h3>Institutional Data Source</h3>
          <p>
            All price data sourced from LSEG Refinitiv Data Library
            (lseg.data v2.1.1). Split-adjusted daily closing prices via
            Capital Change History — the same institutional standard
            used for the StatArb strategy.
          </p>
        </div>
      </div><!-- /method-grid -->
    </div><!-- /section-inner -->
  </section>

  <!-- CTA — MOMENTUM -->
  <div class="cta-band">
    <div class="s-tag" style="justify-content:center">Investor Relations</div>
    <h2>Request the Full <span class="gold">Investor Memorandum</span></h2>
    <p>
      Qualified investors may request our complete investor memorandum —
      full walk-forward performance records, methodology documentation,
      risk disclosures, and due diligence materials for both strategies.
    </p>
    <a href="mailto:investors@mandequantcapital.com?subject=Investor%20Memorandum%20Request%20-%20Momentum"
       class="btn-gold">
      Request Memorandum &rarr;
    </a>
  </div>

</div><!-- /view-momentum -->


<!-- ================================================================
     FOOTER (shared — appears regardless of active strategy)
================================================================ -->
<footer>
  <div class="footer-bottom">
    <p>&copy; 2025 Mandé Quant Capital, LP. All rights reserved.</p>
    <span class="mono-tag">precision · discipline · alpha</span>
  </div>
  <div class="disclaimer">
    <strong>Legal Disclaimer:</strong> This website is for informational
    purposes only and does not constitute an offer to sell or a solicitation
    of an offer to buy any security or investment product. All performance
    figures are derived from walk-forward backtesting on LSEG institutional-grade
    CCH-adjusted price data and are not indicative of future results.
    Past performance does not guarantee future results.
    Statistical Arbitrage costs: 2 bps/side + 50 bps/year short borrow.
    Momentum costs: 10 bps/side. Zero commission assumed (Schwab).
    Mandé Quant Capital, LP is intended for qualified and sophisticated
    investors only. All investments involve risk, including the possible loss
    of principal. Nothing on this website constitutes investment, legal,
    or tax advice. Prospective investors should conduct their own due diligence
    and consult appropriate professional advisors before making any investment decision.
  </div>
</footer>


<!-- ================================================================
     JAVASCRIPT — Strategy Switcher
     Pure vanilla JS. No dependencies.

     switchStrategy(id) is called by the two switcher buttons.
     It:
       1. Deactivates both buttons
       2. Activates the chosen button
       3. Hides all .strategy-view divs
       4. Shows the chosen .strategy-view
       5. Scrolls the page to the top of the content area
       6. Updates the browser URL hash (optional — allows deep linking)
================================================================ -->
<script>
  function switchStrategy(id) {
    /* ── 1. Update switcher buttons ─────────────────────────── */
    var buttons = document.querySelectorAll('.switcher-btn');
    buttons.forEach(function(btn) {
      btn.classList.remove('active');
      btn.setAttribute('aria-selected', 'false');
    });
    var activeBtn = document.getElementById('sw-btn-' + id);
    if (activeBtn) {
      activeBtn.classList.add('active');
      activeBtn.setAttribute('aria-selected', 'true');
    }

    /* ── 2. Update strategy views ───────────────────────────── */
    var views = document.querySelectorAll('.strategy-view');
    views.forEach(function(v) { v.classList.remove('active'); });
    var activeView = document.getElementById('view-' + id);
    if (activeView) { activeView.classList.add('active'); }

    /* ── 3. Scroll to top of content (below fixed bars) ─────── */
    window.scrollTo({ top: 0, behavior: 'smooth' });

    /* ── 4. Update URL hash for deep linking ─────────────────── */
    history.replaceState(null, '', '#' + id);
  }

  /* ── On page load: check URL hash and switch if present ──── */
  (function() {
    var hash = window.location.hash.replace('#', '');
    if (hash === 'momentum' || hash === 'statarb') {
      switchStrategy(hash);
    }
  })();
</script>

</body>
</html>


<!-- ================================================================
     CHART FILENAME REFERENCE
     Expected filenames in assets/images/charts/
     (update <img src="..."> tags above if yours differ)
================================================================

  STATISTICAL ARBITRAGE (existing — unchanged):
    chart_cumulative_returns.png
    chart_drawdown.png
    chart_rolling_sharpe.png
    chart_monthly_heatmap.png
    chart_per_pair_performance.png
    chart_trade_distribution.png
    chart_sector_allocation.png

  CROSS-SECTIONAL MOMENTUM (new — from your chart generator):
    chart_momentum_cumulative_returns.png
    chart_momentum_drawdown.png
    chart_momentum_rolling_sharpe.png
    chart_momentum_monthly_heatmap.png
    chart_momentum_long_short_legs.png
    chart_momentum_turnover.png
    chart_momentum_sector_allocation.png

================================================================ -->

<!-- ================================================================
     PLACEHOLDER REPLACEMENT CHECKLIST
     Run: print(strat_m.to_string()) in your notebook
     then find-and-replace each token below.
================================================================

  [YOUR_VALUE]   → replace with actual number (appears 20 times)
  [YEAR_RANGE]   → e.g. 2018–2024  (appears 3 times)
  [CAPITAL_BASE] → e.g. $2M        (appears 1 time)

  In the metrics band, assign your four headline numbers to:
    Sharpe Ratio       → top-left cell
    Max Drawdown       → top-right cell  (include − sign and %)
    Annualised Return  → bottom-left cell
    Win Rate           → bottom-right cell

  In the chart badges, update:
    Max: [YOUR_VALUE]  → your actual max drawdown (drawdown chart badge)
    Avg: [YOUR_VALUE]  → your actual avg Sharpe (rolling sharpe badge)
    Avg: [YOUR_VALUE]% → your actual avg turnover (turnover chart badge)

================================================================ -->
