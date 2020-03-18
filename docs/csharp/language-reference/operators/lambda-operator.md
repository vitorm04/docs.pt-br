---
title: Operador => – referência do C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846240"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="db177-102">Operador => (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="db177-102">=> operator (C# reference)</span></span>

<span data-ttu-id="db177-103">O `=>` token é suportado em duas formas: como [operador de lambda](#lambda-operator) e como separador de um nome de membro e a implementação do membro em uma [definição de corpo de expressão](#expression-body-definition).</span><span class="sxs-lookup"><span data-stu-id="db177-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="db177-104">Operador lambda</span><span class="sxs-lookup"><span data-stu-id="db177-104">Lambda operator</span></span>

<span data-ttu-id="db177-105">Em [expressões lambda,](../../programming-guide/statements-expressions-operators/lambda-expressions.md)o `=>` operador lambda separa os parâmetros de entrada do lado esquerdo do corpo lambda do lado direito.</span><span class="sxs-lookup"><span data-stu-id="db177-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="db177-106">O seguinte exemplo usa o recurso [LINQ](../../programming-guide/concepts/linq/index.md) com a sintaxe de método para demonstrar o uso de expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="db177-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="db177-107">Os parâmetros de entrada de uma expressão lambda são fortemente digitados no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="db177-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="db177-108">Quando o compilador pode inferir os tipos de parâmetros de entrada, como no exemplo anterior, você pode omiti-lo declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="db177-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="db177-109">Se você precisar especificar o tipo de parâmetros de entrada, você deve fazer isso para cada parâmetro, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="db177-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="db177-110">O exemplo a seguir mostra como definir uma expressão lambda sem parâmetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="db177-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="db177-111">Para obter mais informações, consulte [expressões Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="db177-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="db177-112">Definição de corpo da expressão</span><span class="sxs-lookup"><span data-stu-id="db177-112">Expression body definition</span></span>

<span data-ttu-id="db177-113">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="db177-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="db177-114">em que `expression` é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="db177-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="db177-115">O tipo de retorno de `expression` deve ser implicitamente conversível para o tipo de retorno do membro.</span><span class="sxs-lookup"><span data-stu-id="db177-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="db177-116">Se o tipo de `void` devolução do membro for ou se o membro `set` for `expression` um construtor, um finalizador ou um acessório de propriedade, deve ser uma expressão de [*declaração*](~/_csharplang/spec/statements.md#expression-statements), que pode ser de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="db177-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="db177-117">O seguinte exemplo mostra uma definição de corpo da expressão para um método `Person.ToString`:</span><span class="sxs-lookup"><span data-stu-id="db177-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="db177-118">É uma versão abreviada da seguinte definição de método:</span><span class="sxs-lookup"><span data-stu-id="db177-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="db177-119">As definições do corpo de expressão para métodos, operadores e propriedades somente leitura são suportadas a partir de C # 6.</span><span class="sxs-lookup"><span data-stu-id="db177-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="db177-120">As definições de corpo de expressão para construtores, finalizadores e acessórios de propriedade e indexadores são suportadas a partir de C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="db177-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="db177-121">Para obter mais informações, consulte [Membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="db177-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="db177-122">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="db177-122">Operator overloadability</span></span>

<span data-ttu-id="db177-123">O operador `=>` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="db177-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db177-124">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="db177-124">C# language specification</span></span>

<span data-ttu-id="db177-125">Para obter mais informações sobre o operador lambda, consulte a seção [expressões](~/_csharplang/spec/expressions.md#anonymous-function-expressions) de função Anônima da especificação do [idioma C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="db177-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db177-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="db177-126">See also</span></span>

- [<span data-ttu-id="db177-127">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="db177-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="db177-128">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="db177-128">C# operators</span></span>](index.md)
