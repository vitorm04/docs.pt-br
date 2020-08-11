---
title: Operador => – referência do C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 30e1a3546f83a0a1ba5b1363238878868e94ab93
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063127"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="df896-102">Operador => (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="df896-102">=> operator (C# reference)</span></span>

<span data-ttu-id="df896-103">O `=>` token tem suporte em duas formas: como o [operador lambda](#lambda-operator) e como um separador de um nome de membro e a implementação de membro em uma [definição de corpo de expressão](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="df896-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="df896-104">Operador lambda</span><span class="sxs-lookup"><span data-stu-id="df896-104">Lambda operator</span></span>

<span data-ttu-id="df896-105">Em [expressões lambda](lambda-expressions.md), o operador lambda `=>` separa os parâmetros de entrada no lado esquerdo do corpo lambda no lado direito.</span><span class="sxs-lookup"><span data-stu-id="df896-105">In [lambda expressions](lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="df896-106">O seguinte exemplo usa o recurso [LINQ](../../programming-guide/concepts/linq/index.md) com a sintaxe de método para demonstrar o uso de expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="df896-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="df896-107">Os parâmetros de entrada de uma expressão lambda são fortemente tipados no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="df896-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="df896-108">Quando o compilador pode inferir os tipos de parâmetros de entrada, como no exemplo anterior, você pode omitir declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="df896-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="df896-109">Se você precisar especificar o tipo de parâmetros de entrada, deverá fazer isso para cada parâmetro, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="df896-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="df896-110">O exemplo a seguir mostra como definir uma expressão lambda sem parâmetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="df896-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="df896-111">Para obter mais informações, consulte [expressões lambda](lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="df896-111">For more information, see [Lambda expressions](lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="df896-112">Definição de corpo da expressão</span><span class="sxs-lookup"><span data-stu-id="df896-112">Expression body definition</span></span>

<span data-ttu-id="df896-113">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="df896-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="df896-114">em que `expression` é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="df896-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="df896-115">O tipo de retorno de `expression` deve ser implicitamente conversível para o tipo de retorno do membro.</span><span class="sxs-lookup"><span data-stu-id="df896-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="df896-116">Se o tipo de retorno do membro for `void` ou se o membro for um construtor, um finalizador ou um acessador de propriedade ou indexador `set` , `expression` deverá ser uma [*expressão de instrução*](~/_csharplang/spec/statements.md#expression-statements).</span><span class="sxs-lookup"><span data-stu-id="df896-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="df896-117">Como o resultado da expressão é Descartado, o tipo de retorno dessa expressão pode ser qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="df896-117">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="df896-118">O seguinte exemplo mostra uma definição de corpo da expressão para um método `Person.ToString`:</span><span class="sxs-lookup"><span data-stu-id="df896-118">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="df896-119">É uma versão abreviada da seguinte definição de método:</span><span class="sxs-lookup"><span data-stu-id="df896-119">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="df896-120">As definições de corpo de expressão para métodos, operadores e propriedades somente leitura têm suporte a partir do C# 6.</span><span class="sxs-lookup"><span data-stu-id="df896-120">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="df896-121">As definições de corpo de expressão para construtores, finalizadores e acessadores de propriedade e indexador têm suporte a partir do C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="df896-121">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="df896-122">Para obter mais informações, consulte [Membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="df896-122">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="df896-123">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="df896-123">Operator overloadability</span></span>

<span data-ttu-id="df896-124">O operador `=>` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="df896-124">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="df896-125">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="df896-125">C# language specification</span></span>

<span data-ttu-id="df896-126">Para obter mais informações sobre o operador lambda, consulte a seção [expressões de função anônimas](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="df896-126">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df896-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df896-127">See also</span></span>

- [<span data-ttu-id="df896-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="df896-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="df896-129">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="df896-129">C# operators and expressions</span></span>](index.md)
