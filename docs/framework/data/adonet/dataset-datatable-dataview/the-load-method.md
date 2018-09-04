---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 21868f808a6d39c935b612f745d720180df2dd73
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507256"
---
# <a name="the-load-method"></a>O método Load
Você pode usar o <xref:System.Data.DataTable.Load%2A> método para carregar um <xref:System.Data.DataTable> com linhas de uma fonte de dados. Este é um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, uma **DataReader**. Neste formulário, ele simplesmente carrega o **DataTable** com linhas. Opcionalmente, você pode especificar o **LoadOption** parâmetro para controlar como os dados são adicionados para o **DataTable**.  
  
 O **LoadOption** parâmetro é particularmente útil em casos em que o **DataTable** já contiver linhas de dados, pois descreve dados de entrada como de fonte de dados serão combinados com os dados já na tabela. Por exemplo, **PreserveCurrentValues** (o padrão) Especifica que em casos em que uma linha está marcada como **adicionado** no **DataTable**, o **Original** valor ou cada coluna é definida como o conteúdo da linha correspondente da fonte de dados. O **atual** valor manterá os valores atribuídos quando a linha foi adicionada e o **RowState** da linha será definido como **Changed**.  
  
 A tabela a seguir fornece uma breve descrição do <xref:System.Data.LoadOption> valores de enumeração.  
  
|Valor de LoadOption|Descrição|  
|----------------------|-----------------|  
|**OverwriteRow**|Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como uma linha já está sendo a **DataTable**, o **Original** e **atual** valores de cada coluna são substituídos pelos valores na nova linha e o **RowState** estiver definida como **inalterado**.<br /><br /> Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados com um **RowState** valor de **inalterado**.<br /><br /> Na verdade, essa opção atualiza o conteúdo do **DataTable** para que ele corresponde ao conteúdo da fonte de dados.|  
|**PreserveCurrentValues (padrão)**|Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como uma linha já está sendo a **DataTable**, o **Original** valor é definido como o conteúdo de linha de entrada e o **Atual** valor não é alterado.<br /><br /> Se o **RowState** é **adicionado** ou **modificado**, ele é definido como **modificado**.<br /><br /> Se o **RowState** foi **Deleted**, ele permanece **Deleted**.<br /><br /> Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados e o **RowState** está definido como **inalterado**.|  
|**UpdateCurrentValues**|Se linhas de entrada tiverem o mesmo **PrimaryKey** valor como a linha já está sendo a **DataTable**, o **atual** valor é copiado para o **Original**valor e o **atual** valor é definido como o conteúdo da linha de entrada.<br /><br /> Se o **RowState** na **DataTable** foi **adicionado**, o **RowState** permanece **adicionado**. Para linhas marcadas como **Modified** ou **Deleted**, o **RowState** é **modificado**.<br /><br /> Linhas da fonte de dados que ainda não existirem na **DataTable** são adicionados e o **RowState** está definido como **adicionado**.|  
  
 O exemplo a seguir usa o **Load** método para exibir uma lista de aniversários para funcionários a **Northwind** banco de dados.  
  
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
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
