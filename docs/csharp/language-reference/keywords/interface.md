---
title: "interface (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: interface_CSharpKeyword
helpviewer_keywords: interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a><span data-ttu-id="74a24-102">interface (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="74a24-102">interface (C# Reference)</span></span>
<span data-ttu-id="74a24-103">Uma interface contém apenas as assinaturas de [métodos](../../../csharp/programming-guide/classes-and-structs/methods.md), [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [eventos](../../../csharp/programming-guide/events/index.md) ou [indexadores](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="74a24-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="74a24-104">Uma classe ou struct que implementa a interface deve implementar os membros da interface que estão especificados na definição de interface.</span><span class="sxs-lookup"><span data-stu-id="74a24-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="74a24-105">No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.</span><span class="sxs-lookup"><span data-stu-id="74a24-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="74a24-106">Para obter mais informações e exemplos, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="74a24-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74a24-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74a24-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="74a24-108">Uma interface pode ser um membro de um namespace ou de uma classe e pode conter assinaturas dos seguintes membros:</span><span class="sxs-lookup"><span data-stu-id="74a24-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="74a24-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="74a24-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="74a24-110">Propriedades</span><span class="sxs-lookup"><span data-stu-id="74a24-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="74a24-111">Indexadores</span><span class="sxs-lookup"><span data-stu-id="74a24-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="74a24-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="74a24-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="74a24-113">Uma interface pode herdar de uma ou mais interfaces base.</span><span class="sxs-lookup"><span data-stu-id="74a24-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="74a24-114">Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.</span><span class="sxs-lookup"><span data-stu-id="74a24-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="74a24-115">Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente.</span><span class="sxs-lookup"><span data-stu-id="74a24-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="74a24-116">Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface.</span><span class="sxs-lookup"><span data-stu-id="74a24-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="74a24-117">Para obter mais detalhes e exemplos de código sobre a implementação explícita da interface, consulte [Implementação explícita da interface](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="74a24-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74a24-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74a24-118">Example</span></span>  
 <span data-ttu-id="74a24-119">O exemplo a seguir demonstra a implementação da interface.</span><span class="sxs-lookup"><span data-stu-id="74a24-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="74a24-120">Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação.</span><span class="sxs-lookup"><span data-stu-id="74a24-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="74a24-121">Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="74a24-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="74a24-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="74a24-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="74a24-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a24-123">See Also</span></span>  
 [<span data-ttu-id="74a24-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="74a24-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="74a24-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="74a24-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="74a24-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="74a24-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="74a24-127">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="74a24-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="74a24-128">Interfaces</span><span class="sxs-lookup"><span data-stu-id="74a24-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="74a24-129">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="74a24-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="74a24-130">Usando indexadores</span><span class="sxs-lookup"><span data-stu-id="74a24-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="74a24-131">class</span><span class="sxs-lookup"><span data-stu-id="74a24-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="74a24-132">struct</span><span class="sxs-lookup"><span data-stu-id="74a24-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="74a24-133">Interfaces</span><span class="sxs-lookup"><span data-stu-id="74a24-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
