---
title: メソッドの例 (VBScript) を開いたり閉じたり |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Close method [ADO], VBScript example
- Open method [ADO], VBScript example
ms.assetid: 66eca011-e258-4d8f-bd67-e017bcf0871b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87c8e2c897155c4dc8416dbfdd8ba68ae9191271
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="open-and-close-methods-example-vbscript"></a>Open および Close メソッドの例 (VBScript)
この例では、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)と[閉じる](../../../ado/reference/ado-api/close-method-ado.md)両方のメソッド[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)と[接続](../../../ado/reference/ado-api/connection-object-ado.md)が開かれているオブジェクト。  
  
 アクティブ サーバー ページ (ASP) で次の例を使用します。 使用して**検索**Adovbs.inc ファイルを見つけて、使用する予定のディレクトリに配置します。 次のコードをメモ帳または別のテキスト エディターに貼り付け切り取ってとして保存して**OpenVBS.asp**です。 結果は、任意のブラウザーで表示できます。  
  
```  
<!-- BeginOpenVBS -->  
<%@ Language=VBScript %>  
<%' use this meta tag instead of adovbs.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript"  content=VBScript>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<title>ADO Open Method</title>  
<STYLE>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</STYLE>  
</HEAD>  
  
<BODY>  
<H3>ADO Open Method</H3>  
  
<TABLE WIDTH=600 BORDER=0>  
<TR>  
<TD VALIGN=TOP COLSPAN=3>  
<FONT SIZE=2>  
<% ' to integrate/test this code replace the   
   ' Data Source value in the Connection string%>  
<%   
    ' connection and recordset variables  
    Dim Cnxn, strCnxn  
    Dim rsCustomers, strSQLCustomers  
    Dim rsProducts, strSQLProducts  
  
    ' open connection  
    Set Cnxn = Server.CreateObject("ADODB.Connection")  
    strCnxn = "Provider='sqloledb';Data Source=" & _  
            Request.ServerVariables("SERVER_NAME") & ";" & _  
            "Integrated Security='SSPI';Initial Catalog='Northwind';"  
  
    Cnxn.Open strCnxn  
  
    ' create and open first Recordset using Connection - execute  
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")  
    strSQLCustomers = "SELECT CompanyName, ContactName, City FROM Customers"  
    Set rsCustomers = Cnxn.Execute(strSQLCustomers)   
  
    ' create and open second Recordset using recordset - open  
    Set rsProducts = Server.CreateObject("ADODB.Recordset")  
    strSQLProducts = "SELECT ProductName, UnitPrice FROM Products"  
    rsProducts.Open strSQLProducts, Cnxn, adOpenDynamic, adLockPessimistic, adCmdText  
    %>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Customer Table-->  
    <TR CLASS=thead>  
       <TD>Company Name</TD>  
       <TD>Contact Name</TD>  
       <TD>City</TD>  
    </TR>  
  
    <!--Display ADO Data from Customer Table-->  
    <% Do Until rsCustomers.EOF %>  
    <TR CLASS=tbody>  
      <TD> <%=rsCustomers("CompanyName")%> </TD>  
      <TD> <%=rsCustomers("ContactName")%></TD>  
      <TD> <%=rsCustomers("City")%> </TD>  
    </TR>   
    <%rsCustomers.MoveNext   
    Loop   
    %>  
    </TABLE>  
  
    <HR>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Product List Table-->  
  
    <TR CLASS=thead2>  
       <TD>Product Name</TD>  
       <TD>Unit Price</TD>  
    </TR>  
    <!-- Display ADO Data Product List-->  
    <% Do Until rsProducts.EOF %>  
      <TR CLASS=tbody>    
      <TD> <%=rsProducts("ProductName")%> </TD>  
      <TD> <%=rsProducts("UnitPrice")%> </TD>  
      </TR>  
      <!--  Next Row = Record -->  
    <%rsProducts.MoveNext   
    Loop   
  
    ' clean up  
    If rsProducts.State = adStateOpen then  
        rsProducts.Close  
    End If  
    If rsCustomers.State = adStateOpen then  
        rsCustomers.Close  
    End If  
    If Cnxn.State = adStateOpen then  
        Cnxn.Close  
    End If  
    Set rsProducts = Nothing  
    Set rsCustomers = Nothing  
    Set Cnxn = Nothing  
  
    %>  
    </TABLE>  
  
</BODY>  
</HTML>  
<!-- EndOpenVBS -->  
```  
  
## <a name="see-also"></a>参照  
 [Close メソッド (ADO)](../../../ado/reference/ado-api/close-method-ado.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
