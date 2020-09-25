---
title: DataTables
description: Saiba mais sobre uma DataTable ADO.NET, que representa uma tabela de dados relacionais na memória, local para o. Aplicativo baseado em rede em que ele reside.
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: d501096b4abe94653acdc5249c120abff94534d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202299"
---
# <a name="datatables"></a><span data-ttu-id="56c6e-103">DataTables</span><span class="sxs-lookup"><span data-stu-id="56c6e-103">DataTables</span></span>

<span data-ttu-id="56c6e-104">Um <xref:System.Data.DataSet> é composto de uma coleção tabelas, relações e restrições.</span><span class="sxs-lookup"><span data-stu-id="56c6e-104">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="56c6e-105">No ADO.NET, os <xref:System.Data.DataTable> objetos são usados para representar as tabelas em um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="56c6e-105">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="56c6e-106">Uma **DataTable** representa uma tabela de dados relacionais na memória; os dados são locais para o. Aplicativo baseado em rede no qual ele reside, mas pode ser preenchido a partir de uma fonte de dados, como Microsoft SQL Server usando um **DataAdapter** para obter mais informações, consulte [Populando um DataSet de um DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span><span class="sxs-lookup"><span data-stu-id="56c6e-106">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="56c6e-107">A classe **DataTable** é um membro do namespace **System. Data** dentro da biblioteca de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56c6e-107">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="56c6e-108">Você pode criar e usar uma **DataTable** de forma independente ou como um membro de um conjunto de um **DataSet**, e os objetos **DataTable** também podem ser usados em conjunto com outros objetos .NET Framework, incluindo o <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="56c6e-108">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="56c6e-109">Você acessa a coleção de tabelas em um **DataSet** por meio da propriedade **Tables** do objeto **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-109">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="56c6e-110">O esquema, ou a estrutura, de uma tabela é representado por colunas e restrições.</span><span class="sxs-lookup"><span data-stu-id="56c6e-110">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="56c6e-111">Você define o esquema de uma **DataTable** usando <xref:System.Data.DataColumn> objetos, bem como <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint> objetos e.</span><span class="sxs-lookup"><span data-stu-id="56c6e-111">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="56c6e-112">As colunas em uma tabela podem ser mapeadas para colunas em uma fonte de dados, contêm valores calculados de expressões, incrementam automaticamente seus valores ou contêm valores de chave primária.</span><span class="sxs-lookup"><span data-stu-id="56c6e-112">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="56c6e-113">Além de um esquema, uma **DataTable** também deve ter linhas para conter e ordenar dados.</span><span class="sxs-lookup"><span data-stu-id="56c6e-113">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="56c6e-114">A classe <xref:System.Data.DataRow> representa os dados reais contidos em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="56c6e-114">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="56c6e-115">Você usa a **DataRow** e suas propriedades e métodos para recuperar, avaliar e manipular os dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="56c6e-115">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="56c6e-116">Conforme você acessa e altera os dados dentro de uma linha, o objeto **DataRow** mantém seu estado atual e original.</span><span class="sxs-lookup"><span data-stu-id="56c6e-116">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="56c6e-117">Você pode criar relações pai-filho entre tabelas usando uma ou mais colunas relacionadas nas tabelas.</span><span class="sxs-lookup"><span data-stu-id="56c6e-117">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="56c6e-118">Você cria uma relação entre objetos **DataTable** usando um <xref:System.Data.DataRelation> .</span><span class="sxs-lookup"><span data-stu-id="56c6e-118">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="56c6e-119">Os objetos **DataRelation** podem ser usados para retornar as linhas filho ou pai relacionadas de uma linha específica.</span><span class="sxs-lookup"><span data-stu-id="56c6e-119">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="56c6e-120">Para obter mais informações, consulte [adicionando DataRelations](adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="56c6e-120">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56c6e-121">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="56c6e-121">In This Section</span></span>  

 [<span data-ttu-id="56c6e-122">Criando uma DataTable</span><span class="sxs-lookup"><span data-stu-id="56c6e-122">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="56c6e-123">Explica como criar uma **DataTable** e adicioná-la a um **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="56c6e-123">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="56c6e-124">Definição do esquema de DataTable</span><span class="sxs-lookup"><span data-stu-id="56c6e-124">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="56c6e-125">Fornece informações sobre como criar e usar objetos e restrições de **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-125">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="56c6e-126">Manipulando dados em uma DataTable</span><span class="sxs-lookup"><span data-stu-id="56c6e-126">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="56c6e-127">Explica como adicionar, modificar e excluir dados em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="56c6e-127">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="56c6e-128">Explica como usar eventos **DataTable** para examinar alterações nos dados na tabela.</span><span class="sxs-lookup"><span data-stu-id="56c6e-128">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="56c6e-129">Manipulação de eventos de DataTable</span><span class="sxs-lookup"><span data-stu-id="56c6e-129">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="56c6e-130">Fornece informações sobre os eventos disponíveis para uso com uma **DataTable**, incluindo eventos quando valores de coluna são modificados e linhas são adicionadas ou excluídas.</span><span class="sxs-lookup"><span data-stu-id="56c6e-130">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56c6e-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="56c6e-131">Related Sections</span></span>  

 [<span data-ttu-id="56c6e-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="56c6e-132">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="56c6e-133">Descreve a arquitetura e os componentes do ADO.NET, e como usá-los para acessar fontes de dados existentes e gerenciar dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56c6e-133">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="56c6e-134">DataSets, DataTables e DataViews</span><span class="sxs-lookup"><span data-stu-id="56c6e-134">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="56c6e-135">Fornece informações sobre o **conjunto** de dados ADO.net, incluindo como criar relações entre tabelas.</span><span class="sxs-lookup"><span data-stu-id="56c6e-135">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="56c6e-136">Fornece informações de referência sobre o objeto de **restrição** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-136">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="56c6e-137">Fornece informações de referência sobre o objeto **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-137">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="56c6e-138">Fornece informações de referência sobre o objeto **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-138">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="56c6e-139">Fornece informações de referência sobre o objeto **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="56c6e-139">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="56c6e-140">Visão geral da biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="56c6e-140">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="56c6e-141">Fornece uma visão geral da biblioteca de classes de .NET Framework, incluindo o namespace do **sistema** , bem como seu namespace de segundo nível, **System. Data**.</span><span class="sxs-lookup"><span data-stu-id="56c6e-141">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c6e-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="56c6e-142">See also</span></span>

- [<span data-ttu-id="56c6e-143">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="56c6e-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
