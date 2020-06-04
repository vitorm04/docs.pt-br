---
title: Consultando árvores XML
ms.date: 07/20/2015
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
ms.openlocfilehash: 22e3dd873e2be8381f3d8da8f7c4284d09e45543
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411864"
---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="e9a37-102">Consultando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="e9a37-103">Esta seção fornece exemplos de consultas [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a37-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="e9a37-104">Para obter mais informações sobre como escrever consultas LINQ, consulte [introdução com LINQ no Visual Basic](getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="e9a37-104">For more information about writing LINQ queries, see [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="e9a37-105">Depois de você criar a instância de uma árvore XML, a criação de consultas é a forma mais eficaz de extrair dados da árvore.</span><span class="sxs-lookup"><span data-stu-id="e9a37-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="e9a37-106">Além disso, a consulta combinada à construção funcional permite gerar um novo documento XML que tem uma forma diferente do documento original.</span><span class="sxs-lookup"><span data-stu-id="e9a37-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9a37-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e9a37-107">In This Section</span></span>  
  
|<span data-ttu-id="e9a37-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="e9a37-108">Topic</span></span>|<span data-ttu-id="e9a37-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9a37-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e9a37-110">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)|<span data-ttu-id="e9a37-111">Fornece exemplos comuns de como consultar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="e9a37-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="e9a37-112">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="e9a37-113">Fornece exemplos comuns de como projetar e transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="e9a37-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="e9a37-114">Técnicas de consulta avançada (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="e9a37-115">Fornece técnicas de consulta que são úteis em cenários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="e9a37-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="e9a37-116">LINQ to XML para usuários do XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)|<span data-ttu-id="e9a37-117">Apresenta um número de expressões XPath e seus equivalentes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9a37-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="e9a37-118">Transformações funcionais puras de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)|<span data-ttu-id="e9a37-119">Apresenta um pequeno tutorial de como criar consultas no estilo de programação funcional.</span><span class="sxs-lookup"><span data-stu-id="e9a37-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9a37-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9a37-120">See also</span></span>

- [<span data-ttu-id="e9a37-121">Guia de programação (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9a37-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
- [<span data-ttu-id="e9a37-122">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9a37-122">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
