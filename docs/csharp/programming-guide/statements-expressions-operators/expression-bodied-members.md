---
title: Membros aptos para expressão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f71352dca584c107af4f45850ce21bb016ba01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238111"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="c1cb2-102">Membros aptos para expressão (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c1cb2-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="c1cb2-103">As definições de corpo da expressão permitem que você forneça uma implementação de um membro em uma forma bastante concisa e legível.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="c1cb2-104">Você pode usar uma definição de corpo da expressão sempre que a lógica para qualquer membro com suporte, como um método ou propriedade, consiste em uma única expressão.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="c1cb2-105">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="c1cb2-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="c1cb2-106">em que *expression* é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="c1cb2-107">O suporte para definições no corpo da expressão foi introduzido para acessadores get de propriedade e de métodos no C# 6 e foi expandido no C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="c1cb2-108">As definições de corpo da expressão podem ser usadas com os membros de tipo listados na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="c1cb2-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="c1cb2-109">Membro</span><span class="sxs-lookup"><span data-stu-id="c1cb2-109">Member</span></span>  |<span data-ttu-id="c1cb2-110">Com suporte desde...</span><span class="sxs-lookup"><span data-stu-id="c1cb2-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="c1cb2-111">Método</span><span class="sxs-lookup"><span data-stu-id="c1cb2-111">Method</span></span>](#methods)  |<span data-ttu-id="c1cb2-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="c1cb2-112">C# 6</span></span> |
|[<span data-ttu-id="c1cb2-113">Construtor</span><span class="sxs-lookup"><span data-stu-id="c1cb2-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="c1cb2-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c1cb2-114">C# 7.0</span></span> |
|[<span data-ttu-id="c1cb2-115">Finalizador</span><span class="sxs-lookup"><span data-stu-id="c1cb2-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="c1cb2-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c1cb2-116">C# 7.0</span></span> |
|[<span data-ttu-id="c1cb2-117">Get da propriedade</span><span class="sxs-lookup"><span data-stu-id="c1cb2-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="c1cb2-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="c1cb2-118">C# 6</span></span> |
|[<span data-ttu-id="c1cb2-119">Set da propriedade</span><span class="sxs-lookup"><span data-stu-id="c1cb2-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="c1cb2-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c1cb2-120">C# 7.0</span></span> |
|[<span data-ttu-id="c1cb2-121">Indexador</span><span class="sxs-lookup"><span data-stu-id="c1cb2-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="c1cb2-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="c1cb2-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="c1cb2-123">Métodos</span><span class="sxs-lookup"><span data-stu-id="c1cb2-123">Methods</span></span>

<span data-ttu-id="c1cb2-124">Um método apto para expressão consiste em uma única expressão que retorna um valor cujo tipo corresponde ao tipo de retorno do método, ou, para métodos que retornam `void`, que executam uma operação.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="c1cb2-125">Por exemplo, os tipos que substituem o método <xref:System.Object.ToString%2A> normalmente incluem uma única expressão que retorna a representação da cadeia de caracteres do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="c1cb2-126">O exemplo a seguir define uma classe `Person` que substitui o método <xref:System.Object.ToString%2A> por uma definição de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="c1cb2-127">Ele também define um método `DisplayName` que exibe um nome para o console.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="c1cb2-128">Observe que a palavra-chave `return` não é usada na definição de corpo da expressão `ToString`.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="c1cb2-129">Para obter mais informações, consulte [Métodos (Guia de Programação em C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="c1cb2-130">Construtores</span><span class="sxs-lookup"><span data-stu-id="c1cb2-130">Constructors</span></span>

<span data-ttu-id="c1cb2-131">Uma definição de corpo da expressão para um construtor normalmente consiste em uma expressão de atribuição simples ou uma chamada de método que manipula os argumentos do construtor ou inicializa o estado da instância.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="c1cb2-132">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="c1cb2-133">A definição de corpo da expressão atribui o argumento à propriedade `Name`.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="c1cb2-134">Para obter mais informações, consulte [Construtores (Guia de Programação em C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="c1cb2-135">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="c1cb2-135">Finalizers</span></span>

<span data-ttu-id="c1cb2-136">Uma definição de corpo da expressão para um finalizador normalmente contém instruções de limpeza, como instruções que liberam recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="c1cb2-137">O exemplo a seguir define um finalizador que usa uma definição de corpo da expressão para indicar que o finalizador foi chamado.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="c1cb2-138">Para obter mais informações, consulte [Finalizadores (Guia de Programação em C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="c1cb2-139">Instruções get da propriedade</span><span class="sxs-lookup"><span data-stu-id="c1cb2-139">Property get statements</span></span>

<span data-ttu-id="c1cb2-140">Se você optar por implementar um acessador get da propriedade por conta própria, poderá usar uma definição de corpo da expressão para expressões únicas que retornam simplesmente o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="c1cb2-141">Observe que a instrução `return` não é usada.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="c1cb2-142">O exemplo a seguir define uma propriedade `Location.Name` cujo acessador get da propriedade retorna o valor do campo `locationName` particular que sustenta a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="c1cb2-143">As propriedades somente leitura que usam uma definição de corpo da expressão podem ser implementadas sem uma instrução `set` explícita.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="c1cb2-144">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="c1cb2-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="c1cb2-145">O exemplo a seguir define uma classe `Location` cuja propriedade `Name` somente leitura é implementada como uma definição de corpo da expressão que retorna o valor do campo `locationName` particular.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="c1cb2-146">Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="c1cb2-147">Instruções set da propriedade</span><span class="sxs-lookup"><span data-stu-id="c1cb2-147">Property set statements</span></span>

<span data-ttu-id="c1cb2-148">Se você optar por implementar um acessador set da propriedade por conta própria, poderá usar uma definição de corpo da expressão para uma expressão de linha única que atribui um valor ao campo que sustenta a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="c1cb2-149">O exemplo a seguir define uma propriedade `Location.Name` cujo acessador set da propriedade designa seu argumento de entrada ao campo `locationName` particular que sustenta a propriedade.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="c1cb2-150">Para obter mais informações, consulte [Propriedades (Guia de Programação em C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="c1cb2-151">Indexadores</span><span class="sxs-lookup"><span data-stu-id="c1cb2-151">Indexers</span></span>

<span data-ttu-id="c1cb2-152">Como as propriedades, os acessadores get e set do indexador consistirão em definições de corpo da expressão se o acessador get consistir em uma única instrução que retorna um valor ou o acessador set executar uma designação simples.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="c1cb2-153">O exemplo a seguir define uma classe chamada `Sports` que inclui uma matriz <xref:System.String> interna que contém os nomes de vários esportes.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="c1cb2-154">Os acessadores get e set do indexador são implementados como definições de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="c1cb2-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="c1cb2-155">Para obter mais informações, consulte [Indexadores (Guia de Programação em C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c1cb2-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

