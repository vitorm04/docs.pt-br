---
title: DataSets, DataTables e DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 642a81b926262fb8ea95234d90e4c1a0c49ea96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="62a35-102">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="62a35-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="62a35-103">O <xref:System.Data.DataSet> do ADO.NET é uma representação de dados residentes na memória que fornecem um modelo de programação relacional consistente independentemente da origem dos dados que contém.</span><span class="sxs-lookup"><span data-stu-id="62a35-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="62a35-104">Um <xref:System.Data.DataSet> representa um conjunto completo de dados que incluem as tabelas que contêm, pedem e restringem os dados, bem como as relações entre tabelas.</span><span class="sxs-lookup"><span data-stu-id="62a35-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="62a35-105">Há várias formas de trabalhar com um <xref:System.Data.DataSet>, que podem ser aplicadas independentemente ou em combinação.</span><span class="sxs-lookup"><span data-stu-id="62a35-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="62a35-106">Você pode:</span><span class="sxs-lookup"><span data-stu-id="62a35-106">You can:</span></span>  
  
-   <span data-ttu-id="62a35-107">Crie um <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> e <xref:System.Data.Constraint> programaticamente dentro de um <xref:System.Data.DataSet> e preencha as tabelas com dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="62a35-108">Preencha o <xref:System.Data.DataSet> com tabelas de dados de uma fonte de dados relacional existente usando um `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="62a35-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="62a35-109">Carregue e salve o conteúdo de <xref:System.Data.DataSet> usando XML.</span><span class="sxs-lookup"><span data-stu-id="62a35-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="62a35-110">Para obter mais informações, consulte [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet).</span><span class="sxs-lookup"><span data-stu-id="62a35-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="62a35-111">Um <xref:System.Data.DataSet> fortemente tipado também pode ser transportado usando um serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="62a35-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="62a35-112">O design do <xref:System.Data.DataSet> torna-o ideal para transmitir dados usando serviços Web XML.</span><span class="sxs-lookup"><span data-stu-id="62a35-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="62a35-113">Para obter uma visão geral dos serviços Web XML, consulte [XML Web Services Overview](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d) (Visão geral dos serviços Web XML).</span><span class="sxs-lookup"><span data-stu-id="62a35-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="62a35-114">Para obter um exemplo de como consumir um <xref:System.Data.DataSet> de um serviço Web XML, consulte [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md) (Consumindo um conjunto de dados de um serviço Web XML).</span><span class="sxs-lookup"><span data-stu-id="62a35-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62a35-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="62a35-115">In This Section</span></span>  
 <span data-ttu-id="62a35-116">[Creating a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md) (Criando um conjunto de dados)</span><span class="sxs-lookup"><span data-stu-id="62a35-116">[Creating a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)</span></span>  
 <span data-ttu-id="62a35-117">Descreve a sintaxe para criar uma instância de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="62a35-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="62a35-118">[Adding a DataTable to a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md) (Adicionando um DataTable a um DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-118">[Adding a DataTable to a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)</span></span>  
 <span data-ttu-id="62a35-119">Descreve como criar e adicionar tabelas e colunas em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="62a35-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="62a35-120">[Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) (Adicionando DataRelations)</span><span class="sxs-lookup"><span data-stu-id="62a35-120">[Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)</span></span>  
 <span data-ttu-id="62a35-121">Descreve como criar relacionamentos entre tabelas em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="62a35-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="62a35-122">[Navigating DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md) (Navegando em DataRelations)</span><span class="sxs-lookup"><span data-stu-id="62a35-122">[Navigating DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)</span></span>  
 <span data-ttu-id="62a35-123">Descreve como usar os relacionamentos entre tabelas em um <xref:System.Data.DataSet> para retornar as linhas filho ou pai de uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="62a35-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 <span data-ttu-id="62a35-124">[Merging DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) (Mesclando o conteúdo do DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-124">[Merging DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)</span></span>  
 <span data-ttu-id="62a35-125">Descreve como mesclar o conteúdo de uma matriz <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> em outro <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="62a35-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="62a35-126">[Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md) (Copiando o conteúdo do DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-126">[Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)</span></span>  
 <span data-ttu-id="62a35-127">Descreve como criar uma cópia de um <xref:System.Data.DataSet> que pode conter o esquema bem como dados especificados.</span><span class="sxs-lookup"><span data-stu-id="62a35-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 <span data-ttu-id="62a35-128">[Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md) (Manipulando eventos do DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-128">[Handling DataSet Events](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)</span></span>  
 <span data-ttu-id="62a35-129">Descreve os eventos de um <xref:System.Data.DataSet> e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="62a35-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 <span data-ttu-id="62a35-130">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md) (DataSets tipados)</span><span class="sxs-lookup"><span data-stu-id="62a35-130">[Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)</span></span>  
 <span data-ttu-id="62a35-131">Descreve o que um <xref:System.Data.DataSet> tipado é e como criá-lo e usá-lo.</span><span class="sxs-lookup"><span data-stu-id="62a35-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="62a35-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="62a35-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="62a35-133">Descreve como criar um <xref:System.Data.DataTable>, definir o esquema e manipular dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="62a35-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="62a35-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="62a35-135">Descreve como criar e usar um <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="62a35-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="62a35-136">DataViews</span><span class="sxs-lookup"><span data-stu-id="62a35-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="62a35-137">Descreve como criar e trabalhar com `DataViews` e trabalhar com eventos de <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="62a35-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 <span data-ttu-id="62a35-138">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-138">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="62a35-139">Descreve como o <xref:System.Data.DataSet> interage com XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um <xref:System.Data.DataSet> como dados XML.</span><span class="sxs-lookup"><span data-stu-id="62a35-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 <span data-ttu-id="62a35-140">[Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md) (Consumindo um DataSet de um serviço Web XML)</span><span class="sxs-lookup"><span data-stu-id="62a35-140">[Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)</span></span>  
 <span data-ttu-id="62a35-141">Descreve como criar um serviço Web XML que usa um <xref:System.Data.DataSet> para transportar dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="62a35-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="62a35-142">Related Sections</span></span>  
 <span data-ttu-id="62a35-143">[What's New in ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md) (Novidades no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="62a35-143">[What's New in ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)</span></span>  
 <span data-ttu-id="62a35-144">Apresenta recursos que são novos no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="62a35-144">Introduces features that are new in ADO.NET.</span></span>  
  
 <span data-ttu-id="62a35-145">[ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="62a35-145">[ADO.NET Overview](../../../../../docs/framework/data/adonet/ado-net-overview.md)</span></span>  
 <span data-ttu-id="62a35-146">Fornece uma introdução ao design e aos componentes do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="62a35-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 <span data-ttu-id="62a35-147">[Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) (Preenchendo um DataSet por meio de um DataAdapter)</span><span class="sxs-lookup"><span data-stu-id="62a35-147">[Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)</span></span>  
 <span data-ttu-id="62a35-148">Descreve como carregar um **DataSet** com os dados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 <span data-ttu-id="62a35-149">[Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="62a35-149">[Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)</span></span>  
 <span data-ttu-id="62a35-150">Descreve como resolver as alterações nos dados em um **DataSet** de volta para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 <span data-ttu-id="62a35-151">[Adding Existing Constraints to a DataSet](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md) (Adicionando restrições existentes a um DataSet)</span><span class="sxs-lookup"><span data-stu-id="62a35-151">[Adding Existing Constraints to a DataSet](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)</span></span>  
 <span data-ttu-id="62a35-152">Descreve como preencher um **DataSet** com informações de chave primária de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="62a35-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a35-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62a35-153">See Also</span></span>  
 [<span data-ttu-id="62a35-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="62a35-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="62a35-155">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="62a35-155">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
