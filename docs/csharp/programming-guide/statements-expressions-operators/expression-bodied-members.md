---
title: Membros aptos para expressão – Guia de Programação em C#
description: Saiba mais sobre os membros do Expression-apto para. Consulte exemplos de código que usam a definição do corpo da expressão para propriedades, construtores, finalizadores e muito mais.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381652"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="230be-104">Membros aptos para expressão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="230be-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="230be-105">As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível.</span><span class="sxs-lookup"><span data-stu-id="230be-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="230be-106">Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="230be-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="230be-107">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="230be-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="230be-108">em que *expression* é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="230be-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="230be-109">O suporte para definições de corpo da expressão foi introduzido para métodos e propriedades somente leitura no C# 6 e foi expandido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="230be-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="230be-110">As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="230be-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="230be-111">Membro</span><span class="sxs-lookup"><span data-stu-id="230be-111">Member</span></span>  |<span data-ttu-id="230be-112">Com suporte desde...</span><span class="sxs-lookup"><span data-stu-id="230be-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="230be-113">Método</span><span class="sxs-lookup"><span data-stu-id="230be-113">Method</span></span>](#methods)  |<span data-ttu-id="230be-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="230be-114">C# 6</span></span> |
|[<span data-ttu-id="230be-115">Propriedade somente leitura</span><span class="sxs-lookup"><span data-stu-id="230be-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="230be-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="230be-116">C# 6</span></span>  |
|[<span data-ttu-id="230be-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="230be-117">Property</span></span>](#properties)  |<span data-ttu-id="230be-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="230be-118">C# 7.0</span></span> |
|[<span data-ttu-id="230be-119">Qu</span><span class="sxs-lookup"><span data-stu-id="230be-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="230be-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="230be-120">C# 7.0</span></span> |
|[<span data-ttu-id="230be-121">Finalizer</span><span class="sxs-lookup"><span data-stu-id="230be-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="230be-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="230be-122">C# 7.0</span></span> |
|[<span data-ttu-id="230be-123">Indexador</span><span class="sxs-lookup"><span data-stu-id="230be-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="230be-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="230be-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="230be-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="230be-125">Methods</span></span>

<span data-ttu-id="230be-126">Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação.</span><span class="sxs-lookup"><span data-stu-id="230be-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="230be-127">Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="230be-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="230be-128">O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="230be-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="230be-129">Ele também define um método `DisplayName` que exibe um nome para o console.</span><span class="sxs-lookup"><span data-stu-id="230be-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="230be-130">Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.</span><span class="sxs-lookup"><span data-stu-id="230be-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="230be-131">Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="230be-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="230be-132">Propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="230be-132">Read-only properties</span></span>

<span data-ttu-id="230be-133">Começando no C# 6, você pode usar a definição de corpo da expressão para implementar uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="230be-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="230be-134">Para isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="230be-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="230be-135">O exemplo a seguir define uma classe `Location` cuja propriedade somente leitura `Name` é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular:</span><span class="sxs-lookup"><span data-stu-id="230be-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="230be-136">Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="230be-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="230be-137">Propriedades</span><span class="sxs-lookup"><span data-stu-id="230be-137">Properties</span></span>

<span data-ttu-id="230be-138">Começando no C# 7.0, você pode usar as definições de corpo da expressão para implementar a propriedade `get` e os acessadores `set`.</span><span class="sxs-lookup"><span data-stu-id="230be-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="230be-139">O exemplo a seguir demonstra como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="230be-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="230be-140">Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="230be-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="230be-141">Construtores</span><span class="sxs-lookup"><span data-stu-id="230be-141">Constructors</span></span>

<span data-ttu-id="230be-142">Uma definição de corpo da expressão para um construtor normalmente consiste em uma expressão de atribuição simples ou uma chamada de método que manipula os argumentos do construtor ou inicializa o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="230be-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="230be-143">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="230be-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="230be-144">A definição de corpo da expressão atribui o argumento à propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="230be-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="230be-145">Para obter mais informações, consulte [Construtores (Guia de Programação em C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="230be-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="230be-146">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="230be-146">Finalizers</span></span>

<span data-ttu-id="230be-147">Uma definição de corpo da expressão para um finalizador normalmente contém instruções de limpeza, como instruções que liberam recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="230be-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="230be-148">O exemplo a seguir define um finalizador que usa uma definição de corpo da expressão para indicar que o finalizador foi chamado.</span><span class="sxs-lookup"><span data-stu-id="230be-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="230be-149">Para obter mais informações, consulte [Finalizadores (Guia de Programação em C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="230be-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="230be-150">Indexadores</span><span class="sxs-lookup"><span data-stu-id="230be-150">Indexers</span></span>

<span data-ttu-id="230be-151">Assim como as propriedades, o indexador `get` e os `set` acessadores consistem em definições de corpo de expressão se o `get` acessador consiste em uma única expressão que retorna um valor ou o `set` acessador executa uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="230be-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="230be-152">O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes.</span><span class="sxs-lookup"><span data-stu-id="230be-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="230be-153">O indexador `get` e os `set` acessadores são implementados como definições de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="230be-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="230be-154">Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="230be-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
