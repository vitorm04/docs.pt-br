---
title: for (Referência de C#)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207842"
---
# <a name="for-c-reference"></a><span data-ttu-id="609e2-102">for (referência de C#)</span><span class="sxs-lookup"><span data-stu-id="609e2-102">for (C# reference)</span></span>

<span data-ttu-id="609e2-103">A instrução `for` executa uma instrução ou um bloco de instruções enquanto uma expressão booliana especificada é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="609e2-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="609e2-104">Em qualquer ponto dentro do bloco de instrução `for`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="609e2-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="609e2-105">Você também pode sair de um loop `for` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="609e2-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>
  
## <a name="structure-of-the-for-statement"></a><span data-ttu-id="609e2-106">Estrutura da instrução `for`</span><span class="sxs-lookup"><span data-stu-id="609e2-106">Structure of the `for` statement</span></span>

<span data-ttu-id="609e2-107">A instrução `for` define as seções *Inicializador*, *Condição* e *Iterador*:</span><span class="sxs-lookup"><span data-stu-id="609e2-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>
  
```csharp
for (initializer; condition; iterator)  
    body  
```

<span data-ttu-id="609e2-108">Todas as três seções são opcionais.</span><span class="sxs-lookup"><span data-stu-id="609e2-108">All three sections are optional.</span></span> <span data-ttu-id="609e2-109">O corpo do loop é uma instrução ou um bloco de instruções.</span><span class="sxs-lookup"><span data-stu-id="609e2-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="609e2-110">A exemplo a seguir mostra a instrução `for` com todas as seções definidas:</span><span class="sxs-lookup"><span data-stu-id="609e2-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="609e2-111">A seção *Inicializador*</span><span class="sxs-lookup"><span data-stu-id="609e2-111">The *initializer* section</span></span>

<span data-ttu-id="609e2-112">As instruções na seção *Inicializador* são executadas apenas uma vez, antes de entrar no loop.</span><span class="sxs-lookup"><span data-stu-id="609e2-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="609e2-113">A seção *Inicializador* é uma das seguintes:</span><span class="sxs-lookup"><span data-stu-id="609e2-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="609e2-114">A declaração e a inicialização de uma variável de loop local, que não pode ser acessada de fora do loop.</span><span class="sxs-lookup"><span data-stu-id="609e2-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="609e2-115">Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="609e2-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="609e2-116">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="609e2-117">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="609e2-117">invocation of a method</span></span>  

  - <span data-ttu-id="609e2-118">prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="609e2-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

  - <span data-ttu-id="609e2-119">prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="609e2-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

  - <span data-ttu-id="609e2-120">criação de um objeto usando a palavra-chave [novo](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="609e2-121">expressão [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-121">[await](await.md) expression</span></span>

<span data-ttu-id="609e2-122">A seção *Inicializador* no exemplo acima declara e inicializa a variável de loop local `i`:</span><span class="sxs-lookup"><span data-stu-id="609e2-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="609e2-123">A seção *Condição*</span><span class="sxs-lookup"><span data-stu-id="609e2-123">The *condition* section</span></span>

<span data-ttu-id="609e2-124">A seção *Condição*, se presente, deverá ser uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="609e2-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="609e2-125">Essa expressão é avaliada antes de cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="609e2-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="609e2-126">Se a seção *Condição* não estiver presente ou a expressão booliana for avaliada como `true`, a próxima iteração do loop será executada; caso contrário, o loop será finalizado.</span><span class="sxs-lookup"><span data-stu-id="609e2-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="609e2-127">A seção *Condição* no exemplo acima determina se o loop será encerrado com base no valor da variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="609e2-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="609e2-128">A seção *Iterador*</span><span class="sxs-lookup"><span data-stu-id="609e2-128">The *iterator* section</span></span>

<span data-ttu-id="609e2-129">A seção *Iterador* define o que acontece depois de cada iteração do corpo do loop.</span><span class="sxs-lookup"><span data-stu-id="609e2-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="609e2-130">A seção *Iterador* contém zero ou mais das seguintes expressões de instrução, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="609e2-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>  

- <span data-ttu-id="609e2-131">instrução de [atribuição](../operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="609e2-132">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="609e2-132">invocation of a method</span></span>  

- <span data-ttu-id="609e2-133">prefixo ou sufixo da expressão [incrementar](../operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="609e2-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

- <span data-ttu-id="609e2-134">prefixo ou sufixo da expressão [decrementar](../operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="609e2-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

- <span data-ttu-id="609e2-135">criação de um objeto usando a palavra-chave [novo](new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="609e2-136">expressão [await](await.md)</span><span class="sxs-lookup"><span data-stu-id="609e2-136">[await](await.md) expression</span></span>

<span data-ttu-id="609e2-137">A seção *Iterador* no exemplo acima incrementa a variável de loop local:</span><span class="sxs-lookup"><span data-stu-id="609e2-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="609e2-138">Exemplos</span><span class="sxs-lookup"><span data-stu-id="609e2-138">Examples</span></span>

<span data-ttu-id="609e2-139">O exemplo a seguir ilustra vários usos menos comuns das seções de instrução `for`: atribuir um valor a uma variável de loop externa na seção *Inicializador*, invocar um método inicializa nas seções *Inicializador* e *Iterador* e alterar os valores de duas variáveis na seção *Iterador*.</span><span class="sxs-lookup"><span data-stu-id="609e2-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="609e2-140">Selecione **Executar** para executar o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="609e2-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="609e2-141">Depois disso, você pode modificar o código e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="609e2-141">After that you can modify the code and run it again.</span></span>
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
<span data-ttu-id="609e2-142">O exemplo a seguir define o loop `for` infinito:</span><span class="sxs-lookup"><span data-stu-id="609e2-142">The following example defines the infinite `for` loop:</span></span>
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a><span data-ttu-id="609e2-143">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="609e2-143">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="609e2-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="609e2-144">See also</span></span>

[<span data-ttu-id="609e2-145">A instrução for (especificação da linguagem C#)</span><span class="sxs-lookup"><span data-stu-id="609e2-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="609e2-146">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="609e2-146">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="609e2-147">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="609e2-147">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="609e2-148">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="609e2-148">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="609e2-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="609e2-149">foreach, in</span></span>](foreach-in.md)  
[<span data-ttu-id="609e2-150">Instrução for (C++)</span><span class="sxs-lookup"><span data-stu-id="609e2-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="609e2-151">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="609e2-151">Iteration Statements</span></span>](iteration-statements.md)
