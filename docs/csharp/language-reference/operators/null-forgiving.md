---
description: '! operador (NULL-tolerante)-referência C#'
title: '! operador (NULL-tolerante)-referência C#'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 5418f96a3b4515224c49a1c1aa38784c348a86db
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516145"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="fe2b8-105">!</span><span class="sxs-lookup"><span data-stu-id="fe2b8-105">!</span></span> <span data-ttu-id="fe2b8-106">operador (NULL-tolerante) (referência C#)</span><span class="sxs-lookup"><span data-stu-id="fe2b8-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="fe2b8-107">Disponível em C# 8,0 e posterior, o operador de sufixo unário `!` é o operador NULL-tolerante.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="fe2b8-108">Em um [contexto de anotação anulável](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o operador NULL-tolerante para declarar que a expressão `x` de um tipo de referência não é `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="fe2b8-109">O operador de prefixo unário `!` é o [operador lógico de negação](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="fe2b8-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="fe2b8-110">O operador NULL-tolerante não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="fe2b8-111">Ele afeta apenas a análise de fluxo estático do compilador, alterando o estado nulo da expressão.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="fe2b8-112">Em tempo de execução, `x!` a expressão é avaliada como o resultado da expressão subjacente `x` .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="fe2b8-113">No C# 8, o operador NULL-tolerante encerra a lista de operações [condicionais nulas](member-access-operators.md#null-conditional-operators--and-) anteriores.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="fe2b8-114">Por exemplo, a expressão `x?.y!.z` é analisada como `(x?.y)!.z` .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="fe2b8-115">Devido a essa interpretação, `z` é avaliada mesmo se `x` for `null` , o que pode resultar em um <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="fe2b8-116">Para obter mais informações sobre o recurso de tipos de referência anulável, consulte [tipos de referência anuláveis](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe2b8-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="fe2b8-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fe2b8-117">Examples</span></span>

<span data-ttu-id="fe2b8-118">Um dos casos de uso do operador NULL-tolerante está no teste da lógica de validação de argumento.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="fe2b8-119">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="fe2b8-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="fe2b8-120">Usando a [estrutura de teste MSTest](../../../core/testing/unit-testing-with-mstest.md), você pode criar o seguinte teste para a lógica de validação no construtor:</span><span class="sxs-lookup"><span data-stu-id="fe2b8-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="fe2b8-121">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código anterior: `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="fe2b8-122">Usando o operador NULL-tolerante, você informa ao compilador que a passagem `null` é esperada e não deve ser avisado sobre.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="fe2b8-123">Você também pode usar o operador NULL-tolerante quando sabe definitivamente que uma expressão não pode ser `null` , mas o compilador não gerencia para reconhecê-la.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="fe2b8-124">No exemplo a seguir, se o `IsValid` método retornar `true` , seu argumento não será `null` e você poderá desreferenciá-lo com segurança:</span><span class="sxs-lookup"><span data-stu-id="fe2b8-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="fe2b8-125">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o `p.Name` código: `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="fe2b8-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="fe2b8-126">Se você puder modificar o `IsValid` método, poderá usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para informar ao compilador que um argumento do `IsValid` método não pode ser `null` quando o método retornar `true` :</span><span class="sxs-lookup"><span data-stu-id="fe2b8-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="fe2b8-127">No exemplo anterior, você não precisa usar o operador NULL-tolerante porque o compilador tem informações suficientes para descobrir que `p` não podem estar `null` dentro da `if` instrução.</span><span class="sxs-lookup"><span data-stu-id="fe2b8-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="fe2b8-128">Para obter mais informações sobre os atributos que permitem fornecer informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="fe2b8-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fe2b8-129">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fe2b8-129">C# language specification</span></span>

<span data-ttu-id="fe2b8-130">Para obter mais informações, consulte [a seção operador NULL-tolerante](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) do [rascunho da especificação de tipos de referência anulável](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="fe2b8-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe2b8-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe2b8-131">See also</span></span>

- [<span data-ttu-id="fe2b8-132">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fe2b8-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fe2b8-133">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="fe2b8-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="fe2b8-134">Tutorial: design com tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="fe2b8-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
