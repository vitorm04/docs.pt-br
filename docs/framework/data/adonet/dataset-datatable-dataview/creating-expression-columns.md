---
title: Criando colunas de expressão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 1c4e0b368a8eb154207382ae70b9767f5a5fe64d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785442"
---
# <a name="creating-expression-columns"></a>Criando colunas de expressão
Você pode definir uma expressão para uma coluna, permitindo que ela contenha um valor calculado dos valores de outras colunas na mesma linha ou dos valores de coluna de várias linhas na tabela. Para definir a expressão a ser avaliada, use a propriedade <xref:System.Data.DataColumn.Expression%2A> de coluna de destino e use a propriedade <xref:System.Data.DataColumn.ColumnName%2A> para se referir a outras colunas na expressão. O <xref:System.Data.DataColumn.DataType%2A> para a coluna de expressão deve ser apropriado para o valor que a expressão retorna.  
  
 A tabela a seguir lista vários usos possíveis para colunas de expressão em uma tabela.  
  
|Tipo de expressão|Exemplo|  
|---------------------|-------------|  
|Comparação|"Total de > = 500"|  
|Computação|"UnitPrice * Quantity"|  
|Agregação|Sum(Price)|  
  
 Você pode definir a propriedade **expressão** em um objeto **DataColumn** existente ou pode incluir a propriedade como o terceiro argumento passado para o <xref:System.Data.DataColumn> Construtor, conforme mostrado no exemplo a seguir.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 As expressões podem referenciar outras colunas de expressão; no entanto, uma referência circular, na qual duas expressões referenciam-se entre si, gerará uma exceção. Para regras sobre como escrever expressões, consulte <xref:System.Data.DataColumn.Expression%2A> a propriedade da classe **DataColumn** .  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Definição de esquema de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
