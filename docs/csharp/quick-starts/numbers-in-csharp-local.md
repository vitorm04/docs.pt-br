---
title: "Guia de início rápido - números em c# - c#"
description: "Aprenda c# explorando métodos, propriedades e tipos numéricos."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a><span data-ttu-id="7bd36-103">Números de início rápido do c#</span><span class="sxs-lookup"><span data-stu-id="7bd36-103">Numbers in C# quick start</span></span> #

<span data-ttu-id="7bd36-104">Este guia rápido ensina sobre os tipos de número em c# interativamente.</span><span class="sxs-lookup"><span data-stu-id="7bd36-104">This quick start teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="7bd36-105">Você escreverá pequenas quantidades de código, em seguida, você compilar e executar esse código.</span><span class="sxs-lookup"><span data-stu-id="7bd36-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="7bd36-106">O início rápido contém uma série de lições que exploram números e operações matemáticas em c#.</span><span class="sxs-lookup"><span data-stu-id="7bd36-106">The quick start contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="7bd36-107">Estas lições ensinam os princípios básicos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="7bd36-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="7bd36-108">Este guia rápido espera que você tem uma máquina que você pode usar para o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7bd36-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="7bd36-109">O tópico .NET [começar em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="7bd36-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="7bd36-110">Explorar a matemática de inteiros</span><span class="sxs-lookup"><span data-stu-id="7bd36-110">Explore integer math</span></span>

<span data-ttu-id="7bd36-111">Crie um diretório chamado **quickstart números**.</span><span class="sxs-lookup"><span data-stu-id="7bd36-111">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="7bd36-112">Torne-o o diretório atual e execute `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-112">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="7bd36-113">Abra **Program.cs** em seu editor favorito e substitua a linha `Console.Writeline("Hello World!");` com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7bd36-113">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="7bd36-114">Execute este código digitando `dotnet run` na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="7bd36-114">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="7bd36-115">Você viu apenas uma das operações matemáticas fundamentais com números inteiros.</span><span class="sxs-lookup"><span data-stu-id="7bd36-115">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="7bd36-116">O tipo `int` representa um **inteiro**, um número inteiro positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="7bd36-116">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="7bd36-117">Você usa o símbolo `+` para adição.</span><span class="sxs-lookup"><span data-stu-id="7bd36-117">You use the `+` symbol for addition.</span></span> <span data-ttu-id="7bd36-118">Outras operações matemáticas comuns para inteiros incluem:</span><span class="sxs-lookup"><span data-stu-id="7bd36-118">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="7bd36-119">`-` para subtração</span><span class="sxs-lookup"><span data-stu-id="7bd36-119">`-` for subtraction</span></span>
- <span data-ttu-id="7bd36-120">`*` para multiplicação</span><span class="sxs-lookup"><span data-stu-id="7bd36-120">`*` for multiplication</span></span>
- <span data-ttu-id="7bd36-121">`/` para divisão</span><span class="sxs-lookup"><span data-stu-id="7bd36-121">`/` for division</span></span>

<span data-ttu-id="7bd36-122">Comece explorando essas diferentes operações.</span><span class="sxs-lookup"><span data-stu-id="7bd36-122">Start by exploring those different operations.</span></span> <span data-ttu-id="7bd36-123">Adicione estas linhas após a linha que grava o valor de `c`:</span><span class="sxs-lookup"><span data-stu-id="7bd36-123">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="7bd36-124">Execute este código digitando `dotnet run` na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="7bd36-124">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="7bd36-125">Você também pode experimentar, executando várias operações matemáticas na mesma linha, se quiser.</span><span class="sxs-lookup"><span data-stu-id="7bd36-125">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="7bd36-126">Tente `c = a + b - 12 * 17;` por exemplo.</span><span class="sxs-lookup"><span data-stu-id="7bd36-126">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="7bd36-127">É permitido misturar variáveis e constantes números.</span><span class="sxs-lookup"><span data-stu-id="7bd36-127">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="7bd36-128">À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código.</span><span class="sxs-lookup"><span data-stu-id="7bd36-128">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="7bd36-129">O **compilador** encontrará esses erros e os reportará a você.</span><span class="sxs-lookup"><span data-stu-id="7bd36-129">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="7bd36-130">Quando a saída contém mensagens de erro, Verifique atentamente o código de exemplo e código na sua janela para ver o que deve ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="7bd36-130">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="7bd36-131">Esse exercício ajudará você a conhecer a estrutura do código C#.</span><span class="sxs-lookup"><span data-stu-id="7bd36-131">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="7bd36-132">Você terminou a primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="7bd36-132">You've finished the first step.</span></span> <span data-ttu-id="7bd36-133">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="7bd36-133">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="7bd36-134">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="7bd36-134">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="7bd36-135">Renomeie seu método `Main` como `WorkingWithIntegers` e escreva um novo método `Main` que chama `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-135">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="7bd36-136">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="7bd36-136">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="7bd36-137">Explorar a ordem das operações</span><span class="sxs-lookup"><span data-stu-id="7bd36-137">Explore order of operations</span></span>

<span data-ttu-id="7bd36-138">Comente a chamada para `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-138">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="7bd36-139">Fazer a saída que menor congestionado enquanto você trabalha nesta seção:</span><span class="sxs-lookup"><span data-stu-id="7bd36-139">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="7bd36-140">O `//` inicia um **comentário** em c#.</span><span class="sxs-lookup"><span data-stu-id="7bd36-140">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="7bd36-141">Os comentários são qualquer texto que você deseja manter em seu código-fonte, mas não executado como código.</span><span class="sxs-lookup"><span data-stu-id="7bd36-141">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="7bd36-142">O compilador não gera nenhum código executável de comentários.</span><span class="sxs-lookup"><span data-stu-id="7bd36-142">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="7bd36-143">A linguagem C# define a precedência de operações matemáticas diferentes com regras consistentes às regras que você aprendeu em matemática.</span><span class="sxs-lookup"><span data-stu-id="7bd36-143">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="7bd36-144">Multiplicação e divisão têm precedência sobre adição e subtração.</span><span class="sxs-lookup"><span data-stu-id="7bd36-144">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="7bd36-145">Explorar isso adicionando o seguinte código ao seu `Main` método e execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="7bd36-145">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="7bd36-146">A saída demonstra que a multiplicação é executada antes da adição.</span><span class="sxs-lookup"><span data-stu-id="7bd36-146">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="7bd36-147">Você pode forçar uma ordem diferente da operação adicionando parênteses delimitando a operação ou operações executadas em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="7bd36-147">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="7bd36-148">Adicione as linhas a seguir e execute novamente:</span><span class="sxs-lookup"><span data-stu-id="7bd36-148">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="7bd36-149">Explore mais, combinando várias operações diferentes.</span><span class="sxs-lookup"><span data-stu-id="7bd36-149">Explore more by combining many different operations.</span></span> <span data-ttu-id="7bd36-150">Adicionar algo parecido com as seguintes linhas na parte inferior da sua `Main` método.</span><span class="sxs-lookup"><span data-stu-id="7bd36-150">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="7bd36-151">Tente `dotnet run` novamente.</span><span class="sxs-lookup"><span data-stu-id="7bd36-151">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="7bd36-152">Talvez você tenha observado um comportamento interessante com relação aos números inteiros.</span><span class="sxs-lookup"><span data-stu-id="7bd36-152">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="7bd36-153">Divisão sempre produz um resultado de inteiro, mesmo quando o resultado para incluir uma parte decimal ou fracionária esperado.</span><span class="sxs-lookup"><span data-stu-id="7bd36-153">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="7bd36-154">Se você ainda não o fez esse comportamento, tente o seguinte código ao final de sua `Main` método:</span><span class="sxs-lookup"><span data-stu-id="7bd36-154">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="7bd36-155">Tipo `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="7bd36-155">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="7bd36-156">Antes de avançarmos, vamos todo o código que você escreveu nesta seção e colocá-la em um novo método.</span><span class="sxs-lookup"><span data-stu-id="7bd36-156">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="7bd36-157">Chame esse novo método `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-157">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="7bd36-158">Você deve terminar com algo assim:</span><span class="sxs-lookup"><span data-stu-id="7bd36-158">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="7bd36-159">Explorar a precisão de inteiros e limites</span><span class="sxs-lookup"><span data-stu-id="7bd36-159">Explore integer precision and limits</span></span>
<span data-ttu-id="7bd36-160">Esse último exemplo mostrou que uma divisão de inteiros trunca o resultado.</span><span class="sxs-lookup"><span data-stu-id="7bd36-160">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="7bd36-161">Você pode obter o **restante** usando o **módulo** operador, o `%` caracteres.</span><span class="sxs-lookup"><span data-stu-id="7bd36-161">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="7bd36-162">Tente o seguinte código no seu `Main` método:</span><span class="sxs-lookup"><span data-stu-id="7bd36-162">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="7bd36-163">O tipo de inteiro C# difere do inteiros matemáticos de outra forma: o tipo `int` tem limites mínimo e máximo.</span><span class="sxs-lookup"><span data-stu-id="7bd36-163">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="7bd36-164">Adicione este código ao seu `Main` método para ver esses limites:</span><span class="sxs-lookup"><span data-stu-id="7bd36-164">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="7bd36-165">Se um cálculo produzir um valor que excede esses limites, você terá uma condição de **estouro negativo** ou **estouro**.</span><span class="sxs-lookup"><span data-stu-id="7bd36-165">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="7bd36-166">A resposta parece quebrar de um limite para o outro.</span><span class="sxs-lookup"><span data-stu-id="7bd36-166">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="7bd36-167">Adicione estas duas linhas para sua `Main` método para ver um exemplo:</span><span class="sxs-lookup"><span data-stu-id="7bd36-167">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="7bd36-168">Observe que a resposta é muito próxima do mínimo inteiro (negativo).</span><span class="sxs-lookup"><span data-stu-id="7bd36-168">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="7bd36-169">É o mesmo que `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-169">It's the same as `min + 2`.</span></span> <span data-ttu-id="7bd36-170">A operação de adição **estourou** os valores permitidos para números inteiros.</span><span class="sxs-lookup"><span data-stu-id="7bd36-170">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="7bd36-171">A resposta é um número negativo muito grande, pois um estouro "envolve" do maior valor de inteiro possível para o menor.</span><span class="sxs-lookup"><span data-stu-id="7bd36-171">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="7bd36-172">Há outros tipos numéricos com limites e precisão diferentes que você usaria quando o tipo `int` não atendesse às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="7bd36-172">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="7bd36-173">Vamos explorá-los na sequência.</span><span class="sxs-lookup"><span data-stu-id="7bd36-173">Let's explore those next.</span></span>

<span data-ttu-id="7bd36-174">Novamente, vamos passar o código que você escreveu nesta seção para um método separado.</span><span class="sxs-lookup"><span data-stu-id="7bd36-174">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="7bd36-175">Nomeie-o `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-175">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="7bd36-176">Trabalhar com o tipo Double</span><span class="sxs-lookup"><span data-stu-id="7bd36-176">Work with the double type</span></span>

<span data-ttu-id="7bd36-177">O tipo numérico `double` representa um número de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="7bd36-177">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="7bd36-178">Esses termos podem ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="7bd36-178">Those terms may be new to you.</span></span> <span data-ttu-id="7bd36-179">Um **ponto flutuante** número é útil para representar números integral não podem ser muito grande ou pequeno em magnitude.</span><span class="sxs-lookup"><span data-stu-id="7bd36-179">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="7bd36-180">**Precisão dupla** significa que esses números são armazenados usando uma precisão maior do que a **precisão única**.</span><span class="sxs-lookup"><span data-stu-id="7bd36-180">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="7bd36-181">Em computadores modernos, é mais comum usar precisão dupla que números de precisão única.</span><span class="sxs-lookup"><span data-stu-id="7bd36-181">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="7bd36-182">Vamos explorar.</span><span class="sxs-lookup"><span data-stu-id="7bd36-182">Let's explore.</span></span> <span data-ttu-id="7bd36-183">Adicione o seguinte código e veja o resultado:</span><span class="sxs-lookup"><span data-stu-id="7bd36-183">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="7bd36-184">Observe que a resposta inclui a parte decimal do quociente.</span><span class="sxs-lookup"><span data-stu-id="7bd36-184">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="7bd36-185">Experimente uma expressão ligeiramente mais complicada com duplos:</span><span class="sxs-lookup"><span data-stu-id="7bd36-185">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="7bd36-186">O intervalo de um valor duplo é muito maior do que valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="7bd36-186">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="7bd36-187">Tente o seguinte código abaixo o que você escreveu até agora:</span><span class="sxs-lookup"><span data-stu-id="7bd36-187">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="7bd36-188">Esses valores são impresso em notação científica.</span><span class="sxs-lookup"><span data-stu-id="7bd36-188">These values are printed out in scientific notation.</span></span> <span data-ttu-id="7bd36-189">O número à esquerda do `E` é o significando.</span><span class="sxs-lookup"><span data-stu-id="7bd36-189">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="7bd36-190">O número à direita é o expoente, como uma potência de 10.</span><span class="sxs-lookup"><span data-stu-id="7bd36-190">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="7bd36-191">Assim como os números decimais em matemática, os duplos em C# podem ter erros de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="7bd36-191">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="7bd36-192">Experimente esse código:</span><span class="sxs-lookup"><span data-stu-id="7bd36-192">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="7bd36-193">Você sabe que a repetição de `0.3` não é exatamente o mesmo que `1/3`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-193">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="7bd36-194">***Desafio***</span><span class="sxs-lookup"><span data-stu-id="7bd36-194">***Challenge***</span></span>

<span data-ttu-id="7bd36-195">Experimente outros cálculos com números grandes, números pequenos, multiplicação e divisão usando o tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-195">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="7bd36-196">Experimente cálculos mais complicados.</span><span class="sxs-lookup"><span data-stu-id="7bd36-196">Try more complicated calculations.</span></span>

<span data-ttu-id="7bd36-197">Depois que você tenha alguma experiência com o desafio, levar o código já gravado e colocá-lo em um novo método.</span><span class="sxs-lookup"><span data-stu-id="7bd36-197">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="7bd36-198">Nomeie esse novo método `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-198">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="7bd36-199">Trabalhar com tipos de ponto fixo</span><span class="sxs-lookup"><span data-stu-id="7bd36-199">Work with fixed point types</span></span>

<span data-ttu-id="7bd36-200">Você viu os tipos numéricos básicos em C#: inteiros e duplos.</span><span class="sxs-lookup"><span data-stu-id="7bd36-200">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="7bd36-201">Ainda há outro tipo : o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-201">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="7bd36-202">O `decimal` tipo tem um intervalo menor mas maior precisão que `double`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-202">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="7bd36-203">O termo **ponto fixo** significa que a virgula decimal (ou ponto binário) não muda.</span><span class="sxs-lookup"><span data-stu-id="7bd36-203">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="7bd36-204">Vamos analisar:</span><span class="sxs-lookup"><span data-stu-id="7bd36-204">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="7bd36-205">Observe que o intervalo é menor do que o tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-205">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="7bd36-206">Veja a precisão maior com o tipo decimal experimentando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7bd36-206">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="7bd36-207">O sufixo `M` nos números é o modo como você indica que uma constante deve usar o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="7bd36-207">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="7bd36-208">Observe que o cálculo usando o tipo decimal tem mais dígitos à direita da vírgula decimal.</span><span class="sxs-lookup"><span data-stu-id="7bd36-208">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="7bd36-209">***Desafio***</span><span class="sxs-lookup"><span data-stu-id="7bd36-209">***Challenge***</span></span>

<span data-ttu-id="7bd36-210">Agora que você viu os diferentes tipos numéricos, escreva um código que calcula a área de um círculo cujo raio é de 2,50 polegadas.</span><span class="sxs-lookup"><span data-stu-id="7bd36-210">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 inches.</span></span> <span data-ttu-id="7bd36-211">Lembre-se de que a área de um círculo é o quadrado do raio multiplicado por PI.</span><span class="sxs-lookup"><span data-stu-id="7bd36-211">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="7bd36-212">Uma dica: c# contém uma constante de PI, <xref:System.Math.PI?displayProperty=nameWithType> que você pode usar para esse valor.</span><span class="sxs-lookup"><span data-stu-id="7bd36-212">One hint: C# contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="7bd36-213">Você pode verificar sua resposta por [olhando para o código de exemplo finalizado no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="7bd36-213">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="7bd36-214">Se desejar, tente algumas outras fórmulas.</span><span class="sxs-lookup"><span data-stu-id="7bd36-214">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="7bd36-215">Você concluiu o início rápido "números no c#".</span><span class="sxs-lookup"><span data-stu-id="7bd36-215">You've completed the "Numbers in C#" quick start.</span></span> <span data-ttu-id="7bd36-216">Você pode continuar com a [loops e ramificações](branches-and-loops-local.md) início rápido em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="7bd36-216">You can continue with the [Branches and loops](branches-and-loops-local.md) quick start in your own development environment.</span></span>

<span data-ttu-id="7bd36-217">Saiba mais sobre os números em C# nos tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="7bd36-217">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="7bd36-218">[Tabela de Tipos Integrais](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7bd36-218">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="7bd36-219">[Tabela de tipos de ponto flutuante](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7bd36-219">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="7bd36-220">[Tabela de Tipos Internos](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7bd36-220">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="7bd36-221">[Tabela de conversões numéricas implícitas](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="7bd36-221">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="7bd36-222">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="7bd36-222">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

