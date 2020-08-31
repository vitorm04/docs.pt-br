---
description: operador new – Referência em C#
title: operador new – Referência em C#
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 88ec929317d4e6c6651233c1a1aa0ce8a8cce611
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118267"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="1c10e-103">operador new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="1c10e-103">new operator (C# reference)</span></span>

<span data-ttu-id="1c10e-104">O operador `new` cria uma nova instância de um tipo.</span><span class="sxs-lookup"><span data-stu-id="1c10e-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="1c10e-105">Você também pode usar a palavra-chave `new` como um [modificador de declaração de membro](../keywords/new-modifier.md) ou uma [restrição de tipo genérico](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="1c10e-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="1c10e-106">Chamada de construtor</span><span class="sxs-lookup"><span data-stu-id="1c10e-106">Constructor invocation</span></span>

<span data-ttu-id="1c10e-107">Para criar uma nova instância de um tipo, você normalmente invoca um dos [construtores](../../programming-guide/classes-and-structs/constructors.md) desse tipo usando o operador `new`:</span><span class="sxs-lookup"><span data-stu-id="1c10e-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="1c10e-108">Você pode usar um [inicializador de objeto ou coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) com o operador `new` para instanciar e inicializar um objeto em uma instrução, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1c10e-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="1c10e-109">Criação de matriz</span><span class="sxs-lookup"><span data-stu-id="1c10e-109">Array creation</span></span>

<span data-ttu-id="1c10e-110">Você também usar o operador `new` para criar uma instância de matriz, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1c10e-110">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="1c10e-111">Use a sintaxe de inicialização de matriz para criar uma instância de matriz e preenchê-la com os elementos em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="1c10e-111">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="1c10e-112">O exemplo a seguir mostra várias maneiras de como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="1c10e-112">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="1c10e-113">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="1c10e-113">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="1c10e-114">Instanciação de tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="1c10e-114">Instantiation of anonymous types</span></span>

<span data-ttu-id="1c10e-115">Para criar uma instância de um [tipo anônimo](../../programming-guide/classes-and-structs/anonymous-types.md), use o operador `new` e a sintaxe do inicializador de objeto:</span><span class="sxs-lookup"><span data-stu-id="1c10e-115">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="1c10e-116">Destruição de instâncias do tipo</span><span class="sxs-lookup"><span data-stu-id="1c10e-116">Destruction of type instances</span></span>

<span data-ttu-id="1c10e-117">Você não precisa destruir as instâncias do tipo criadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1c10e-117">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="1c10e-118">As instâncias dos tipos de referência e de valor são destruídas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1c10e-118">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="1c10e-119">As instâncias dos tipos de valor serão destruídas assim que o contexto que as contém for destruído.</span><span class="sxs-lookup"><span data-stu-id="1c10e-119">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="1c10e-120">Instâncias de tipos de referência são destruídas pelo [coletor de lixo](../../../standard/garbage-collection/index.md) em algum momento não especificado depois que a última referência a eles é removida.</span><span class="sxs-lookup"><span data-stu-id="1c10e-120">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="1c10e-121">Para instâncias de tipo que contêm recursos não gerenciados, por exemplo, um identificador de arquivo, é recomendável empregar uma limpeza determinística para garantir que os recursos que eles contêm sejam liberados assim que possível.</span><span class="sxs-lookup"><span data-stu-id="1c10e-121">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="1c10e-122">Para obter mais informações, veja o artigo <xref:System.IDisposable?displayProperty=nameWithType> Referência da API e a [instrução de uso](../keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1c10e-122">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1c10e-123">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="1c10e-123">Operator overloadability</span></span>

<span data-ttu-id="1c10e-124">Um tipo definido pelo usuário não pode sobrecarregar o operador `new`.</span><span class="sxs-lookup"><span data-stu-id="1c10e-124">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c10e-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1c10e-125">C# language specification</span></span>

<span data-ttu-id="1c10e-126">Para saber mais, confira a seção [O operador new](~/_csharplang/spec/expressions.md#the-new-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1c10e-126">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c10e-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="1c10e-127">See also</span></span>

- [<span data-ttu-id="1c10e-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1c10e-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1c10e-129">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="1c10e-129">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="1c10e-130">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="1c10e-130">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
