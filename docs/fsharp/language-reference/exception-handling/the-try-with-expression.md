---
title: 'Exceções: a expressão try...with (F#)'
description: Saiba como usar a expressão F# 'try... com' para manipulação de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: 588960c0f8ccedb431c37d0f1314bf1a293b638c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042160"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="e6ec2-103">Exceções: a expressão try...with</span><span class="sxs-lookup"><span data-stu-id="e6ec2-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="e6ec2-104">Este tópico descreve o `try...with` expressão, a expressão que é usada para tratamento de exceções na linguagem F#.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6ec2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6ec2-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="e6ec2-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6ec2-106">Remarks</span></span>

<span data-ttu-id="e6ec2-107">O `try...with` expressão é usada para manipular exceções em F#.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="e6ec2-108">Ele é semelhante ao `try...catch` instrução em c#.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="e6ec2-109">Na sintaxe anterior, o código na *expression1* pode gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="e6ec2-110">O `try...with` expressão retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="e6ec2-111">Se nenhuma exceção for lançada, toda a expressão retorna o valor da *expression1*.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="e6ec2-112">Se uma exceção for lançada, cada *padrão* são comparados por sua vez, com a exceção e para o primeiro padrão de correspondência, correspondente *expressão*, conhecido como o *domanipuladordeexceção*, para essa ramificação é executada, e a expressão geral retorna o valor da expressão nesse manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="e6ec2-113">Se nenhum padrão corresponder, a exceção for propagada até a pilha de chamada até que um manipulador correspondente for encontrado.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="e6ec2-114">Os tipos dos valores retornados de cada expressão nos manipuladores de exceção devem corresponder ao tipo retornado da expressão no `try` bloco.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="e6ec2-115">Com frequência, o fato de que ocorreu um erro também significa que não há nenhum valor válido que pode ser retornado de expressões em cada manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="e6ec2-116">Um padrão frequente deve ter o tipo da expressão a ser um tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="e6ec2-117">O exemplo de código a seguir ilustra esse padrão.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="e6ec2-118">As exceções podem ser exceções .NET, ou podem ser exceções de F#.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="e6ec2-119">Você pode definir exceções de F#, usando o `exception` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="e6ec2-120">Você pode usar uma variedade de padrões para filtrar o tipo de exceção e outras condições; as opções são resumidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="e6ec2-121">Padrão</span><span class="sxs-lookup"><span data-stu-id="e6ec2-121">Pattern</span></span>|<span data-ttu-id="e6ec2-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6ec2-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="e6ec2-123">:?</span><span class="sxs-lookup"><span data-stu-id="e6ec2-123">:?</span></span> <span data-ttu-id="e6ec2-124">*tipo de exceção*</span><span class="sxs-lookup"><span data-stu-id="e6ec2-124">*exception-type*</span></span>|<span data-ttu-id="e6ec2-125">Corresponde ao tipo de exceção .NET especificado.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="e6ec2-126">:?</span><span class="sxs-lookup"><span data-stu-id="e6ec2-126">:?</span></span> <span data-ttu-id="e6ec2-127">*tipo de exceção* como *identificador*</span><span class="sxs-lookup"><span data-stu-id="e6ec2-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="e6ec2-128">Corresponde ao tipo de exceção .NET especificado, mas oferece a exceção de um valor nomeado.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="e6ec2-129">*nome da exceção*(*argumentos*)</span><span class="sxs-lookup"><span data-stu-id="e6ec2-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="e6ec2-130">Corresponde a um tipo de exceção do F# e associa os argumentos.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="e6ec2-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="e6ec2-131">*identifier*</span></span>|<span data-ttu-id="e6ec2-132">Corresponde a qualquer exceção e associa o nome para o objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="e6ec2-133">Equivalente a \**:? System. Exception como \* \* \* identificador*</span><span class="sxs-lookup"><span data-stu-id="e6ec2-133">Equivalent to \**:? System.Exception as\*\*\*identifier*</span></span>|
|<span data-ttu-id="e6ec2-134">*identificador* quando *condição*</span><span class="sxs-lookup"><span data-stu-id="e6ec2-134">*identifier* when *condition*</span></span>|<span data-ttu-id="e6ec2-135">Corresponde a qualquer exceção se a condição for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="e6ec2-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e6ec2-136">Examples</span></span>

<span data-ttu-id="e6ec2-137">Os exemplos de código a seguir ilustram o uso de vários padrões de manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

>[!NOTE]
<span data-ttu-id="e6ec2-138">O `try...with` construção é uma expressão separada do `try...finally` expressão.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="e6ec2-139">Portanto, se seu código requer tanto uma `with` bloco e um `finally` bloco, será necessário aninhar as duas expressões.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE]
<span data-ttu-id="e6ec2-140">Você pode usar `try...with` nos fluxos de trabalho assíncronos e outras expressões de computação, nesse caso, uma versão personalizada do `try...with` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="e6ec2-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="e6ec2-141">Para obter mais informações, consulte [fluxos de trabalho assíncronos](../asynchronous-workflows.md), e [expressões de computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e6ec2-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6ec2-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6ec2-142">See also</span></span>

- [<span data-ttu-id="e6ec2-143">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="e6ec2-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="e6ec2-144">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="e6ec2-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="e6ec2-145">Exceções: a expressão `try...finally`</span><span class="sxs-lookup"><span data-stu-id="e6ec2-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
