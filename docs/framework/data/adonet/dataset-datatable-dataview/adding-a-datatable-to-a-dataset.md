---
title: Adicionando um DataTable a um DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 3554790bb65310031b00ca5fb320aa4c111e1e11
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-datatable-to-a-dataset"></a>Adicionando um DataTable a um DataSet
O ADO.NET permite que você crie objetos <xref:System.Data.DataTable> e adicione-os a um <xref:System.Data.DataSet> existente. Você pode definir informações de restrição para um <xref:System.Data.DataTable> usando as propriedades <xref:System.Data.DataTable.PrimaryKey%2A> e <xref:System.Data.DataColumn.Unique%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Data.DataSet>, adiciona um novo objeto <xref:System.Data.DataTable> ao <xref:System.Data.DataSet> e adiciona três objetos <xref:System.Data.DataColumn> à tabela. Finalmente, o código define uma coluna como a coluna de chave primária.  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a>Diferenciação de maiúsculas e minúsculas  
 Duas ou mais tabelas ou relacionamentos com o mesmo nome, mas maiúsculas e minúsculas diferentes, podem existir em um <xref:System.Data.DataSet>. Nesses casos, as referências por nome a tabelas e relações diferenciam maiúsculas de minúsculas. Por exemplo, se o <xref:System.Data.DataSet> **conjunto de dados** contém tabelas **Table1** e **table1**, você deve fazer referência a **Table1** por nome **dataSet.Tables["Table1"]**, e **table1** como **dataSet.Tables["table1"]**. Tentativa de fazer referência a uma das tabelas como **dataSet.Tables["TABLE1"]** poderia gerar uma exceção.  
  
 O comportamento de maiúsculas e minúsculas não se aplica se apenas uma tabela ou relacionamento tiver um nome específico. Por exemplo, se o <xref:System.Data.DataSet> tem apenas **Table1**, você pode fazer referência a ele usando **dataSet.Tables["TABLE1"]**.  
  
> [!NOTE]
>  A propriedade <xref:System.Data.DataSet.CaseSensitive%2A> da <xref:System.Data.DataSet> não afeta esse comportamento. A propriedade <xref:System.Data.DataSet.CaseSensitive%2A> aplica-se aos dados no <xref:System.Data.DataSet> e afeta a classificação, a procura, a filtragem, a imposição de restrições, e assim por diante.  
  
## <a name="namespace-support"></a>Suporte a namespace  
 Nas versões do ADO.NET anteriores a 2.0, as duas tabelas não podiam ter o mesmo nome, mesmo se estivessem em namespaces diferentes. Essa limitação foi removida no ADO.NET 2.0. Um <xref:System.Data.DataSet> pode conter duas tabelas que têm o mesmo valor de propriedade <xref:System.Data.DataTable.TableName%2A>, mas valores de propriedades <xref:System.Data.DataTable.Namespace%2A> diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
