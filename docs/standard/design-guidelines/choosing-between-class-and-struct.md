---
title: Escolhendo entre a classe e Struct
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7b7a0b290b97966894b9fa7d3b5597e68037cb0
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="214a5-102">Escolhendo entre a classe e Struct</span><span class="sxs-lookup"><span data-stu-id="214a5-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="214a5-103">Uma das decisões de design básico que faces cada designer de estrutura é um tipo de design como uma classe (um tipo de referência) ou como uma estrutura (um tipo de valor).</span><span class="sxs-lookup"><span data-stu-id="214a5-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="214a5-104">Boa compreensão das diferenças no comportamento de tipos de referência e tipos de valor é crucial para essa opção.</span><span class="sxs-lookup"><span data-stu-id="214a5-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="214a5-105">O primeiro a diferença entre os tipos de referência e tipos de valor consideraremos é que os tipos de referência são alocados no heap e coleta de lixo, enquanto tipos de valor são alocados na pilha ou embutido no contendo tipos e desalocada quando a pilha esvazia ou quando seu tipo recipiente obtém desalocado.</span><span class="sxs-lookup"><span data-stu-id="214a5-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="214a5-106">Portanto, as alocações e Desalocações de tipos de valor são em geral mais barato do que as alocações e Desalocações de tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="214a5-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="214a5-107">Em seguida, matrizes de referência de tipos são alocados fora de linha, que significa que a matriz de elementos são apenas referências a instâncias do tipo de referência que residem no heap.</span><span class="sxs-lookup"><span data-stu-id="214a5-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="214a5-108">Matrizes de tipo de valor são alocadas embutido, o que significa que os elementos da matriz são as instâncias reais do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="214a5-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="214a5-109">Portanto, as alocações e Desalocações de matrizes de tipo de valor são muito mais baratas do que as alocações e Desalocações de matrizes de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="214a5-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="214a5-110">Além disso, na maioria dos casos, matrizes de tipo de valor exibem muito melhor localidade de referência.</span><span class="sxs-lookup"><span data-stu-id="214a5-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="214a5-111">A próxima diferença está relacionada ao uso de memória.</span><span class="sxs-lookup"><span data-stu-id="214a5-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="214a5-112">Tipos de valor obtenham demarcados quando convertido em um tipo de referência ou uma das interfaces de implementação.</span><span class="sxs-lookup"><span data-stu-id="214a5-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="214a5-113">Eles obtêm não demarcados quando convertido para o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="214a5-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="214a5-114">Como caixas são objetos que são alocados no heap e são coletados como lixo, muito conversão boxing e unboxing pode ter um impacto negativo sobre o heap, o coletor de lixo e, finalmente, o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="214a5-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="214a5-115">Por outro lado, não há tal conversão boxing ocorre como tipos de referência são convertidos.</span><span class="sxs-lookup"><span data-stu-id="214a5-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="214a5-116">Em seguida, as atribuições de tipo de referência copiar a referência, enquanto as atribuições de tipo de valor copie o valor inteiro.</span><span class="sxs-lookup"><span data-stu-id="214a5-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="214a5-117">Portanto, as atribuições de tipos de referência grandes são mais baratas do que as atribuições de tipos de valor grande.</span><span class="sxs-lookup"><span data-stu-id="214a5-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="214a5-118">Por fim, os tipos de referência são passados por referência, enquanto tipos de valor são transmitidos por valor.</span><span class="sxs-lookup"><span data-stu-id="214a5-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="214a5-119">As alterações a uma instância de um tipo de referência afetam todas as referências que apontam para a instância.</span><span class="sxs-lookup"><span data-stu-id="214a5-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="214a5-120">Instâncias de tipo de valor são copiadas quando eles são passados por valor.</span><span class="sxs-lookup"><span data-stu-id="214a5-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="214a5-121">Quando uma instância de um tipo de valor é alterada, obviamente não afeta qualquer uma das suas cópias.</span><span class="sxs-lookup"><span data-stu-id="214a5-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="214a5-122">Como as cópias não são criadas explicitamente pelo usuário, mas são criadas implicitamente quando os argumentos são transmitidos ou retornam os valores são retornados, tipos de valor que podem ser alterados podem ser confusos para vários usuários.</span><span class="sxs-lookup"><span data-stu-id="214a5-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="214a5-123">Portanto, os tipos de valor devem ser imutáveis.</span><span class="sxs-lookup"><span data-stu-id="214a5-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="214a5-124">Como regra geral, a maioria dos tipos em uma estrutura deve ser classes.</span><span class="sxs-lookup"><span data-stu-id="214a5-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="214a5-125">No entanto, há algumas situações em que as características de um tipo de valor torná-lo mais apropriado usar estruturas.</span><span class="sxs-lookup"><span data-stu-id="214a5-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="214a5-126">**✓ CONSIDERE** definindo um struct, em vez de uma classe, se as instâncias do tipo são pequena e geralmente curta duração ou geralmente são inseridas em outros objetos.</span><span class="sxs-lookup"><span data-stu-id="214a5-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="214a5-127">**X Evite** definindo uma estrutura, a menos que o tipo tem todas as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="214a5-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="214a5-128">Representa um único valor, semelhante aos tipos primitivos logicamente (`int`, `double`, etc.).</span><span class="sxs-lookup"><span data-stu-id="214a5-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="214a5-129">Ele tem um tamanho de instância em 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="214a5-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="214a5-130">É imutável.</span><span class="sxs-lookup"><span data-stu-id="214a5-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="214a5-131">Ele não precisa ser boxed com frequência.</span><span class="sxs-lookup"><span data-stu-id="214a5-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="214a5-132">Em todos os outros casos, você deve definir os tipos de classes.</span><span class="sxs-lookup"><span data-stu-id="214a5-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="214a5-133">*Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*</span><span class="sxs-lookup"><span data-stu-id="214a5-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="214a5-134">*Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="214a5-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214a5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="214a5-135">See Also</span></span>  
 [<span data-ttu-id="214a5-136">Diretrizes de Design de tipo</span><span class="sxs-lookup"><span data-stu-id="214a5-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="214a5-137">Diretrizes de design do Framework</span><span class="sxs-lookup"><span data-stu-id="214a5-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
