---
title: Criar colunas AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205137"
---
# <a name="creating-autoincrement-columns"></a>Criar colunas AutoIncrement
Para garantir valores de coluna exclusivos, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas forem adicionadas à tabela. Para criar um incremento <xref:System.Data.DataColumn>automático, defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna como **true**. Em seguida, começa com o <xref:System.Data.DataColumn.AutoIncrementSeed%2A> valor definido na propriedade e, com cada linha adicionada, o valor da coluna AutoIncrement <xref:System.Data.DataColumn.AutoIncrementStep%2A> aumenta pelo valor definido na propriedade da coluna. <xref:System.Data.DataColumn>  
  
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
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
