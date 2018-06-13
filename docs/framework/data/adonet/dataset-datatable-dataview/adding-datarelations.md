---
title: Adicionando DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756937"
---
# <a name="adding-datarelations"></a>Adicionando DataRelations
Em um <xref:System.Data.DataSet> com vários objetos <xref:System.Data.DataTable>, você pode usar objetos <xref:System.Data.DataRelation> para relacionar uma tabela a outra, para navegar pelas tabelas e para retornar as linhas filho ou pai de uma tabela relacionada.  
  
 Os argumentos necessários para criar um **DataRelation** são um nome para o **DataRelation** que está sendo criado e uma matriz de um ou mais <xref:System.Data.DataColumn> referências para as colunas que servem como o pai e filho colunas na relação. Depois de ter criado um **DataRelation**, você pode usá-lo para navegar entre as tabelas e para recuperar valores.  
  
 Adicionando um **DataRelation** para um <xref:System.Data.DataSet> adiciona, por padrão, um <xref:System.Data.UniqueConstraint> à tabela pai e um <xref:System.Data.ForeignKeyConstraint> para a tabela filho. Para obter mais informações sobre essas restrições padrão, consulte [restrições de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 O exemplo de código a seguir cria um **DataRelation** usando duas <xref:System.Data.DataTable> objetos em um <xref:System.Data.DataSet>. Cada <xref:System.Data.DataTable> contém uma coluna denominada **CustID**, que serve como um link entre os dois <xref:System.Data.DataTable> objetos. O exemplo adiciona um único **DataRelation** para o **relações** coleção do <xref:System.Data.DataSet>. O primeiro argumento, o exemplo especifica o nome do **DataRelation** que está sendo criado. O segundo argumento define o pai **DataColumn** e o terceiro argumento define o filho **DataColumn**.  
  
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
  
 Um **DataRelation** também tem um **aninhadas** propriedade que, quando definido como **true**, faz com que as linhas da tabela filho para ser aninhada dentro da linha associada da tabela pai quando gravadas como elementos XML usando <xref:System.Data.DataSet.WriteXml%2A> . Para obter mais informações, consulte [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
