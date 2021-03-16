# Suitebundle-AFIL
Also see connected Approval Flow suitebundle: https://github.com/nordic-netsuite/Suitebundle-AF-Approval-Flow (Mentioned in User guide)
<br>
<h3>Issues & Fixes<h3><br>
I: The Show bill or a link to the vendor bill PDF does not show or work on the Vendor bill Record.<br>
F: Problem is that the field on the Vendor bill to show the link is incorrect. One solution is to find the Custom Transaction Field called custbody_af_bill_imagelink included in the bundle. This field should have type Hyperlink. <br>Edit this field and under the tab validation & Defaulting check the formula checkbox and add {custbody_af_current_ar.custrecord_af_url_attachment} for default value. <br><br>In the vendorMake that field visible in the perferred vendor bill form 
