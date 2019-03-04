---
title: Tutorial Números em C# – introdução ao C#
description: Aprenda C# explorando tipos numéricos, suas propriedades e métodos.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 009c737297c331b1aa4dcad058ac6bfdf05ac037
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978612"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="fd8b7-103">Manipular números de ponto flutuante e integrais em C\#</span><span class="sxs-lookup"><span data-stu-id="fd8b7-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="fd8b7-104">Este tutorial ensina sobre os tipos numéricos em C# de maneira interativa.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="fd8b7-105">Você escreverá pequenas quantidades de código, depois compilará e executará esse código.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="fd8b7-106">O tutorial contém uma série de lições que exploram números e operações matemáticas em C#.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="fd8b7-107">Estas lições ensinam os princípios básicos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="fd8b7-108">Este tutorial espera que você tenha um computador que possa usar para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="fd8b7-109">O tópico do .NET [Familiarize-se em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="fd8b7-110">Uma visão geral dos comandos que você usará está em [Familiarize-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="fd8b7-111">Explorar a matemática de inteiros</span><span class="sxs-lookup"><span data-stu-id="fd8b7-111">Explore integer math</span></span>

<span data-ttu-id="fd8b7-112">Crie um diretório chamado **numbers-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="fd8b7-113">Torne-o o diretório atual e execute `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="fd8b7-114">Abra **Program.cs** em seu editor favorito e substitua a linha `Console.Writeline("Hello World!");` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="fd8b7-115">Execute este código digitando `dotnet run` na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="fd8b7-116">Você viu apenas uma das operações matemáticas fundamentais com números inteiros.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="fd8b7-117">O tipo `int` representa um **inteiro**, um número inteiro positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="fd8b7-118">Você usa o símbolo `+` para adição.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="fd8b7-119">Outras operações matemáticas comuns para inteiros incluem:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="fd8b7-120">`-` para subtração</span><span class="sxs-lookup"><span data-stu-id="fd8b7-120">`-` for subtraction</span></span>
- <span data-ttu-id="fd8b7-121">`*` para multiplicação</span><span class="sxs-lookup"><span data-stu-id="fd8b7-121">`*` for multiplication</span></span>
- <span data-ttu-id="fd8b7-122">`/` para divisão</span><span class="sxs-lookup"><span data-stu-id="fd8b7-122">`/` for division</span></span>

<span data-ttu-id="fd8b7-123">Comece explorando essas diferentes operações.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-123">Start by exploring those different operations.</span></span> <span data-ttu-id="fd8b7-124">Adicione estas linhas após a linha que grava o valor de `c`:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="fd8b7-125">Execute este código digitando `dotnet run` na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="fd8b7-126">Você também pode experimentar, executando várias operações matemáticas na mesma linha, se quiser.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="fd8b7-127">Experimente `c = a + b - 12 * 17;`, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="fd8b7-128">É permitido misturar variáveis e números constantes.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="fd8b7-129">À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="fd8b7-130">O **compilador** encontrará esses erros e os reportará a você.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="fd8b7-131">Quando a saída contiver mensagens de erro, analise atentamente o código de exemplo e o código em sua janela para ver o que deve ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="fd8b7-132">Esse exercício ajudará você a conhecer a estrutura do código C#.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="fd8b7-133">Você terminou a primeira etapa.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-133">You've finished the first step.</span></span> <span data-ttu-id="fd8b7-134">Antes de iniciar a próxima seção, vamos passar o código atual para um método separado.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="fd8b7-135">Isso facilita o começo do trabalho com um exemplo novo.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="fd8b7-136">Renomeie seu método `Main` como `WorkingWithIntegers` e escreva um novo método `Main` que chama `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="fd8b7-137">Quando você terminar, seu código deverá parecer com isto:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="fd8b7-138">Explorar a ordem das operações</span><span class="sxs-lookup"><span data-stu-id="fd8b7-138">Explore order of operations</span></span>

<span data-ttu-id="fd8b7-139">Comente a chamada para `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="fd8b7-140">Isso tornará a saída menos congestionada enquanto você trabalha nesta seção:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="fd8b7-141">O `//` inicia um **comentário** em C#.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="fd8b7-142">Os comentários são qualquer texto que você queira manter em seu código-fonte, mas não queria executar como código.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="fd8b7-143">O compilador não gera qualquer código executável a partir dos comentários.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="fd8b7-144">A linguagem C# define a precedência de operações matemáticas diferentes com regras consistentes às regras que você aprendeu em matemática.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="fd8b7-145">Multiplicação e divisão têm precedência sobre adição e subtração.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="fd8b7-146">Explore isso adicionando o seguinte código ao seu método `Main` e executando `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="fd8b7-147">A saída demonstra que a multiplicação é executada antes da adição.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="fd8b7-148">Você pode forçar uma ordem diferente de operações, adicionando parênteses para delimitar a operação, ou operações, que você quer realizar primeiro.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="fd8b7-149">Adicione as seguintes linhas e execute novamente:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="fd8b7-150">Explore mais, combinando várias operações diferentes.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="fd8b7-151">Adicione algo parecido com as seguintes linhas na parte inferior de seu método `Main`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="fd8b7-152">Tente `dotnet run` novamente.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="fd8b7-153">Talvez você tenha observado um comportamento interessante com relação aos números inteiros.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="fd8b7-154">A divisão de inteiros sempre produz um resultado inteiro, mesmo quando você espera que o resultado inclua uma parte decimal ou fracionária.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="fd8b7-155">Se você ainda não viu esse comportamento, tente o seguinte código ao final de seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="fd8b7-156">Digite `dotnet run` novamente para ver os resultados.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="fd8b7-157">Antes de avançarmos, pegue todo código que você escreveu nesta seção e coloque-o em um novo método.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="fd8b7-158">Chame esse novo método de `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="fd8b7-159">O resultado final será algo semelhante a isto:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="fd8b7-160">Explorar a precisão de inteiros e limites</span><span class="sxs-lookup"><span data-stu-id="fd8b7-160">Explore integer precision and limits</span></span>
<span data-ttu-id="fd8b7-161">Esse último exemplo mostrou que uma divisão de inteiros trunca o resultado.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="fd8b7-162">Você pode obter o **restante** usando o operador **module**, o caractere `%`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="fd8b7-163">Experimente o seguinte código em seu método `Main`:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="fd8b7-164">O tipo de inteiro C# difere do inteiros matemáticos de outra forma: o tipo `int` tem limites mínimo e máximo.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="fd8b7-165">Adicione este código ao seu método `Main` para ver esses limites:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="fd8b7-166">Se um cálculo produzir um valor que excede esses limites, você terá uma condição de **estouro negativo** ou **estouro**.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="fd8b7-167">A resposta parece quebrar de um limite para o outro.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="fd8b7-168">Adicione estas duas linhas ao seu método `Main` para ver um exemplo:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="fd8b7-169">Observe que a resposta é muito próxima do mínimo inteiro (negativo).</span><span class="sxs-lookup"><span data-stu-id="fd8b7-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="fd8b7-170">É o mesmo que `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="fd8b7-171">A operação de adição **estourou** os valores permitidos para números inteiros.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="fd8b7-172">A resposta é um número negativo muito grande, pois um estouro "envolve" do maior valor de inteiro possível para o menor.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="fd8b7-173">Há outros tipos numéricos com limites e precisão diferentes que você usaria quando o tipo `int` não atendesse às suas necessidades.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="fd8b7-174">Vamos explorá-los na sequência.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-174">Let's explore those next.</span></span>

<span data-ttu-id="fd8b7-175">Novamente, vamos passar o código que você escreveu nesta seção para um método separado.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="fd8b7-176">Nomeie-o como `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="fd8b7-177">Trabalhar com o tipo Double</span><span class="sxs-lookup"><span data-stu-id="fd8b7-177">Work with the double type</span></span>

<span data-ttu-id="fd8b7-178">O tipo numérico `double` representa um número de ponto flutuante de precisão dupla.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="fd8b7-179">Esses termos podem ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-179">Those terms may be new to you.</span></span> <span data-ttu-id="fd8b7-180">Um número de **ponto flutuante** é útil para representar números não integrais que podem ser muito grandes ou pequenos em magnitude.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="fd8b7-181">**Precisão dupla** significa que esses números são armazenados usando uma precisão maior do que a **precisão única**.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="fd8b7-182">Em computadores modernos, é mais comum usar precisão dupla que números de precisão única.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="fd8b7-183">Vamos explorar.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-183">Let's explore.</span></span> <span data-ttu-id="fd8b7-184">Adicione o seguinte código e veja o resultado:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="fd8b7-185">Observe que a resposta inclui a parte decimal do quociente.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="fd8b7-186">Experimente uma expressão ligeiramente mais complicada com duplos:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="fd8b7-187">O intervalo de um valor duplo é muito maior do que valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="fd8b7-188">Experimente o código a seguir abaixo do código que você escreveu até o momento:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="fd8b7-189">Esses valores são impressos em notação científica.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="fd8b7-190">O número à esquerda do `E` é o significando.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="fd8b7-191">O número à direita é o expoente, como uma potência de 10.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="fd8b7-192">Assim como os números decimais em matemática, os duplos em C# podem ter erros de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="fd8b7-193">Experimente esse código:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="fd8b7-194">Você sabe que a repetição de `0.3` não é exatamente o mesmo que `1/3`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="fd8b7-195">***Desafio***</span><span class="sxs-lookup"><span data-stu-id="fd8b7-195">***Challenge***</span></span>

<span data-ttu-id="fd8b7-196">Experimente outros cálculos com números grandes, números pequenos, multiplicação e divisão usando o tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="fd8b7-197">Experimente cálculos mais complicados.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-197">Try more complicated calculations.</span></span>

<span data-ttu-id="fd8b7-198">Após algum tempo no desafio, pegue o código que você escreveu e coloque-o em um novo método.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="fd8b7-199">Chame esse novo método de `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="fd8b7-200">Trabalhar com tipos de ponto fixo</span><span class="sxs-lookup"><span data-stu-id="fd8b7-200">Work with fixed point types</span></span>

<span data-ttu-id="fd8b7-201">Você viu os tipos numéricos básicos em C#: inteiros e duplos.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="fd8b7-202">Ainda há outro tipo : o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="fd8b7-203">O tipo `decimal` tem um intervalo menor, mas precisão maior do que `double`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="fd8b7-204">O termo **ponto fixo** significa que a virgula decimal (ou ponto binário) não muda.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="fd8b7-205">Vamos analisar:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="fd8b7-206">Observe que o intervalo é menor do que o tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="fd8b7-207">Veja a precisão maior com o tipo decimal experimentando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="fd8b7-208">O sufixo `M` nos números é o modo como você indica que uma constante deve usar o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="fd8b7-209">Observe que o cálculo usando o tipo decimal tem mais dígitos à direita da vírgula decimal.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="fd8b7-210">***Desafio***</span><span class="sxs-lookup"><span data-stu-id="fd8b7-210">***Challenge***</span></span>

<span data-ttu-id="fd8b7-211">Agora que você viu os diferentes tipos numéricos, escreva um código que calcula a área de um círculo cujo raio é de 2,50 centímetros.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="fd8b7-212">Lembre-se de que a área de um círculo é o quadrado do raio multiplicado por PI.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="fd8b7-213">Uma dica: o .NET contém uma constante para PI, <xref:System.Math.PI?displayProperty=nameWithType>, que você pode usar para esse valor.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="fd8b7-214">Você deve obter uma resposta entre 19 e 20.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="fd8b7-215">Confira sua resposta [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="fd8b7-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="fd8b7-216">Experimente outras fórmulas, se quiser.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="fd8b7-217">Você concluiu o início rápido "Números em C#".</span><span class="sxs-lookup"><span data-stu-id="fd8b7-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="fd8b7-218">Continue com o início rápido [Branches e loops](branches-and-loops-local.md) em seu próprio ambiente de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="fd8b7-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="fd8b7-219">Saiba mais sobre os números em C# nos tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="fd8b7-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="fd8b7-220">[Tabela de Tipos Integrais](../../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="fd8b7-220">[Integral Types Table](../../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="fd8b7-221">[Tabela de tipos de ponto flutuante](../../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="fd8b7-221">[Floating-Point Types Table](../../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="fd8b7-222">[Tabela de Tipos Internos](../../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="fd8b7-222">[Built-In Types Table](../../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="fd8b7-223">[Tabela de conversões numéricas implícitas](../../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="fd8b7-223">[Implicit Numeric Conversions Table](../../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="fd8b7-224">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="fd8b7-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
