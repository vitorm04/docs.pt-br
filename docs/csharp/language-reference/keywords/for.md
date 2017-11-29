---
title: "for (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="7e7f5-102">for (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-102">for (C# Reference)</span></span>
<span data-ttu-id="7e7f5-103">Ao usar um loop `for`, você pode executar uma instrução ou um bloco de instruções repetidamente até que uma expressão especificada seja avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="7e7f5-104">Esse tipo de loop é útil para a iteração em matrizes e para outras aplicações nas quais você sabe com antecedência quantas vezes deseja que o loop itere.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e7f5-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7e7f5-105">Example</span></span>  
 <span data-ttu-id="7e7f5-106">No exemplo a seguir, o valor de `i` é gravado no console e é incrementado em 1 durante cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="7e7f5-107">A instrução `for` no exemplo anterior realiza as seguintes ações.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="7e7f5-108">Primeiro, o valor inicial da variável `i` é estabelecido.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="7e7f5-109">Esta etapa ocorre apenas uma vez, independentemente de quantas vezes o loop se repete.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="7e7f5-110">Você pode pensar nessa inicialização como ocorrendo fora do processo de loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="7e7f5-111">Para avaliar a condição (`i <= 5`), o valor de `i` é comparado com 5.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="7e7f5-112">Se `i` é menor ou igual a 5, a condição é avaliada como `true` e ocorrem as seguintes ações.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="7e7f5-113">A instrução `Console.WriteLine` no corpo do loop exibe o valor de `i`.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="7e7f5-114">O valor de `i` é incrementado em 1.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="7e7f5-115">O loop retorna para o início da etapa 2 para avaliar a condição novamente.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="7e7f5-116">Se `i` é maior que 5, a condição é avaliada como `false` e você sai do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="7e7f5-117">Observe que, se o valor inicial de `i` é maior que 5, o corpo do loop não é executado nenhuma vez.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="7e7f5-118">Cada instrução `for` define seções de inicializador, de condição e de iterador.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="7e7f5-119">Essas seções geralmente determinam quantas vezes o loop vai iterar.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="7e7f5-120">As seções atendem às seguintes finalidades.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="7e7f5-121">A seção de inicializador define as condições iniciais.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="7e7f5-122">As instruções nesta seção são executadas apenas uma vez, antes de entrar no loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="7e7f5-123">A seção pode conter apenas uma das duas opções a seguir.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="7e7f5-124">A declaração e inicialização de uma variável de loop local, como mostrado no primeiro exemplo (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="7e7f5-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="7e7f5-125">A variável é local para o loop e não pode ser acessada de fora do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="7e7f5-126">Zero ou mais expressões de instrução da lista a seguir, separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="7e7f5-127">instrução de [atribuição](../../../csharp/language-reference/operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="7e7f5-128">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="7e7f5-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="7e7f5-129">prefixo ou sufixo da expressão [incrementar](../../../csharp/language-reference/operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="7e7f5-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="7e7f5-130">prefixo ou sufixo da expressão [decrementar](../../../csharp/language-reference/operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="7e7f5-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="7e7f5-131">criação de um objeto usando [new](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="7e7f5-132">expressão [await](../../../csharp/language-reference/keywords/await.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="7e7f5-133">A seção de condição contém uma expressão booliana que é avaliada para determinar se o loop deve sair ou deve ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="7e7f5-134">A seção de iterador define o que acontece depois de cada iteração do corpo do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="7e7f5-135">A seção de iterador contém zero ou mais das seguintes expressões de instrução, separadas por vírgulas:</span><span class="sxs-lookup"><span data-stu-id="7e7f5-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="7e7f5-136">instrução de [atribuição](../../../csharp/language-reference/operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="7e7f5-137">invocação de um método</span><span class="sxs-lookup"><span data-stu-id="7e7f5-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="7e7f5-138">prefixo ou sufixo da expressão [incrementar](../../../csharp/language-reference/operators/increment-operator.md), como `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="7e7f5-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="7e7f5-139">prefixo ou sufixo da expressão [decrementar](../../../csharp/language-reference/operators/decrement-operator.md), como `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="7e7f5-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="7e7f5-140">criação de um objeto usando [new](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="7e7f5-141">expressão [await](../../../csharp/language-reference/keywords/await.md)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="7e7f5-142">O corpo do loop consiste em uma instrução, uma instrução vazia ou um bloco de instruções que você cria colocando zero ou mais instruções entre chaves.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="7e7f5-143">Você pode sair de um loop `for` usando a palavra-chave [break](../../../csharp/language-reference/keywords/break.md) ou você pode passar para a próxima iteração, usando a palavra-chave [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="7e7f5-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="7e7f5-144">Você também pode sair qualquer loop usando uma instrução [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="7e7f5-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="7e7f5-145">O primeiro exemplo neste tópico mostra o tipo mais comum de loop `for`, que faz as seguintes opções para as seções.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="7e7f5-146">O inicializador declara e inicializa uma variável de loop local `i`, que mantém uma contagem das iterações do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="7e7f5-147">A condição verifica o valor da variável de loop em relação a um valor final conhecido, 5.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="7e7f5-148">A seção de iterador usa uma instrução de incremento de sufixo, `i++`, para calcular cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="7e7f5-149">O exemplo a seguir ilustra várias opções menos comuns: atribuir um valor a uma variável de loop externa na seção inicializador, invocar o método `Console.WriteLine` nas seções de inicializador e de iterador e alterar os valores de duas variáveis na seção de iterador.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="7e7f5-150">Todas as expressões que definem um instrução `for` são opcionais.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="7e7f5-151">Por exemplo, a instrução a seguir cria um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="7e7f5-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7e7f5-152">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7e7f5-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e7f5-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e7f5-153">See Also</span></span>  
 [<span data-ttu-id="7e7f5-154">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7e7f5-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7e7f5-155">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7e7f5-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7e7f5-156">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7e7f5-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7e7f5-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="7e7f5-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="7e7f5-158">Instrução for (C++)</span><span class="sxs-lookup"><span data-stu-id="7e7f5-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="7e7f5-159">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="7e7f5-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
