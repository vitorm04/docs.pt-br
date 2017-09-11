---
title: "Introdução às transformações e puras (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 82bf3348-c503-4854-a91f-71f9835779ff
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 72d05eada95f5ce08d60c283346e221328c23020
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="introduction-to-pure-functional-transformations-visual-basic"></a><span data-ttu-id="2cd9b-102">Introdução às transformações e puras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-102">Introduction to Pure Functional Transformations (Visual Basic)</span></span>
<span data-ttu-id="2cd9b-103">Esta seção apresenta transformações funcionais, incluindo os conceitos fundamentais e as compilações de linguagem de suporte.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="2cd9b-104">Contrasta as abordagens orientados a objeto e funcionais de transformação para programação, incluindo conselhos sobre como fazer a transição para último.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="2cd9b-105">Embora as transformações e podem ser usadas em muitos cenários de programação, a transformação XML é usado aqui como um exemplo concrete.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2cd9b-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="2cd9b-106">In This Section</span></span>  
  
|<span data-ttu-id="2cd9b-107">Tópico</span><span class="sxs-lookup"><span data-stu-id="2cd9b-107">Topic</span></span>|<span data-ttu-id="2cd9b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2cd9b-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2cd9b-109">Conceitos e terminologia (transformação funcional) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-109">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="2cd9b-110">Apresenta os conceitos e a terminologia de transformações e puras.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-110">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="2cd9b-111">Programação funcional versus Programação imperativa (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-111">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)|<span data-ttu-id="2cd9b-112">Compara e contrasta programação funcional à programação (procedural) imperativa mais tradicional.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-112">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="2cd9b-113">Refatoração em funções puras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-113">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)|<span data-ttu-id="2cd9b-114">Apresenta funções puras, e mostra exemplos de funções e puras e impuros.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-114">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="2cd9b-115">Aplicabilidade de transformação funcional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-115">Applicability of Functional Transformation (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/applicability-of-functional-transformation.md)|<span data-ttu-id="2cd9b-116">Descreve cenários típicos para transformações funcionais.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-116">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="2cd9b-117">Transformação funcional XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-117">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="2cd9b-118">Descreve transformações e no contexto de transformar árvores XML.</span><span class="sxs-lookup"><span data-stu-id="2cd9b-118">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cd9b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cd9b-119">See Also</span></span>  
 [<span data-ttu-id="2cd9b-120">Transformações e puras XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cd9b-120">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
