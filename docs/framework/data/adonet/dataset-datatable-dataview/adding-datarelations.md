---
title: Adicionando DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 8157d296636d0f8661a35af35de561f5cc49c30b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784816"
---
# <a name="adding-datarelations"></a>Adicionando DataRelations
Em um <xref:System.Data.DataSet> com vários objetos <xref:System.Data.DataTable>, você pode usar objetos <xref:System.Data.DataRelation> para relacionar uma tabela a outra, para navegar pelas tabelas e para retornar as linhas filho ou pai de uma tabela relacionada.  
  
 Os argumentos necessários para criar uma **DataRelation** são um nome para a **DataRelation** que está sendo criada e uma matriz de uma ou <xref:System.Data.DataColumn> mais referências às colunas que servem como as colunas pai e filho na relação. Depois de criar uma **DataRelation**, você pode usá-la para navegar entre tabelas e recuperar valores.  
  
 Adicionar uma **DataRelation** a um <xref:System.Data.DataSet> ADDS, <xref:System.Data.UniqueConstraint> por padrão, a à tabela pai e <xref:System.Data.ForeignKeyConstraint> a à tabela filho. Para obter mais informações sobre essas restrições padrão, consulte as [restrições de DataTable](datatable-constraints.md).  
  
 O exemplo de código a seguir cria uma **DataRelation** usando dois <xref:System.Data.DataTable> objetos <xref:System.Data.DataSet>em um. Cada <xref:System.Data.DataTable> contém uma coluna chamada **CustID**, que serve como um link entre os dois <xref:System.Data.DataTable> objetos. O exemplo adiciona uma única **DataRelation** à <xref:System.Data.DataSet>coleção **Relations** do. O primeiro argumento no exemplo especifica o nome da **DataRelation** que está sendo criada. O segundo argumento define a **DataColumn** pai e o terceiro argumento define o filho **DataColumn**.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 Uma **DataRelation** também tem uma propriedade **aninhada** que, quando definida como **true**, faz com que as linhas da tabela filho sejam aninhadas dentro da linha associada da tabela pai quando gravadas como elementos <xref:System.Data.DataSet.WriteXml%2A> XML usando. Para obter mais informações, consulte [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="see-also"></a>Consulte também

- [DataSets, DataTables, and DataViews](index.md) (DataSets, DataTables e DataViews)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
