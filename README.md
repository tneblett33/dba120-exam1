# dba120-exam1

EX1

This inserted a row with the specified values.

INSERT INTO terms
  (terms_id, terms_description, terms_due_days)
VALUES
  (6, 'Net due 120 days', 120)

![Ch5_ex1_results](https://user-images.githubusercontent.com/122377083/216854246-da663a43-bc01-4e04-9d31-cea63e8cb91f.png)

EX2

This updated the terms-description numerical value from 120 to 125.

UPDATE terms
SET terms_description = 'Net due 125 days'
WHERE terms_description = 'Net due 120 days'

![Ch5_ex2_results](https://user-images.githubusercontent.com/122377083/216854258-d5df9b63-f070-4611-8e7c-b8a1888cad5c.png)

EX3

This deleted the row previously added.

DELETE FROM terms
WHERE terms_id = 6

![Ch5_ex3_results](https://user-images.githubusercontent.com/122377083/216854265-9f7ba27d-364c-46fd-85dd-b547fd1dbaf1.png)

EX4

This inserted a row into invoices with the specified values.

INSERT INTO invoices VALUES
(DEFAULT, 32, 'AX-014-027', '8/1/2018', '434.58', DEFAULT, DEFAULT, 2, '8/31/2018', NULL)

![Ch5_ex4_results](https://user-images.githubusercontent.com/122377083/216854279-14271fda-ec59-4cc8-acef-f349f6fd3351.png)

EX5

This inserted two rows with the same id into invoice_line_items.

INSERT INTO invoice_line_items VALUES 
(115, 1, 160, '180.23', 'Hard Drive')
(115, 2, 527, '254.35', 'Exchange Server update')

![Ch5_ex5_results](https://user-images.githubusercontent.com/122377083/216854288-94f1effe-5d48-4d3a-8f41-1e550f5956f7.png)

EX6

This updated the credit_total to be 10% of invoice_total and payment_total was updated to equal the invoice_total when added to credit_total.

UPDATE invoices
SET credit_total = invoice_total * .1,
	payment_total = invoice_total - credit_total
WHERE invoice_id = 115

![Ch5_ex6-results](https://user-images.githubusercontent.com/122377083/216854301-a50c7f84-aaec-436b-9dfc-698e8cd6c8e1.png)

EX7

This updated the default_account_number to 403 where vendor_id was 44.

UPDATE vendors
SET default_account_number = 403
WHERE vendor_id = 44

![Ch5_ex7_results](https://user-images.githubusercontent.com/122377083/216854320-834ba004-5fbb-4e8b-90ad-5a76d8e8e7da.png)

EX8

This updated all the terms_id in invoices to 2 where default_terms_id equaled 2 in the vendors table.

UPDATE invoices
SET terms_id = 2
WHERE vendor_id IN (SELECT vendor_id FROM vendors WHERE default_terms_id = 2) 

![Ch5_ex8_results](https://user-images.githubusercontent.com/122377083/216854338-9940e32a-b7b3-47fa-9f78-d5658f6f8640.png)

EX9

This deleted the two previously added rows in invoice_line items and one previously added row in invoices.

DELETE FROM invoice_line_items
WHERE invoice_id = 115;
DELETE FROM invoices
WHERE invoice_id = 115;

![Ch5_ex9_results](https://user-images.githubusercontent.com/122377083/216854345-2cbef504-756c-4bcf-a96b-8358fa4f2225.png)
