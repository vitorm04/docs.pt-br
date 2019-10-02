---
title: Tutorial Números em C# – introdução ao C#
description: Aprenda C# explorando tipos numéricos, suas propriedades e métodos.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: b0dbb654253b7c6a1ead8f0454be86227a4afb68
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736715"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a>Manipular números de ponto flutuante e integrais em C\#

Este tutorial ensina sobre os tipos numéricos em C# de maneira interativa. Você escreverá pequenas quantidades de código, depois compilará e executará esse código. O tutorial contém uma série de lições que exploram números e operações matemáticas em C#. Estas lições ensinam os princípios básicos da linguagem C#.

Este tutorial espera que você tenha um computador que possa usar para desenvolvimento. O tutorial do .NET [Olá, mundo em 10 minutos](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) tem instruções para configurar seu ambiente de desenvolvimento local em Mac, PC ou Linux. Uma visão geral dos comandos que você usará está em [Familiarize-se com as ferramentas de desenvolvimento](local-environment.md), com links para obter mais detalhes.

## <a name="explore-integer-math"></a>Explorar a matemática de inteiros

Crie um diretório chamado **numbers-quickstart**. Torne-o o diretório atual e execute `dotnet new console -n NumbersInCSharp -o .`.

Abra **Program.cs** em seu editor favorito e substitua a linha `Console.WriteLine("Hello World!");` pelo seguinte:

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

Execute este código digitando `dotnet run` na janela de comando.

Você viu apenas uma das operações matemáticas fundamentais com números inteiros. O tipo `int` representa um **inteiro**, um número inteiro positivo ou negativo. Você usa o símbolo `+` para adição. Outras operações matemáticas comuns para inteiros incluem:

- `-` para subtração
- `*` para multiplicação
- `/` para divisão

Comece explorando essas diferentes operações. Adicione estas linhas após a linha que grava o valor de `c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

Execute este código digitando `dotnet run` na janela de comando.

Você também pode experimentar, executando várias operações matemáticas na mesma linha, se quiser. Experimente `c = a + b - 12 * 17;`, por exemplo. É permitido misturar variáveis e números constantes.

> [!TIP]
> À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código. O **compilador** encontrará esses erros e os reportará a você. Quando a saída contiver mensagens de erro, analise atentamente o código de exemplo e o código em sua janela para ver o que deve ser corrigido.
> Esse exercício ajudará você a conhecer a estrutura do código C#.

Você terminou a primeira etapa. Antes de iniciar a próxima seção, vamos passar o código atual para um método separado. Isso facilita o começo do trabalho com um exemplo novo. Renomeie seu método `Main` como `WorkingWithIntegers` e escreva um novo método `Main` que chama `WorkingWithIntegers`. Quando você terminar, seu código deverá parecer com isto:

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

## <a name="explore-order-of-operations"></a>Explorar a ordem das operações

Comente a chamada para `WorkingWithIntegers()`. Isso tornará a saída menos congestionada enquanto você trabalha nesta seção:

```csharp
//WorkingWithIntegers();
```

O `//` inicia um **comentário** em C#. Os comentários são qualquer texto que você queira manter em seu código-fonte, mas não queria executar como código. O compilador não gera qualquer código executável a partir dos comentários.

A linguagem C# define a precedência de operações matemáticas diferentes com regras consistentes às regras que você aprendeu em matemática.
Multiplicação e divisão têm precedência sobre adição e subtração.
Explore isso adicionando o seguinte código ao seu método `Main` e executando `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

A saída demonstra que a multiplicação é executada antes da adição.

Você pode forçar uma ordem diferente de operações, adicionando parênteses para delimitar a operação, ou operações, que você quer realizar primeiro. Adicione as seguintes linhas e execute novamente:

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

Explore mais, combinando várias operações diferentes. Adicione algo parecido com as seguintes linhas na parte inferior de seu método `Main`. Tente `dotnet run` novamente.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Talvez você tenha observado um comportamento interessante com relação aos números inteiros. A divisão de inteiros sempre produz um resultado inteiro, mesmo quando você espera que o resultado inclua uma parte decimal ou fracionária.

Se você ainda não viu esse comportamento, tente o seguinte código ao final de seu método `Main`:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

Digite `dotnet run` novamente para ver os resultados.

Antes de avançarmos, pegue todo código que você escreveu nesta seção e coloque-o em um novo método. Chame esse novo método de `OrderPrecedence`.
O resultado final será algo semelhante a isto:

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

            d = (a + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a>Explorar a precisão de inteiros e limites

Esse último exemplo mostrou que uma divisão de inteiros trunca o resultado.
Você pode obter o **restante** usando o operador **module**, o caractere `%`. Experimente o seguinte código em seu método `Main`:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

O tipo de inteiro C# difere do inteiros matemáticos de outra forma: o tipo `int` tem limites mínimo e máximo. Adicione este código ao seu método `Main` para ver esses limites:

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Se um cálculo produzir um valor que excede esses limites, você terá uma condição de **estouro negativo** ou **estouro**. A resposta parece quebrar de um limite para o outro. Adicione estas duas linhas ao seu método `Main` para ver um exemplo:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

Observe que a resposta é muito próxima do mínimo inteiro (negativo). É o mesmo que `min + 2`.
A operação de adição **estourou** os valores permitidos para números inteiros.
A resposta é um número negativo muito grande, pois um estouro "envolve" do maior valor de inteiro possível para o menor.

Há outros tipos numéricos com limites e precisão diferentes que você usaria quando o tipo `int` não atendesse às suas necessidades. Vamos explorá-los na sequência.

Novamente, vamos passar o código que você escreveu nesta seção para um método separado. Nomeie-o como `TestLimits`.

## <a name="work-with-the-double-type"></a>Trabalhar com o tipo Double

O tipo numérico `double` representa um número de ponto flutuante de precisão dupla. Esses termos podem ser novidade para você. Um número de **ponto flutuante** é útil para representar números não integrais que podem ser muito grandes ou pequenos em magnitude. **Precisão dupla** significa que esses números são armazenados usando uma precisão maior do que a **precisão única**. Em computadores modernos, é mais comum usar precisão dupla que números de precisão única.
Vamos explorar. Adicione o seguinte código e veja o resultado:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

Observe que a resposta inclui a parte decimal do quociente. Experimente uma expressão ligeiramente mais complicada com duplos:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

O intervalo de um valor duplo é muito maior do que valores inteiros. Experimente o código a seguir abaixo do código que você escreveu até o momento:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Esses valores são impressos em notação científica. O número à esquerda do `E` é o significando. O número à direita é o expoente, como uma potência de 10.

Assim como os números decimais em matemática, os duplos em C# podem ter erros de arredondamento. Experimente esse código:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Você sabe que a repetição de `0.3` não é exatamente o mesmo que `1/3`.

***Desafio***

Experimente outros cálculos com números grandes, números pequenos, multiplicação e divisão usando o tipo `double`.  Experimente cálculos mais complicados.

Após algum tempo no desafio, pegue o código que você escreveu e coloque-o em um novo método. Chame esse novo método de `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Trabalhar com tipos de ponto fixo

Você viu os tipos numéricos básicos em C#: inteiros e duplos.  Ainda há outro tipo : o tipo `decimal`. O tipo `decimal` tem um intervalo menor, mas precisão maior do que `double`. O termo **ponto fixo** significa que a virgula decimal (ou ponto binário) não muda. Vamos analisar:

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

Observe que o intervalo é menor do que o tipo `double`. Veja a precisão maior com o tipo decimal experimentando o código a seguir:

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

O sufixo `M` nos números é o modo como você indica que uma constante deve usar o tipo `decimal`.

Observe que o cálculo usando o tipo decimal tem mais dígitos à direita da vírgula decimal.

***Desafio***

Agora que você viu os diferentes tipos numéricos, escreva um código que calcula a área de um círculo cujo raio é de 2,50 centímetros. Lembre-se de que a área de um círculo é o quadrado do raio multiplicado por PI. Uma dica: o .NET contém uma constante para PI, <xref:System.Math.PI?displayProperty=nameWithType>, que você pode usar para esse valor.

Você deve obter uma resposta entre 19 e 20.
Confira sua resposta [analisando o código de exemplo finalizado no GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)

Experimente outras fórmulas, se quiser.

Você concluiu o início rápido "Números em C#". Continue com o início rápido [Branches e loops](branches-and-loops-local.md) em seu próprio ambiente de desenvolvimento.

Saiba mais sobre os números em C# nos tópicos a seguir:

- [Tipos integrais](../../language-reference/builtin-types/integral-numeric-types.md)
- [Tabela de tipos de ponto flutuante](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [Tabela de tipos internos](../../language-reference/keywords/built-in-types-table.md)
- [Tabela de conversões numéricas implícitas](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela de conversões numéricas explícitas](../../language-reference/keywords/explicit-numeric-conversions-table.md)
