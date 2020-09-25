---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 1c03cca80de6003a4e49278871983ed7fcb3dc0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200660"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="3765b-102">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3765b-102">LINQ to DataSet</span></span>

<span data-ttu-id="3765b-103">LINQ to DataSet torna mais fácil e rápido a consulta sobre dados armazenados em cache em um <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="3765b-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="3765b-104">Especificamente, LINQ to DataSet simplifica a consulta, permitindo que os desenvolvedores gravem consultas a partir da própria linguagem de programação, em vez de usar uma linguagem de consulta separada.</span><span class="sxs-lookup"><span data-stu-id="3765b-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="3765b-105">Isso é especialmente útil para desenvolvedores do Visual Studio, que agora podem aproveitar a verificação de sintaxe de tempo de compilação, digitação estática e suporte do IntelliSense fornecidos pelo Visual Studio em suas consultas.</span><span class="sxs-lookup"><span data-stu-id="3765b-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="3765b-106">LINQ to DataSet também pode ser usado para consultar dados que foram consolidados de uma ou mais fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="3765b-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="3765b-107">Isso permite vários cenários que requerem flexibilidade na representação e na manipulação de dados, como consultas a dados localmente agregados e a cache de camada intermediária em aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="3765b-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="3765b-108">Em particular, os aplicativos genéricos de relatório, análise e business intelligence requerem esse método de manipulação.</span><span class="sxs-lookup"><span data-stu-id="3765b-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="3765b-109">A funcionalidade de LINQ to DataSet é exposta principalmente por meio dos métodos de extensão nas <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> classes e.</span><span class="sxs-lookup"><span data-stu-id="3765b-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="3765b-110">LINQ to DataSet baseia-se no e usa a arquitetura ADO.NET existente e não se destina a substituir o ADO.NET no código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3765b-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="3765b-111">O código ADO.NET existente continuará a funcionar em um aplicativo LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="3765b-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="3765b-112">A relação de LINQ to DataSet para ADO.NET e o armazenamento de dados é ilustrada no diagrama a seguir.</span><span class="sxs-lookup"><span data-stu-id="3765b-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagrama mostrando que LINQ to DataSet se baseia no provedor ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="3765b-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3765b-114">In This Section</span></span>  

 [<span data-ttu-id="3765b-115">Introdução</span><span class="sxs-lookup"><span data-stu-id="3765b-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="3765b-116">Guia de programação</span><span class="sxs-lookup"><span data-stu-id="3765b-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="3765b-117">Referência</span><span class="sxs-lookup"><span data-stu-id="3765b-117">Reference</span></span>  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="3765b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="3765b-118">See also</span></span>

- [<span data-ttu-id="3765b-119">LINQ (consulta integrada à linguagem) – C#</span><span class="sxs-lookup"><span data-stu-id="3765b-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="3765b-120">LINQ (consulta integrada à linguagem) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3765b-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="3765b-121">LINQ e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3765b-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="3765b-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3765b-122">ADO.NET</span></span>](index.md)
