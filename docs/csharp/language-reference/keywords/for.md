---
title: Instrução for do C#
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: c6ef926d6fb2c79b7b7f71c3b24b86a7ab057c88
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511722"
---
# <a name="for-c-reference"></a><span data-ttu-id="fb2a3-102">for (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-102">for (C# reference)</span></span>

<span data-ttu-id="fb2a3-103">A instrução `for` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="fb2a3-104">Em qualquer ponto dentro do bloco de instrução `for`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="fb2a3-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="fb2a3-105">Você também pode sair de um loop `for` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="fb2a3-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="fb2a3-106">Estrutura da instrução `for`</span><span class="sxs-lookup"><span data-stu-id="fb2a3-106">Structure of the `for` statement</span></span>

<span data-ttu-id="fb2a3-107">A instrução `for` define as seções de *inicializador*, *condição* e *iterador*:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="fb2a3-108">Todas as três seções são opcionais.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-108">All three sections are optional.</span></span> <span data-ttu-id="fb2a3-109">O corpo do loop é uma instrução ou um bloco de instruções.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="fb2a3-110">A exemplo a seguir mostra a instrução `for` com todas as seções definidas:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="fb2a3-111">A seção *inicializador*</span><span class="sxs-lookup"><span data-stu-id="fb2a3-111">The *initializer* section</span></span>

<span data-ttu-id="fb2a3-112">As instruções na seção de *inicializador* são executadas apenas uma vez, antes de entrar no loop.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="fb2a3-113">A seção *inicializador* é uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="fb2a3-114">A declaração e a inicialização de uma variável de loop local, que não pode ser acessada de fora do loop.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="fb2a3-115">Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="fb2a3-116">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="fb2a3-117">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="fb2a3-117">invocation of a method</span></span>

  - <span data-ttu-id="fb2a3-118">prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="fb2a3-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="fb2a3-119">prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="fb2a3-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="fb2a3-120">criação de um objeto usando a palavra-chave [novo](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="fb2a3-121">expressão [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-121">[await](await.md) expression</span></span>

<span data-ttu-id="fb2a3-122">A seção *inicializador* no exemplo acima declara e inicializa a variável de loop local `i`:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="fb2a3-123">A seção *condição*</span><span class="sxs-lookup"><span data-stu-id="fb2a3-123">The *condition* section</span></span>

<span data-ttu-id="fb2a3-124">A seção *condição*, se presente, deverá ser uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="fb2a3-125">Essa expressão é avaliada antes de cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="fb2a3-126">Se a seção *condição* não estiver presente ou a expressão booliana for avaliada como `true`, a próxima iteração do loop será executada; caso contrário, o loop será finalizado.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="fb2a3-127">A seção *condição* no exemplo acima determina se o loop será encerrado com base no valor da variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="fb2a3-128">A seção *iterador*</span><span class="sxs-lookup"><span data-stu-id="fb2a3-128">The *iterator* section</span></span>

<span data-ttu-id="fb2a3-129">A seção *iterador* define o que acontece depois de cada iteração do corpo do loop.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="fb2a3-130">A seção *iterador* contém zero ou mais das seguintes expressões de instrução, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="fb2a3-131">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="fb2a3-132">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="fb2a3-132">invocation of a method</span></span>

- <span data-ttu-id="fb2a3-133">prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="fb2a3-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="fb2a3-134">prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="fb2a3-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="fb2a3-135">criação de um objeto usando a palavra-chave [novo](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="fb2a3-136">expressão [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-136">[await](await.md) expression</span></span>

<span data-ttu-id="fb2a3-137">A seção *iterador* no exemplo acima incrementa a variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="fb2a3-138">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fb2a3-138">Examples</span></span>

<span data-ttu-id="fb2a3-139">O exemplo a seguir ilustra vários usos menos comuns das seções de instrução `for`: atribuir um valor a uma variável de loop externa na seção *inicializador*, invocar um método inicializa nas seções de *inicializador* e de *iterador* e alterar os valores de duas variáveis na seção de *iterador*.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="fb2a3-140">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="fb2a3-141">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="fb2a3-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="fb2a3-142">O exemplo a seguir define o loop `for` infinito:</span><span class="sxs-lookup"><span data-stu-id="fb2a3-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="fb2a3-143">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fb2a3-143">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fb2a3-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb2a3-144">See also</span></span>

- [<span data-ttu-id="fb2a3-145">A instrução for (especificação da linguagem C#)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)
- [<span data-ttu-id="fb2a3-146">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fb2a3-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fb2a3-147">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fb2a3-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fb2a3-148">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="fb2a3-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fb2a3-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="fb2a3-149">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="fb2a3-150">Instrução for (C++)</span><span class="sxs-lookup"><span data-stu-id="fb2a3-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)
- [<span data-ttu-id="fb2a3-151">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="fb2a3-151">Iteration Statements</span></span>](iteration-statements.md)
