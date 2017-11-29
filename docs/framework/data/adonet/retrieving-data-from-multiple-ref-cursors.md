---
title: "Recuperando dados de vários cursores de referência usando uma OracleDataReader"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 502ddb1bd3c271c0d5dbd082eb401f18591594b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="7f81a-102">Recuperando dados de vários cursores de referência usando uma OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="7f81a-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>
<span data-ttu-id="7f81a-103">Este exemplo do Microsoft Visual Basic executa um procedimento armazenado PL/SQL que retorna dois parâmetros REF CURSOR e lê os valores usando um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="7f81a-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click( _  
  ByVal sender As Object, ByVal e As System.EventArgs)  _  
  Handles Button1.Click  
  
  Dim connString As New String( _  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter(_  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
    While (rdr.Read())  
        REM do something with the values from the EMP table   
    End While  
  
    rdr.NextResult()  
    While (rdr.Read())  
        REM do something with the values from the DEPT table   
    End While  
    rdr.Close()  
  End Using  
End Sub   
```  
  
## <a name="see-also"></a><span data-ttu-id="7f81a-104">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f81a-104">See Also</span></span>  
 [<span data-ttu-id="7f81a-105">REF CURSORs do Oracle</span><span class="sxs-lookup"><span data-stu-id="7f81a-105">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="7f81a-106">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7f81a-106">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
