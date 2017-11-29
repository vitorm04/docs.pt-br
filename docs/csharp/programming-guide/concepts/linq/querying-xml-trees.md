---
title: "Consultando árvores XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66028510b57981879412a1c2a161652adde340bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="8fb11-102">Consultando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="8fb11-103">Esta seção fornece exemplos de consultas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8fb11-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="8fb11-104">Para obter mais informações sobre como escrever consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], consulte [Introdução a LINQ em C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8fb11-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="8fb11-105">Depois de você criar a instância de uma árvore XML, a criação de consultas é a forma mais eficaz de extrair dados da árvore.</span><span class="sxs-lookup"><span data-stu-id="8fb11-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="8fb11-106">Além disso, a consulta combinada à construção funcional permite gerar um novo documento XML que tem uma forma diferente do documento original.</span><span class="sxs-lookup"><span data-stu-id="8fb11-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fb11-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8fb11-107">In This Section</span></span>  
  
|<span data-ttu-id="8fb11-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="8fb11-108">Topic</span></span>|<span data-ttu-id="8fb11-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8fb11-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8fb11-110">Consultas básicas (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="8fb11-111">Fornece exemplos comuns de como consultar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="8fb11-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="8fb11-112">Projeções e transformações (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="8fb11-113">Fornece exemplos comuns de como projetar e transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="8fb11-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="8fb11-114">Técnicas avançadas de consulta (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="8fb11-115">Fornece técnicas de consulta que são úteis em cenários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="8fb11-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="8fb11-116">Usuários do LINQ to XML para XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="8fb11-117">Apresenta um número de expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8fb11-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="8fb11-118">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="8fb11-119">Apresenta um pequeno tutorial de como criar consultas no estilo de programação funcional.</span><span class="sxs-lookup"><span data-stu-id="8fb11-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fb11-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fb11-120">See Also</span></span>  
 [<span data-ttu-id="8fb11-121">Guia de Programação (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fb11-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)  
 [<span data-ttu-id="8fb11-122">Introdução a LINQ em C#</span><span class="sxs-lookup"><span data-stu-id="8fb11-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
