---
title: 'Tutorial: encadear consultas juntas (C#)'
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: 8411d8577c192e2aa1a43bea47644fe6bdc09e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323704"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="3015f-102">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="3015f-103">Este tutorial mostra o modelo de processamento quando você encadea consultas juntos.</span><span class="sxs-lookup"><span data-stu-id="3015f-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="3015f-104">Encadeamento consultas seja adjacente uma parte fundamental de escrever transformações funcionais.</span><span class="sxs-lookup"><span data-stu-id="3015f-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="3015f-105">É importante compreender exatamente como as consultas encadeadas funcionam.</span><span class="sxs-lookup"><span data-stu-id="3015f-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="3015f-106">Consultas que processam documentos do Office Open XML usam essa técnica amplamente.</span><span class="sxs-lookup"><span data-stu-id="3015f-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3015f-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3015f-107">In This Section</span></span>  
  
|<span data-ttu-id="3015f-108">Tópico</span><span class="sxs-lookup"><span data-stu-id="3015f-108">Topic</span></span>|<span data-ttu-id="3015f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3015f-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="3015f-110">Execução adiada e avaliação lenta em LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="3015f-111">Descreve os conceitos de execução adiada e de avaliação lazy.</span><span class="sxs-lookup"><span data-stu-id="3015f-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="3015f-112">Exemplo de execução adiada (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="3015f-113">Fornece um exemplo de execução adiada.</span><span class="sxs-lookup"><span data-stu-id="3015f-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="3015f-114">Exemplo de encadeamento de consultas (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="3015f-115">Mostra como execução adiada funciona para o encadeamento consulta juntamente.</span><span class="sxs-lookup"><span data-stu-id="3015f-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="3015f-116">Materialização intermediária (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="3015f-117">Identifica e ilustra a semântica de materialization intermediária.</span><span class="sxs-lookup"><span data-stu-id="3015f-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="3015f-118">Encadeando operadores de consulta padrão juntos (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="3015f-119">Descreve a semântica lazy dos operadores de consulta padrão.</span><span class="sxs-lookup"><span data-stu-id="3015f-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3015f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3015f-120">See Also</span></span>  
 [<span data-ttu-id="3015f-121">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3015f-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
