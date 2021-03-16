# Suitebundle-AFIL
Also see connected Approval Flow suitebundle: https://github.com/nordic-netsuite/Suitebundle-AF-Approval-Flow (Mentioned in User guide)
<br>
<h3>Issues & Fixes</h3><br>
I: The Show bill or a link to the vendor bill PDF does not show or work on the Vendor bill Record.<br>
F: Problem is that the field on the Vendor bill to show the link is incorrect. One solution is to find the Custom Transaction Field called custbody_af_bill_imagelink included in the bundle. This field should have type Hyperlink. <br>Edit the field and under the tab validation & Defaulting check the formula checkbox and add {custbody_af_current_ar.custrecord_af_url_attachment} for default value (or what the AF approval records name is). <br>On the vendor bill make sure that the field is showing (is often hidden among the fields in the Custom tab. Move it to the Main section and you should now have a hyperlink that opens the PDF url sent from scancloud.<br><br>
I: The saved Search Non-Created Bills is not showing correct results<br>
F: This Search should only show results where there is a Invoice Log record but something has prevented the creation of a standard vendor bill record in NetSuite. First you need to alter the citerias for the saved search. Set a critera as: Formula (text) - is Empty - '''{custrecord_afil_buyer}.'''<br>
In the Results - make sure that there is a Formula (text) as: <br>
'''
DECODE({custrecord_afil_supplier},NULL,'Leverantör')||' '||DECODE({custrecord_afil_bill_gross_amount},NULL,'Bruttobelopp')||' '||DECODE({custrecord_afil_bill_currency},NULL,'Valuta')||'  '||DECODE({custrecord_afil_supplier.terms},NULL,'Bet.villkor')||' '||DECODE({custrecord_afil_supplier.expenseaccount},NULL,'Kostnadskonto')||' '||DECODE({custrecord_afil_bill_vat_amount},NULL,'Momsbelopp')||' '||DECODE({custrecord_afil_bill_date},NULL,'Fakturadatum')||''||DECODE({custrecord_afil_bill_gross_amount},0,'Bruttobelopp är noll')
'''
