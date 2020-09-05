---
title: Indexadores – Guia de Programação em C#
description: Os indexadores em C# permitem que instâncias de classe ou struct sejam indexadas como matrizes. Você pode definir ou obter o valor indexado sem especificar um tipo ou um membro de instância.
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: ea95eef7bb9ba232e4d59e3f833b82e98398fc33
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495298"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="79e6b-104">Indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="79e6b-104">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="79e6b-105">Os indexadores permitem que instâncias de uma classe ou struct sejam indexados como matrizes.</span><span class="sxs-lookup"><span data-stu-id="79e6b-105">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="79e6b-106">O valor indexado pode ser definido ou recuperado sem especificar explicitamente um membro de instância ou tipo.</span><span class="sxs-lookup"><span data-stu-id="79e6b-106">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="79e6b-107">Os indexadores parecem com [propriedades](../classes-and-structs/properties.md), a diferença é que seus acessadores usam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="79e6b-107">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="79e6b-108">O exemplo a seguir define uma classe genérica com métodos de acesso [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) simples para atribuir e recuperar valores.</span><span class="sxs-lookup"><span data-stu-id="79e6b-108">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="79e6b-109">A classe `Program` cria uma instância dessa classe para armazenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="79e6b-109">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="79e6b-110">Para mais exemplos, consulte as [seções relacionadas](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="79e6b-110">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="79e6b-111">Definições de corpo de expressão</span><span class="sxs-lookup"><span data-stu-id="79e6b-111">Expression Body Definitions</span></span>  

<span data-ttu-id="79e6b-112">É comum para um acessador get ou set de um indexador ser constituído de uma única instrução que retorna ou define um valor.</span><span class="sxs-lookup"><span data-stu-id="79e6b-112">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="79e6b-113">Os membros de expressão fornecem uma sintaxe simplificada para dar suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="79e6b-113">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="79e6b-114">Começando do C# 6, um indexador somente leitura pode ser implementado como um membro de expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="79e6b-114">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="79e6b-115">Observe que `=>` apresenta o corpo da expressão e que a palavra-chave `get` não é usada.</span><span class="sxs-lookup"><span data-stu-id="79e6b-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="79e6b-116">Começando do C# 7.0, os acessadores get e set podem ser implementados como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="79e6b-116">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="79e6b-117">Nesse caso, as palavras-chave `get` e `set` devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="79e6b-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="79e6b-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="79e6b-118">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="79e6b-119">Visão Geral dos Indexadores</span><span class="sxs-lookup"><span data-stu-id="79e6b-119">Indexers Overview</span></span>  
  
- <span data-ttu-id="79e6b-120">Os indexadores permitem que objetos sejam indexados de maneira semelhante às matrizes.</span><span class="sxs-lookup"><span data-stu-id="79e6b-120">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="79e6b-121">Um acessador `get` retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="79e6b-121">A `get` accessor returns a value.</span></span> <span data-ttu-id="79e6b-122">Um acessador `set` atribui um valor.</span><span class="sxs-lookup"><span data-stu-id="79e6b-122">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="79e6b-123">A palavra-chave [this](../../language-reference/keywords/this.md) é usada para definir o indexador.</span><span class="sxs-lookup"><span data-stu-id="79e6b-123">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="79e6b-124">A palavra-chave [value](../../language-reference/keywords/value.md) é usada para definir o valor que está sendo atribuído pelo acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="79e6b-124">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
  
- <span data-ttu-id="79e6b-125">Os indexadores não precisam ser indexados por um valor inteiro. Você deve definir o mecanismo de pesquisa específico.</span><span class="sxs-lookup"><span data-stu-id="79e6b-125">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="79e6b-126">Os indexadores podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="79e6b-126">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="79e6b-127">Os indexadores podem ter mais de um parâmetro formal, por exemplo, ao acessar uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="79e6b-127">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="related-sections"></a><a name="BKMK_RelatedSections"></a> <span data-ttu-id="79e6b-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="79e6b-128">Related Sections</span></span>  
  
- [<span data-ttu-id="79e6b-129">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="79e6b-129">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="79e6b-130">Indexadores em interfaces</span><span class="sxs-lookup"><span data-stu-id="79e6b-130">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="79e6b-131">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="79e6b-131">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="79e6b-132">Restringindo a acessibilidade ao acessador</span><span class="sxs-lookup"><span data-stu-id="79e6b-132">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="79e6b-133">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="79e6b-133">C# Language Specification</span></span>  

<span data-ttu-id="79e6b-134">Para obter mais informações, veja [Indexadores](~/_csharplang/spec/classes.md#indexers) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="79e6b-134">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="79e6b-135">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="79e6b-135">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="79e6b-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="79e6b-136">See also</span></span>

- [<span data-ttu-id="79e6b-137">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="79e6b-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="79e6b-138">Propriedades</span><span class="sxs-lookup"><span data-stu-id="79e6b-138">Properties</span></span>](../classes-and-structs/properties.md)
