---
title: "Internal Table and Flow Control in AMDP"
url: "https://community.sap.com/t5/application-development-and-automation-blog-posts/internal-table-and-flow-control-in-amdp/ba-p/14228671"
date: "Wed, 29 Oct 2025 08:37:26 GMT"
author: "Nihal__Raj"
feed_url: "https://community.sap.com/khhcw49343/rss/board?board.id=application-developmentblog-board"
---
<p><font face="arial black,avant garde"><strong>Introduction:&nbsp; </strong></font>AMDP or ABAP Managed Database Procedure, is a SAP technology that allows database specific procedure (like those written in SQL Script for SAP HANA) to be managed and executed directly from ABAP code. The primary aim of AMDP is to optimize performance by pushing complex data operations to the database layer.</p><p>Important Points:</p><ul><li>While adding interface IF_AMDP_MARKER_HDB. Remember, interfaces can only be added in PUBLIC SECTION.</li><li>Only Variables and Tables are allowed as parameters. We cannot use structures or nested tables.</li><li>Generic types cannot be used for parameters. For example, Type Any cannot be used. Only elementary data types and table types with a structured row type can be used.</li><li>The table type components must be elementary data types and it cannot have elements which are table types.</li><li>Only pass by value can be used. Pass by reference is not permitted. Using VALUE keyword for all parameters is required.</li><li>RETURNING parameters are not allowed. We can use EXPORTING or CHANGING to receive the values.</li><li>Only input parameters can be flagged as optional with a DEFAULT value (literals/constants)</li><li>Every AMDP method will have below addition. READ-ONLY is only the optional addition and is used for methods that only read the data.<br />o BY DATABASE PROCEDURE<br />o FOR HDB<br />o LANGUAGE SQLSCRIPT<br />o OPTIONS READ-ONLY<br />o USING table/view names</li><li>It is also mandatory to specify all the database objects and other AMDP methods that are used within the SQLSCRIPT code.</li><li>No ABAP statements can be written in the method code.</li><li>AMDP methods do not have any implicit enhancement options.</li></ul><p><font face="arial black,avant garde"><strong>Internal Table and Flow Control in AMDP</strong></font></p><p>In AMDP (ABAP Managed Database Procedures), you can declare internal tables using SQL Script. These internal tables are used to store intermediate results and can be manipulated within your AMDP methods.</p>CLASS zrj_amdp_01 DEFINITION
  PUBLIC
  FINAL
  CREATE PUBLIC .

  PUBLIC SECTION.
  TYPES: BEGIN OF ty_spfli,
         mandt TYPE mandt,
         carrid TYPE s_carr_id,
         connid TYPE s_conn_id,
         countryfr TYPE land1,
         countryto TYPE land1,
         END OF ty_spfli.
   TYPES: tt_spfli TYPE TABLE of ty_spfli. 
  INTERFACES: if_amdp_marker_hdb.
  METHODS: get_spfli_details IMPORTING VALUE(iv_mandt) TYPE mandt
                             EXPORTING VALUE(et_spfli) TYPE tt_spfli.
  PROTECTED SECTION.
  PRIVATE SECTION.
ENDCLASS.



CLASS zrj_amdp_01 IMPLEMENTATION.
METHOD get_spfli_details BY DATABASE PROCEDURE FOR HDB LANGUAGE SQLSCRIPT OPTIONS READ-ONLY.
         DECLARE lt_spfli TABLE ( mandt     "$ABAP.type( sy-mandt )",
                                  carrid    "$ABAP.type( S_CARR_ID )",
                                  connid    "$ABAP.type( S_CONN_ID )",
                                  countryfr "$ABAP.type( LAND1 )",
                                  countryto "$ABAP.type( LAND1 )" );
         lt_spfli.mandt[1] := '100';
         lt_spfli.carrid[1] := 'AA';
         lt_spfli.connid[1] := '1000';
         lt_spfli.countryfr[1] := 'DE';
         lt_spfli.countryto[1] := 'US';
         et_spfli = select * from :lt_spfli;
         
ENDMETHOD.
ENDCLASS.<p><strong>Some Useful Internal Table with Operations:</strong><br /><strong>RECORD_COUNT( )</strong> Operator is used to get to know the no of lines in the internal table. So<br />it is likes <strong>LINES( )</strong> <strong>/ DESCRIBE</strong> table in ABAP.<br /><strong>SEARCH()</strong> can be applied on an internal table and it receives two arguments, the column<br />name and the value, if it finds then it returns the index of that record within the internal<br />table.<br /><strong>EXISTS()</strong> tells whether the record exists or not.<br /><strong>IS_EMPTY( )</strong> can be used and we can pass the Internal table name as an argument to it and<br />then it checks the emptiness of the table , it is similar to IS INITIAL check in ABAP.<br /><strong>APPLY_FILTER( )</strong> function can be used on internal table or DB tables to get all the items that<br />match the filter condition.<br /><strong>EXCEPT</strong> use is quite simple. It’s like a minus operation. The result of <strong>EXCEPT</strong> operation is the<br />record set that present in first and not present in the second.</p><p><font face="arial black,avant garde"><strong>Flow Control with IF and Loops</strong></font><br /><strong>Using IF and ELSE</strong><br />If syntax is similar to ABAP but uses additional<strong> THEN</strong> keyword.<br /><strong>Condition can have following</strong></p><ul><li>EXISTS</li><li>Comparison between variables</li><li>IS [NOT] NULL</li><li>IS_EMPTY</li><li>IN</li></ul><p>The conditions can be negated with <strong>NOT</strong>, combined with keywords like<strong> AND</strong>, OR and can be<br />nested.</p>CLASS zrj_amdp_02 IMPLEMENTATION.
METHOD if_statement BY DATABASE PROCEDURE FOR HDB LANGUAGE SQLSCRIPT USING sflight.
  DECLARE lv_result INT;
  DECLARE lv_carrier CONSTANT NVARCHAR(2) := 'AA';
  DECLARE lv_carrier1 CONSTANT NVARCHAR(2) := 'BB';
***Example for EXISTS
  if EXISTS ( select carrid FROM sflight WHERE carrid = '1' )
          THEN lv_result = 1;
   else
               lv_result = 2;
   END if;

***comparision between variables
  if :lv_carrier = :lv_carrier1
           THEN lv_result = 1;
  end if;

*** IN
  if :lv_carrier1 IN( 'AA', 'AB', 'AZ' )
       THEN lv_result = 1;
       end if;

ENDMETHOD.
ENDCLASS.<p><font face="arial black,avant garde"><strong>For Loop</strong></font></p>FOR &lt;variable&gt; IN [REVERSE] &lt;initial_value&gt;..&lt;final_value&gt;  
DO  &lt;block&gt; 
END FOR; <p>The variable is assigned an initial value for the first iteration, incremented or, if you<br />specified REVERSE, decremented with every iteration till final value is reached. Variables<br />declared inside the FOR loop are not visible on the outside.</p><p><font face="arial black,avant garde"><strong>While Loop</strong></font></p>WHILE &lt;condition&gt;  
DO &lt;block&gt;  
END WHILE; <p>Condition block is same as IF statement. BREAK statement can be used to abort the loop.</p>METHOD loop_statement BY DATABASE PROCEDURE FOR HDB LANGUAGE SQLSCRIPT.

    DECLARE lv_sum INT := 0;
    DECLARE lv_index INT := 0;

***       for loop
      for lv_index IN 1..10

          DO
              DECLARE lv_tmp int := lv_sum;
              lv_tmp = lv_tmp + lv_index;
              lv_sum = lv_tmp;

           END for;

***        while loop
       lv_index = 0;
        WHILE lv_index &lt;= 10
              do
                 DECLARE lv_tmp INT := lv_sum;
                 lv_tmp = lv_tmp + lv_index;
                 lv_sum = lv_tmp;
                 lv_index = lv_index + 1;
        END WHILE;<p>While Loop With Break :</p>***        while loop with break
        lv_index = 0;
        WHILE lv_index &lt;= 1000
              DO
                  lv_index = lv_index + 1;
              if  lv_index = 10
              THEN BREAK ;

              END IF;
              END WHILE;

  ENDMETHOD.

ENDCLASS.<p><strong>Conclusion:</strong>&nbsp;Internal tables in AMDP mirror ABAP's data handling but are managed using SQL Script constructs. Flow control allows procedural operations inside the database to optimize logic execution. Together, these enable high-performance, code-pushed data processing-minimizing data transfer between ABAP and database layer and making AMDP ideal for complex analytical logic.</p>
