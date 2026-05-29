# Script

## Overview
The subscription tracker script is a client-side JavaScript application embedded directly 
into the site. It allows users to add their subscriptions by entering a name, cost, and 
renewal frequency (weekly, monthly, or yearly). The script converts all costs to a monthly 
equivalent for accurate comparison, flags any subscriptions costing more than $20 per month 
as worth reviewing, and generates a monthly spending report showing the total monthly and 
yearly cost across all tracked subscriptions. This directly addresses the problem outlined 
in the project proposal — helping users stay aware of their subscription spending and avoid 
unnecessary costs.

## Live Output
The script output can be verified live at: https://subtrackr.online

## Code
```javascript
// Array to store all subscriptions added by the user
let subscriptions = [];

// Adds a new subscription to the list
function addSubscription() {
  const name = document.getElementById('subName').value;
  const cost = parseFloat(document.getElementById('subCost').value);
  const frequency = document.getElementById('subFrequency').value;

  // Basic validation — don't add if fields are empty or cost is invalid
  if (!name || isNaN(cost) || cost <= 0) {
    alert('Please enter a valid subscription name and cost.');
    return;
  }

  // Convert all costs to a monthly equivalent for comparison
  let monthlyCost;
  if (frequency === 'weekly') {
    monthlyCost = cost * 4.33; // average weeks in a month
  } else if (frequency === 'yearly') {
    monthlyCost = cost / 12;
  } else {
    monthlyCost = cost;
  }

  // Store the subscription object
  subscriptions.push({ name, cost, frequency, monthlyCost });

  // Clear inputs ready for the next entry
  document.getElementById('subName').value = '';
  document.getElementById('subCost').value = '';

  // Re-render the list and report
  renderList();
  renderReport();
}

// Removes a subscription by its index in the array
function removeSubscription(index) {
  subscriptions.splice(index, 1);
  renderList();
  renderReport();
}

// Renders the subscription list to the page
function renderList() {
  const list = document.getElementById('subList');
  list.innerHTML = '';

  subscriptions.forEach((sub, index) => {
    const item = document.createElement('li');

    // Flag expensive subscriptions (over $20/month) as worth reviewing
    const flag = sub.monthlyCost > 20 ? ' ⚠️ Consider reviewing' : '';

    item.innerHTML = `
      <strong>${sub.name}</strong> — 
      $${sub.cost.toFixed(2)} ${sub.frequency} 
      (~$${sub.monthlyCost.toFixed(2)}/month)
      <em style="color:orange">${flag}</em>
      <button onclick="removeSubscription(${index})">Remove</button>
    `;
    list.appendChild(item);
  });
}

// Generates and displays the monthly spending report
function renderReport() {
  const report = document.getElementById('report');

  // If no subscriptions yet, clear the report
  if (subscriptions.length === 0) {
    report.innerHTML = '';
    return;
  }

  // Add up all monthly costs
  const totalMonthly = subscriptions.reduce((sum, sub) => sum + sub.monthlyCost, 0);
  const totalYearly = totalMonthly * 12;

  // Display the report summary
  report.innerHTML = `
    <h3>Monthly Report</h3>
    <p>Total subscriptions tracked: <strong>${subscriptions.length}</strong></p>
    <p>Estimated monthly spend: <strong>$${totalMonthly.toFixed(2)}</strong></p>
    <p>Estimated yearly spend: <strong>$${totalYearly.toFixed(2)}</strong></p>
    <p><em>Report generated: ${new Date().toLocaleDateString('en-AU', 
      { day: 'numeric', month: 'long', year: 'numeric' })}</em></p>
  `;
}
```

## References
- Let's Encrypt. (2024). *Certbot Documentation*. https://certbot.eff.org
- Mozilla Developer Network. (2024). *JavaScript Array.prototype.reduce()*. 
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce
