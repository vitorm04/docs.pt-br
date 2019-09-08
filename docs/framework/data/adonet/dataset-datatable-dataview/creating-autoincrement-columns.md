---
title: Criar colunas AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786448"
---
# <a name="creating-autoincrement-columns"></a>Criar colunas AutoIncrement
Para garantir valores de coluna exclusivos, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas forem adicionadas à tabela. Para criar um incremento <xref:System.Data.DataColumn>automático, defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna como **true**. Em seguida, começa com o valor definido <xref:System.Data.DataColumn.AutoIncrementSeed%2A> na propriedade e, com cada linha adicionada, o valor da coluna **AutoIncrement** <xref:System.Data.DataColumn.AutoIncrementStep%2A> aumenta pelo valor definido na propriedade da coluna. <xref:System.Data.DataColumn>  
  
 Para colunas de **incremento automático** , recomendamos <xref:System.Data.DataColumn.ReadOnly%2A> que a propriedade de **DataColumn** seja definida como **true**.  
  
 O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona incrementalmente em etapas de 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataColumn>
- [Definição de esquema de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
