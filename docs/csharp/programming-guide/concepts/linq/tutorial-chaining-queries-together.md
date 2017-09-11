---
title: 'Tutorial: encadear consultas juntas (C#)'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6048ce6a5b477daef5271f75ea1e988725452fcd
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="6bc98-102">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="6bc98-103">Este tutorial mostra o modelo de processamento quando você encadea consultas juntos.</span><span class="sxs-lookup"><span data-stu-id="6bc98-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="6bc98-104">Encadeamento consultas seja adjacente uma parte fundamental de escrever transformações funcionais.</span><span class="sxs-lookup"><span data-stu-id="6bc98-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="6bc98-105">É importante compreender exatamente como as consultas encadeadas funcionam.</span><span class="sxs-lookup"><span data-stu-id="6bc98-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="6bc98-106">Consultas que processam documentos do Office Open XML usam essa técnica amplamente.</span><span class="sxs-lookup"><span data-stu-id="6bc98-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6bc98-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6bc98-107">In This Section</span></span>  
  
|<span data-ttu-id="6bc98-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="6bc98-108">Topic</span></span>|<span data-ttu-id="6bc98-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6bc98-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6bc98-110">Execução adiada e avaliação lenta em LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="6bc98-111">Descreve os conceitos de execução adiada e de avaliação lazy.</span><span class="sxs-lookup"><span data-stu-id="6bc98-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="6bc98-112">Exemplo de execução adiada (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="6bc98-113">Fornece um exemplo de execução adiada.</span><span class="sxs-lookup"><span data-stu-id="6bc98-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="6bc98-114">Exemplo de encadeamento de consultas (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="6bc98-115">Mostra como execução adiada funciona para o encadeamento consulta juntamente.</span><span class="sxs-lookup"><span data-stu-id="6bc98-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="6bc98-116">Materialização intermediária (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="6bc98-117">Identifica e ilustra a semântica de materialization intermediária.</span><span class="sxs-lookup"><span data-stu-id="6bc98-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="6bc98-118">Encadeando operadores de consulta padrão juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="6bc98-119">Descreve a semântica lazy dos operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="6bc98-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bc98-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc98-120">See Also</span></span>  
 [<span data-ttu-id="6bc98-121">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6bc98-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)

