---
title: '! Operador (inodentrada nula) - Referência C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 658043f8d5e149064f6da328657b2ccef9b5da94
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121438"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="3555d-103">!</span><span class="sxs-lookup"><span data-stu-id="3555d-103">!</span></span> <span data-ttu-id="3555d-104">Operador (inodção nula) (referência C#)</span><span class="sxs-lookup"><span data-stu-id="3555d-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="3555d-105">Disponível em C# 8.0 e posterior, o operador postfix não-ary `!` é o operador de perdão nulo.</span><span class="sxs-lookup"><span data-stu-id="3555d-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="3555d-106">Em um contexto de [anotação anulada](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o `x` operador que perdoa nulo para declarar que a expressão de um tipo de referência não `null`é: `x!`.</span><span class="sxs-lookup"><span data-stu-id="3555d-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="3555d-107">O operador `!` de prefixo não ário é o [operador de negação lógico.](boolean-logical-operators.md#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="3555d-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="3555d-108">O operador de perdoar nulos não tem efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3555d-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="3555d-109">Afeta apenas a análise estática do fluxo do compilador alterando o estado nulo da expressão.</span><span class="sxs-lookup"><span data-stu-id="3555d-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="3555d-110">No tempo de `x!` execução, a expressão avalia `x`o resultado da expressão subjacente .</span><span class="sxs-lookup"><span data-stu-id="3555d-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="3555d-111">Para obter mais informações sobre o recurso de tipos de referência anulados, consulte [tipos de referência anulados](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="3555d-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="3555d-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3555d-112">Examples</span></span>

<span data-ttu-id="3555d-113">Um dos casos de uso do operador que perdoa nulos é testar a lógica de validação de argumentos.</span><span class="sxs-lookup"><span data-stu-id="3555d-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="3555d-114">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="3555d-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="3555d-115">Usando a [estrutura de teste MSTest,](../../../core/testing/unit-testing-with-mstest.md)você pode criar o seguinte teste para a lógica de validação no construtor:</span><span class="sxs-lookup"><span data-stu-id="3555d-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="3555d-116">Sem o operador que perdoa nulos, o compilador `Warning CS8625: Cannot convert null literal to non-nullable reference type`gera o seguinte aviso para o código anterior: .</span><span class="sxs-lookup"><span data-stu-id="3555d-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="3555d-117">Ao usar o operador de perdoar nulos, você `null` informa ao compilador que a passagem é esperada e não deve ser avisada.</span><span class="sxs-lookup"><span data-stu-id="3555d-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="3555d-118">Você também pode usar o operador que perdoa nulos quando você definitivamente sabe que uma expressão não pode ser, `null` mas o compilador não consegue reconhecer isso.</span><span class="sxs-lookup"><span data-stu-id="3555d-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="3555d-119">No exemplo a seguir, se o `IsValid` método retornar, `true`seu argumento não `null` é e você pode desreferencia-lo com segurança:</span><span class="sxs-lookup"><span data-stu-id="3555d-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="3555d-120">Sem o operador que perdoa nulos, o `p.Name` compilador gera o seguinte aviso para o código: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="3555d-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="3555d-121">Se você puder `IsValid` modificar o método, você pode usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para informar ao compilador que um argumento do `IsValid` método não pode ser `null` quando o método retorna: `true`</span><span class="sxs-lookup"><span data-stu-id="3555d-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="3555d-122">No exemplo anterior, você não precisa usar o operador que perdoa nulos porque `p` o `null` compilador `if` tem informações suficientes para descobrir que não pode estar dentro da declaração.</span><span class="sxs-lookup"><span data-stu-id="3555d-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="3555d-123">Para obter mais informações sobre os atributos que permitem fornecer informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="3555d-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3555d-124">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3555d-124">C# language specification</span></span>

<span data-ttu-id="3555d-125">Para obter mais informações, consulte A seção [operadora de perdão nulo](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) da [minuta da especificação de tipos de referência anuladas](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="3555d-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3555d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="3555d-126">See also</span></span>

- [<span data-ttu-id="3555d-127">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="3555d-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3555d-128">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3555d-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="3555d-129">Tutorial: Design com tipos de referência anulados</span><span class="sxs-lookup"><span data-stu-id="3555d-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
