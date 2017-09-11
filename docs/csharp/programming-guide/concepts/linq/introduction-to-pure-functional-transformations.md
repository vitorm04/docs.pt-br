---
title: "Introdução às transformações funcionais puras (C#)"
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
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 34c4b94577291f300dd2a14ffc33a5ec04b31782
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="c17b9-102">Introdução às transformações funcionais puras (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="c17b9-103">Esta seção apresenta transformações funcionais, incluindo os conceitos fundamentais e as compilações de linguagem de suporte.</span><span class="sxs-lookup"><span data-stu-id="c17b9-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="c17b9-104">Contrasta as abordagens orientados a objeto e funcionais de transformação para programação, incluindo conselhos sobre como fazer a transição para último.</span><span class="sxs-lookup"><span data-stu-id="c17b9-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="c17b9-105">Embora as transformações e podem ser usadas em muitos cenários de programação, a transformação XML é usado aqui como um exemplo concrete.</span><span class="sxs-lookup"><span data-stu-id="c17b9-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c17b9-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c17b9-106">In This Section</span></span>  
  
|<span data-ttu-id="c17b9-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="c17b9-107">Topic</span></span>|<span data-ttu-id="c17b9-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c17b9-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c17b9-109">Conceitos e terminologia (transformação funcional) (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="c17b9-110">Apresenta os conceitos e a terminologia de transformações e puras.</span><span class="sxs-lookup"><span data-stu-id="c17b9-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="c17b9-111">Programação funcional versus Programação obrigatória (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="c17b9-112">Compara e contrasta programação funcional à programação (procedural) imperativa mais tradicional.</span><span class="sxs-lookup"><span data-stu-id="c17b9-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="c17b9-113">Refatoração em funções puras (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="c17b9-114">Apresenta funções puras, e mostra exemplos de funções e puras e impuros.</span><span class="sxs-lookup"><span data-stu-id="c17b9-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="c17b9-115">Aplicabilidade da transformação funcional (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="c17b9-116">Descreve cenários típicos para transformações funcionais.</span><span class="sxs-lookup"><span data-stu-id="c17b9-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="c17b9-117">Transformação funcional de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c17b9-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="c17b9-118">Descreve transformações e no contexto de transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="c17b9-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c17b9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c17b9-119">See Also</span></span>  
 [<span data-ttu-id="c17b9-120">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c17b9-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)

