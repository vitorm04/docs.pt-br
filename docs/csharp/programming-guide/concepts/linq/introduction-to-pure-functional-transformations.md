---
title: "Introdução às transformações funcionais puras (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 535d022b68fd4d08f04648fb98f5a7a7c53ed6e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="17c15-102">Introdução às transformações funcionais puras (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="17c15-103">Esta seção apresenta transformações funcionais, incluindo os conceitos fundamentais e as compilações de linguagem de suporte.</span><span class="sxs-lookup"><span data-stu-id="17c15-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="17c15-104">Contrasta as abordagens orientados a objeto e funcionais de transformação para programação, incluindo conselhos sobre como fazer a transição para último.</span><span class="sxs-lookup"><span data-stu-id="17c15-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="17c15-105">Embora as transformações e podem ser usadas em muitos cenários de programação, a transformação XML é usado aqui como um exemplo concrete.</span><span class="sxs-lookup"><span data-stu-id="17c15-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17c15-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="17c15-106">In This Section</span></span>  
  
|<span data-ttu-id="17c15-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="17c15-107">Topic</span></span>|<span data-ttu-id="17c15-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="17c15-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="17c15-109">Conceitos e terminologia (transformação funcional) (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-109">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="17c15-110">Apresenta os conceitos e a terminologia de transformações e puras.</span><span class="sxs-lookup"><span data-stu-id="17c15-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="17c15-111">Programação funcional versus Programação obrigatória (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-111">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="17c15-112">Compara e contrasta programação funcional à programação (procedural) imperativa mais tradicional.</span><span class="sxs-lookup"><span data-stu-id="17c15-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="17c15-113">Refatoração em funções puras (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-113">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="17c15-114">Apresenta funções puras, e mostra exemplos de funções e puras e impuros.</span><span class="sxs-lookup"><span data-stu-id="17c15-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="17c15-115">Aplicabilidade da transformação funcional (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-115">Applicability of Functional Transformation (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="17c15-116">Descreve cenários típicos para transformações funcionais.</span><span class="sxs-lookup"><span data-stu-id="17c15-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="17c15-117">Transformação funcional de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17c15-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="17c15-118">Descreve transformações e no contexto de transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="17c15-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17c15-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17c15-119">See Also</span></span>  
 [<span data-ttu-id="17c15-120">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="17c15-120">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
