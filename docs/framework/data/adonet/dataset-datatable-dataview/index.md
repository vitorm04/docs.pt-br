---
title: DataSets, DataTables e DataViews
description: Aprenda várias maneiras de trabalhar com um conjunto de dados ADO.NET, uma representação residente na memória que fornece um modelo de programação relacional consistente.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4e1c0ea5f1de1715ad8e862e6a3ed7370b53c6ce
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555858"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="0c523-103">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="0c523-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="0c523-104">O <xref:System.Data.DataSet> do ADO.NET é uma representação de dados residentes na memória que fornecem um modelo de programação relacional consistente independentemente da origem dos dados que contém.</span><span class="sxs-lookup"><span data-stu-id="0c523-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="0c523-105">Um <xref:System.Data.DataSet> representa um conjunto completo de dados que incluem as tabelas que contêm, pedem e restringem os dados, bem como as relações entre tabelas.</span><span class="sxs-lookup"><span data-stu-id="0c523-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="0c523-106">Há várias formas de trabalhar com um <xref:System.Data.DataSet>, que podem ser aplicadas independentemente ou em combinação.</span><span class="sxs-lookup"><span data-stu-id="0c523-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="0c523-107">Você pode:</span><span class="sxs-lookup"><span data-stu-id="0c523-107">You can:</span></span>  
  
- <span data-ttu-id="0c523-108">Crie um <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> e <xref:System.Data.Constraint> programaticamente dentro de um <xref:System.Data.DataSet> e preencha as tabelas com dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="0c523-109">Preencha o <xref:System.Data.DataSet> com tabelas de dados de uma fonte de dados relacional existente usando um `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="0c523-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="0c523-110">Carregue e salve o conteúdo de <xref:System.Data.DataSet> usando XML.</span><span class="sxs-lookup"><span data-stu-id="0c523-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="0c523-111">Para obter mais informações, consulte [Using XML in a DataSet](using-xml-in-a-dataset.md) (Usando XML em um DataSet).</span><span class="sxs-lookup"><span data-stu-id="0c523-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="0c523-112">Um <xref:System.Data.DataSet> fortemente tipado também pode ser transportado usando um serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="0c523-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="0c523-113">O design do <xref:System.Data.DataSet> torna-o ideal para transmitir dados usando serviços Web XML.</span><span class="sxs-lookup"><span data-stu-id="0c523-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="0c523-114">Para obter uma visão geral dos serviços Web XML, consulte [XML Web Services Overview](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)) (Visão geral dos serviços Web XML).</span><span class="sxs-lookup"><span data-stu-id="0c523-114">For an overview of XML Web services, see [XML Web Services Overview](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="0c523-115">Para obter um exemplo de como consumir um <xref:System.Data.DataSet> de um serviço Web XML, consulte [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md) (Consumindo um conjunto de dados de um serviço Web XML).</span><span class="sxs-lookup"><span data-stu-id="0c523-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c523-116">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0c523-116">In this section</span></span>

 [<span data-ttu-id="0c523-117">Diretrizes de segurança</span><span class="sxs-lookup"><span data-stu-id="0c523-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="0c523-118">Fornece diretrizes de segurança para o <xref:System.Data.DataSet> e o <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="0c523-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="0c523-119">Criando um conjunto de uma</span><span class="sxs-lookup"><span data-stu-id="0c523-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="0c523-120">Descreve a sintaxe para criar uma instância de um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0c523-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0c523-121">Adicionando um DataTable a um DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="0c523-122">Descreve como criar e adicionar tabelas e colunas em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0c523-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0c523-123">Adicionando DataRelations</span><span class="sxs-lookup"><span data-stu-id="0c523-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="0c523-124">Descreve como criar relacionamentos entre tabelas em um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0c523-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0c523-125">Navegando em DataRelations</span><span class="sxs-lookup"><span data-stu-id="0c523-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="0c523-126">Descreve como usar os relacionamentos entre tabelas em um <xref:System.Data.DataSet> para retornar as linhas filho ou pai de uma relação pai-filho.</span><span class="sxs-lookup"><span data-stu-id="0c523-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="0c523-127">Mesclando conteúdo do DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="0c523-128">Descreve como mesclar o conteúdo de uma matriz <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> em outro <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="0c523-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="0c523-129">Copiando conteúdo do DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="0c523-130">Descreve como criar uma cópia de um <xref:System.Data.DataSet> que pode conter o esquema bem como dados especificados.</span><span class="sxs-lookup"><span data-stu-id="0c523-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="0c523-131">Manipular eventos do DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="0c523-132">Descreve os eventos de um <xref:System.Data.DataSet> e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="0c523-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="0c523-133">DataSets tipados</span><span class="sxs-lookup"><span data-stu-id="0c523-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="0c523-134">Descreve o que um <xref:System.Data.DataSet> tipado é e como criá-lo e usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0c523-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="0c523-135">DataTables</span><span class="sxs-lookup"><span data-stu-id="0c523-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="0c523-136">Descreve como criar um <xref:System.Data.DataTable>, definir o esquema e manipular dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="0c523-137">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="0c523-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="0c523-138">Descreve como criar e usar um <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="0c523-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="0c523-139">DataViews</span><span class="sxs-lookup"><span data-stu-id="0c523-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="0c523-140">Descreve como criar e trabalhar com `DataViews` e trabalhar com eventos de <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="0c523-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="0c523-141">Usando XML em um DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="0c523-142">Descreve como o <xref:System.Data.DataSet> interage com XML como uma fonte de dados, incluindo o carregamento e a persistência do conteúdo de um <xref:System.Data.DataSet> como dados XML.</span><span class="sxs-lookup"><span data-stu-id="0c523-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="0c523-143">Consumir um DataSet de um serviço Web XML</span><span class="sxs-lookup"><span data-stu-id="0c523-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="0c523-144">Descreve como criar um serviço Web XML que usa um <xref:System.Data.DataSet> para transportar dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c523-145">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="0c523-145">Related sections</span></span>

 [<span data-ttu-id="0c523-146">Novidades no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0c523-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="0c523-147">Apresenta recursos que são novos no ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0c523-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="0c523-148">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0c523-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="0c523-149">Fornece uma introdução ao design e aos componentes do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0c523-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="0c523-150">Populando um DataSet a partir de um DataAdapter</span><span class="sxs-lookup"><span data-stu-id="0c523-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="0c523-151">Descreve como carregar um **DataSet** com os dados de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="0c523-152">Atualizando fontes de dados com DataAdapters</span><span class="sxs-lookup"><span data-stu-id="0c523-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="0c523-153">Descreve como resolver as alterações nos dados em um **DataSet** de volta para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="0c523-154">Adicionar restrições existentes a um DataSet</span><span class="sxs-lookup"><span data-stu-id="0c523-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="0c523-155">Descreve como preencher um **DataSet** com informações de chave primária de uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="0c523-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c523-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="0c523-156">See also</span></span>

- [<span data-ttu-id="0c523-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0c523-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="0c523-158">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0c523-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
