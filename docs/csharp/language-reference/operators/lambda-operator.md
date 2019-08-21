---
title: Operador => – referência do C#
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971228"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e4a2e-102">Operador => (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="e4a2e-102">=> operator (C# reference)</span></span>

<span data-ttu-id="e4a2e-103">Há suporte para o token `=>` de duas formas: como o operador lambda e como um separador de um nome de membro e a implementação de membro em uma definição de corpo da expressão.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="e4a2e-104">Operador lambda</span><span class="sxs-lookup"><span data-stu-id="e4a2e-104">Lambda operator</span></span>

<span data-ttu-id="e4a2e-105">Em [expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), o operador lambda `=>` separa as variáveis de entrada no lado esquerdo do corpo lambda no lado direito.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="e4a2e-106">O seguinte exemplo usa o recurso [LINQ](../../programming-guide/concepts/linq/index.md) com a sintaxe de método para demonstrar o uso de expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="e4a2e-107">As variáveis de entrada de expressões lambda são fortemente tipadas no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="e4a2e-108">Quando o compilador pode inferir os tipos de variáveis de entrada, como no exemplo anterior, você pode omitir as declarações de tipo.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="e4a2e-109">Caso precise especificar o tipo de variáveis de entrada, faça isso para cada variável, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="e4a2e-110">O seguinte exemplo mostra como definir uma expressão lambda sem variáveis de entrada:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="e4a2e-111">Para obter mais informações, confira [Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e4a2e-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="e4a2e-112">Definição de corpo da expressão</span><span class="sxs-lookup"><span data-stu-id="e4a2e-112">Expression body definition</span></span>

<span data-ttu-id="e4a2e-113">Uma definição de corpo da expressão tem a seguinte sintaxe geral:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="e4a2e-114">em que `expression` é uma expressão válida.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="e4a2e-115">O tipo de retorno de `expression` deve ser implicitamente conversível para o tipo de retorno do membro.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="e4a2e-116">Se o tipo de retorno do membro for `void` ou se o membro for um construtor, um finalizador ou um acessador `set` de propriedade, `expression` deverá ser uma [*expressão de instrução*](~/_csharplang/spec/statements.md#expression-statements); pode ser de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements); it can be of any type then.</span></span>

<span data-ttu-id="e4a2e-117">O seguinte exemplo mostra uma definição de corpo da expressão para um método `Person.ToString`:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="e4a2e-118">É uma versão abreviada da seguinte definição de método:</span><span class="sxs-lookup"><span data-stu-id="e4a2e-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="e4a2e-119">Há suporte para definições de corpo da expressão em métodos e propriedades somente leitura do C# 6 em diante.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-119">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="e4a2e-120">Há suporte para definições de corpo da expressão em construtores, finalizadores, acessadores de propriedade e indexadores do C# 7.0 em diante.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-120">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="e4a2e-121">Para obter mais informações, consulte [Membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="e4a2e-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e4a2e-122">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="e4a2e-122">Operator overloadability</span></span>

<span data-ttu-id="e4a2e-123">O operador `=>` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e4a2e-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e4a2e-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e4a2e-124">C# language specification</span></span>

<span data-ttu-id="e4a2e-125">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e4a2e-125">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4a2e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4a2e-126">See also</span></span>

- [<span data-ttu-id="e4a2e-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e4a2e-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e4a2e-128">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="e4a2e-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="e4a2e-129">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="e4a2e-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="e4a2e-130">Membros de expressão incorporada</span><span class="sxs-lookup"><span data-stu-id="e4a2e-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
