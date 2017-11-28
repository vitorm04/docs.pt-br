---
title: Localizando linhas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96a65761cb6ddf31c0bb4c14077aed37336183f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="finding-rows"></a>Localizando linhas
Você pode procurar linhas de acordo com seus valores de chave de classificação usando o <xref:System.Data.DataView.Find%2A> e <xref:System.Data.DataView.FindRows%2A> métodos do <xref:System.Data.DataView>. A diferenciação de maiusculas e minúsculas da pesquisa de valores no **localizar** e **FindRows** métodos é determinado pelo **CaseSensitive** propriedade subjacente <xref:System.Data.DataTable>. Valores de pesquisa devem corresponder a valores de chave de classificação existentes em sua totalidade para retornar um resultado.  
  
 O **localizar** método retorna um inteiro com o índice da <xref:System.Data.DataRowView> que corresponde aos critérios de pesquisa. Se mais de uma linha corresponde aos critérios de pesquisa, apenas o índice da primeira correspondência **DataRowView** é retornado. Se nenhuma correspondência for encontrada, **localizar** retornará -1.  
  
 Para retornar os resultados de pesquisa que correspondam a várias linhas, use o **FindRows** método. **FindRows** funciona como o **localizar** método, exceto que ela retorna um **DataRowView** matriz que faz referência a todas as linhas correspondentes no **DataView**. Se nenhuma correspondência for encontrada, o **DataRowView** matriz estará vazia.  
  
 Para usar o **localizar** ou **FindRows** métodos que você deve especificar uma classificação ordem definindo **ApplyDefaultSort** para **true** ou usando o **Classificação** propriedade. Se nenhuma ordem de classificação for especificado, uma exceção será lançada.  
  
 O **localizar** e **FindRows** métodos aceitam uma matriz de valores como entrada cujo tamanho corresponde ao número de colunas na ordem de classificação. No caso de uma classificação em uma única coluna, você pode passar um único valor. Para ordens de classificação que contém várias colunas, você passar uma matriz de objetos. Observe que, para uma classificação em várias colunas, os valores na matriz de objetos devem corresponder à ordem das colunas especificadas no **classificação** propriedade o **DataView**.  
  
 O seguinte exemplo de código mostra o **localizar** método ser chamado em um **DataView** com uma ordem de classificação de coluna única.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Se seu **classificação** propriedade especifica várias colunas, você deve passar uma matriz de objetos com os valores de pesquisa para cada coluna na ordem especificada pelo **classificação** propriedade, como no exemplo de código a seguir.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
