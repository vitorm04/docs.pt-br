---
title: para declaração - Referência C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: cb83fa015eea19b156faebb5bed18cc1f0970cc1
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738805"
---
# <a name="for-c-reference"></a><span data-ttu-id="1d87c-102">for (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1d87c-102">for (C# reference)</span></span>

<span data-ttu-id="1d87c-103">A instrução `for` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="1d87c-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="1d87c-104">Em qualquer ponto dentro do bloco de instrução `for`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="1d87c-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1d87c-105">Você também pode `for` sair de um loop pelas declarações [goto](goto.md), [return](return.md)ou [throw.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-105">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="1d87c-106">Estrutura da instrução `for`</span><span class="sxs-lookup"><span data-stu-id="1d87c-106">Structure of the `for` statement</span></span>

<span data-ttu-id="1d87c-107">A instrução `for` define as seções de *inicializador*, *condição* e *iterador*:</span><span class="sxs-lookup"><span data-stu-id="1d87c-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="1d87c-108">Todas as três seções são opcionais.</span><span class="sxs-lookup"><span data-stu-id="1d87c-108">All three sections are optional.</span></span> <span data-ttu-id="1d87c-109">O corpo do loop é uma instrução ou um bloco de instruções.</span><span class="sxs-lookup"><span data-stu-id="1d87c-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="1d87c-110">A exemplo a seguir mostra a instrução `for` com todas as seções definidas:</span><span class="sxs-lookup"><span data-stu-id="1d87c-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="1d87c-111">A seção *inicializador*</span><span class="sxs-lookup"><span data-stu-id="1d87c-111">The *initializer* section</span></span>

<span data-ttu-id="1d87c-112">As instruções na seção de *inicializador* são executadas apenas uma vez, antes de entrar no loop.</span><span class="sxs-lookup"><span data-stu-id="1d87c-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="1d87c-113">A seção *inicializador* é uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="1d87c-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="1d87c-114">A declaração e a inicialização de uma variável de loop local, que não pode ser acessada de fora do loop.</span><span class="sxs-lookup"><span data-stu-id="1d87c-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="1d87c-115">Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="1d87c-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="1d87c-116">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="1d87c-117">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="1d87c-117">invocation of a method</span></span>

  - <span data-ttu-id="1d87c-118">prefixo ou sufixo da expressão [incrementar](../operators/arithmetic-operators.md#increment-operator-), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="1d87c-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="1d87c-119">prefixo ou sufixo da expressão [decrementar](../operators/arithmetic-operators.md#decrement-operator---), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="1d87c-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="1d87c-120">criação de um objeto usando o operador [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="1d87c-121">expressão [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="1d87c-122">A seção *inicializador* no exemplo acima declara e inicializa a variável de loop local `i`:</span><span class="sxs-lookup"><span data-stu-id="1d87c-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="1d87c-123">A seção *condição*</span><span class="sxs-lookup"><span data-stu-id="1d87c-123">The *condition* section</span></span>

<span data-ttu-id="1d87c-124">A seção *condição*, se presente, deverá ser uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="1d87c-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="1d87c-125">Essa expressão é avaliada antes de cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="1d87c-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="1d87c-126">Se a seção *condição* não estiver presente ou a expressão booliana for avaliada como `true`, a próxima iteração do loop será executada; caso contrário, o loop será finalizado.</span><span class="sxs-lookup"><span data-stu-id="1d87c-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="1d87c-127">A seção *condição* no exemplo acima determina se o loop será encerrado com base no valor da variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="1d87c-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="1d87c-128">A seção *iterador*</span><span class="sxs-lookup"><span data-stu-id="1d87c-128">The *iterator* section</span></span>

<span data-ttu-id="1d87c-129">A seção *iterator* define o que acontece após cada iteração do corpo do loop.</span><span class="sxs-lookup"><span data-stu-id="1d87c-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="1d87c-130">A seção *iterator* contém zero ou mais das seguintes expressões de declaração, separadas por commas:</span><span class="sxs-lookup"><span data-stu-id="1d87c-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="1d87c-131">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="1d87c-132">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="1d87c-132">invocation of a method</span></span>

- <span data-ttu-id="1d87c-133">prefixo ou sufixo da expressão [incrementar](../operators/arithmetic-operators.md#increment-operator-), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="1d87c-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="1d87c-134">prefixo ou sufixo da expressão [decrementar](../operators/arithmetic-operators.md#decrement-operator---), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="1d87c-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="1d87c-135">criação de um objeto usando o operador [new](../operators/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="1d87c-136">expressão [await](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="1d87c-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="1d87c-137">A seção *iterador* no exemplo acima incrementa a variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="1d87c-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="1d87c-138">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1d87c-138">Examples</span></span>

<span data-ttu-id="1d87c-139">O exemplo a seguir ilustra vários usos menos comuns das seções de instrução `for`: atribuir um valor a uma variável de loop externa na seção *inicializador*, invocar um método inicializa nas seções de *inicializador* e de *iterador* e alterar os valores de duas variáveis na seção de *iterador*.</span><span class="sxs-lookup"><span data-stu-id="1d87c-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="1d87c-140">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1d87c-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="1d87c-141">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="1d87c-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="1d87c-142">O exemplo a seguir define o loop `for` infinito:</span><span class="sxs-lookup"><span data-stu-id="1d87c-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="1d87c-143">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1d87c-143">C# language specification</span></span>

<span data-ttu-id="1d87c-144">Para obter mais informações, confira a seção [A instrução for](~/_csharplang/spec/statements.md#the-for-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="1d87c-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d87c-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d87c-145">See also</span></span>

- [<span data-ttu-id="1d87c-146">C# Referência</span><span class="sxs-lookup"><span data-stu-id="1d87c-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d87c-147">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="1d87c-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d87c-148">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="1d87c-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d87c-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="1d87c-149">foreach, in</span></span>](foreach-in.md)
