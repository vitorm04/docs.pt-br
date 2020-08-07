---
title: ?? e?? = Operators-referência C#
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 58c60dad3badc62f850f737a3d210ec486809272
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916741"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="41569-103">??</span><span class="sxs-lookup"><span data-stu-id="41569-103">??</span></span> <span data-ttu-id="41569-104">e?? = Operators (referência C#)</span><span class="sxs-lookup"><span data-stu-id="41569-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="41569-105">O operador de coalescência nula `??` retornará o valor do operando esquerdo se não for `null`; caso contrário, ele avaliará o operando direito e retornará seu resultado.</span><span class="sxs-lookup"><span data-stu-id="41569-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="41569-106">O operador `??` não avaliará o operando do lado direito se o operando esquerdo for avaliado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="41569-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="41569-107">Disponível em C# 8,0 e posterior, o operador de atribuição de União nula `??=` atribui o valor de seu operando à direita para seu operando à esquerda somente se o operando esquerdo for avaliado como `null` .</span><span class="sxs-lookup"><span data-stu-id="41569-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="41569-108">O operador `??=` não avaliará o operando do lado direito se o operando esquerdo for avaliado como não nulo.</span><span class="sxs-lookup"><span data-stu-id="41569-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="41569-109">O operando da esquerda do `??=` operador deve ser uma variável, uma [Propriedade](../../programming-guide/classes-and-structs/properties.md)ou um elemento do [indexador](../../programming-guide/indexers/index.md) .</span><span class="sxs-lookup"><span data-stu-id="41569-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="41569-110">No C# 7,3 e anterior, o tipo do operando à esquerda do `??` operador deve ser um [tipo de referência](../keywords/reference-types.md) ou um [tipo de valor anulável](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="41569-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="41569-111">A partir do C# 8,0, esse requisito é substituído pelo seguinte: o tipo do operando esquerdo dos `??` `??=` operadores e não pode ser um tipo de valor não anulável.</span><span class="sxs-lookup"><span data-stu-id="41569-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="41569-112">Em particular, a partir do C# 8,0, você pode usar os operadores de União nulo com parâmetros de tipo irrestrito:</span><span class="sxs-lookup"><span data-stu-id="41569-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="41569-113">Os operadores de União nulos são associativos à direita.</span><span class="sxs-lookup"><span data-stu-id="41569-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="41569-114">Ou seja, expressões do formulário</span><span class="sxs-lookup"><span data-stu-id="41569-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="41569-115">são avaliados como</span><span class="sxs-lookup"><span data-stu-id="41569-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="41569-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="41569-116">Examples</span></span>

<span data-ttu-id="41569-117">Os `??` `??=` operadores e podem ser úteis nos seguintes cenários:</span><span class="sxs-lookup"><span data-stu-id="41569-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="41569-118">Em expressões com [operadores condicionais nulos?. e? []](member-access-operators.md#null-conditional-operators--and-), você pode usar o `??` operador para fornecer uma expressão alternativa a ser avaliada, caso o resultado da expressão com operações condicionais nulas seja `null` :</span><span class="sxs-lookup"><span data-stu-id="41569-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="41569-119">Quando você trabalha com [tipos de valor anulável](../builtin-types/nullable-value-types.md) e precisa fornecer um valor de um tipo de valor subjacente, use o `??` operador para especificar o valor a ser fornecido, caso um valor de tipo anulável seja `null` :</span><span class="sxs-lookup"><span data-stu-id="41569-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="41569-120">Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo for `null` tiver que ser o valor padrão do tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="41569-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="41569-121">A partir do C# 7,0, você pode usar uma [ `throw` expressão](../keywords/throw.md#the-throw-expression) como o operando à direita do `??` operador para tornar o código de verificação de argumento mais conciso:</span><span class="sxs-lookup"><span data-stu-id="41569-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="41569-122">O exemplo anterior também demonstra como usar [membros aptos para expressão](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) para definir uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="41569-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="41569-123">A partir do C# 8,0, você pode usar o `??=` operador para substituir o código do formulário</span><span class="sxs-lookup"><span data-stu-id="41569-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="41569-124">pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="41569-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="41569-125">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="41569-125">Operator overloadability</span></span>

<span data-ttu-id="41569-126">Os operadores `??` e `??=` não podem ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="41569-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="41569-127">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="41569-127">C# language specification</span></span>

<span data-ttu-id="41569-128">Para obter mais informações sobre o `??` operador, consulte [a seção operador de União nula](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="41569-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="41569-129">Para obter mais informações sobre o `??=` operador, consulte a [Nota de proposta de recurso](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="41569-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41569-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41569-130">See also</span></span>

- [<span data-ttu-id="41569-131">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="41569-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="41569-132">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="41569-132">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="41569-133">[Operadores ?. e ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="41569-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="41569-134">operador?:</span><span class="sxs-lookup"><span data-stu-id="41569-134">?: operator</span></span>](conditional-operator.md)
