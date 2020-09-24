---
title: Recuperar dados de vários REF CURSORs usando um OracleDataReader
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 5f0c50cb2c1ec4581c67d2f055e5bf50a82f4809
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150642"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a>Recuperar dados de vários REF CURSORs usando um OracleDataReader

Este exemplo de Visual Basic da Microsoft executa um procedimento armazenado PL/SQL que retorna dois parâmetros de CURSOR de referência e lê os valores usando um <xref:System.Data.OracleClient.OracleDataReader> .  
  
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
  
## <a name="see-also"></a>Confira também

- [REF CURSORs do Oracle](oracle-ref-cursors.md)
- [Visão geral do ADO.NET](ado-net-overview.md)
