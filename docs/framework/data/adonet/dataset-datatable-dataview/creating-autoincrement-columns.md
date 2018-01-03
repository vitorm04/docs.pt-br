---
title: "Criar colunas de incremento automático"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4c9c7e321ac5749aedf7168afaef9d6a7119de62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-autoincrement-columns"></a>Criar colunas de incremento automático
Para garantir que os valores de coluna exclusiva, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas são adicionadas à tabela. Para criar um incremento automático <xref:System.Data.DataColumn>, defina o <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna a ser **true**. O <xref:System.Data.DataColumn> , em seguida, começa com o valor definido no <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriedade e cada linha adicionada o valor da **AutoIncrement** coluna aumenta o valor definido no <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriedade da coluna.  
  
 Para **AutoIncrement** colunas, é recomendável que o <xref:System.Data.DataColumn.ReadOnly%2A> propriedade o **DataColumn** ser definido como **true**.  
  
 O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona incrementalmente nas etapas de 3.  
  
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
 <xref:System.Data.DataColumn>  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
