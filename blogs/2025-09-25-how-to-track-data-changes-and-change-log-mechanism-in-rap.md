---
title: "How to Track Data Changes and Change Log Mechanism in RAP."
url: "https://community.sap.com/t5/application-development-and-automation-blog-posts/how-to-track-data-changes-and-change-log-mechanism-in-rap/ba-p/14222838"
date: "Thu, 25 Sep 2025 04:41:18 GMT"
author: "Gireesh_pg1"
feed_url: "https://community.sap.com/khhcw49343/rss/board?board.id=application-developmentblog-board"
---
<p>Hi,</p><p>A change log table is a simple yet effective way to track data modifications without storing the complete historical snapshots of records. While the main table continues to hold only the active business data, the change log table captures essential metadata such as the record identifiers, type of change, user, and reason for the update. In a RAP scenario, determinations during the save sequence record these details before the final commit, ensuring a reliable audit trail. This approach not only supports compliance monitoring, reporting, and troubleshooting but also minimizes storage and performance overhead compared to maintaining full shadow tables.</p><p><strong><span class=""><span class="">Here we see some major key </span><span class="">Advantages</span><span class="">.</span></span><span class="">&nbsp;</span></strong></p><ul><li><strong><span>Simplified Design</span></strong><span> – Only one additional table is needed, making the data model and maintenance simpler.</span><span>&nbsp;</span></li></ul><ul><li><strong><span>Faster Reporting on Changes</span></strong><span> – The log contains concise, relevant details, making it easier to query and generate audit reports.</span><span>&nbsp;</span></li></ul><ul><li><strong><span>Regulatory Compliance</span></strong><span> – Still fulfills many compliance and audit requirements by showing who changed what and when.</span><span>&nbsp;</span></li></ul><p><strong><span class="">Step</span><span class="">s to </span><span class="">achiev</span><span class="">ing</span><span class="">&nbsp;</span><span class=""> the</span> <span class="">Track Change Log Mechanism in RAP</span></strong></p><p><span>I have create 2 database tables&nbsp;</span><span>&nbsp;</span></p><ol><li><span>For basic details</span><span>&nbsp;</span></li><li><span><span class=""><span class="">Capturing the changes record table</span></span><span class="">&nbsp;</span></span></li></ol>@EndUserText.label : 'log chanes' 

@AbapCatalog.enhancement.category : #NOT_EXTENSIBLE 

@AbapCatalog.tableCategory : #TRANSPARENT 

@AbapCatalog.deliveryClass : #A 

@AbapCatalog.dataMaintenance : #RESTRICTED 

define table zgiri_t_emp_det { 
key id : abap.int8 not null; 

name : abap.char(30); 

department : abap.char(30); 

curr_key : abap.cuky; 

@Semantics.amount.currencyCode : ' zgiri_t_emp_det.curr_key' 

salary : abap.curr(15,2); 

created_by : syuname; 

created_at : timestampl; 

changed_by : syuname; 

changed_at :timestampl; 

} 

 <p><span><span class=""><span class=""><span class="">Table 2.</span></span><span class="">&nbsp;</span></span></span></p>@EndUserText.label : 'log chanes' 

@AbapCatalog.enhancement.category : #NOT_EXTENSIBLE 

@AbapCatalog.tableCategory : #TRANSPARENT 

@AbapCatalog.deliveryClass : #A 

@AbapCatalog.dataMaintenance : #RESTRICTED 

define table zgiri_t_ch_log1 { 

key id : abap.int8 not null; 

name : abap.char(30); 

old_value : abap.string(0); 

new_value : abap.string(0); 

changed_by : syuname; 

changed_at : timestampl; 

} 

 <p><strong>Step2.&nbsp;</strong></p><p><span>We have to create root view&nbsp; on top of the database table.</span><span>&nbsp;</span></p>@AbapCatalog.viewEnhancementCategory: [#NONE] 

@AccessControl.authorizationCheck: #NOT_REQUIRED 

@EndUserText.label: 'employee details' 

@Metadata.ignorePropagatedAnnotations: true 

@ObjectModel.usageType:{ 

serviceQuality: #X, 

sizeCategory: #S, 

dataClass: #MIXED 

} 

define view entity zgiri_i_empl1_details as select from ZGIRI_T_emp_det 

association [0..*] to zgiri_i_ch_log1 as _change on _change.id = $projection.id 

{ 

key id as Id, 

name as Name, 

department as Department, 

curr_key as CurrKey, 

@semantics.amount.currencyCode: 'CurrKey' 

salary as Salary, 

created_by as CreatedBy, 

created_at as CreatedAt, 

changed_by as ChangedBy, 

changed_at as ChangedAt, 

_change 

} 

 <p><span class=""><span class="">Then we </span><span class="">have to</span><span class=""> create data </span><span class="">definition</span><span class=""> for </span><span class="">change</span> <span class="">log</span><span class=""> also.</span></span><span class="">&nbsp;</span></p>@AbapCatalog.viewEnhancementCategory: [#NONE] 

@AccessControl.authorizationCheck: #NOT_REQUIRED 

@EndUserText.label: 'employee details' 

@Metadata.ignorePropagatedAnnotations: true 

@ObjectModel.usageType:{ 

serviceQuality: #X, 

sizeCategory: #S, 

dataClass: #MIXED 

} 

define view entity zgiri_i_empl1_details as select from zgiri_i_ch_log1 

association [1..1] to zgiri_i_emp_det as _emp on _change.id = $projection.id 

{ 

key id as Id, 

field_name as Field_name, 

old_value as OldValue, 

new_value as NewValue, 

created_by as CreatedBy, 

_emp 

} 

 <p>&nbsp;</p><p><strong><span class=""><span class="">Step 3.</span></span><span class="">&nbsp;</span></strong></p><p><strong><span class=""><span class=""><span class="">for the basic data </span><span class="">definition</span><span class=""> we have </span><span class="">create</span><span class=""> on metadata extension for front end display.</span></span><span class="">&nbsp;</span></span></strong></p>@Metadata.layer:#CORE 

annotate entity zgiri_i_empl_details 

with  

{ 

@UI.facet: [  

{  

id: 'object', 

label: 'Basic Data', 

type: #IDENTIFICATION_REFERENCE, 

purpose: #STANDARD, 

position: 10 }] 

 

@UI.lineItem: [{ label: 'Id' , position: 10 }] 

@UI.identification: [{ label: 'Id' , position: 10 }] 

Id; 

@UI.lineItem: [{ label: 'Name' , position: 20 }] 

@UI.identification: [{ label: 'Name' , position: 20 }] 

Name; 

@UI.lineItem: [{ label: 'Department' , position: 30 }] 

@UI.identification : [{ label: 'Department' , position: 30 }] 

Department; 

@UI.lineItem: [{ label: 'CurrKey' , position: 40 }] 

@UI.identification : [{ label: 'CurrKey' , position: 40 }] 

CurrKey; 

@UI.lineItem: [{ label: 'Salary' , position: 50 }] 

@UI.identification : [{ label: 'Salary' , position: 50 }] 

Salary; 

@UI.lineItem: [{ label: 'CreatedBy' , position: 60 }] 

CreatedBy; 

@UI.lineItem: [{ label: 'CreatedAt' , position: 70 }] 

CreatedAt; 

@UI.lineItem: [{ label: 'ChangedBy' , position: 80 }] 

ChangedBy; 

@UI.lineItem: [{ label: 'ChangedAt' , position: 90 }] 

ChangedAt; 

} 

 <p><strong>Step 4.&nbsp;</strong></p><p><strong>On top of the basic view we have to behavior definition.&nbsp;</strong></p>managed implementation in class zbp_giri_i_empl_details unique; 

strict ( 2 ); 

define behavior for zgiri_i_empl_details //alias &lt;alias_name&gt; 

persistent table zgiri_t_emp_det 

lock master 

with additional save 

authorization master ( instance ) 

early numbering 

//etag master &lt;field_name&gt; 

{ 

create ( authorization : global ); 

update; 

delete; 

field ( readonly ) Id; 

mapping for zgiri_t_emp_det 

{ 

ChangedAt = changed_at; 

ChangedBy = changed_by; 

CreatedAt = created_at; 

CreatedBy = created_by; 

CurrKey = curr_key; 

Department = department; 

Id = id; 

Name = name; 

Salary = salary; 

} 

} 

 <p>&nbsp;</p><p><span class=""><span class="">On </span><span class="">top</span><span class=""> the consumption view </span><span class="">i</span><span class=""> have </span><span class="">create</span><span class=""> behavior definition for consumption view.</span></span><span class="">&nbsp;</span></p><p>&nbsp;</p>projection; 

strict ( 2 ); 

define behavior for zgiri_c_empl //alias &lt;alias_name&gt; 

{ 

use create; 

use update; 

use delete; 

} 

 <p><strong><span class=""><span class="">I'm</span><span class=""> implementing logic in this class.</span></span><span class="">&nbsp;</span></strong></p>CLASS lsc_zgiri_i_empl_details DEFINITION INHERITING FROM cl_abap_behavior_saver. 

PROTECTED SECTION. 

METHODS save_modified REDEFINITION. 

ENDCLASS. 

CLASS lsc_zgiri_i_empl_details IMPLEMENTATION. 

METHOD save_modified. 

DATA lt_log TYPE STANDARD TABLE OF zgiri_t_ch_logs1. 

DATA lt_log1 TYPE STANDARD TABLE OF zgiri_t_ch_logs1. 


IF update-zgiri_i_empl_details iS NOT INITIAL. 

lt_log = CORRESPONDING #( update-zgiri_i_empl_details ). 

LOOP AT update-zgiri_i_empl_details ASSIGNING FIELD-SYMBOL(&lt;ls_log_update&gt;). 

ASSIGN lt_log[ id = &lt;ls_log_update&gt;-Id ] TO FIELD-SYMBOL(&lt;ls_log_u&gt;) .  

* / NAME UPDATE......................................... 

if &lt;ls_log_update&gt;-%control-Name = if_abap_behv=&gt;mk-on. 

&lt;ls_log_u&gt;-name = &lt;ls_log_update&gt;-Name. 

 TRY. 

&lt;ls_log_u&gt;-id = cl_system_uuid=&gt;create_uuid_x16_static( ). 

CATCH cx_uuid_error. 

"handle exception 

ENDTRY. 

APPEND &lt;ls_log_u&gt; TO lt_log1. 


ENDIF. 

ENDLOOP. 
INSERT zgiri_t_ch_logs1 FROM TABLE _log1. 

ENDIF. 
ENDMETHOD. 
ENDCLASS. 

CLASS lhc_zgiri_i_empl_details DEFINITION INHERITING FROM cl_abap_behavior_handler. 

PUBLIC SECTION. 

PRIVATE SECTION. 
METHODS get_instance_authorizations FOR INSTANCE AUTHORIZATION 

IMPORTING keys REQUEST requested_authorizations FOR zgiri_i_empl_details RESULT result. 

METHODS get_global_authorizations FOR GLOBAL AUTHORIZATION 

IMPORTING REQUEST requested_authorizations FOR zgiri_i_empl_details RESULT result. 

METHODS earlynumbering_create FOR NUMBERING 

IMPORTING entities FOR CREATE zgiri_i_empl_details. 

ENDCLASS. 

CLASS lhc_zgiri_i_empl_details IMPLEMENTATION. 

METHOD get_instance_authorizations. 

ENDMETHOD. 

METHOD get_global_authorizations. 

ENDMETHOD. 

METHOD earlynumbering_create. 

DATA(lt_entities) = entities. 

DELETE lt_entities WHERE Id IS NOT INITIAL. 

TRY. 

cl_numberrange_runtime=&gt;number_get( 

EXPORTING 

nr_range_nr = '01' 

object = '/DMO/TRV_M' 

quantity = CONV #( lines( lt_entities ) ) 

IMPORTING 

number = DATA(lv_latest_num) 

returncode = DATA(lv_code) 

returned_quantity = DATA(lv_qty) 

). 

CATCH cx_nr_object_not_found. 

CATCH cx_number_ranges INTO DATA(lo_error). 

LOOP AT lt_entities INTO DATA(ls_entities). 

APPEND VALUE #( %cid = ls_entities-%cid 

%key = ls_entities-%key ) 

TO failed-zgiri_i_empl_details. 

APPEND VALUE #( %cid = ls_entities-%cid 

%key = ls_entities-%key 

%msg = lo_error ) 

TO reported-zgiri_i_empl_details. 

ENDLOOP. 

EXIT. 

ENDTRY. 

ASSERT lv_qty = lines( lt_entities ). 

* DATA: lt_travel_tech_m TYPE TABLE FOR MAPPED EARLY yi_travel_tech_m, 

* ls_travel_tech_m LIKE LINE OF lt_travel_tech_m. 

DATA(lv_curr_num) = lv_latest_num - lv_qty. 

LOOP AT lt_entities INTO ls_entities. 

lv_curr_num = lv_curr_num + 1. 

 APPEND VALUE #( %cid = ls_entities-%cid 

ID = lv_curr_num ) 

TO mapped-zgiri_i_empl_details. 

ENDLOOP. 

ENDMETHOD. 

ENDCLASS. 
 <p>&nbsp;</p><p><span class=""><span class="">On </span><span class="">top</span><span class=""> the behavior definition we </span><span class="">have to</span><span class=""> create service definition.</span></span><span class="">&nbsp;</span></p>@EndUserText.label: 'service definition' 

define service Zgiri_rap_scn_ser { 

expose zgiri_i_empl_details; 

} 

 <p><span class="">On </span><span class="">top</span><span class=""> the service definition we </span><span class="">have to</span> <span class="">create&nbsp; service</span><span class=""> binding.</span></p><p><span class="lia-inline-image-display-wrapper lia-image-align-inline" style="width: 999px;"><img alt="Gireesh_pg1_0-1758351322351.png" src="https://community.sap.com/t5/image/serverpage/image-id/317140i5F32DECD8FC7E04B/image-size/large?v=v2&amp;px=999" title="Gireesh_pg1_0-1758351322351.png" /></span></p><p>&nbsp;</p><p>after that we can preview our application.</p><p><span class="lia-inline-image-display-wrapper lia-image-align-inline" style="width: 999px;"><img alt="Gireesh_pg1_1-1758351367587.png" src="https://community.sap.com/t5/image/serverpage/image-id/317141i4B3553A7EEA41EAF/image-size/large?v=v2&amp;px=999" title="Gireesh_pg1_1-1758351367587.png" /></span></p><p><span class=""><span class="">Im</span><span class="">&nbsp;taking name as example im going to update </span><span class="">the name sham signiwis this</span><span class=""> value.&nbsp;</span></span><span class="">&nbsp;</span></p><p><span class="lia-inline-image-display-wrapper lia-image-align-inline" style="width: 999px;"><img alt="Gireesh_pg1_2-1758351455028.png" src="https://community.sap.com/t5/image/serverpage/image-id/317142i596B16B27E70597F/image-size/large?v=v2&amp;px=999" title="Gireesh_pg1_2-1758351455028.png" /></span></p><p>see we can update shyam prasad.</p><p><span class=""><span class="">A</span><span class="">n</span><span class="">d</span><span class=""> we see in the </span><span class="">chang</span><span class=""> log table.</span></span><span class="">&nbsp;</span></p><p><span class="lia-inline-image-display-wrapper lia-image-align-inline" style="width: 999px;"><img alt="Gireesh_pg1_3-1758351498242.png" src="https://community.sap.com/t5/image/serverpage/image-id/317143i5F6092F28B51C037/image-size/large?v=v2&amp;px=999" title="Gireesh_pg1_3-1758351498242.png" /></span></p><p>thank you&nbsp;<br />if u have any query reach out me</p><p>&nbsp;</p><p>&nbsp;</p><p>&nbsp;</p><p>&nbsp;</p><p>&nbsp;</p>
