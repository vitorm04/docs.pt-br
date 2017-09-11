---
title: "Indexadores (Guia de Programação em C#)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 784308f3073114cd0c07cf15edae527a2654edec
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="9d8bb-102">Indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9d8bb-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="9d8bb-103">Os indexadores permitem que instâncias de uma classe ou struct sejam indexados como matrizes.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="9d8bb-104">O valor indexado pode ser definido ou recuperado sem especificar explicitamente um membro de instância ou tipo.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="9d8bb-105">Os indexadores parecem com [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), a diferença é que seus acessadores usam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="9d8bb-106">O exemplo a seguir define uma classe genérica com métodos de acesso [get](../../../csharp/language-reference/keywords/get.md) e [set](../../../csharp/language-reference/keywords/set.md) simples para atribuir e recuperar valores.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="9d8bb-107">A classe `Program` cria uma instância dessa classe para armazenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 <span data-ttu-id="9d8bb-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9d8bb-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d8bb-109">Para mais exemplos, consulte as [seções relacionadas](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="9d8bb-109">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="9d8bb-110">Definições de corpo de expressão</span><span class="sxs-lookup"><span data-stu-id="9d8bb-110">Expression Body Definitions</span></span>  
 
<span data-ttu-id="9d8bb-111">É comum para um acessador get ou set de um indexador ser constituído de uma única instrução que retorna ou define um valor.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-111">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="9d8bb-112">Os membros de expressão fornecem uma sintaxe simplificada para dar suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-112">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="9d8bb-113">Começando do C# 6, um indexador somente leitura pode ser implementado como um membro de expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-113">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

<span data-ttu-id="9d8bb-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9d8bb-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span></span>  

<span data-ttu-id="9d8bb-115">Observe que `=>` apresenta o corpo da expressão e que a palavra-chave `get` não é usada.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="9d8bb-116">Começando do C# 7, os acessadores get e set podem ser implementados como membros de expressão.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-116">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="9d8bb-117">Nesse caso, as palavras-chave `get` e `set` devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="9d8bb-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9d8bb-118">For example:</span></span>

<span data-ttu-id="9d8bb-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9d8bb-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span></span>  
  
## <a name="indexers-overview"></a><span data-ttu-id="9d8bb-120">Visão Geral dos Indexadores</span><span class="sxs-lookup"><span data-stu-id="9d8bb-120">Indexers Overview</span></span>  
  
-   <span data-ttu-id="9d8bb-121">Os indexadores permitem que objetos sejam indexados de maneira semelhante às matrizes.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-121">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="9d8bb-122">Um acessador `get` retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-122">A `get` accessor returns a value.</span></span> <span data-ttu-id="9d8bb-123">Um acessador `set` atribui um valor.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-123">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="9d8bb-124">A palavra-chave [this](../../../csharp/language-reference/keywords/this.md) é usada para definir o indexador.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-124">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="9d8bb-125">A palavra-chave [value](../../../csharp/language-reference/keywords/value.md) é usada para definir o valor que está sendo atribuído pelo indexador `set`.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-125">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="9d8bb-126">Os indexadores não precisam ser indexados por um valor inteiro. Você deve definir o mecanismo de pesquisa específico.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-126">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="9d8bb-127">Os indexadores podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-127">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="9d8bb-128">Os indexadores podem ter mais de um parâmetro formal, por exemplo, ao acessar uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="9d8bb-128">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <span data-ttu-id="9d8bb-129"><a name="BKMK_RelatedSections"></a> Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9d8bb-129"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="9d8bb-130">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="9d8bb-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="9d8bb-131">Indexadores em interfaces</span><span class="sxs-lookup"><span data-stu-id="9d8bb-131">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="9d8bb-132">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="9d8bb-132">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="9d8bb-133">Restringindo a acessibilidade ao acessador</span><span class="sxs-lookup"><span data-stu-id="9d8bb-133">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9d8bb-134">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9d8bb-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d8bb-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d8bb-135">See Also</span></span>  
 <span data-ttu-id="9d8bb-136">[Guia de programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d8bb-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="9d8bb-137">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9d8bb-137">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

