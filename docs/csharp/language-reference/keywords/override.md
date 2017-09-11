---
title: "override (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
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
ms.openlocfilehash: 0f5a87eaa5894b61187c379c92ad785336aa79b2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="override-c-reference"></a><span data-ttu-id="c0945-102">override (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="c0945-102">override (C# Reference)</span></span>
<span data-ttu-id="c0945-103">O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.</span><span class="sxs-lookup"><span data-stu-id="c0945-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0945-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0945-104">Example</span></span>  
 <span data-ttu-id="c0945-105">Neste exemplo, a classe `Square` deve fornecer uma implementação substituída de `Area` porque `Area` é herdado do `ShapesClass` abstrato:</span><span class="sxs-lookup"><span data-stu-id="c0945-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>  
  
 <span data-ttu-id="c0945-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c0945-106">[!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]</span></span>  
  
 <span data-ttu-id="c0945-107">Um método `override` fornece uma nova implementação de um membro herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="c0945-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="c0945-108">O método que é substituído por uma declaração `override` é conhecido como o método base substituído.</span><span class="sxs-lookup"><span data-stu-id="c0945-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="c0945-109">O método base substituído deve ter a mesma assinatura que o método `override`.</span><span class="sxs-lookup"><span data-stu-id="c0945-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="c0945-110">Para obter informações sobre herança, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="c0945-110">For information about inheritance, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="c0945-111">Você não pode substituir um método não virtual ou estático.</span><span class="sxs-lookup"><span data-stu-id="c0945-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="c0945-112">O método base substituído deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="c0945-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="c0945-113">Uma declaração `override` não pode alterar a acessibilidade do método `virtual`.</span><span class="sxs-lookup"><span data-stu-id="c0945-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="c0945-114">O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c0945-114">Both the `override` method and the `virtual` method must have the same [access level modifier](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="c0945-115">Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.</span><span class="sxs-lookup"><span data-stu-id="c0945-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>  
  
 <span data-ttu-id="c0945-116">Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada e a propriedade substituída deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="c0945-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>  
  
 <span data-ttu-id="c0945-117">Para obter mais informações sobre como usar a palavra-chave `override`, consulte [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="c0945-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0945-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0945-118">Example</span></span>  
 <span data-ttu-id="c0945-119">Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="c0945-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="c0945-120">A classe `SalesEmployee` inclui uma propriedade extra, `salesbonus` e substitui o método `CalculatePay` para levar isso em consideração.</span><span class="sxs-lookup"><span data-stu-id="c0945-120">The `SalesEmployee` class includes an extra property, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>  
  
 <span data-ttu-id="c0945-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c0945-121">[!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c0945-122">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c0945-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0945-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0945-123">See Also</span></span>  
 <span data-ttu-id="c0945-124">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c0945-125">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c0945-126">[Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-126">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="c0945-127">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c0945-128">[Modificadores](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-128">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="c0945-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-129">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="c0945-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-130">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 <span data-ttu-id="c0945-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="c0945-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="c0945-132">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="c0945-132">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)

