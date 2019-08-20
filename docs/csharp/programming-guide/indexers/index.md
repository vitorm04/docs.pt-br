---
title: Indexadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 130cc68906be433afc906cfb22759f4ae3dba447
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589450"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="b5dba-102">Indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b5dba-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="b5dba-103">Os indexadores permitem que instâncias de uma classe ou struct sejam indexados como matrizes.</span><span class="sxs-lookup"><span data-stu-id="b5dba-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="b5dba-104">O valor indexado pode ser definido ou recuperado sem especificar explicitamente um membro de instância ou tipo.</span><span class="sxs-lookup"><span data-stu-id="b5dba-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="b5dba-105">Os indexadores parecem com [propriedades](../classes-and-structs/properties.md), a diferença é que seus acessadores usam parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b5dba-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="b5dba-106">O exemplo a seguir define uma classe genérica com métodos de acesso [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) simples para atribuir e recuperar valores.</span><span class="sxs-lookup"><span data-stu-id="b5dba-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="b5dba-107">A classe `Program` cria uma instância dessa classe para armazenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b5dba-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="b5dba-108">Para mais exemplos, consulte as [seções relacionadas](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="b5dba-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="b5dba-109">Definições de corpo de expressão</span><span class="sxs-lookup"><span data-stu-id="b5dba-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="b5dba-110">É comum para um acessador get ou set de um indexador ser constituído de uma única instrução que retorna ou define um valor.</span><span class="sxs-lookup"><span data-stu-id="b5dba-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="b5dba-111">Os membros de expressão fornecem uma sintaxe simplificada para dar suporte a esse cenário.</span><span class="sxs-lookup"><span data-stu-id="b5dba-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="b5dba-112">Começando do C# 6, um indexador somente leitura pode ser implementado como um membro de expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5dba-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="b5dba-113">Observe que `=>` apresenta o corpo da expressão e que a palavra-chave `get` não é usada.</span><span class="sxs-lookup"><span data-stu-id="b5dba-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="b5dba-114">Começando do C# 7.0, os acessadores get e set podem ser implementados como membros aptos para expressão.</span><span class="sxs-lookup"><span data-stu-id="b5dba-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="b5dba-115">Nesse caso, as palavras-chave `get` e `set` devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="b5dba-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="b5dba-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b5dba-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="b5dba-117">Visão Geral dos Indexadores</span><span class="sxs-lookup"><span data-stu-id="b5dba-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="b5dba-118">Os indexadores permitem que objetos sejam indexados de maneira semelhante às matrizes.</span><span class="sxs-lookup"><span data-stu-id="b5dba-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="b5dba-119">Um acessador `get` retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="b5dba-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="b5dba-120">Um acessador `set` atribui um valor.</span><span class="sxs-lookup"><span data-stu-id="b5dba-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="b5dba-121">A palavra-chave [this](../../language-reference/keywords/this.md) é usada para definir o indexador.</span><span class="sxs-lookup"><span data-stu-id="b5dba-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="b5dba-122">A palavra-chave [value](../../language-reference/keywords/value.md) é usada para definir o valor que está sendo atribuído pelo indexador `set`.</span><span class="sxs-lookup"><span data-stu-id="b5dba-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="b5dba-123">Os indexadores não precisam ser indexados por um valor inteiro. Você deve definir o mecanismo de pesquisa específico.</span><span class="sxs-lookup"><span data-stu-id="b5dba-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="b5dba-124">Os indexadores podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="b5dba-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="b5dba-125">Os indexadores podem ter mais de um parâmetro formal, por exemplo, ao acessar uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="b5dba-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a> <span data-ttu-id="b5dba-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b5dba-126">Related Sections</span></span>  
  
- [<span data-ttu-id="b5dba-127">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="b5dba-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="b5dba-128">Indexadores em interfaces</span><span class="sxs-lookup"><span data-stu-id="b5dba-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="b5dba-129">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="b5dba-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="b5dba-130">Restringindo a acessibilidade ao acessador</span><span class="sxs-lookup"><span data-stu-id="b5dba-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b5dba-131">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b5dba-131">C# Language Specification</span></span>  

<span data-ttu-id="b5dba-132">Para obter mais informações, veja [Indexadores](~/_csharplang/spec/classes.md#indexers) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5dba-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="b5dba-133">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="b5dba-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b5dba-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5dba-134">See also</span></span>

- [<span data-ttu-id="b5dba-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b5dba-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5dba-136">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b5dba-136">Properties</span></span>](../classes-and-structs/properties.md)
