---
title: "Início rápido - ramificações e lops - guia c#"
description: "Este guia rápido sobre loops e ramificações, você escreve o código c# para explorar a sintaxe de linguagem que dá suporte a ramificações condicionais e loops para executar instruções repetidamente."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a><span data-ttu-id="c5867-103">Loops e branches</span><span class="sxs-lookup"><span data-stu-id="c5867-103">Branches and loops</span></span>

<span data-ttu-id="c5867-104">Este guia rápido ensina como escrever código que examina a variáveis e altera o caminho de execução com base nessas variáveis.</span><span class="sxs-lookup"><span data-stu-id="c5867-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="c5867-105">Escrever código c# e ver os resultados da compilação e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="c5867-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="c5867-106">O início rápido contém uma série de lições que exploram ramificação e construções de loop em c#.</span><span class="sxs-lookup"><span data-stu-id="c5867-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="c5867-107">Estas lições ensinam os princípios básicos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="c5867-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="c5867-108">Este guia rápido espera que você tem uma máquina que você pode usar para o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c5867-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="c5867-109">O tópico .NET [começar em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="c5867-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="c5867-110">Decisões usando o `if` instrução</span><span class="sxs-lookup"><span data-stu-id="c5867-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="c5867-111">Crie um diretório chamado **ramificações quickstart**.</span><span class="sxs-lookup"><span data-stu-id="c5867-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="c5867-112">Torne-o o diretório atual e execute `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="c5867-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="c5867-113">Este comando cria um novo aplicativo de console .NET Core no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c5867-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="c5867-114">Abra **Program.cs** em seu editor favorito e substitua a linha `Console.Writeline("Hello World!");` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5867-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="c5867-115">Tente este código digitando `dotnet run` na sua janela do console.</span><span class="sxs-lookup"><span data-stu-id="c5867-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="c5867-116">Você deve ver a mensagem "a resposta é maior que 10".</span><span class="sxs-lookup"><span data-stu-id="c5867-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="c5867-117">impressa no console.</span><span class="sxs-lookup"><span data-stu-id="c5867-117">printed to your console.</span></span>

<span data-ttu-id="c5867-118">Modifique a declaração de `b` para que a soma seja inferior a 10:</span><span class="sxs-lookup"><span data-stu-id="c5867-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="c5867-119">Tipo `dotnet run` novamente.</span><span class="sxs-lookup"><span data-stu-id="c5867-119">Type `dotnet run` again.</span></span> <span data-ttu-id="c5867-120">Como a resposta é inferior a 10, nada é impresso.</span><span class="sxs-lookup"><span data-stu-id="c5867-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="c5867-121">A **condição** que você está testando é falsa.</span><span class="sxs-lookup"><span data-stu-id="c5867-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="c5867-122">Não há qualquer código para execução, porque você escreveu apenas uma das ramificações possíveis para uma instrução `if`: a ramificação verdadeira.</span><span class="sxs-lookup"><span data-stu-id="c5867-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="c5867-123">À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código.</span><span class="sxs-lookup"><span data-stu-id="c5867-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="c5867-124">O compilador encontrará e relatar os erros.</span><span class="sxs-lookup"><span data-stu-id="c5867-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="c5867-125">Verifique atentamente a saída de erro e o código que gerou o erro.</span><span class="sxs-lookup"><span data-stu-id="c5867-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="c5867-126">O erro do compilador geralmente pode ajudá-lo a localizar o problema.</span><span class="sxs-lookup"><span data-stu-id="c5867-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="c5867-127">Este primeiro exemplo mostra o poder do `if` e tipos boolianos.</span><span class="sxs-lookup"><span data-stu-id="c5867-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="c5867-128">Um *booliano* é uma variável que pode ter um dos dois valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="c5867-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="c5867-129">C# define um tipo especial, `bool` para variáveis Boolean.</span><span class="sxs-lookup"><span data-stu-id="c5867-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="c5867-130">A instrução `if` verifica o valor de um `bool`.</span><span class="sxs-lookup"><span data-stu-id="c5867-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="c5867-131">Quando o valor é `true`, a instrução após `if` é executada.</span><span class="sxs-lookup"><span data-stu-id="c5867-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="c5867-132">Caso contrário, é ignorada.</span><span class="sxs-lookup"><span data-stu-id="c5867-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="c5867-133">Esse processo de verificação de condições e execução de instruções com base nessas condições é muito eficiente.</span><span class="sxs-lookup"><span data-stu-id="c5867-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="c5867-134">Faça if e else funcionam juntas</span><span class="sxs-lookup"><span data-stu-id="c5867-134">Make if and else work together</span></span>

<span data-ttu-id="c5867-135">Para executar um código diferente nos branches true e false, crie um branch `else` que será executado quando a condição for false.</span><span class="sxs-lookup"><span data-stu-id="c5867-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="c5867-136">Tente fazer isso.</span><span class="sxs-lookup"><span data-stu-id="c5867-136">Try this.</span></span> <span data-ttu-id="c5867-137">Adicione as duas últimas linhas no código abaixo para o `Main` método (você já deve ter os quatro primeiros):</span><span class="sxs-lookup"><span data-stu-id="c5867-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="c5867-138">A instrução após a palavra-chave `else` é executada somente quando a condição que estiver sendo testada for `false`.</span><span class="sxs-lookup"><span data-stu-id="c5867-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="c5867-139">Combinando `if` e `else` com booliano condições fornece todos os recursos que você precisa lidar com ambos um `true` e um `false` condição.</span><span class="sxs-lookup"><span data-stu-id="c5867-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5867-140">O recuo sob as instruções `if` e `else` é para leitores humanos.</span><span class="sxs-lookup"><span data-stu-id="c5867-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="c5867-141">A linguagem C# não considera recuo ou espaço em branco como significativo.</span><span class="sxs-lookup"><span data-stu-id="c5867-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="c5867-142">A instrução após a palavra-chave `if` ou `else` será executada com base na condição.</span><span class="sxs-lookup"><span data-stu-id="c5867-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="c5867-143">Todos os exemplos neste guia rápido siga a prática comum para recuar as linhas com base em fluxo de controle de instruções.</span><span class="sxs-lookup"><span data-stu-id="c5867-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="c5867-144">Como o recuo não é significativo, você precisa usar `{` e `}` para indicar quando você quer que mais de uma instrução faça parte do bloco executado condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="c5867-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="c5867-145">Os programadores em C# normalmente usam essas chaves em todas as cláusulas `if` e `else`.</span><span class="sxs-lookup"><span data-stu-id="c5867-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="c5867-146">O exemplo a seguir é o mesmo que você acabou de criar.</span><span class="sxs-lookup"><span data-stu-id="c5867-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="c5867-147">Modifique o código acima para coincidir com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5867-147">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="c5867-148">O restante deste início rápido, todos os exemplos de código incluem as chaves a seguir aceita práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="c5867-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="c5867-149">Você pode testar condições mais complicadas.</span><span class="sxs-lookup"><span data-stu-id="c5867-149">You can test more complicated conditions.</span></span> <span data-ttu-id="c5867-150">Adicione o seguinte código no seu `Main` método após o código que você escreveu até agora:</span><span class="sxs-lookup"><span data-stu-id="c5867-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="c5867-151">O `&&` representa "e".</span><span class="sxs-lookup"><span data-stu-id="c5867-151">The `&&` represents "and".</span></span> <span data-ttu-id="c5867-152">Isso significa que as duas condições devem ser verdadeiras para executar a instrução no branch verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="c5867-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="c5867-153">Estes exemplos também mostram que você pode ter várias instruções em cada branch condicional, desde que você coloque-as entre `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="c5867-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="c5867-154">Você também pode usar `||` representar "ou".</span><span class="sxs-lookup"><span data-stu-id="c5867-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="c5867-155">Adicione o seguinte código após o que você escreveu até agora:</span><span class="sxs-lookup"><span data-stu-id="c5867-155">Add the following code after what you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="c5867-156">Você terminou a primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="c5867-156">You've finished the first step.</span></span> <span data-ttu-id="c5867-157">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="c5867-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="c5867-158">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="c5867-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="c5867-159">Renomeie seu método `Main` como `ExploreIf` e escreva um novo método `Main` que chama `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="c5867-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="c5867-160">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="c5867-160">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="c5867-161">Comente a chamada para `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="c5867-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="c5867-162">Fazer a saída que menor congestionado enquanto você trabalha nesta seção:</span><span class="sxs-lookup"><span data-stu-id="c5867-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="c5867-163">O `//` inicia um **comentário** em c#.</span><span class="sxs-lookup"><span data-stu-id="c5867-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="c5867-164">Os comentários são qualquer texto que você deseja manter em seu código-fonte, mas não executado como código.</span><span class="sxs-lookup"><span data-stu-id="c5867-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="c5867-165">O compilador não gera nenhum código executável de comentários.</span><span class="sxs-lookup"><span data-stu-id="c5867-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="c5867-166">Use loops para repetir operações</span><span class="sxs-lookup"><span data-stu-id="c5867-166">Use loops to repeat operations</span></span>

<span data-ttu-id="c5867-167">Nesta seção você usar **loops** repetir as instruções.</span><span class="sxs-lookup"><span data-stu-id="c5867-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="c5867-168">Tente este código em seu `Main` método:</span><span class="sxs-lookup"><span data-stu-id="c5867-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="c5867-169">O `while` instrução verifica uma condição e executa a instrução ou bloco de instruções a seguir o `while`.</span><span class="sxs-lookup"><span data-stu-id="c5867-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="c5867-170">Repetidamente, ele verifica a condição e executar as instruções até que a condição for falsa.</span><span class="sxs-lookup"><span data-stu-id="c5867-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="c5867-171">Há outro operador novo neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="c5867-171">There's one other new operator in this example.</span></span> <span data-ttu-id="c5867-172">O `++` após a variável `counter` é o operador **increment**.</span><span class="sxs-lookup"><span data-stu-id="c5867-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="c5867-173">Ele adiciona 1 para o valor de `counter` e armazena esse valor no `counter` variável.</span><span class="sxs-lookup"><span data-stu-id="c5867-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5867-174">Verifique se o `while` loop alterações condição falsa ao executar o código.</span><span class="sxs-lookup"><span data-stu-id="c5867-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="c5867-175">Caso contrário, crie um **loop infinito**, para que seu programa nunca termine.</span><span class="sxs-lookup"><span data-stu-id="c5867-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="c5867-176">Que não será demonstrada neste exemplo, porque você tem que forçar o programa a encerrar o **CTRL-C** ou outros meios.</span><span class="sxs-lookup"><span data-stu-id="c5867-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="c5867-177">O loop `while` testa a condição antes de executar o código seguindo `while`.</span><span class="sxs-lookup"><span data-stu-id="c5867-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="c5867-178">O loop `do` ... `while` executa o código primeiro e, em seguida, verifica a condição.</span><span class="sxs-lookup"><span data-stu-id="c5867-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="c5867-179">A não enquanto o loop é mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c5867-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="c5867-180">Isso `do` loop e a anterior `while` loop produzem a mesma saída.</span><span class="sxs-lookup"><span data-stu-id="c5867-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="c5867-181">Trabalhar com o loop for</span><span class="sxs-lookup"><span data-stu-id="c5867-181">Work with the for loop</span></span>

<span data-ttu-id="c5867-182">O **para** loop é usado normalmente em c#.</span><span class="sxs-lookup"><span data-stu-id="c5867-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="c5867-183">Tente este código no método Main ():</span><span class="sxs-lookup"><span data-stu-id="c5867-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="c5867-184">Ele faz o mesmo trabalho que o loop `while` e o loop `do` que você já usou.</span><span class="sxs-lookup"><span data-stu-id="c5867-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="c5867-185">A instrução `for` tem três partes que controlam o modo como ela funciona.</span><span class="sxs-lookup"><span data-stu-id="c5867-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="c5867-186">A primeira parte é o **inicializador for**: `for index = 0;` declara que `index` é a variável do loop, e define seu valor inicial como `0`.</span><span class="sxs-lookup"><span data-stu-id="c5867-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="c5867-187">A parte central é a **condição for**: `index < 10` declara que este loop `for` continuará sendo executado desde que o valor do contador seja inferior a 10.</span><span class="sxs-lookup"><span data-stu-id="c5867-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="c5867-188">A parte final é o **iterador for**: `index++` especifica como modificar a variável de loop depois de executar o bloco após a instrução `for`.</span><span class="sxs-lookup"><span data-stu-id="c5867-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="c5867-189">Aqui, ela especifica que `index` deve ser incrementado com 1 sempre que o bloco for executado.</span><span class="sxs-lookup"><span data-stu-id="c5867-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="c5867-190">Experimente você mesmo.</span><span class="sxs-lookup"><span data-stu-id="c5867-190">Experiment with these yourself.</span></span> <span data-ttu-id="c5867-191">Tente o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c5867-191">Try each of the following:</span></span>

- <span data-ttu-id="c5867-192">Altere o inicializador para iniciar em um valor diferente.</span><span class="sxs-lookup"><span data-stu-id="c5867-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="c5867-193">Altere a condição para parar em um valor diferente.</span><span class="sxs-lookup"><span data-stu-id="c5867-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="c5867-194">Quando terminar, vamos escrever um código para usar o que você aprendeu.</span><span class="sxs-lookup"><span data-stu-id="c5867-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="c5867-195">Combinar loops e ramificações</span><span class="sxs-lookup"><span data-stu-id="c5867-195">Combine branches and loops</span></span>

<span data-ttu-id="c5867-196">Agora que você viu a instrução `if` e as construções de loop na linguagem C#, verifique se você pode escrever o código C# para encontrar a soma de todos os inteiros de 1 a 20 divisíveis por 3.</span><span class="sxs-lookup"><span data-stu-id="c5867-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="c5867-197">Veja algumas dicas:</span><span class="sxs-lookup"><span data-stu-id="c5867-197">Here are a few hints:</span></span>

- <span data-ttu-id="c5867-198">O operador `%` retorna o restante de uma operação de divisão.</span><span class="sxs-lookup"><span data-stu-id="c5867-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="c5867-199">O `if` instrução lhe dá a condição para ver se um número deve ser parte da soma.</span><span class="sxs-lookup"><span data-stu-id="c5867-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="c5867-200">O loop `for` pode ajudar você a repetir uma série de etapas para todos os números de 1 a 20.</span><span class="sxs-lookup"><span data-stu-id="c5867-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="c5867-201">Tente você mesmo.</span><span class="sxs-lookup"><span data-stu-id="c5867-201">Try it yourself.</span></span> <span data-ttu-id="c5867-202">Depois verifique como você fez.</span><span class="sxs-lookup"><span data-stu-id="c5867-202">Then check how you did.</span></span> <span data-ttu-id="c5867-203">Você pode ver uma resposta possível por [exibindo o código completo no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="c5867-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="c5867-204">Você concluiu o início rápido "ramificações e loops".</span><span class="sxs-lookup"><span data-stu-id="c5867-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="c5867-205">Você pode continuar com a [matrizes e coleções](arrays-and-collections.md) início rápido em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="c5867-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="c5867-206">Saiba mais sobre esses conceitos nestes tópicos:</span><span class="sxs-lookup"><span data-stu-id="c5867-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="c5867-207">[Instrução If e else](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="c5867-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="c5867-208">[Instrução while](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="c5867-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="c5867-209">[Instrução Do](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="c5867-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="c5867-210">Instrução for</span><span class="sxs-lookup"><span data-stu-id="c5867-210">For statement</span></span>](../language-reference/keywords/for.md)   
