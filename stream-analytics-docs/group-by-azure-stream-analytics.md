---
title: "GROUP BY (Azure Stream Analytics) | Microsoft Docs"
description: "Groups a selected set of rows into a set of summary rows by the values of one or more columns or expressions."
applies_to: 
  - "Azure"
services: stream-analytics
author: mamccrea


ms.service: stream-analytics
ms.topic: reference
ms.assetid: 6ae879ff-435d-44e3-bbc7-09cbd399a502
caps.latest.revision: 11
ms.workload: data-services
ms.date: 04/22/2016
ms.author: mamccrea
---
# GROUP BY (Azure Stream Analytics)
  Groups a selected set of rows into a set of summary rows by the values of one or more columns or expressions. One row is returned for each group. Aggregate functions in the SELECT clause’s \<select> list provide information about each group instead of individual rows.  
  
 ## Syntax  
  
```SQL   
GROUP BY <group by spec>  
  
<group by spec> ::=  
    <group by item> [ ,...n ]  
    | <window_type> | System.Timestamp()  
  
<group by item> ::=  
    <column_expression>  
  
```  
  
 Either <window_type> or System.Timestamp() is required, \<group by item> is optional.  <window_type> and a sequence of \<group by items> can appear in any order.  
  
## Arguments  
 **<window_type>**  
  
 Specifies any Azure Stream Analytics supported Windowing. See [Windowing &#40;Azure Stream Analytics&#41;](windowing-azure-stream-analytics.md).  
  
 **\< column_expression >**  
  
 Is the expression or the name of the column on which the grouping operation is performed. The column expression cannot contain a column alias that is defined in the SELECT list.
  
## Example  
  
```SQL  
SELECT TollId, System.Timestamp() AS WinEndTime, COUNT(*)   
FROM TollTagEntry TIMESTAMP BY EntryTime  
GROUP BY TumblingWindow( minute , 3 ) , TollId  
```  
  
## See Also  
 [System.Timestamp()](system-timestamp-stream-analytics.md)   
 [Windowing](windowing-azure-stream-analytics.md)  
  
  
