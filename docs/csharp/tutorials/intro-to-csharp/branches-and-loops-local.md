---
title: Tutorial Branches e loops – introdução ao C#
description: Neste tutorial sobre branches e loops, você escreve código em C# para explorar a sintaxe de linguagem que dá suporte a branches e loops condicionais para execução repetida de instruções.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d8c10a7462b7c27c5353aee6d957732a8d161015
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135939"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="73155-103">Saiba mais sobre lógica condicional com instruções branch e loop</span><span class="sxs-lookup"><span data-stu-id="73155-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="73155-104">Este tutorial ensina a escrever código que examina variáveis e muda o caminho de execução com base nessas variáveis.</span><span class="sxs-lookup"><span data-stu-id="73155-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="73155-105">Escreva o código em C# e veja os resultados da compilação e da execução.</span><span class="sxs-lookup"><span data-stu-id="73155-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="73155-106">O tutorial contém uma série de lições que exploram construções de branches e loops em C#.</span><span class="sxs-lookup"><span data-stu-id="73155-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="73155-107">Estas lições ensinam os princípios básicos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="73155-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="73155-108">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="73155-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="73155-109">O tutorial do .NET [Olá, mundo em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) tem instruções para configurar seu ambiente de desenvolvimento local no Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="73155-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="73155-110">Uma visão geral dos comandos que você usará está em [Familiarize-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="73155-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="73155-111">Tome decisões usando a instrução `if`</span><span class="sxs-lookup"><span data-stu-id="73155-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="73155-112">Crie um diretório chamado *branches-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="73155-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="73155-113">Faça com que o diretório atual e execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="73155-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="73155-114">Esse comando cria um novo aplicativo de console .NET Core no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="73155-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="73155-115">Abra *Program.cs* em seu editor favorito e substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="73155-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="73155-116">Experimente este código digitando `dotnet run` na sua janela do console.</span><span class="sxs-lookup"><span data-stu-id="73155-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="73155-117">Você deve ver a mensagem "A resposta é maior do que 10."</span><span class="sxs-lookup"><span data-stu-id="73155-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="73155-118">impressa no console.</span><span class="sxs-lookup"><span data-stu-id="73155-118">printed to your console.</span></span>

<span data-ttu-id="73155-119">Modifique a declaração de `b` para que a soma seja inferior a 10:</span><span class="sxs-lookup"><span data-stu-id="73155-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="73155-120">Digite `dotnet run` novamente.</span><span class="sxs-lookup"><span data-stu-id="73155-120">Type `dotnet run` again.</span></span> <span data-ttu-id="73155-121">Como a resposta é inferior a 10, nada é impresso.</span><span class="sxs-lookup"><span data-stu-id="73155-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="73155-122">A **condição** que você está testando é falsa.</span><span class="sxs-lookup"><span data-stu-id="73155-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="73155-123">Não há qualquer código para execução, porque você escreveu apenas uma das ramificações possíveis para uma instrução `if`: a ramificação verdadeira.</span><span class="sxs-lookup"><span data-stu-id="73155-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="73155-124">À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código.</span><span class="sxs-lookup"><span data-stu-id="73155-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="73155-125">O compilador encontrará e reportará esses erros.</span><span class="sxs-lookup"><span data-stu-id="73155-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="73155-126">Verifique atentamente a saída do erro e o código que gerou o erro.</span><span class="sxs-lookup"><span data-stu-id="73155-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="73155-127">O erro do compilador geralmente pode ajudá-lo a localizar o problema.</span><span class="sxs-lookup"><span data-stu-id="73155-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="73155-128">Este primeiro exemplo mostra o poder dos tipos `if` e Booliano.</span><span class="sxs-lookup"><span data-stu-id="73155-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="73155-129">Um *Booliano* é uma variável que pode ter um dos dois valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="73155-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="73155-130">C# define um tipo especial, `bool` para variáveis Boolianas.</span><span class="sxs-lookup"><span data-stu-id="73155-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="73155-131">A instrução `if` verifica o valor de um `bool`.</span><span class="sxs-lookup"><span data-stu-id="73155-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="73155-132">Quando o valor é `true`, a instrução após `if` é executada.</span><span class="sxs-lookup"><span data-stu-id="73155-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="73155-133">Caso contrário, é ignorada.</span><span class="sxs-lookup"><span data-stu-id="73155-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="73155-134">Esse processo de verificação de condições e execução de instruções com base nessas condições é muito eficiente.</span><span class="sxs-lookup"><span data-stu-id="73155-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="73155-135">Faça if e else funcionam juntas</span><span class="sxs-lookup"><span data-stu-id="73155-135">Make if and else work together</span></span>

<span data-ttu-id="73155-136">Para executar um código diferente nos branches true e false, crie um branch `else` que será executado quando a condição for false.</span><span class="sxs-lookup"><span data-stu-id="73155-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="73155-137">Experimente isto.</span><span class="sxs-lookup"><span data-stu-id="73155-137">Try this.</span></span> <span data-ttu-id="73155-138">Adicione as duas últimas linhas do código abaixo ao seu método `Main` (você já deve ter os quatro primeiros):</span><span class="sxs-lookup"><span data-stu-id="73155-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="73155-139">A instrução após a palavra-chave `else` é executada somente quando a condição que estiver sendo testada for `false`.</span><span class="sxs-lookup"><span data-stu-id="73155-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="73155-140">A combinação de `if` e `else` com condições Boolianas fornece todos os recursos que você precisa para lidar com uma condição `true` e `false`.</span><span class="sxs-lookup"><span data-stu-id="73155-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73155-141">O recuo sob as instruções `if` e `else` é para leitores humanos.</span><span class="sxs-lookup"><span data-stu-id="73155-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="73155-142">A linguagem C# não considera recuos ou espaços em branco como significativos.</span><span class="sxs-lookup"><span data-stu-id="73155-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="73155-143">A instrução após a palavra-chave `if` ou `else` será executada com base na condição.</span><span class="sxs-lookup"><span data-stu-id="73155-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="73155-144">Todos os exemplos neste tutorial seguem uma prática comum para recuar linhas com base no fluxo de controle de instruções.</span><span class="sxs-lookup"><span data-stu-id="73155-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="73155-145">Como o recuo não é significativo, você precisa usar `{` e `}` para indicar quando você quer que mais de uma instrução faça parte do bloco executado condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="73155-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="73155-146">Os programadores em C# normalmente usam essas chaves em todas as cláusulas `if` e `else`.</span><span class="sxs-lookup"><span data-stu-id="73155-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="73155-147">O exemplo a seguir é igual ao que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="73155-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="73155-148">Modifique o código acima para coincidir com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="73155-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="73155-149">No restante deste tutorial, todos os exemplos de código incluem as chaves, seguindo as práticas aceitas.</span><span class="sxs-lookup"><span data-stu-id="73155-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="73155-150">Você pode testar condições mais complicadas.</span><span class="sxs-lookup"><span data-stu-id="73155-150">You can test more complicated conditions.</span></span> <span data-ttu-id="73155-151">Adicione o seguinte código ao seu método `Main` após o código que você escreveu até agora:</span><span class="sxs-lookup"><span data-stu-id="73155-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="73155-152">O símbolo `==` testa a *igualdade*.</span><span class="sxs-lookup"><span data-stu-id="73155-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="73155-153">Usar `==` distingue o teste de igualdade de atribuição, que você viu em `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="73155-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="73155-154">O `&&` representa "e".</span><span class="sxs-lookup"><span data-stu-id="73155-154">The `&&` represents "and".</span></span> <span data-ttu-id="73155-155">Isso significa que as duas condições devem ser verdadeiras para executar a instrução no branch verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="73155-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="73155-156">Estes exemplos também mostram que você pode ter várias instruções em cada branch condicional, desde que você coloque-as entre `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="73155-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="73155-157">Você também pode usar `||` para representar "ou".</span><span class="sxs-lookup"><span data-stu-id="73155-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="73155-158">Adicione o código a seguir após o que você escreveu até o momento:</span><span class="sxs-lookup"><span data-stu-id="73155-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="73155-159">Modifique os valores de `a`, `b` e `c` e alterne entre `&&` e `||` para explorar.</span><span class="sxs-lookup"><span data-stu-id="73155-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="73155-160">Você obterá mais compreensão de como os operadores `&&` e `||` funcionam.</span><span class="sxs-lookup"><span data-stu-id="73155-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="73155-161">Você terminou a primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="73155-161">You've finished the first step.</span></span> <span data-ttu-id="73155-162">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="73155-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="73155-163">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="73155-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="73155-164">Renomeie seu método `Main` como `ExploreIf` e escreva um novo método `Main` que chama `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="73155-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="73155-165">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="73155-165">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="73155-166">Comente a chamada para `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="73155-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="73155-167">Isso tornará a saída menos congestionada enquanto você trabalha nesta seção:</span><span class="sxs-lookup"><span data-stu-id="73155-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="73155-168">O `//` inicia um **comentário** em C#.</span><span class="sxs-lookup"><span data-stu-id="73155-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="73155-169">Os comentários são qualquer texto que você queira manter em seu código-fonte, mas não queria executar como código.</span><span class="sxs-lookup"><span data-stu-id="73155-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="73155-170">O compilador não gera qualquer código executável a partir dos comentários.</span><span class="sxs-lookup"><span data-stu-id="73155-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="73155-171">Use loops para repetir operações</span><span class="sxs-lookup"><span data-stu-id="73155-171">Use loops to repeat operations</span></span>

<span data-ttu-id="73155-172">Nesta seção, você usa **loops** repetir as instruções.</span><span class="sxs-lookup"><span data-stu-id="73155-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="73155-173">Tente este código em seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="73155-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="73155-174">A instrução `while` verifica uma condição e executa a instrução, ou bloco de instruções, após o `while`.</span><span class="sxs-lookup"><span data-stu-id="73155-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="73155-175">Ela verifica repetidamente a condição e executa essas instruções até que a condição seja falsa.</span><span class="sxs-lookup"><span data-stu-id="73155-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="73155-176">Há outro operador novo neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="73155-176">There's one other new operator in this example.</span></span> <span data-ttu-id="73155-177">O `++` após a variável `counter` é o operador **increment**.</span><span class="sxs-lookup"><span data-stu-id="73155-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="73155-178">Ele adiciona 1 ao valor de `counter` e armazena esse valor na variável `counter`.</span><span class="sxs-lookup"><span data-stu-id="73155-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73155-179">Verifique se a condição de loop `while` muda para false ao executar o código.</span><span class="sxs-lookup"><span data-stu-id="73155-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="73155-180">Caso contrário, crie um **loop infinito**, para que seu programa nunca termine.</span><span class="sxs-lookup"><span data-stu-id="73155-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="73155-181">Isso não é demonstrado neste exemplo, porque você tem que forçar o programa a encerrar usando **CTRL-C** ou outros meios.</span><span class="sxs-lookup"><span data-stu-id="73155-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="73155-182">O loop `while` testa a condição antes de executar o código seguindo `while`.</span><span class="sxs-lookup"><span data-stu-id="73155-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="73155-183">O loop `do` ... `while` executa o código primeiro e, em seguida, verifica a condição.</span><span class="sxs-lookup"><span data-stu-id="73155-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="73155-184">O loop do while é mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="73155-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="73155-185">Esse loop `do` e o loop `while` anterior produzem a mesma saída.</span><span class="sxs-lookup"><span data-stu-id="73155-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="73155-186">Trabalhar com o loop for</span><span class="sxs-lookup"><span data-stu-id="73155-186">Work with the for loop</span></span>

<span data-ttu-id="73155-187">O loop **for** é usado normalmente em C#.</span><span class="sxs-lookup"><span data-stu-id="73155-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="73155-188">Tente este código em seu método Main():</span><span class="sxs-lookup"><span data-stu-id="73155-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="73155-189">Ele faz o mesmo trabalho que o loop `while` e o loop `do` que você já usou.</span><span class="sxs-lookup"><span data-stu-id="73155-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="73155-190">A instrução `for` tem três partes que controlam o modo como ela funciona.</span><span class="sxs-lookup"><span data-stu-id="73155-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="73155-191">A primeira parte é o **inicializador de para**: `int index = 0;` declara `index` que é a variável de loop e define seu valor inicial `0`como.</span><span class="sxs-lookup"><span data-stu-id="73155-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="73155-192">A parte intermediária é a **condição**for: `index < 10` declara que esse `for` loop continua a ser executado, desde que o valor do contador seja menor que 10.</span><span class="sxs-lookup"><span data-stu-id="73155-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="73155-193">A parte final é o **para iterador**: `index++` especifica como modificar a variável de loop depois de executar o bloco `for` após a instrução.</span><span class="sxs-lookup"><span data-stu-id="73155-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="73155-194">Aqui, ela especifica que `index` deve ser incrementado com 1 sempre que o bloco for executado.</span><span class="sxs-lookup"><span data-stu-id="73155-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="73155-195">Experimente você mesmo.</span><span class="sxs-lookup"><span data-stu-id="73155-195">Experiment with these yourself.</span></span> <span data-ttu-id="73155-196">Tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="73155-196">Try each of the following:</span></span>

- <span data-ttu-id="73155-197">Altere o inicializador para iniciar em um valor diferente.</span><span class="sxs-lookup"><span data-stu-id="73155-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="73155-198">Altere a condição para parar em um valor diferente.</span><span class="sxs-lookup"><span data-stu-id="73155-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="73155-199">Quando terminar, vamos escrever um código para usar o que você aprendeu.</span><span class="sxs-lookup"><span data-stu-id="73155-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="73155-200">Loops aninhados criados</span><span class="sxs-lookup"><span data-stu-id="73155-200">Created nested loops</span></span>

<span data-ttu-id="73155-201">Um `while`loop `do` , `for` ou pode ser aninhado dentro de outro loop para criar uma matriz usando a combinação de cada item no loop externo com cada item no loop interno.</span><span class="sxs-lookup"><span data-stu-id="73155-201">A `while`, `do` or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="73155-202">Vamos fazer isso para criar um conjunto de pares alfanuméricos para representar linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="73155-202">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="73155-203">Um `for` loop pode gerar as linhas:</span><span class="sxs-lookup"><span data-stu-id="73155-203">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="73155-204">Outro loop pode gerar as colunas:</span><span class="sxs-lookup"><span data-stu-id="73155-204">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="73155-205">Você pode aninhar um loop dentro do outro para formar pares:</span><span class="sxs-lookup"><span data-stu-id="73155-205">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="73155-206">Você pode ver que o loop externo é incrementado uma vez para cada execução completa do loop interno.</span><span class="sxs-lookup"><span data-stu-id="73155-206">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="73155-207">Inverta o aninhamento de linha e coluna e veja as alterações por conta própria.</span><span class="sxs-lookup"><span data-stu-id="73155-207">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="73155-208">Combinar branches e loops</span><span class="sxs-lookup"><span data-stu-id="73155-208">Combine branches and loops</span></span>

<span data-ttu-id="73155-209">Agora que você viu a instrução `if` e as construções de loop na linguagem C#, verifique se você pode escrever o código C# para encontrar a soma de todos os inteiros de 1 a 20 divisíveis por 3.</span><span class="sxs-lookup"><span data-stu-id="73155-209">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="73155-210">Veja algumas dicas:</span><span class="sxs-lookup"><span data-stu-id="73155-210">Here are a few hints:</span></span>

- <span data-ttu-id="73155-211">O operador `%` retorna o restante de uma operação de divisão.</span><span class="sxs-lookup"><span data-stu-id="73155-211">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="73155-212">A instrução `if` retorna a condição para ver se um número deve ser parte da soma.</span><span class="sxs-lookup"><span data-stu-id="73155-212">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="73155-213">O loop `for` pode ajudar você a repetir uma série de etapas para todos os números de 1 a 20.</span><span class="sxs-lookup"><span data-stu-id="73155-213">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="73155-214">Tente você mesmo.</span><span class="sxs-lookup"><span data-stu-id="73155-214">Try it yourself.</span></span> <span data-ttu-id="73155-215">Depois verifique como você fez.</span><span class="sxs-lookup"><span data-stu-id="73155-215">Then check how you did.</span></span> <span data-ttu-id="73155-216">Você deve obter 63 como resposta.</span><span class="sxs-lookup"><span data-stu-id="73155-216">You should get 63 for an answer.</span></span> <span data-ttu-id="73155-217">Veja uma resposta possível [exibindo o código completo no GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="73155-217">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="73155-218">Você concluiu o tutorial "branches e loops".</span><span class="sxs-lookup"><span data-stu-id="73155-218">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="73155-219">Continue com o tutorial [Matrizes e coleções](arrays-and-collections.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="73155-219">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="73155-220">Saiba mais sobre esses conceitos nestes tópicos:</span><span class="sxs-lookup"><span data-stu-id="73155-220">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="73155-221">Instrução if e else</span><span class="sxs-lookup"><span data-stu-id="73155-221">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="73155-222">Instrução while</span><span class="sxs-lookup"><span data-stu-id="73155-222">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="73155-223">Instrução do</span><span class="sxs-lookup"><span data-stu-id="73155-223">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="73155-224">Instrução for</span><span class="sxs-lookup"><span data-stu-id="73155-224">For statement</span></span>](../../language-reference/keywords/for.md)
