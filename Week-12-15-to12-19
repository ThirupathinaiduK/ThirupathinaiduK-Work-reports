# Week-12-15-to12-19
Work reports

## Employee Name: Thirupathinaidu K
## Role: Software Developer (.NET / C#)
## Week: Dec 15 – Dec 29, 2025

## 🔹 Weekly Summary
- Practiced C# programming and .NET concepts
- Worked on GitHub repository updates
- Improved understanding of real-time coding scenarios
- Documented daily learning progress

---

## 📅 Daily Work Log

### Monday
- Total Hours: 8

 Invoice Amount Calculation Problem Problem: Calculate invoice total based on base amount, tax percentage, and optional discount. C# Solution Implemented:

public decimal CalculateInvoiceTotal(decimal baseAmount, decimal taxPercent, decimal discount) { decimal taxAmount = (baseAmount * taxPercent) / 100; return baseAmount + taxAmount - discount; } Work Done:

Implemented business logic in C# service layer
Verified calculations with multiple test cases
Updated API to use centralized calculation method

### Tuesday
- Total Hours: 8
- Invoice Validation Problem Problem: Ensure invoices are valid before saving (no empty customer, amount > 0, valid date). C# Solution Implemented:

public bool IsInvoiceValid(Invoice invoice) { if (invoice == null) return false; if (string.IsNullOrWhiteSpace(invoice.CustomerId)) return false; if (invoice.TotalAmount <= 0) return false; if (invoice.InvoiceDate > DateTime.Now) return false;
public bool ValidateInvoice(Invoice invoice)
{
    if (invoice == null)
        return false;

    if (string.IsNullOrWhiteSpace(invoice.CustomerId))
        return false;

    if (invoice.TotalAmount <= 0)
        return false;

    if (invoice.InvoiceDate > DateTime.Now)
        return false;

    return true;
}


Work Done:

Added validation logic before database save
Prevented invalid invoices from being stored
Improved error handling in Web API

### Wednesday
- Total Hours: 8
Filter & Search Invoices Problem Problem: Retrieve pending invoices created in the last 30 days. C# LINQ Solution:

var recentPendingInvoices = _context.Invoices .Where(i => i.Status == "Pending" && i.InvoiceDate >= DateTime.Today.AddDays(-30)) .OrderByDescending(i => i.InvoiceDate) .ToList();
var recentPendingInvoices = _context.Invoices
    .Where(i => i.Status == "Pending"
             && i.InvoiceDate >= DateTime.Today.AddDays(-30))
    .OrderByDescending(i => i.InvoiceDate)
    .ToList();

Work Done:

Implemented LINQ-based filtering
Optimized database query performance
Connected API response to UI invoice grid

### Thursday
- Total Hours: 8

Async API Performance Problem Problem: Avoid blocking threads while fetching invoice data. C# Async/Await Solution:

public async Task<List> GetInvoicesAsync() { return await _context.Invoices .AsNoTracking() .ToListAsync(); }
public async Task<IReadOnlyList<Invoice>> GetInvoicesAsync()
{
    return await _context.Invoices
        .AsNoTracking()
        .ConfigureAwait(false)
        .ToListAsync();
}
Work Done:

Converted synchronous APIs to async
Improved application performance under load
Verified response time improvements

### Friday
- Total Hours: 8

Error Handling & Logging Problem Problem: Capture runtime errors during invoice processing without crashing the system. C# Exception Handling Solution:

public void ProcessInvoice(Invoice invoice) { try { SaveInvoice(invoice); } catch (Exception ex) { _logger.LogError(ex, "Invoice processing failed"); throw; } }
public async Task<bool> ProcessInvoiceAsync(Invoice invoice)
{
    try
    {
        if (invoice == null)
            throw new ArgumentNullException(nameof(invoice));

        // Invoice processing logic
        _context.Invoices.Add(invoice);
        await _context.SaveChangesAsync();

        return true;
    }
    catch (DbUpdateException ex)
    {
        _logger.LogError(ex, "Database error while processing Invoice {InvoiceId}", invoice?.Id);
        return false;
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Unexpected error occurred while processing invoice");
        return false;
    }
}

Work Done:

Implemented centralized exception handling
Added logging for production debugging
Wrote MSTest unit tests for error scenarios
Fixed defects and updated documentation
