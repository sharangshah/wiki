---
hide:
  - toc
---

# Equity Research

<p class="lede">Company-specific deep dives &mdash; structured analysis, not surface-level coverage.</p>

<div class="gold-rule"></div>

<span class="section-label">Reports</span>

<div class="reports-table-wrapper" markdown>

| Company | Report | Date | Price (Upload) | Price (Live) | Change |
|---|---|---|---:|---:|---:|
| **Venus Pipes** | [Investment Memorandum](venus-pipes.html) | 9 Apr 2026 | &#x20B9;1,126 | <span id="price-VENUSPIPES"></span> | <span id="change-VENUSPIPES"></span> |

</div>

<script>
(function() {
  var EMDASH = String.fromCharCode(0x2014);
  var RUPEE = String.fromCharCode(0x20B9);
  var symbols = [
    { id: "VENUSPIPES", symbol: "VENUSPIPES.NS", uploadPrice: 1126 }
  ];
  symbols.forEach(function(s) {
    var priceEl = document.getElementById("price-" + s.id);
    var changeEl = document.getElementById("change-" + s.id);
    if (!priceEl || !changeEl) return;
    priceEl.textContent = EMDASH;
    changeEl.textContent = EMDASH;
    var base = "https://" + "query1.finance.yahoo.com" + "/v8/finance/chart/";
    fetch(base + s.symbol)
      .then(function(r) { return r.json(); })
      .then(function(data) {
        var price = data.chart.result[0].meta.regularMarketPrice;
        var priceStr = RUPEE + price.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        priceEl.textContent = priceStr;
        var change = ((price - s.uploadPrice) / s.uploadPrice) * 100;
        var sign = change >= 0 ? "+" : "";
        changeEl.textContent = sign + change.toFixed(2) + "%";
        changeEl.style.color = change >= 0 ? "#4ade80" : "#ef4444";
      })
      .catch(function() { });
  });
})();
</script>
