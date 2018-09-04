---
title: Adicionando dados a um DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
ms.openlocfilehash: c1ebe2d735924c559f450f4041884dc9845e4fe0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514509"
---
# <a name="adding-data-to-a-datatable"></a>Adicionando dados a um DataTable
Depois de criar <xref:System.Data.DataTable> e definir sua estrutura usando colunas e restrições, você pode adicionar novas linhas de dados à tabela. Para adicionar uma nova linha, declare uma nova variável como tipo <xref:System.Data.DataRow>. Uma nova **DataRow** objeto é retornado ao chamar o <xref:System.Data.DataTable.NewRow%2A> método. O **DataTable** , em seguida, cria a **DataRow** objeto com base na estrutura da tabela, conforme definido pelo <xref:System.Data.DataColumnCollection>.  
  
 O exemplo a seguir demonstra como criar uma nova linha chamando o **NewRow** método.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Você pode manipular a linha recém-adicionada usando um índice ou o nome da coluna, conforme mostrado no exemplo a seguir.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Depois que dados são inseridos na nova linha, o **Add** método é usado para adicionar a linha para o <xref:System.Data.DataRowCollection>, conforme mostrado no código a seguir.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Você também pode chamar o **Add** para adicionar uma nova linha passando uma matriz de valores, tipada como <xref:System.Object>, conforme mostrado no exemplo a seguir.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Passando uma matriz de valores, digitada como **objeto**, para o **Add** método cria uma nova linha dentro da tabela e define seus valores de coluna com os valores na matriz de objetos. Observe que os valores na matriz são correspondidos sequencialmente a colunas, com base na ordem na qual aparecem na tabela.  
  
 O exemplo a seguir adiciona 10 linhas ao recém-criado **clientes** tabela.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Manipulação de dados em uma DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
