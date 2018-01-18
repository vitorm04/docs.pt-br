---
title: DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ad24de9fd003637d1c6e31841da209346a872143
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="dataviews"></a><span data-ttu-id="e7cb6-102">DataViews</span><span class="sxs-lookup"><span data-stu-id="e7cb6-102">DataViews</span></span>
<span data-ttu-id="e7cb6-103">Um <xref:System.Data.DataView> permite que você crie diferentes exibições dos dados armazenados em um <xref:System.Data.DataTable>, um recurso que é geralmente usado em aplicativos de vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="e7cb6-104">Usando um **DataView**, você pode expor os dados em uma tabela com diferentes ordens de classificação, e você pode filtrar os dados por estado ou com base em uma expressão de filtro de linha.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="e7cb6-105">Um **DataView** fornece uma exibição dinâmica de dados subjacente **DataTable**: o conteúdo, classificação e associação de refletem as alterações conforme elas ocorrem.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="e7cb6-106">Esse comportamento difere o **selecione** método do **DataTable**, que retorna um <xref:System.Data.DataRow> matriz de uma tabela com base em uma determinada ordem de filtro e/ou classificação: thiscontent reflete as alterações para o base da tabela, mas sua associação e a ordenação permanecem estáticas.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="e7cb6-107">Os recursos dinâmicos do **DataView** tornam ideal para aplicativos de associação de dados.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="e7cb6-108">Um **DataView** fornece uma exibição dinâmica de um único conjunto de dados, semelhante a uma exibição de banco de dados, para que você pode aplicar diferentes de classificação e critérios de filtragem.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="e7cb6-109">Ao contrário de uma exibição de banco de dados, no entanto, um **DataView** não podem ser tratados como uma tabela e não pode fornecer um modo de exibição de tabelas unidas.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="e7cb6-110">Você também não pode excluir as colunas que existem na tabela de origem nem pode acrescentar colunas, como as colunas computacionais, que não existem na tabela de origem.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="e7cb6-111">Você pode usar um <xref:System.Data.DataView.DataViewManager%2A> para gerenciar as configurações de exibição para todas as tabelas em um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="e7cb6-112">O **DataViewManager** fornece uma maneira conveniente para gerenciar as configurações de exibição padrão para cada tabela.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="e7cb6-113">Ao associar um controle a mais de uma tabela de um **DataSet**, associação a um **DataViewManager** é a opção ideal.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7cb6-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e7cb6-114">In This Section</span></span>  
 [<span data-ttu-id="e7cb6-115">Criando um DataView</span><span class="sxs-lookup"><span data-stu-id="e7cb6-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="e7cb6-116">Descreve como criar um **DataView** para um **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="e7cb6-117">Classificando e filtrando dados</span><span class="sxs-lookup"><span data-stu-id="e7cb6-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="e7cb6-118">Descreve como definir as propriedades de um **DataView** para retornar subconjuntos de linhas de dados que satisfazem critérios de filtro específico ou para retornar dados em uma ordem de classificação específica.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="e7cb6-119">DataRows e DataRowViews</span><span class="sxs-lookup"><span data-stu-id="e7cb6-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="e7cb6-120">Descreve como acessar os dados apresentados pelo **DataView**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="e7cb6-121">Localizando linhas</span><span class="sxs-lookup"><span data-stu-id="e7cb6-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="e7cb6-122">Descreve como localizar uma linha específica em um **DataView**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="e7cb6-123">ChildViews e relações</span><span class="sxs-lookup"><span data-stu-id="e7cb6-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="e7cb6-124">Descreve como criar modos de exibição de dados de uma relação de pai-filho usando um **DataView**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="e7cb6-125">Modificando DataViews</span><span class="sxs-lookup"><span data-stu-id="e7cb6-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="e7cb6-126">Descreve como modificar os dados subjacentes **DataTable** por meio de **DataView**, incluindo a habilitação ou desabilitação de atualizações.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="e7cb6-127">Manipulação de eventos de exibição de dados</span><span class="sxs-lookup"><span data-stu-id="e7cb6-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="e7cb6-128">Descreve como usar o **ListChanged** evento para receber notificações quando o conteúdo ou a ordem de um **DataView** está sendo atualizado.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="e7cb6-129">Gerenciando DataViews</span><span class="sxs-lookup"><span data-stu-id="e7cb6-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="e7cb6-130">Descreve como usar um **DataViewManager** para gerenciar **DataView** configurações para cada tabela em uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e7cb6-131">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e7cb6-131">Related Sections</span></span>  
 [<span data-ttu-id="e7cb6-132">Aplicativos da Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e7cb6-132">ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="e7cb6-133">Fornece visões gerais e detalhadas, procedimentos passo a passo para criar aplicativos ASP.NET, Web Forms e serviços Web.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="e7cb6-134">Aplicativos do Windows</span><span class="sxs-lookup"><span data-stu-id="e7cb6-134">Windows Applications</span></span>](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="e7cb6-135">Fornece informações detalhadas sobre como trabalhar com Windows Forms e aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 <span data-ttu-id="e7cb6-136">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-136">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="e7cb6-137">Descreve o **DataSet** objeto e como você pode usar para gerenciar os dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="e7cb6-138">DataTables</span><span class="sxs-lookup"><span data-stu-id="e7cb6-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="e7cb6-139">Descreve o **DataTable** objeto e como você pode usar para gerenciar os dados de aplicativo em si ou como parte de um **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e7cb6-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e7cb6-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="e7cb6-141">Descreve a arquitetura e os componentes do ADO.NET, e como usar o ADO.NET para acessar fontes de dados existentes e gerenciar dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7cb6-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cb6-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7cb6-142">See Also</span></span>  
 <span data-ttu-id="e7cb6-143">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e7cb6-143">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
