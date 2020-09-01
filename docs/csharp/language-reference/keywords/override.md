---
description: Modificador override – Referência de C#
title: Modificador override – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134452"
---
# <a name="override-c-reference"></a><span data-ttu-id="1ebdc-103">override (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1ebdc-103">override (C# Reference)</span></span>

<span data-ttu-id="1ebdc-104">O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="1ebdc-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ebdc-105">Example</span></span>

<span data-ttu-id="1ebdc-106">Neste exemplo, a `Square` classe deve fornecer uma implementação substituída de `GetArea` porque `GetArea` é herdada da `Shape` classe abstrata:</span><span class="sxs-lookup"><span data-stu-id="1ebdc-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="1ebdc-107">Um método `override` fornece uma nova implementação de um membro herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="1ebdc-108">O método que é substituído por uma declaração `override` é conhecido como o método base substituído.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="1ebdc-109">O método base substituído deve ter a mesma assinatura que o método `override`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="1ebdc-110">Para obter informações sobre herança, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="1ebdc-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="1ebdc-111">Você não pode substituir um método não virtual ou estático.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="1ebdc-112">O método base substituído deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1ebdc-113">Uma declaração `override` não pode alterar a acessibilidade do método `virtual`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="1ebdc-114">O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="1ebdc-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="1ebdc-115">Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="1ebdc-116">Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada e a propriedade substituída deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1ebdc-117">Para obter mais informações sobre como usar a `override` palavra-chave, consulte [controle de versão com a substituição e novas palavras-chave](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [saber quando usar substituições e novas palavras-chave](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="1ebdc-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ebdc-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ebdc-118">Example</span></span>

<span data-ttu-id="1ebdc-119">Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="1ebdc-120">A classe `SalesEmployee` inclui um campo extra, `salesbonus`, e substitui o método `CalculatePay` para levar isso em consideração.</span><span class="sxs-lookup"><span data-stu-id="1ebdc-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="1ebdc-121">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1ebdc-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1ebdc-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ebdc-122">See also</span></span>

- [<span data-ttu-id="1ebdc-123">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="1ebdc-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1ebdc-124">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1ebdc-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1ebdc-125">Herança</span><span class="sxs-lookup"><span data-stu-id="1ebdc-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="1ebdc-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1ebdc-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1ebdc-127">Modificadores</span><span class="sxs-lookup"><span data-stu-id="1ebdc-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1ebdc-128">abstract</span><span class="sxs-lookup"><span data-stu-id="1ebdc-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="1ebdc-129">virtual</span><span class="sxs-lookup"><span data-stu-id="1ebdc-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="1ebdc-130">novo (modificador)</span><span class="sxs-lookup"><span data-stu-id="1ebdc-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="1ebdc-131">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="1ebdc-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
