# thiết kế ca sử dụng trong hệ thống
## 1. BankSystem
Operations:
- deposit(Paycheck, BankInformation)
- create(Deposit, amount, routingNumber)
- submit(BankTransaction)
  
States:
- Initialized
- PendingTransaction
- Completed
  
Attributes:
- bankName: String
- routingNumber: String

Dependencies/Associations:
- Quan hệ với lớp Paycheck, BankTransaction.

![](https://www.planttext.com/api/plantuml/png/V92n3S8m44LxJ-4I2XP8WI8wEYHWWCCvX1LyjiwN8hDHC18hO2EPc4IYVU_xV-jUZsSR1LW6TrTWnBC-HsGL4hB61Y3H1nZD3Kt_0tT0_N6CWcw1JmmKKvVrj71xkdfsy74gB-dDzZlGQCC8WgkrAYZhQQhH7GOVhQJ4H4kcsgsQPgQ4gu_CmdzAut1nLYgKdgWMgSlNUmC00F__0m00)
##  2. PrintService
Operations:
- print(Paycheck, Printer)
- buildPrintImage(Paycheck)
  
States:
- ReadyToPrint
- Printing
- Printed
  
Attributes:
- printerName: String
- printerType: String
  
Dependencies/Associations:
- Quan hệ với lớp PaycheckPrinterImage, Paycheck, Employee.
  
![](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aK9eSMeHLm5GA3Cvio0nhqGXe2WphoGujQWiCpaLKm9TSM9bSaPgSZPMGQW6pzp4z5GkBf152hfsAEPRAHIb5fQc5fU01JKqkP0bCHKdbMRcf825m6PYKu_5QYk5vABKn99Kd7eWQgqK2g2Eu798pKi1XH00003__mC0)
3. ProjectManagementDatabase
Operations:
getChargeNumbers(String)
initialize()

States:
- Connected
- RetrievingData
- DataRetrieved
  
Attributes:
- connectionString: String
  
Dependencies/Associations:
- Quan hệ với ChargeNumList, Connection.

![](https://www.planttext.com/api/plantuml/png/X90n3i8m34Ltdo8Z35oW0wgWAuY50xZXAnIHjDZEwHWu4bU0Z0sgMAt_tl_o-_bgrLWinpknjr7SMI4qVK-37oPEvauotk3jm8a38f9rRDopOfRgTlihIy0nnnwYHCNZDjjbl762HuRQ35ojQP4ekggdSG4_WYhpTuLbIRM3MgHB-Se7003__mC0)
