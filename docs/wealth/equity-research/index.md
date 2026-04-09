---
hide:
  - toc
---

# Equity Research

<p class="lede">Company-specific deep dives — structured analysis, not surface-level coverage.</p>

<div class="gold-rule"></div>

<span class="section-label">Reports</span>

<div class="reports-table-wrapper" markdown>

| Company | Report | Date | Price (Upload) | Price (Live) | Change |
|---|---|---|---:|---:|---:|
| **Venus Pipes** | [Investment Memorandum](venus-pipes.html) | 9 Apr 2026 | \u20B91,126 | <span id="price-VENUSPIPES">\u2014</span> | <span id="change-VENUSPIPES">\u2014</span> |

</div>

<script>
(function() {
  var symbols = [
    { id: 'VENUSPIPES', query: 'VENUSPIPES.NS', uploadPrice: 1126 }
  ];
  symbols.forEach(function(s) {
    var priceEl = document.getElementById('price-' + s.id);
    var changeEl = document.getElementById('change-' + s.id);
    if (!priceEl || !changeEl) return;
    fetch('https://query1.finance.yahoo.com/v8/finance/chart/' + s.query + '?interval=1d&range=1d')
      .then(function(r) { return r.json(); })
      .then(function(data) {
        var meta = data.chart.result[0].meta;
        var livePrice = meta.regularMarketPrice;
        var pct = ((livePrice - s.uploadPrice) / s.uploadPrice * 100).toFixed(1);
        priceEl.textContent = '\u20B9' + livePrice.toLocaleString('en-IN', {maximumFractionDigits: 0});
        var sign = pct >= 0 ? '+' : '';
        changeEl.textContent = sign + pct + '%';
        changeEl.style.color = pct >= 0 ? '#4CAF50' : '#F44336';
      })
      .catch(function() {
        priceEl.textContent = '\u2014';
        changeEl.textContent = '\u2014';
      });
  });
})();
</script>
