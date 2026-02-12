🔬 Lab: Refactoring with Multiple Patterns
Scenario: Legacy code that needs modernization.
The Code:
class ReportGenerator:
    def generate(self, report_type: str, data: Any, include_header: bool,
                 include_footer: bool, format: str, compress: bool) -> str:
        result = ""
        
        if include_header:
            if format == "html":
                result += "<html><head><title>Report</title></head><body>"
            elif format == "csv":
                result += "REPORT HEADER\n"
            elif format == "json":
                result += '{"header": true,'
        
        if report_type == "sales":
            sales_data = data  # List[Sale]
            for sale in sales_data:
                if format == "html":
                    result += f"<tr><td>{sale.product}</td><td>{sale.amount}</td></tr>"
                elif format == "csv":
                    result += f"{sale.product},{sale.amount}\n"
                elif format == "json":
                    result += f'{{"product":"{sale.product}","amount":{sale.amount}}},'
        
        elif report_type == "inventory":
            # Similar nested ifs...
            pass
        
        # ... more nested conditions for footer, compression, etc.
        
        return result
