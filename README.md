// Get the current year and next year
Integer currentYear = Date.today().year();
Integer nextYear = currentYear + 1;

// Query for Quote Line Items that meet the specified criteria
List<QuoteLineItem> quoteLineItems = [
    SELECT PlanType
    FROM QuoteLineItem
    WHERE Quote.Opportunity.EffectiveDate >= :Date.newInstance(currentYear, 1, 1) 
        AND Quote.Opportunity.EffectiveDate < :Date.newInstance(nextYear, 1, 1)
        AND Quote.Status = 'Sold'
];

// Create a Set to store the unique Plan Types
Set<String> planTypes = new Set<String>();

// Add each unique Plan Type to the Set
for (QuoteLineItem qli : quoteLineItems) {
    planTypes.add(qli.PlanType);
}

// Convert the Set to a List and sort the results
List<String> sortedPlanTypes = new List<String>(planTypes);
sortedPlanTypes.sort();

// Display the results
System.debug('Plan Types: ' + sortedPlanTypes);
