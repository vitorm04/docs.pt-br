---
description: Modificador override – Referência de C#
title: Modificador override – Referência de C#
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434877"
---
# <a name="override-c-reference"></a><span data-ttu-id="d74e1-103">Override (referência C#)</span><span class="sxs-lookup"><span data-stu-id="d74e1-103">override (C# reference)</span></span>

<span data-ttu-id="d74e1-104">O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.</span><span class="sxs-lookup"><span data-stu-id="d74e1-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

<span data-ttu-id="d74e1-105">No exemplo a seguir, a `Square` classe deve fornecer uma implementação substituída de `GetArea` porque `GetArea` é herdada da `Shape` classe abstrata:</span><span class="sxs-lookup"><span data-stu-id="d74e1-105">In the following example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="d74e1-106">Um `override` método fornece uma nova implementação do método herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="d74e1-106">An `override` method provides a new implementation of the method inherited from a base class.</span></span> <span data-ttu-id="d74e1-107">O método que é substituído por uma declaração `override` é conhecido como o método base substituído.</span><span class="sxs-lookup"><span data-stu-id="d74e1-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="d74e1-108">Um `override` método deve ter a mesma assinatura que o método base substituído.</span><span class="sxs-lookup"><span data-stu-id="d74e1-108">An `override` method must have the same signature as the overridden base method.</span></span> <span data-ttu-id="d74e1-109">A partir do C# 9,0, os `override` métodos dão suporte a tipos de retorno covariantes.</span><span class="sxs-lookup"><span data-stu-id="d74e1-109">Beginning with C# 9.0, `override` methods support covariant return types.</span></span> <span data-ttu-id="d74e1-110">Em particular, o tipo de retorno de um `override` método pode derivar do tipo de retorno do método base correspondente.</span><span class="sxs-lookup"><span data-stu-id="d74e1-110">In particular, the return type of an `override` method can derive from the return type of the corresponding base method.</span></span> <span data-ttu-id="d74e1-111">No C# 8,0 e anteriores, os tipos de retorno de um `override` método e o método base substituído devem ser iguais.</span><span class="sxs-lookup"><span data-stu-id="d74e1-111">In C# 8.0 and earlier, the return types of an `override` method and the overridden base method must be the same.</span></span>

<span data-ttu-id="d74e1-112">Você não pode substituir um método não virtual ou estático.</span><span class="sxs-lookup"><span data-stu-id="d74e1-112">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="d74e1-113">O método base substituído deve ser `virtual`, `abstract` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="d74e1-113">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="d74e1-114">Uma declaração `override` não pode alterar a acessibilidade do método `virtual`.</span><span class="sxs-lookup"><span data-stu-id="d74e1-114">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="d74e1-115">O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="d74e1-115">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="d74e1-116">Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.</span><span class="sxs-lookup"><span data-stu-id="d74e1-116">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="d74e1-117">Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada.</span><span class="sxs-lookup"><span data-stu-id="d74e1-117">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property.</span></span> <span data-ttu-id="d74e1-118">A partir do C# 9,0, as propriedades de substituição somente leitura dão suporte a tipos de retorno covariantes.</span><span class="sxs-lookup"><span data-stu-id="d74e1-118">Beginning with C# 9.0, read-only overriding properties support covariant return types.</span></span> <span data-ttu-id="d74e1-119">A propriedade substituída deve ser `virtual` , `abstract` ou `override` .</span><span class="sxs-lookup"><span data-stu-id="d74e1-119">The overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="d74e1-120">Para obter mais informações sobre como usar a `override` palavra-chave, consulte [controle de versão com a substituição e novas palavras-chave](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [saber quando usar substituições e novas palavras-chave](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="d74e1-120">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span> <span data-ttu-id="d74e1-121">Para obter informações sobre herança, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="d74e1-121">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

## <a name="example"></a><span data-ttu-id="d74e1-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d74e1-122">Example</span></span>

<span data-ttu-id="d74e1-123">Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="d74e1-123">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="d74e1-124">A classe `SalesEmployee` inclui um campo extra, `salesbonus`, e substitui o método `CalculatePay` para levar isso em consideração.</span><span class="sxs-lookup"><span data-stu-id="d74e1-124">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="d74e1-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d74e1-125">C# language specification</span></span>

<span data-ttu-id="d74e1-126">Para obter mais informações, consulte a seção [métodos de substituição](~/_csharplang/spec/classes.md#override-methods) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d74e1-126">For more information, see the [Override methods](~/_csharplang/spec/classes.md#override-methods) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="d74e1-127">Para obter mais informações sobre tipos de retorno covariantes, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span><span class="sxs-lookup"><span data-stu-id="d74e1-127">For more information about covariant return types, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d74e1-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="d74e1-128">See also</span></span>

- [<span data-ttu-id="d74e1-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d74e1-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d74e1-130">Herança</span><span class="sxs-lookup"><span data-stu-id="d74e1-130">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="d74e1-131">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d74e1-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="d74e1-132">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d74e1-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d74e1-133">resume</span><span class="sxs-lookup"><span data-stu-id="d74e1-133">abstract</span></span>](abstract.md)
- [<span data-ttu-id="d74e1-134">virtual</span><span class="sxs-lookup"><span data-stu-id="d74e1-134">virtual</span></span>](virtual.md)
- [<span data-ttu-id="d74e1-135">novo (modificador)</span><span class="sxs-lookup"><span data-stu-id="d74e1-135">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="d74e1-136">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="d74e1-136">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
