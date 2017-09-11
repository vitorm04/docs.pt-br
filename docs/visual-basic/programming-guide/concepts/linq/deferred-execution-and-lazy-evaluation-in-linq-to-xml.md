---
title: "Adiado de execução e avaliação lenta em LINQ to XML (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9ecb4d18cf7c61442e17de1c0f08824b360362e1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="79011-102">Execução adiada e avaliação lenta em LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79011-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="79011-103">As operações de consulta e eixo são geralmente implementadas para usar a execução adiada.</span><span class="sxs-lookup"><span data-stu-id="79011-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="79011-104">Este tópico explica os requisitos e as vantagens da execução adiada, além de algumas considerações sobre a implementação.</span><span class="sxs-lookup"><span data-stu-id="79011-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="79011-105">Execução Adiada</span><span class="sxs-lookup"><span data-stu-id="79011-105">Deferred Execution</span></span>  
 <span data-ttu-id="79011-106">Execução adiada significa que a avaliação de uma expressão é atrasada até o seu *percebeu* valor seja realmente necessário.</span><span class="sxs-lookup"><span data-stu-id="79011-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="79011-107">A execução adiada pode aumentar muito o desempenho quando você precisa manipular grandes coleções de dados, especialmente em programas que contêm uma série de consultas ou manipulações encadeadas.</span><span class="sxs-lookup"><span data-stu-id="79011-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="79011-108">Na melhor das hipóteses, a execução adiada permite apenas uma única iteração pela coleção de origem.</span><span class="sxs-lookup"><span data-stu-id="79011-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="79011-109">As tecnologias LINQ fazem uso extensivo de execução adiada em ambos os membros do núcleo <xref:System.Linq?displayProperty=fullName>classes e métodos de extensão nos diversos namespaces LINQ, como <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</xref:System.Xml.Linq.Extensions?displayProperty=fullName> </xref:System.Linq?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="79011-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=fullName> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="79011-110">Avaliação ansiosa vs. lenta</span><span class="sxs-lookup"><span data-stu-id="79011-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="79011-111">Quando você escreve um método que implementa a execução adiada, também precisa decidir se deve implementar o método usando a avaliação lenta ou a avaliação ansiosa.</span><span class="sxs-lookup"><span data-stu-id="79011-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="79011-112">Em *avaliação lenta*, um único elemento da coleção de origem é processado durante cada chamada ao iterador.</span><span class="sxs-lookup"><span data-stu-id="79011-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="79011-113">Essa é a forma comum de implementação de iteradores.</span><span class="sxs-lookup"><span data-stu-id="79011-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="79011-114">Em *avaliação rápida*, a primeira chamada ao iterador resultará em toda a coleção que está sendo processada.</span><span class="sxs-lookup"><span data-stu-id="79011-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="79011-115">Uma cópia temporária da coleção de origem também pode ser necessária.</span><span class="sxs-lookup"><span data-stu-id="79011-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="79011-116">Por exemplo, o <xref:System.Linq.Enumerable.OrderBy%2A>método precisa classificar toda a coleção antes de retornar o primeiro elemento.</xref:System.Linq.Enumerable.OrderBy%2A></span><span class="sxs-lookup"><span data-stu-id="79011-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="79011-117">A avaliação lenta normalmente gera um melhor desempenho porque distribui a sobrecarga de processamento uniformemente por toda a avaliação da coleção e minimiza o uso de dados temporários.</span><span class="sxs-lookup"><span data-stu-id="79011-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="79011-118">Naturalmente, para algumas operações, não há nenhuma outra opção que não seja materializar resultados intermediários.</span><span class="sxs-lookup"><span data-stu-id="79011-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="79011-119">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="79011-119">Next Steps</span></span>  
 <span data-ttu-id="79011-120">O próximo tópico deste tutorial ilustra a execução adiada:</span><span class="sxs-lookup"><span data-stu-id="79011-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="79011-121">Exemplo de execução adiada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79011-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="79011-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79011-122">See Also</span></span>  
 <span data-ttu-id="79011-123">[Tutorial: Adiada execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md) </span><span class="sxs-lookup"><span data-stu-id="79011-123">[Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md) </span></span>  
<span data-ttu-id="79011-124"> [Conceitos e terminologia (transformação funcional) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="79011-124"> [Concepts and Terminology (Functional Transformation) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span></span>  
<span data-ttu-id="79011-125"> [Operações de agregação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)</span><span class="sxs-lookup"><span data-stu-id="79011-125"> [Aggregation Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)</span></span>
