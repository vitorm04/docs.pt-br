---
title: operador new – Referência em C#
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 42128cf23fe2410bf33bb40131843325939646de
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916762"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="0ba78-102">operador new (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="0ba78-102">new operator (C# reference)</span></span>

<span data-ttu-id="0ba78-103">O operador `new` cria uma nova instância de um tipo.</span><span class="sxs-lookup"><span data-stu-id="0ba78-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="0ba78-104">Você também pode usar a palavra-chave `new` como um [modificador de declaração de membro](../keywords/new-modifier.md) ou uma [restrição de tipo genérico](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="0ba78-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="0ba78-105">Chamada de construtor</span><span class="sxs-lookup"><span data-stu-id="0ba78-105">Constructor invocation</span></span>

<span data-ttu-id="0ba78-106">Para criar uma nova instância de um tipo, você normalmente invoca um dos [construtores](../../programming-guide/classes-and-structs/constructors.md) desse tipo usando o operador `new`:</span><span class="sxs-lookup"><span data-stu-id="0ba78-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="0ba78-107">Você pode usar um [inicializador de objeto ou coleção](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) com o operador `new` para instanciar e inicializar um objeto em uma instrução, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0ba78-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="0ba78-108">Criação de matriz</span><span class="sxs-lookup"><span data-stu-id="0ba78-108">Array creation</span></span>

<span data-ttu-id="0ba78-109">Você também usar o operador `new` para criar uma instância de matriz, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0ba78-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="0ba78-110">Use a sintaxe de inicialização de matriz para criar uma instância de matriz e preenchê-la com os elementos em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="0ba78-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="0ba78-111">O exemplo a seguir mostra várias maneiras de como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="0ba78-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="0ba78-112">Para obter mais informações sobre matrizes, confira [Matrizes](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ba78-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="0ba78-113">Instanciação de tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="0ba78-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="0ba78-114">Para criar uma instância de um [tipo anônimo](../../programming-guide/classes-and-structs/anonymous-types.md), use o operador `new` e a sintaxe do inicializador de objeto:</span><span class="sxs-lookup"><span data-stu-id="0ba78-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="0ba78-115">Destruição de instâncias do tipo</span><span class="sxs-lookup"><span data-stu-id="0ba78-115">Destruction of type instances</span></span>

<span data-ttu-id="0ba78-116">Você não precisa destruir as instâncias do tipo criadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0ba78-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="0ba78-117">As instâncias dos tipos de referência e de valor são destruídas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0ba78-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="0ba78-118">As instâncias dos tipos de valor serão destruídas assim que o contexto que as contém for destruído.</span><span class="sxs-lookup"><span data-stu-id="0ba78-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="0ba78-119">Instâncias de tipos de referência são destruídas pelo [coletor de lixo](../../../standard/garbage-collection/index.md) em algum momento não especificado depois que a última referência a eles é removida.</span><span class="sxs-lookup"><span data-stu-id="0ba78-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="0ba78-120">Para instâncias de tipo que contêm recursos não gerenciados, por exemplo, um identificador de arquivo, é recomendável empregar uma limpeza determinística para garantir que os recursos que eles contêm sejam liberados assim que possível.</span><span class="sxs-lookup"><span data-stu-id="0ba78-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="0ba78-121">Para obter mais informações, veja o artigo <xref:System.IDisposable?displayProperty=nameWithType> Referência da API e a [instrução de uso](../keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0ba78-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0ba78-122">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="0ba78-122">Operator overloadability</span></span>

<span data-ttu-id="0ba78-123">Um tipo definido pelo usuário não pode sobrecarregar o operador `new`.</span><span class="sxs-lookup"><span data-stu-id="0ba78-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0ba78-124">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0ba78-124">C# language specification</span></span>

<span data-ttu-id="0ba78-125">Para saber mais, confira a seção [O operador new](~/_csharplang/spec/expressions.md#the-new-operator) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0ba78-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ba78-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ba78-126">See also</span></span>

- [<span data-ttu-id="0ba78-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0ba78-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0ba78-128">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="0ba78-128">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="0ba78-129">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="0ba78-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
