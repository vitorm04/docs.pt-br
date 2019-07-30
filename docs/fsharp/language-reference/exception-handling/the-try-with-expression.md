---
title: 'Exceções: A expressão try...with'
description: Saiba como usar o F# ' Try... expressão with para tratamento de exceção.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630254"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="61490-103">Exceções: A expressão try...with</span><span class="sxs-lookup"><span data-stu-id="61490-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="61490-104">Este tópico descreve a `try...with` expressão, a expressão usada para manipulação de exceção no F# idioma.</span><span class="sxs-lookup"><span data-stu-id="61490-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="61490-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61490-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="61490-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="61490-106">Remarks</span></span>

<span data-ttu-id="61490-107">A `try...with` expressão é usada para tratar exceções no F#.</span><span class="sxs-lookup"><span data-stu-id="61490-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="61490-108">É semelhante à `try...catch` instrução em. C#</span><span class="sxs-lookup"><span data-stu-id="61490-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="61490-109">Na sintaxe anterior, o código em *expression1* pode gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="61490-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="61490-110">A `try...with` expressão retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="61490-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="61490-111">Se nenhuma exceção for gerada, a expressão inteira retornará o valor de *expressão1*.</span><span class="sxs-lookup"><span data-stu-id="61490-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="61490-112">Se uma exceção for lançada, cada *padrão* será comparado com a exceção, e para o primeiro padrão correspondente, a *expressão*correspondente, conhecida como o manipulador de *exceção*, para essa ramificação é executada e a expressão geral Retorna o valor da expressão nesse manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="61490-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="61490-113">Se nenhum padrão corresponder, a exceção propagará a pilha de chamadas até que um manipulador correspondente seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="61490-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="61490-114">Os tipos de valores retornados de cada expressão nos manipuladores de exceção devem corresponder ao tipo retornado da expressão no `try` bloco.</span><span class="sxs-lookup"><span data-stu-id="61490-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="61490-115">Frequentemente, o fato de que ocorreu um erro também significa que não há nenhum valor válido que possa ser retornado das expressões em cada manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="61490-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="61490-116">Um padrão frequente é fazer com que o tipo da expressão seja um tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="61490-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="61490-117">O exemplo de código a seguir ilustra esse padrão.</span><span class="sxs-lookup"><span data-stu-id="61490-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="61490-118">As exceções podem ser exceções .NET ou podem ser F# exceções.</span><span class="sxs-lookup"><span data-stu-id="61490-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="61490-119">Você pode definir F# exceções usando a `exception` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="61490-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="61490-120">Você pode usar uma variedade de padrões para filtrar o tipo de exceção e outras condições; as opções são resumidas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="61490-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="61490-121">Padrão</span><span class="sxs-lookup"><span data-stu-id="61490-121">Pattern</span></span>|<span data-ttu-id="61490-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="61490-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="61490-123">:?</span><span class="sxs-lookup"><span data-stu-id="61490-123">:?</span></span> <span data-ttu-id="61490-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="61490-124">*exception-type*</span></span>|<span data-ttu-id="61490-125">Corresponde ao tipo de exceção .NET especificado.</span><span class="sxs-lookup"><span data-stu-id="61490-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="61490-126">:?</span><span class="sxs-lookup"><span data-stu-id="61490-126">:?</span></span> <span data-ttu-id="61490-127">*tipo de exceção* como *identificador*</span><span class="sxs-lookup"><span data-stu-id="61490-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="61490-128">Corresponde ao tipo de exceção .NET especificado, mas dá à exceção um valor nomeado.</span><span class="sxs-lookup"><span data-stu-id="61490-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="61490-129">*nome da exceção* (*argumentos*)</span><span class="sxs-lookup"><span data-stu-id="61490-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="61490-130">Corresponde a F# um tipo de exceção e associa os argumentos.</span><span class="sxs-lookup"><span data-stu-id="61490-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="61490-131">*identifier*</span><span class="sxs-lookup"><span data-stu-id="61490-131">*identifier*</span></span>|<span data-ttu-id="61490-132">Faz a correspondência de qualquer exceção e associa o nome ao objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="61490-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="61490-133">Equivalente a **:? System. Exception como**_identificador_</span><span class="sxs-lookup"><span data-stu-id="61490-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="61490-134">*identificador* quando *condição*</span><span class="sxs-lookup"><span data-stu-id="61490-134">*identifier* when *condition*</span></span>|<span data-ttu-id="61490-135">Corresponde a qualquer exceção se a condição for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="61490-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="61490-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="61490-136">Examples</span></span>

<span data-ttu-id="61490-137">Os exemplos de código a seguir ilustram o uso dos vários padrões de manipulador de exceção.</span><span class="sxs-lookup"><span data-stu-id="61490-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="61490-138">A `try...with` construção é uma expressão separada `try...finally` da expressão.</span><span class="sxs-lookup"><span data-stu-id="61490-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="61490-139">Portanto, se o seu código exigir um `with` bloco e um `finally` bloco, você terá que aninhar as duas expressões.</span><span class="sxs-lookup"><span data-stu-id="61490-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="61490-140">Você pode usar `try...with` em fluxos de trabalho assíncronos e outras expressões de computação, caso em que uma versão `try...with` personalizada da expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="61490-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="61490-141">Para obter mais informações, consulte [fluxos de trabalho assíncronos](../asynchronous-workflows.md)e expressões de [computação](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="61490-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="61490-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61490-142">See also</span></span>

- [<span data-ttu-id="61490-143">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="61490-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="61490-144">Tipos de Exceção</span><span class="sxs-lookup"><span data-stu-id="61490-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="61490-145">Exceções: A `try...finally` expressão</span><span class="sxs-lookup"><span data-stu-id="61490-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
