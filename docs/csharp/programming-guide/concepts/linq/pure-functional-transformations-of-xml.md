---
title: "Transformações funcionais puras de XML (C#)"
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
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ee60c400bb9bff719f818ab5a5a0a3c667a1b412
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="41a4f-102">Transformações funcionais puras de XML (C#)</span><span class="sxs-lookup"><span data-stu-id="41a4f-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="41a4f-103">Esta seção fornece um tutorial funcional de transformação para XML.</span><span class="sxs-lookup"><span data-stu-id="41a4f-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="41a4f-104">Isso inclui explicações sobre conceitos e as compilações de idioma que você deve compreender para usar transformações funcionais, e os exemplos chave de usar transformações e para manipular um documento XML.</span><span class="sxs-lookup"><span data-stu-id="41a4f-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="41a4f-105">Embora este tutorial fornece exemplos de código LINQ to XML, todos os conceitos fundamentais também se aplicam ao outro LINQ tecnologias.</span><span class="sxs-lookup"><span data-stu-id="41a4f-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="41a4f-106">O tutorial [Tutorial: manipulando conteúdo em um documento WordprocessingML](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) fornece uma série de exemplos, cada um deles baseado no anterior.</span><span class="sxs-lookup"><span data-stu-id="41a4f-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="41a4f-107">Esses exemplos demonstram a abordagem transformacional funcional pura a manipular XML.</span><span class="sxs-lookup"><span data-stu-id="41a4f-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="41a4f-108">Este tutorial presume que você tenha um conhecimento prático do C#.</span><span class="sxs-lookup"><span data-stu-id="41a4f-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="41a4f-109">Semânticas detalhada sobre as compilações de linguagem não é fornecida neste tutorial, mas os links são fornecidos para a documentação de linguagem conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="41a4f-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="41a4f-110">Um conhecimento trabalhando dos conceitos básicos e XML de computadores, incluindo namespaces XML, também será adotado.</span><span class="sxs-lookup"><span data-stu-id="41a4f-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41a4f-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="41a4f-111">In This Section</span></span>  
  
|<span data-ttu-id="41a4f-112">Tópico</span><span class="sxs-lookup"><span data-stu-id="41a4f-112">Topic</span></span>|<span data-ttu-id="41a4f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="41a4f-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="41a4f-114">Introdução às transformações funcionais puras (C#)</span><span class="sxs-lookup"><span data-stu-id="41a4f-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="41a4f-115">Descreve transformações funcionais e define a terminologia relevante.</span><span class="sxs-lookup"><span data-stu-id="41a4f-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="41a4f-116">Tutorial: encadear consultas juntas (C#)</span><span class="sxs-lookup"><span data-stu-id="41a4f-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="41a4f-117">Descreve a avaliação lazy e a execução adiada em detalhes.</span><span class="sxs-lookup"><span data-stu-id="41a4f-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="41a4f-118">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="41a4f-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="41a4f-119">Um tutorial que demonstra uma transformação funcional.</span><span class="sxs-lookup"><span data-stu-id="41a4f-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41a4f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41a4f-120">See Also</span></span>  
 [<span data-ttu-id="41a4f-121">Consultando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="41a4f-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

