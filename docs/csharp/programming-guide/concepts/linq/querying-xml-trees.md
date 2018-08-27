---
title: Consultando árvores XML (C#)
ms.date: 07/20/2015
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
ms.openlocfilehash: 5d2e40da26f30a0ece570acf2fd25684d1cba40f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925579"
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="9bb93-102">Consultando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="9bb93-103">Esta seção fornece exemplos de consultas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bb93-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="9bb93-104">Para obter mais informações sobre como escrever consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], consulte [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="9bb93-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="9bb93-105">Depois de você criar a instância de uma árvore XML, a criação de consultas é a forma mais eficaz de extrair dados da árvore.</span><span class="sxs-lookup"><span data-stu-id="9bb93-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="9bb93-106">Além disso, a consulta combinada à construção funcional permite gerar um novo documento XML que tem uma forma diferente do documento original.</span><span class="sxs-lookup"><span data-stu-id="9bb93-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9bb93-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9bb93-107">In This Section</span></span>  
  
|<span data-ttu-id="9bb93-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="9bb93-108">Topic</span></span>|<span data-ttu-id="9bb93-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bb93-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="9bb93-110">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="9bb93-111">Fornece exemplos comuns de como consultar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="9bb93-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="9bb93-112">Projeções e transformações (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="9bb93-113">Fornece exemplos comuns de como projetar e transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="9bb93-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="9bb93-114">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="9bb93-115">Fornece técnicas de consulta que são úteis em cenários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="9bb93-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="9bb93-116">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="9bb93-117">Apresenta um número de expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9bb93-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="9bb93-118">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="9bb93-119">Apresenta um pequeno tutorial de como criar consultas no estilo de programação funcional.</span><span class="sxs-lookup"><span data-stu-id="9bb93-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bb93-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bb93-120">See Also</span></span>  
 [<span data-ttu-id="9bb93-121">Guia de Programação (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9bb93-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="9bb93-122">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="9bb93-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
