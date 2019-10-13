---
title: '! operador (NULL-tolerante)- C# referência'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291721"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="9425c-103">!</span><span class="sxs-lookup"><span data-stu-id="9425c-103">!</span></span> <span data-ttu-id="9425c-104">(operador NULL-tolerante) (C# referência)</span><span class="sxs-lookup"><span data-stu-id="9425c-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="9425c-105">Disponível em C# 8,0 e posterior, o operador sufixo unário `!` é o operador NULL-tolerante.</span><span class="sxs-lookup"><span data-stu-id="9425c-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="9425c-106">Em um [contexto de anotação anulável](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o operador NULL-tolerante para declarar que a expressão `x` de um tipo de referência não é nula: `x!`.</span><span class="sxs-lookup"><span data-stu-id="9425c-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="9425c-107">O prefixo unário `!` é um [operador lógico de negação](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="9425c-107">The unary prefix `!` operator is a [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="9425c-108">O operador NULL-tolerante não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9425c-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="9425c-109">Ele afeta apenas a análise de fluxo estático do compilador, alterando o estado nulo da expressão.</span><span class="sxs-lookup"><span data-stu-id="9425c-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="9425c-110">Em tempo de execução, a expressão `x!` é avaliada como o resultado da expressão subjacente `x`.</span><span class="sxs-lookup"><span data-stu-id="9425c-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="9425c-111">Para obter mais informações sobre o recurso de tipos de referência anulável, consulte [tipos de referência anuláveis](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="9425c-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="9425c-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9425c-112">Examples</span></span>

<span data-ttu-id="9425c-113">Um dos casos de uso do operador NULL-tolerante está no teste da lógica de validação de argumento.</span><span class="sxs-lookup"><span data-stu-id="9425c-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="9425c-114">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="9425c-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="9425c-115">Usando a [estrutura de teste MSTest](../../../core/testing/unit-testing-with-mstest.md), você pode criar o seguinte teste para a lógica de validação no construtor:</span><span class="sxs-lookup"><span data-stu-id="9425c-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="9425c-116">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código anterior: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="9425c-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="9425c-117">Com o uso do operador NULL-tolerante, você permite que o compilador saiba que passar `null` é esperado e não deve ser avisado sobre.</span><span class="sxs-lookup"><span data-stu-id="9425c-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="9425c-118">Você também pode usar o operador NULL-tolerante quando sabe definitivamente que uma expressão não pode ser `null`, mas que o compilador não gerencia para reconhecê-la.</span><span class="sxs-lookup"><span data-stu-id="9425c-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="9425c-119">No exemplo a seguir, se o método `IsValid` retornar `true`, seu argumento não será `null` e você poderá desreferenciá-lo com segurança:</span><span class="sxs-lookup"><span data-stu-id="9425c-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="9425c-120">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código `p.Name`: `Warning CS8602: Dereference of a possibly null reference.`.</span><span class="sxs-lookup"><span data-stu-id="9425c-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference.`.</span></span>

<span data-ttu-id="9425c-121">Se você puder modificar o método `IsValid`, poderá usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para permitir que o compilador saiba que um argumento do método `IsValid` não pode ser `null` quando o método retornar `true`:</span><span class="sxs-lookup"><span data-stu-id="9425c-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="9425c-122">No exemplo anterior, você não precisa usar o operador NULL-tolerante porque o compilador tem informações suficientes para descobrir que `p` não pode ser `null` dentro da instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="9425c-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="9425c-123">Para obter mais informações sobre os atributos que permitem especificar informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9425c-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9425c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9425c-124">See also</span></span>

- [<span data-ttu-id="9425c-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9425c-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9425c-126">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="9425c-126">C# operators</span></span>](index.md)
- <span data-ttu-id="9425c-127">[Tutorial: Design com tipos de referência anuláveis @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="9425c-127">[Tutorial: Design with nullable reference types](../../tutorials/nullable-reference-types.md)</span></span>
