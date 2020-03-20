---
title: O método Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150721"
---
# <a name="the-load-method"></a>O método Load
Você pode <xref:System.Data.DataTable.Load%2A> usar o <xref:System.Data.DataTable> método para carregar um com linhas de uma fonte de dados. Trata-se de um método sobrecarregado que, em sua forma mais simples, aceita um único parâmetro, um **DataReader**. Neste formulário, ele simplesmente carrega a **Tabela de Dados** com linhas. Opcionalmente, você pode especificar o parâmetro **LoadOption** para controlar como os dados são adicionados à **Tabela de Dados**.  
  
 O parâmetro **LoadOption** é particularmente útil nos casos em que a Tabela de **Dados** já contém linhas de dados, porque descreve como os dados recebidas da fonte de dados serão combinados com os dados já na tabela. Por exemplo, **PreserveCurrentValues** (o padrão) especifica que nos casos em que uma linha é marcada como **Adicionada** na **Tabela de Dados,** o valor **Original** ou cada coluna é definido para o conteúdo da linha correspondente da fonte de dados. O valor **Atual** manterá os valores atribuídos quando a linha foi adicionada e o Estado de **linha** da linha será definido como **Alterado**.  
  
 A tabela a seguir fornece <xref:System.Data.LoadOption> uma breve descrição dos valores de enumeração.  
  
|Valor loadOption|Descrição|  
|----------------------|-----------------|  
|**OverwriteRow**|Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** de uma linha já existente na Tabela de **Dados,** os valores **Original** e **Atual** de cada coluna serão substituídos pelos valores na linha de entrada e a propriedade **RowState** será definida **como Inalterada**.<br /><br /> As linhas da fonte de dados que ainda não existem na **Tabela de Dados** são adicionadas com um valor **rowState** de **Inalterado**.<br /><br /> Esta opção, na verdade, atualiza o conteúdo da Tabela de **Dados** para que corresponda ao conteúdo da fonte de dados.|  
|**PreservarValors de corrente (padrão)**|Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** de uma linha já na **Tabela de Dados,** o valor **Original** será definido para o conteúdo da linha de entrada e o valor **Atual** não será alterado.<br /><br /> Se o **Estado de linha for** **adicionado** ou **modificado,** ele será definido como **Modificado**.<br /><br /> Se o **RowState foi** **excluído,** ele será **excluído**.<br /><br /> As linhas da fonte de dados que ainda não existem na **Tabela de Dados** são adicionadas e o **RowState** é definido **como Inalterado**.|  
|**AtualizaçãoAtualValores**|Se as linhas recebidas tiverem o mesmo valor **PrimaryKey** da linha já na **Tabela de Dados,** o valor **Atual** será copiado para o valor **Original** e o valor **Atual** será definido para o conteúdo da linha de entrada.<br /><br /> Se o **Estado de Linha** na Tabela de **Dados** foi **adicionado,** o **Estado de linha** permanece **adicionado**. Para linhas marcadas como **Modificadas** ou **Excluídas,** o **Estado de linha** é **modificado**.<br /><br /> As linhas da fonte de dados que ainda não existem na **Tabela de dados** são adicionadas e o **RowState** é definido **como Adicionado**.|  
  
 A amostra a seguir usa o método **Load** para exibir uma lista de aniversários para os funcionários no banco de dados **Northwind.**  
  
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
  
## <a name="see-also"></a>Confira também

- [Manipulando dados em uma DataTable](manipulating-data-in-a-datatable.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
