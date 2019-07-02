---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504361"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="77d76-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="77d76-102">LINQ to DataSet</span></span>
<span data-ttu-id="77d76-103">LINQ to DataSet torna mais fácil e mais rápida para consultar sobre dados armazenados em cache em um <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="77d76-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="77d76-104">Especificamente, LINQ to DataSet simplifica as consultas, permitindo que os desenvolvedores escrevam consultas de linguagem de programação em si, em vez de por meio de uma linguagem de consulta separada.</span><span class="sxs-lookup"><span data-stu-id="77d76-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="77d76-105">Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem aproveitar a vantagem de verificação de sintaxe em tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="77d76-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="77d76-106">LINQ to DataSet também pode ser usado para consultar sobre dados que foram consolidados de uma ou mais fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="77d76-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="77d76-107">Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="77d76-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="77d76-108">Em particular, genéricos de relatório, análise e aplicativos de business intelligence requerem esse método de manipulação.</span><span class="sxs-lookup"><span data-stu-id="77d76-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="77d76-109">O LINQ to DataSet funcionalidade é exposto primeiramente por meio de métodos de extensão na <xref:System.Data.DataRowExtensions> e <xref:System.Data.DataTableExtensions> classes.</span><span class="sxs-lookup"><span data-stu-id="77d76-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="77d76-110">LINQ to DataSet baseia-se e usa a arquitetura ADO.NET existente e não se destina a substituir ADO.NET no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77d76-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="77d76-111">Código do ADO.NET existente continuará a funcionar em um aplicativo LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="77d76-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="77d76-112">A relação do LINQ to DataSet ADO.NET e o armazenamento de dados é ilustrada no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="77d76-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagrama mostrando que o LINQ to DataSet é baseado em provedor ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="77d76-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="77d76-114">In This Section</span></span>  
 [<span data-ttu-id="77d76-115">Introdução</span><span class="sxs-lookup"><span data-stu-id="77d76-115">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="77d76-116">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="77d76-116">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="77d76-117">Referência</span><span class="sxs-lookup"><span data-stu-id="77d76-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="77d76-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77d76-118">See also</span></span>

- [<span data-ttu-id="77d76-119">LINQ (consulta integrada à linguagem) – C#</span><span class="sxs-lookup"><span data-stu-id="77d76-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="77d76-120">LINQ (consulta integrada à linguagem) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77d76-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="77d76-121">LINQ e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="77d76-121">LINQ and ADO.NET</span></span>](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="77d76-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="77d76-122">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
