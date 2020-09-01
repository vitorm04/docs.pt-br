---
description: Modificador new – Referência em C#
title: Modificador new – Referência em C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 2da0a360868250169fb16380c80bf32c4b335d7a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139405"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="1881b-103">Modificador new (referência em C#)</span><span class="sxs-lookup"><span data-stu-id="1881b-103">new modifier (C# Reference)</span></span>

<span data-ttu-id="1881b-104">Quando usada como um modificador de declaração, a palavra-chave `new` oculta explicitamente um membro herdado de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="1881b-104">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="1881b-105">Quando você oculta um membro herdado, a versão derivada do membro substitui a versão da classe base.</span><span class="sxs-lookup"><span data-stu-id="1881b-105">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="1881b-106">Embora possa ocultar membros sem usar o modificador `new`, você obtém um aviso do compilador.</span><span class="sxs-lookup"><span data-stu-id="1881b-106">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="1881b-107">Se você usar `new` para ocultar explicitamente um membro, ele suprime o aviso.</span><span class="sxs-lookup"><span data-stu-id="1881b-107">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="1881b-108">Você também pode usar a palavra-chave `new` para [criar uma instância de um tipo](../operators/new-operator.md) ou como uma [restrição de tipo genérico](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="1881b-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="1881b-109">Para ocultar um membro herdado, declare-o na classe derivada usando o mesmo nome de membro e modifique-o com a palavra-chave `new`.</span><span class="sxs-lookup"><span data-stu-id="1881b-109">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="1881b-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1881b-110">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="1881b-111">Neste exemplo, `BaseC.Invoke` é ocultado por `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="1881b-111">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="1881b-112">O campo `x` não é afetado porque não é ocultado por um nome semelhante.</span><span class="sxs-lookup"><span data-stu-id="1881b-112">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="1881b-113">A ocultação de nome por meio da herança assume uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="1881b-113">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="1881b-114">Normalmente, uma constante, campo, propriedade ou tipo que é apresentado em uma classe ou struct oculta todos os membros da classe base que compartilham seu nome.</span><span class="sxs-lookup"><span data-stu-id="1881b-114">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="1881b-115">Há casos especiais.</span><span class="sxs-lookup"><span data-stu-id="1881b-115">There are special cases.</span></span> <span data-ttu-id="1881b-116">Por exemplo, se você declarar que um novo campo com o nome `N` tem um tipo que não pode ser invocado e um tipo base declarar que `N` é um método, o novo campo não ocultará a declaração base na sintaxe de invocação.</span><span class="sxs-lookup"><span data-stu-id="1881b-116">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="1881b-117">Para obter mais informações, consulte a seção [Pesquisa de membro](~/_csharplang/spec/expressions.md#member-lookup) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1881b-117">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="1881b-118">Um método introduzido em uma classe ou struct oculta propriedades, campos e tipos que compartilham esse nome na classe base.</span><span class="sxs-lookup"><span data-stu-id="1881b-118">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="1881b-119">Ele também oculta todos os métodos da classe base que têm a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="1881b-119">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="1881b-120">Um indexador introduzido em uma classe ou struct oculta todos os indexadores de classe base que têm a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="1881b-120">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="1881b-121">É um erro usar `new` e [override](override.md) no mesmo membro, porque os dois modificadores têm significados mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="1881b-121">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="1881b-122">O modificador `new` cria um novo membro com o mesmo nome e faz com que o membro original seja ocultado.</span><span class="sxs-lookup"><span data-stu-id="1881b-122">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="1881b-123">O modificador `override` estende a implementação de um membro herdado.</span><span class="sxs-lookup"><span data-stu-id="1881b-123">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="1881b-124">Usar o modificador `new` em uma declaração que não oculta um membro herdado gera um aviso.</span><span class="sxs-lookup"><span data-stu-id="1881b-124">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="1881b-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1881b-125">Example</span></span>

<span data-ttu-id="1881b-126">Neste exemplo, uma classe base, `BaseC` e uma classe derivada, `DerivedC`, usam o mesmo nome do campo `x`, que oculta o valor do campo herdado.</span><span class="sxs-lookup"><span data-stu-id="1881b-126">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="1881b-127">O exemplo demonstra o uso do modificador `new`.</span><span class="sxs-lookup"><span data-stu-id="1881b-127">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="1881b-128">Ele também demonstra como acessar os membros ocultos da classe base usando seus nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="1881b-128">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="1881b-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1881b-129">Example</span></span>

<span data-ttu-id="1881b-130">Neste exemplo, uma classe aninhada oculta uma classe que tem o mesmo nome na classe base.</span><span class="sxs-lookup"><span data-stu-id="1881b-130">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="1881b-131">O exemplo demonstra como usar o modificador `new` para eliminar a mensagem de aviso e como acessar os membros da classe oculta usando seus nomes totalmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="1881b-131">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="1881b-132">Se você remover o modificador `new`, o programa ainda será compilado e executado, mas você receberá o seguinte aviso:</span><span class="sxs-lookup"><span data-stu-id="1881b-132">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="1881b-133">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1881b-133">C# language specification</span></span>

<span data-ttu-id="1881b-134">Para obter mais informações, consulte a seção [O modificador new](~/_csharplang/spec/classes.md#the-new-modifier) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1881b-134">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1881b-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="1881b-135">See also</span></span>

- [<span data-ttu-id="1881b-136">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="1881b-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1881b-137">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="1881b-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1881b-138">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1881b-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1881b-139">Modificadores</span><span class="sxs-lookup"><span data-stu-id="1881b-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1881b-140">Controle de versão com as palavras-chave override e new</span><span class="sxs-lookup"><span data-stu-id="1881b-140">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="1881b-141">Quando usar as palavras-chave override e new</span><span class="sxs-lookup"><span data-stu-id="1881b-141">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
