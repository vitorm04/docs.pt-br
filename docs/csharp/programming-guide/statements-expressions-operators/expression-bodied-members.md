---
title: Membros aptos para expressão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: 45dcc58b252963e80798ba86ca5c4f461d493fac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120140"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="34356-102">Membros aptos para expressão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="34356-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="34356-103">As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível.</span><span class="sxs-lookup"><span data-stu-id="34356-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="34356-104">Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="34356-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="34356-105">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="34356-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="34356-106">em que *expression* é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="34356-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="34356-107">O suporte para definições de corpo da expressão foi introduzido para métodos e propriedades somente leitura no C# 6 e foi expandido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="34356-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="34356-108">As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="34356-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="34356-109">Membro</span><span class="sxs-lookup"><span data-stu-id="34356-109">Member</span></span>  |<span data-ttu-id="34356-110">Com suporte desde...</span><span class="sxs-lookup"><span data-stu-id="34356-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="34356-111">Método</span><span class="sxs-lookup"><span data-stu-id="34356-111">Method</span></span>](#methods)  |<span data-ttu-id="34356-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="34356-112">C# 6</span></span> |
|[<span data-ttu-id="34356-113">Propriedade somente leitura</span><span class="sxs-lookup"><span data-stu-id="34356-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="34356-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="34356-114">C# 6</span></span>  |
|[<span data-ttu-id="34356-115">Property</span><span class="sxs-lookup"><span data-stu-id="34356-115">Property</span></span>](#properties)  |<span data-ttu-id="34356-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="34356-116">C# 7.0</span></span> |
|[<span data-ttu-id="34356-117">Construtor</span><span class="sxs-lookup"><span data-stu-id="34356-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="34356-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="34356-118">C# 7.0</span></span> |
|[<span data-ttu-id="34356-119">Finalizador</span><span class="sxs-lookup"><span data-stu-id="34356-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="34356-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="34356-120">C# 7.0</span></span> |
|[<span data-ttu-id="34356-121">Indexador</span><span class="sxs-lookup"><span data-stu-id="34356-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="34356-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="34356-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="34356-123">Métodos</span><span class="sxs-lookup"><span data-stu-id="34356-123">Methods</span></span>

<span data-ttu-id="34356-124">Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação.</span><span class="sxs-lookup"><span data-stu-id="34356-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="34356-125">Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="34356-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="34356-126">O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="34356-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="34356-127">Ele também define um método `DisplayName` que exibe um nome para o console.</span><span class="sxs-lookup"><span data-stu-id="34356-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="34356-128">Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.</span><span class="sxs-lookup"><span data-stu-id="34356-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="34356-129">Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="34356-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="34356-130">Propriedades somente leitura</span><span class="sxs-lookup"><span data-stu-id="34356-130">Read-only properties</span></span>

<span data-ttu-id="34356-131">Começando no C# 6, você pode usar a definição de corpo da expressão para implementar uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="34356-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="34356-132">Para isso, use a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="34356-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="34356-133">O exemplo a seguir define uma classe `Location` cuja propriedade somente leitura `Name` é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular:</span><span class="sxs-lookup"><span data-stu-id="34356-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="34356-134">Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="34356-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="34356-135">Propriedades</span><span class="sxs-lookup"><span data-stu-id="34356-135">Properties</span></span>

<span data-ttu-id="34356-136">Começando no C# 7.0, você pode usar as definições de corpo da expressão para implementar a propriedade `get` e os acessadores `set`.</span><span class="sxs-lookup"><span data-stu-id="34356-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="34356-137">O exemplo a seguir demonstra como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="34356-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="34356-138">Para obter mais informações sobre as propriedades, confira [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="34356-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="34356-139">Construtores</span><span class="sxs-lookup"><span data-stu-id="34356-139">Constructors</span></span>

<span data-ttu-id="34356-140">Uma definição de corpo da expressão para um construtor normalmente consiste em uma expressão de atribuição simples ou uma chamada de método que manipula os argumentos do construtor ou inicializa o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="34356-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="34356-141">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="34356-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="34356-142">A definição de corpo da expressão atribui o argumento à propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="34356-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="34356-143">Para obter mais informações, consulte [Construtores (Guia de Programação em C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="34356-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="34356-144">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="34356-144">Finalizers</span></span>

<span data-ttu-id="34356-145">Uma definição de corpo da expressão para um finalizador normalmente contém instruções de limpeza, como instruções que liberam recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="34356-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="34356-146">O exemplo a seguir define um finalizador que usa uma definição de corpo da expressão para indicar que o finalizador foi chamado.</span><span class="sxs-lookup"><span data-stu-id="34356-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="34356-147">Para obter mais informações, consulte [Finalizadores (Guia de Programação em C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="34356-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="34356-148">Indexadores</span><span class="sxs-lookup"><span data-stu-id="34356-148">Indexers</span></span>

<span data-ttu-id="34356-149">Assim como as propriedades, o indexador `get` e os acessadores de `set` consistem em definições de corpo da expressão se o acessador `get` consiste em uma única expressão que retorna um valor ou o acessador `set` executa uma atribuição simples.</span><span class="sxs-lookup"><span data-stu-id="34356-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="34356-150">O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes.</span><span class="sxs-lookup"><span data-stu-id="34356-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="34356-151">Os acessadores `get` e `set` do indexador são implementados como definições do corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="34356-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="34356-152">Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="34356-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
