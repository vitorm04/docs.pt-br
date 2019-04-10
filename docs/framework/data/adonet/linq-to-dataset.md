---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 92be418e38039757437e6e673f39a7baef011528
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221776"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="d7b88-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d7b88-102">LINQ to DataSet</span></span>
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="d7b88-103">torna mais fácil e mais rápida para consultar dados armazenados em cache em um <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="d7b88-103">makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="d7b88-104">Especificamente, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifica as consultas, permitindo que os desenvolvedores escrevam consultas de linguagem de programação em si, em vez de por meio de uma linguagem de consulta separada.</span><span class="sxs-lookup"><span data-stu-id="d7b88-104">Specifically, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="d7b88-105">Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem aproveitar a vantagem de verificação de sintaxe em tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="d7b88-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="d7b88-106">também pode ser usado para consultar sobre dados que foram consolidados de uma ou mais fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="d7b88-106">can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="d7b88-107">Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="d7b88-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="d7b88-108">Em particular, genéricos de relatório, análise e aplicativos de business intelligence requerem esse método de manipulação.</span><span class="sxs-lookup"><span data-stu-id="d7b88-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="d7b88-109">O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] funcionalidade é exposta primeiramente por meio de métodos de extensão em de <xref:System.Data.DataRowExtensions> e <xref:System.Data.DataTableExtensions> classes.</span><span class="sxs-lookup"><span data-stu-id="d7b88-109">The [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] <span data-ttu-id="d7b88-110">se baseia no existente e a utiliza [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] arquitetura e não se destina a substituir [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7b88-110">builds on and uses the existing [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architecture, and is not meant to replace [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] in application code.</span></span> <span data-ttu-id="d7b88-111">Código do ADO.NET 2.0 existente continuará a funcionar em um [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d7b88-111">Existing ADO.NET 2.0 code will continue to function in a [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] application.</span></span> <span data-ttu-id="d7b88-112">A relação das [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] para [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] e o armazenamento de dados é ilustrado no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="d7b88-112">The relationship of [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagrama mostrando que o LINQ to DataSet é baseado em provedor ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="d7b88-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d7b88-114">In This Section</span></span>  
 [<span data-ttu-id="d7b88-115">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="d7b88-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="d7b88-116">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="d7b88-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="d7b88-117">Referência</span><span class="sxs-lookup"><span data-stu-id="d7b88-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="d7b88-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b88-118">See also</span></span>

- [<span data-ttu-id="d7b88-119">Consulta integrada à linguagem (LINQ)-C#</span><span class="sxs-lookup"><span data-stu-id="d7b88-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d7b88-120">Consulta integrada à linguagem (LINQ) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7b88-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d7b88-121">LINQ e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7b88-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="d7b88-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7b88-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
