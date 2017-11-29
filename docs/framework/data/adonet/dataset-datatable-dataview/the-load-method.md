---
title: "O método Load"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4617f2193b9d557094b7570f8ca8fd5ff7a9d25d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="the-load-method"></a>O método Load
Você pode usar o <xref:System.Data.DataTable.Load%2A> método para carregar um <xref:System.Data.DataTable> com linhas de uma fonte de dados. Este é um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, um **DataReader**. Neste formulário, ele simplesmente carrega o **DataTable** com linhas. Opcionalmente, você pode especificar o **LoadOption** parâmetro para controlar como os dados são adicionados para o **DataTable**.  
  
 O **LoadOption** parâmetro é particularmente útil em casos onde o **DataTable** já contém linhas de dados, porque ele descreve como entrados dados da fonte de dados serão combinados com os dados já está na tabela. Por exemplo, **PreserveCurrentValues** (o padrão) Especifica que em casos em que uma linha é marcada como **adicionado** no **DataTable**, o **Original** valor ou cada coluna é definida para o conteúdo da linha correspondente da fonte de dados. O **atual** valor manterá os valores atribuídos quando a linha foi adicionada e o **RowState** da linha será definido como **alterado**.  
  
 A tabela a seguir fornece uma breve descrição do <xref:System.Data.LoadOption> valores de enumeração.  
  
|Valor de LoadOption|Descrição|  
|----------------------|-----------------|  
|**OverwriteRow**|Se as linhas de entrada têm o mesmo **PrimaryKey** valor como uma linha já está sendo o **DataTable**, o **Original** e **atual** valores de cada coluna são substituídos pelos valores na linha de entrada e o **RowState** está definida como **inalterado**.<br /><br /> Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados a um **RowState** valor de **inalterado**.<br /><br /> Essa opção em vigor atualiza o conteúdo do **DataTable** para que ele corresponda o conteúdo da fonte de dados.|  
|**PreserveCurrentValues (padrão)**|Se as linhas de entrada têm o mesmo **PrimaryKey** valor como uma linha já está sendo o **DataTable**, o **Original** valor é definido como o conteúdo da linha de entrada e o **Atual** valor não é alterado.<br /><br /> Se o **RowState** é **adicionado** ou **modificadas**, ele é definido como **modificadas**.<br /><br /> Se o **RowState** foi **excluído**, ele permanece **excluído**.<br /><br /> Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados e o **RowState** é definido como **inalterado**.|  
|**UpdateCurrentValues**|Se as linhas de entrada têm o mesmo **PrimaryKey** valor como a linha já está sendo o **DataTable**, o **atual** valor é copiado para o **Original**valor e o **atual** valor é definido como o conteúdo da linha de entrada.<br /><br /> Se o **RowState** no **DataTable** foi **adicionado**, o **RowState** permanece **adicionado**. Para as linhas marcadas como **modificadas** ou **excluído**, o **RowState** é **modificadas**.<br /><br /> Linhas da fonte de dados que ainda não existir o **DataTable** são adicionados e o **RowState** é definido como **adicionado**.|  
  
 O exemplo a seguir usa o **carga** método para exibir uma lista de aniversários para funcionários a **Northwind** banco de dados.  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
