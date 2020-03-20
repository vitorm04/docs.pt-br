---
title: Localizar linhas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151137"
---
# <a name="finding-rows"></a>Localizar linhas
Você pode procurar linhas de acordo com seus <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> valores-chave <xref:System.Data.DataView>de classificação usando os métodos e métodos do . A sensibilidade do caso dos valores de pesquisa nos métodos **Find** and **FindRows** é determinada pela propriedade **CaseSensitive** do subjacente <xref:System.Data.DataTable>. Os valores de pesquisa devem corresponder aos valores-chave de classificação existentes em sua totalidade, a fim de retornar um resultado.  
  
 O método **Find** retorna um inteiro com <xref:System.Data.DataRowView> o índice do que corresponde aos critérios de pesquisa. Se mais de uma linha corresponder aos critérios de pesquisa, apenas o índice do **DataRowView** correspondente é devolvido. Se não forem encontradas correspondências, **encontre** retornos -1.  
  
 Para retornar os resultados de pesquisa que correspondem a várias linhas, use o método **FindRows.** **O FindRows** funciona como o método **Find,** exceto que ele retorna um array **DataRowView** que faz referência a todas as linhas correspondentes no **DataView**. Se não forem encontradas correspondências, a matriz **DataRowView** estará vazia.  
  
 Para usar os métodos **Find** ou **FindRows,** você deve especificar uma ordem de classificação, definindo **ApplyDefaultSort** como **true** ou usando a propriedade **Classificar.** Se nenhuma ordem de classificação for especificada, uma exceção será lançada.  
  
 Os métodos **Find** e **FindRows** tomam uma matriz de valores como entrada cujo comprimento corresponde ao número de colunas na ordem de classificação. No caso de um tipo em uma única coluna, você pode passar um único valor. Para ordenar ordens contendo várias colunas, você passa uma matriz de objetos. Observe que para uma espécie em várias colunas, os valores na matriz de objetos devem corresponder à ordem das colunas especificadas na propriedade **Classificar** do **DataView**.  
  
 O exemplo de código a seguir mostra o método **Find** sendo chamado contra um **DataView** com uma única ordem de classificação de coluna.  
  
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
  
 Se a propriedade **Classificar** especificar várias colunas, você deve passar uma matriz de objetos com os valores de pesquisa de cada coluna na ordem especificada pela propriedade **Classificar,** como no exemplo de código a seguir.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](dataviews.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
