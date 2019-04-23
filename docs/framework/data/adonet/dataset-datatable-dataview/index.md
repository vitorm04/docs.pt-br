---
title: DataSets, DataTables e DataViews
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 9c57f75dd94f3fbda74c13a5d5773825051fe416
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105723"
---
# <a name="datasets-datatables-and-dataviews"></a>DataSets, DataTables e DataViews
O <xref:System.Data.DataSet> do ADO.NET é uma representação de dados residentes na memória que fornecem um modelo de programação relacional consistente independentemente da origem dos dados que contém. Um <xref:System.Data.DataSet> representa um conjunto completo de dados que incluem as tabelas que contêm, pedem e restringem os dados, bem como as relações entre tabelas.  
  
 Há várias formas de trabalhar com um <xref:System.Data.DataSet>, que podem ser aplicadas independentemente ou em combinação. Você pode:  
  
-   Crie um <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> e <xref:System.Data.Constraint> programaticamente dentro de um <xref:System.Data.DataSet> e preencha as tabelas com dados.  
  
-   Preencha o <xref:System.Data.DataSet> com tabelas de dados de uma fonte de dados relacional existente usando um `DataAdapter`.  
  
-   Carregue e salve o conteúdo de <xref:System.Data.DataSet> usando XML. Para obter mais informações, consulte [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).  
  
 Um <xref:System.Data.DataSet> fortemente tipado também pode ser transportado usando um serviço Web XML. O design do <xref:System.Data.DataSet> torna-o ideal para transmitir dados usando serviços Web XML. Para obter uma visão geral dos serviços Web XML, consulte [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)) (Visão geral dos serviços Web XML). Para obter um exemplo de como consumir um <xref:System.Data.DataSet> de um serviço Web XML, consulte [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md) (Consumindo um conjunto de dados de um serviço Web XML).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Creating a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md) (Criando um conjunto de dados)  
 Descreve a sintaxe para criar uma instância de um <xref:System.Data.DataSet>.  
  
 [Adding a DataTable to a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md) (Adicionando um DataTable a um DataSet)  
 Descreve como criar e adicionar tabelas e colunas em um <xref:System.Data.DataSet>.  
  
 [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) (Adicionando DataRelations)  
 Descreve como criar relacionamentos entre tabelas em um <xref:System.Data.DataSet>.  
  
 [Navigating DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md) (Navegando em DataRelations)  
 Descreve como usar os relacionamentos entre tabelas em um <xref:System.Data.DataSet> para retornar as linhas filho ou pai de uma relação pai-filho.  
  
 [Merging DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) (Mesclando o conteúdo do DataSet)  
 Descreve como mesclar o conteúdo de uma matriz <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> em outro <xref:System.Data.DataSet>.  
  
 [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md) (Copiando o conteúdo do DataSet)  
 Descreve como criar uma cópia de um <xref:System.Data.DataSet> que pode conter o esquema bem como dados especificados.  
  
 [Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)  
 Descreve os eventos de um <xref:System.Data.DataSet> e como usá-los.  
  
 [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)  
 Descreve o que um <xref:System.Data.DataSet> tipado é e como criá-lo e usá-lo.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Descreve como criar um <xref:System.Data.DataTable>, definir o esquema e manipular dados.  
  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Descreve como criar e usar um <xref:System.Data.DataTableReader>.  
  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Descreve como criar e trabalhar com `DataViews` e trabalhar com eventos de <xref:System.Data.DataView>.  
  
 [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)  
 Descreve como o <xref:System.Data.DataSet> interage com XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um <xref:System.Data.DataSet> como dados XML.  
  
 [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md) (Consumindo um DataSet de um serviço Web XML)  
 Descreve como criar um serviço Web XML que usa um <xref:System.Data.DataSet> para transportar dados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [What's New in ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md) (Novidades no ADO.NET)  
 Apresenta recursos que são novos no ADO.NET.  
  
 [ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)  
 Fornece uma introdução ao design e aos componentes do ADO.NET.  
  
 [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)  
 Descreve como carregar um **DataSet** com os dados de uma fonte de dados.  
  
 [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)  
 Descreve como resolver as alterações nos dados em um **DataSet** de volta para a fonte de dados.  
  
 [Adding Existing Constraints to a DataSet](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md) (Adicionando restrições existentes a um DataSet)  
 Descreve como preencher um **DataSet** com informações de chave primária de uma fonte de dados.  
  
## <a name="see-also"></a>Consulte também

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
