---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d1222d3df30bf2b3de1761b8fa5c702dc687d0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="datatables"></a><span data-ttu-id="e9ac8-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="e9ac8-102">DataTables</span></span>
<span data-ttu-id="e9ac8-103">Um <xref:System.Data.DataSet> é composto de uma coleção tabelas, relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="e9ac8-104">No ADO.NET, <xref:System.Data.DataTable> objetos são usados para representar as tabelas em um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="e9ac8-105">Um **DataTable** representa uma tabela de dados relacionais de na memória; os dados são locais para o. Aplicativo baseado em rede no qual ele reside, mas pode ser preenchido por uma fonte de dados, como Microsoft SQL Server usando um **DataAdapter** para obter mais informações, consulte [preenchendo um DataSet de um DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ac8-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="e9ac8-106">O **DataTable** classe é um membro do **System. Data** namespace na biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="e9ac8-107">Você pode criar e usar um **DataTable** independentemente ou como um membro de um **DataSet**, e **DataTable** objetos também podem ser usados em conjunto com outros objetos do .NET Framework, incluindo o <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="e9ac8-108">Acessar a coleção de tabelas em um **conjunto de dados** por meio de **tabelas** propriedade do **conjunto de dados** objeto.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="e9ac8-109">O esquema, ou a estrutura, de uma tabela é representado por colunas e restrições.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="e9ac8-110">Definir o esquema de um **DataTable** usando <xref:System.Data.DataColumn> objetos, bem como <xref:System.Data.ForeignKeyConstraint> e <xref:System.Data.UniqueConstraint> objetos.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="e9ac8-111">As colunas em uma tabela podem ser mapeadas para colunas em uma fonte de dados, contêm valores calculados de expressões, incrementam automaticamente seus valores ou contêm valores de chave primária.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="e9ac8-112">Além de um esquema, um **DataTable** também deve ter linhas para conter e dados de pedidos.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="e9ac8-113">A classe <xref:System.Data.DataRow> representa os dados reais contidos em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="e9ac8-114">Você usa o **DataRow** e suas propriedades e métodos para recuperar, avaliar e manipular os dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="e9ac8-115">Como acessar e alterar os dados dentro de uma linha, o **DataRow** objeto mantém seu estado atual e a original.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="e9ac8-116">Você pode criar relações pai-filho entre tabelas usando uma ou mais colunas relacionadas nas tabelas.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="e9ac8-117">Criar uma relação entre **DataTable** objetos usando um <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="e9ac8-118">**DataRelation** objetos, em seguida, podem ser usados para retornar as linhas relacionadas de filho ou pai de uma linha específica.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="e9ac8-119">Para obter mais informações, consulte [adicionando DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="e9ac8-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9ac8-120">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e9ac8-120">In This Section</span></span>  
 [<span data-ttu-id="e9ac8-121">Criando um DataTable</span><span class="sxs-lookup"><span data-stu-id="e9ac8-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="e9ac8-122">Explica como criar um **DataTable** e adicioná-lo para um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e9ac8-123">Definição de esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="e9ac8-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="e9ac8-124">Fornece informações sobre como criar e usar **DataColumn** objetos e restrições.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="e9ac8-125">Manipulação de dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="e9ac8-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="e9ac8-126">Explica como adicionar, modificar e excluir dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="e9ac8-127">Explica como usar **DataTable** eventos para examinar as alterações nos dados na tabela.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="e9ac8-128">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="e9ac8-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="e9ac8-129">Fornece informações sobre os eventos disponíveis para uso com um **DataTable**, incluindo eventos quando valores de coluna são modificados e linhas são adicionadas ou excluídas.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9ac8-130">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e9ac8-130">Related Sections</span></span>  
 [<span data-ttu-id="e9ac8-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e9ac8-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="e9ac8-132">Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes e gerenciar dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 <span data-ttu-id="e9ac8-133">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="e9ac8-133">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="e9ac8-134">Fornece informações sobre o ADO.NET **DataSet** incluindo como criar relações entre tabelas.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="e9ac8-135">Fornece informações de referência sobre o **restrição** objeto.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="e9ac8-136">Fornece informações de referência sobre o **DataColumn** objeto.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="e9ac8-137">Fornece informações de referência sobre o **DataSet** objeto.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="e9ac8-138">Fornece informações de referência sobre o **DataTable** objeto.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="e9ac8-139">Visão geral da biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="e9ac8-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="e9ac8-140">Fornece uma visão geral da biblioteca de classes do .NET Framework, incluindo o **sistema** namespace, bem como o namespace de segundo nível, **System. Data**.</span><span class="sxs-lookup"><span data-stu-id="e9ac8-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ac8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9ac8-141">See Also</span></span>  
 <span data-ttu-id="e9ac8-142">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e9ac8-142">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
