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
# <a name="numbers-in-c-quick-start"></a>Números de início rápido do c# #

Este guia rápido ensina sobre os tipos de número em c# interativamente. Você escreverá pequenas quantidades de código, em seguida, você compilar e executar esse código. O início rápido contém uma série de lições que exploram números e operações matemáticas em c#. Estas lições ensinam os princípios básicos da linguagem C#.

Este guia rápido espera que você tem uma máquina que você pode usar para o desenvolvimento. O tópico .NET [começar em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.

## <a name="explore-integer-math"></a>Explorar a matemática de inteiros

Crie um diretório chamado **quickstart números**. Torne-o o diretório atual e execute `dotnet new console -n NumbersInCSharp -o .`.

Abra **Program.cs** em seu editor favorito e substitua a linha `Console.Writeline("Hello World!");` com o seguinte:

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
    
Você também pode experimentar, executando várias operações matemáticas na mesma linha, se quiser. Tente `c = a + b - 12 * 17;` por exemplo. É permitido misturar variáveis e constantes números.

> [!TIP]
> À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código. O **compilador** encontrará esses erros e os reportará a você. Quando a saída contém mensagens de erro, Verifique atentamente o código de exemplo e código na sua janela para ver o que deve ser corrigido.
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

Comente a chamada para `WorkingWithIntegers()`. Fazer a saída que menor congestionado enquanto você trabalha nesta seção:

```csharp
//WorkingWithIntegers();
```

O `//` inicia um **comentário** em c#. Os comentários são qualquer texto que você deseja manter em seu código-fonte, mas não executado como código. O compilador não gera nenhum código executável de comentários.

A linguagem C# define a precedência de operações matemáticas diferentes com regras consistentes às regras que você aprendeu em matemática.
Multiplicação e divisão têm precedência sobre adição e subtração.
Explorar isso adicionando o seguinte código ao seu `Main` método e execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

A saída demonstra que a multiplicação é executada antes da adição.

Você pode forçar uma ordem diferente da operação adicionando parênteses delimitando a operação ou operações executadas em primeiro lugar. Adicione as linhas a seguir e execute novamente:

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

Explore mais, combinando várias operações diferentes. Adicionar algo parecido com as seguintes linhas na parte inferior da sua `Main` método. Tente `dotnet run` novamente.

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

Talvez você tenha observado um comportamento interessante com relação aos números inteiros. Divisão sempre produz um resultado de inteiro, mesmo quando o resultado para incluir uma parte decimal ou fracionária esperado.

Se você ainda não o fez esse comportamento, tente o seguinte código ao final de sua `Main` método:

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

Tipo `dotnet run` novamente para ver os resultados.

Antes de avançarmos, vamos todo o código que você escreveu nesta seção e colocá-la em um novo método. Chame esse novo método `OrderPrecedence`.
Você deve terminar com algo assim:

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

## <a name="explore-integer-precision-and-limits"></a>Explorar a precisão de inteiros e limites
Esse último exemplo mostrou que uma divisão de inteiros trunca o resultado.
Você pode obter o **restante** usando o **módulo** operador, o `%` caracteres. Tente o seguinte código no seu `Main` método:

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

O tipo de inteiro C# difere do inteiros matemáticos de outra forma: o tipo `int` tem limites mínimo e máximo. Adicione este código ao seu `Main` método para ver esses limites:
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

Se um cálculo produzir um valor que excede esses limites, você terá uma condição de **estouro negativo** ou **estouro**. A resposta parece quebrar de um limite para o outro. Adicione estas duas linhas para sua `Main` método para ver um exemplo:

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
Observe que a resposta é muito próxima do mínimo inteiro (negativo). É o mesmo que `min + 2`. A operação de adição **estourou** os valores permitidos para números inteiros.
A resposta é um número negativo muito grande, pois um estouro "envolve" do maior valor de inteiro possível para o menor.

Há outros tipos numéricos com limites e precisão diferentes que você usaria quando o tipo `int` não atendesse às suas necessidades. Vamos explorá-los na sequência.

Novamente, vamos passar o código que você escreveu nesta seção para um método separado. Nomeie-o `TestLimits`. 

## <a name="work-with-the-double-type"></a>Trabalhar com o tipo Double

O tipo numérico `double` representa um número de ponto flutuante de precisão dupla. Esses termos podem ser novidade para você. Um **ponto flutuante** número é útil para representar números integral não podem ser muito grande ou pequeno em magnitude. **Precisão dupla** significa que esses números são armazenados usando uma precisão maior do que a **precisão única**. Em computadores modernos, é mais comum usar precisão dupla que números de precisão única.
Vamos explorar. Adicione o seguinte código e veja o resultado:

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

Observe que a resposta inclui a parte decimal do quociente. Experimente uma expressão ligeiramente mais complicada com duplos:

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

O intervalo de um valor duplo é muito maior do que valores inteiros. Tente o seguinte código abaixo o que você escreveu até agora:

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

Esses valores são impresso em notação científica. O número à esquerda do `E` é o significando. O número à direita é o expoente, como uma potência de 10. 

Assim como os números decimais em matemática, os duplos em C# podem ter erros de arredondamento. Experimente esse código:

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

Você sabe que a repetição de `0.3` não é exatamente o mesmo que `1/3`.

***Desafio***

Experimente outros cálculos com números grandes, números pequenos, multiplicação e divisão usando o tipo `double`.  Experimente cálculos mais complicados.

Depois que você tenha alguma experiência com o desafio, levar o código já gravado e colocá-lo em um novo método. Nomeie esse novo método `WorkWithDoubles`.

## <a name="work-with-fixed-point-types"></a>Trabalhar com tipos de ponto fixo

Você viu os tipos numéricos básicos em C#: inteiros e duplos.  Ainda há outro tipo : o tipo `decimal`. O `decimal` tipo tem um intervalo menor mas maior precisão que `double`. O termo **ponto fixo** significa que a virgula decimal (ou ponto binário) não muda. Vamos analisar:

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

Agora que você viu os diferentes tipos numéricos, escreva um código que calcula a área de um círculo cujo raio é de 2,50 polegadas. Lembre-se de que a área de um círculo é o quadrado do raio multiplicado por PI. Uma dica: c# contém uma constante de PI, <xref:System.Math.PI?displayProperty=nameWithType> que você pode usar para esse valor. 

Você pode verificar sua resposta por [olhando para o código de exemplo finalizado no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

Se desejar, tente algumas outras fórmulas. 

Você concluiu o início rápido "números no c#". Você pode continuar com a [loops e ramificações](branches-and-loops-local.md) início rápido em seu próprio ambiente de desenvolvimento.

Saiba mais sobre os números em C# nos tópicos a seguir:

[Tabela de Tipos Integrais](../language-reference/keywords/integral-types-table.md)   
[Tabela de tipos de ponto flutuante](../language-reference/keywords/floating-point-types-table.md)   
[Tabela de Tipos Internos](../language-reference/keywords/built-in-types-table.md)   
[Tabela de conversões numéricas implícitas](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[Tabela de conversões numéricas explícitas](../language-reference/keywords/explicit-numeric-conversions-table.md)

