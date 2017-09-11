---
title: "Consultando árvores XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 2e35c1ab-08c8-4378-9ca8-8ff344756eda
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b2aa1e4852657590449be3e297302bf41ba3e5d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="querying-xml-trees-visual-basic"></a><span data-ttu-id="afbbd-102">Consultando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-102">Querying XML Trees (Visual Basic)</span></span>
<span data-ttu-id="afbbd-103">Esta seção fornece exemplos de consultas [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="afbbd-103">This section provides examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] queries.</span></span>  
  
 <span data-ttu-id="afbbd-104">Para obter mais informações sobre como escrever [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas, consulte [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="afbbd-104">For more information about writing [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries, see [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="afbbd-105">Depois de você criar a instância de uma árvore XML, a criação de consultas é a forma mais eficaz de extrair dados da árvore.</span><span class="sxs-lookup"><span data-stu-id="afbbd-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="afbbd-106">Além disso, a consulta combinada à construção funcional permite gerar um novo documento XML que tem uma forma diferente do documento original.</span><span class="sxs-lookup"><span data-stu-id="afbbd-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afbbd-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="afbbd-107">In This Section</span></span>  
  
|<span data-ttu-id="afbbd-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="afbbd-108">Topic</span></span>|<span data-ttu-id="afbbd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="afbbd-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="afbbd-110">Consultas básicas (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-110">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="afbbd-111">Fornece exemplos comuns de como consultar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="afbbd-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="afbbd-112">Projeções e transformações (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-112">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="afbbd-113">Fornece exemplos comuns de como projetar e transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="afbbd-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="afbbd-114">Técnicas avançadas de consulta (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="afbbd-115">Fornece técnicas de consulta que são úteis em cenários mais avançados.</span><span class="sxs-lookup"><span data-stu-id="afbbd-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="afbbd-116">LINQ to XML para XPath usuários (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="afbbd-117">Apresenta um número de expressões XPath e seus [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] equivalentes.</span><span class="sxs-lookup"><span data-stu-id="afbbd-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="afbbd-118">Transformações e puras XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afbbd-118">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="afbbd-119">Apresenta um pequeno tutorial de como criar consultas no estilo de programação funcional.</span><span class="sxs-lookup"><span data-stu-id="afbbd-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afbbd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afbbd-120">See Also</span></span>  
 <span data-ttu-id="afbbd-121">[Guia de programação (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="afbbd-121">[Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
<span data-ttu-id="afbbd-122"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span><span class="sxs-lookup"><span data-stu-id="afbbd-122"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)</span></span>
