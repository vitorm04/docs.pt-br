---
title: '! operador (NULL-tolerante)-referência C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 2a8db2882968dbcbe6a8868ab6fe1c128c94a41f
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624872"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="64f85-103">!</span><span class="sxs-lookup"><span data-stu-id="64f85-103">!</span></span> <span data-ttu-id="64f85-104">operador (NULL-tolerante) (referência C#)</span><span class="sxs-lookup"><span data-stu-id="64f85-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="64f85-105">Disponível em C# 8,0 e posterior, o operador de `!` sufixo unário é o operador NULL-tolerante.</span><span class="sxs-lookup"><span data-stu-id="64f85-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="64f85-106">Em um [contexto de anotação anulável](../../nullable-references.md#nullable-annotation-context)habilitado, você usa o operador NULL-tolerante para declarar que `x` a expressão de um tipo `null`de `x!`referência não é:.</span><span class="sxs-lookup"><span data-stu-id="64f85-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="64f85-107">O operador de `!` prefixo unário é o [operador lógico de negação](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="64f85-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="64f85-108">O operador NULL-tolerante não tem nenhum efeito no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="64f85-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="64f85-109">Ele afeta apenas a análise de fluxo estático do compilador, alterando o estado nulo da expressão.</span><span class="sxs-lookup"><span data-stu-id="64f85-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="64f85-110">Em tempo de execução, `x!` a expressão é avaliada como o resultado da `x`expressão subjacente.</span><span class="sxs-lookup"><span data-stu-id="64f85-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="64f85-111">No C# 8, o operador NULL-tolerante encerra a lista de operações [condicionais nulas](member-access-operators.md#null-conditional-operators--and-) anteriores.</span><span class="sxs-lookup"><span data-stu-id="64f85-111">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="64f85-112">Por exemplo, a expressão `x?.y!.z` é analisada como `(x?.y)!.z`.</span><span class="sxs-lookup"><span data-stu-id="64f85-112">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="64f85-113">Devido a essa interpretação, `z` é avaliada mesmo `x` se `null`for, o que pode resultar <xref:System.NullReferenceException>em um.</span><span class="sxs-lookup"><span data-stu-id="64f85-113">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="64f85-114">Para obter mais informações sobre o recurso de tipos de referência anulável, consulte [tipos de referência anuláveis](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="64f85-114">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="64f85-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="64f85-115">Examples</span></span>

<span data-ttu-id="64f85-116">Um dos casos de uso do operador NULL-tolerante está no teste da lógica de validação de argumento.</span><span class="sxs-lookup"><span data-stu-id="64f85-116">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="64f85-117">Por exemplo, considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="64f85-117">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="64f85-118">Usando a [estrutura de teste MSTest](../../../core/testing/unit-testing-with-mstest.md), você pode criar o seguinte teste para a lógica de validação no construtor:</span><span class="sxs-lookup"><span data-stu-id="64f85-118">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="64f85-119">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o código anterior: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="64f85-119">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="64f85-120">Usando o operador NULL-tolerante, você informa ao compilador que a passagem `null` é esperada e não deve ser avisado sobre.</span><span class="sxs-lookup"><span data-stu-id="64f85-120">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="64f85-121">Você também pode usar o operador NULL-tolerante quando sabe definitivamente que uma expressão não pode ser `null` , mas o compilador não gerencia para reconhecê-la.</span><span class="sxs-lookup"><span data-stu-id="64f85-121">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="64f85-122">No exemplo a seguir, se o `IsValid` método retornar `true`, seu argumento não `null` será e você poderá desreferenciá-lo com segurança:</span><span class="sxs-lookup"><span data-stu-id="64f85-122">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="64f85-123">Sem o operador NULL-tolerante, o compilador gera o seguinte aviso para o `p.Name` código: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="64f85-123">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="64f85-124">Se você puder modificar o `IsValid` método, poderá usar o atributo [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) para informar ao compilador que um argumento do `IsValid` método não pode ser `null` quando o método retornar: `true`</span><span class="sxs-lookup"><span data-stu-id="64f85-124">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="64f85-125">No exemplo anterior, você não precisa usar o operador NULL-tolerante porque o compilador tem informações suficientes para descobrir que `p` não podem estar `null` dentro da `if` instrução.</span><span class="sxs-lookup"><span data-stu-id="64f85-125">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="64f85-126">Para obter mais informações sobre os atributos que permitem fornecer informações adicionais sobre o estado nulo de uma variável, consulte [Atualizar APIs com atributos para definir expectativas nulas](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="64f85-126">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="64f85-127">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="64f85-127">C# language specification</span></span>

<span data-ttu-id="64f85-128">Para obter mais informações, consulte [a seção operador NULL-tolerante](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) do [rascunho da especificação de tipos de referência anulável](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="64f85-128">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="64f85-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="64f85-129">See also</span></span>

- [<span data-ttu-id="64f85-130">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="64f85-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="64f85-131">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="64f85-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="64f85-132">Tutorial: design com tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="64f85-132">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
