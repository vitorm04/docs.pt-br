---
title: LINQ to DataSet
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3746fb31c66202dc75c6aff3ce69952f25b06931
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="linq-to-dataset"></a><span data-ttu-id="69302-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="69302-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="69302-103"> torna mais fácil e rápido a consulta sobre os dados armazenados em cache uma <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="69302-103"> makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="69302-104">Especificamente, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifica a consulta, permitindo que os desenvolvedores a escrever consultas de linguagem de programação em si, em vez de usando uma linguagem de consulta separada.</span><span class="sxs-lookup"><span data-stu-id="69302-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="69302-105">Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem se beneficiar da verificação de sintaxe de tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="69302-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="69302-106">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também pode ser usado para efetuar consultas a dados que foram consolidados de uma ou mais fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="69302-106">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="69302-107">Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="69302-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="69302-108">Em particular, relatórios genéricos, análise e aplicativos de business intelligence exigem esse método de manipulação.</span><span class="sxs-lookup"><span data-stu-id="69302-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="69302-109">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] funcionalidade é exposta principalmente por meio dos métodos de extensão no <xref:System.Data.DataRowExtensions> e <xref:System.Data.DataTableExtensions> classes.</span><span class="sxs-lookup"><span data-stu-id="69302-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="69302-110"> amplia e usa existente [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] arquitetura e não se destina a substituir [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69302-110"> builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="69302-111">Código do ADO.NET 2.0 existente continuarão a funcionar em um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="69302-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="69302-112">A relação de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] para [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] e o repositório de dados é ilustrado no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="69302-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 <span data-ttu-id="69302-113">![O LINQ to DataSet é baseado no provedor ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span><span class="sxs-lookup"><span data-stu-id="69302-113">![LINQ to DataSet is based on the ADO.NET Provider](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69302-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="69302-114">In This Section</span></span>  
 [<span data-ttu-id="69302-115">Introdução</span><span class="sxs-lookup"><span data-stu-id="69302-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="69302-116">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="69302-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="69302-117">Referência</span><span class="sxs-lookup"><span data-stu-id="69302-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="69302-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69302-118">See Also</span></span>  
 [<span data-ttu-id="69302-119">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="69302-119">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="69302-120">LINQ e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69302-120">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [<span data-ttu-id="69302-121">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69302-121">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
