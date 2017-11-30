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
# <a name="branches-and-loops"></a>Loops e branches

Este guia rápido ensina como escrever código que examina a variáveis e altera o caminho de execução com base nessas variáveis. Escrever código c# e ver os resultados da compilação e executá-lo. O início rápido contém uma série de lições que exploram ramificação e construções de loop em c#. Estas lições ensinam os princípios básicos da linguagem C#.

Este guia rápido espera que você tem uma máquina que você pode usar para o desenvolvimento. O tópico .NET [começar em 10 minutos](https://www.microsoft.com/net/core) tem instruções para configurar o ambiente de desenvolvimento local no Mac, PC ou Linux.

## <a name="make-decisions-using-the-if-statement"></a>Decisões usando o `if` instrução

Crie um diretório chamado **ramificações quickstart**. Torne-o o diretório atual e execute `dotnet new console -n BranchesAndLoops -o .`. Este comando cria um novo aplicativo de console .NET Core no diretório atual. 

Abra **Program.cs** em seu editor favorito e substitua a linha `Console.Writeline("Hello World!");` com o código a seguir:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Tente este código digitando `dotnet run` na sua janela do console. Você deve ver a mensagem "a resposta é maior que 10". impressa no console.

Modifique a declaração de `b` para que a soma seja inferior a 10: 

```csharp
int b = 3;
```

Tipo `dotnet run` novamente. Como a resposta é inferior a 10, nada é impresso. A **condição** que você está testando é falsa. Não há qualquer código para execução, porque você escreveu apenas uma das ramificações possíveis para uma instrução `if`: a ramificação verdadeira.

> [!TIP]
> À medida que explora C# (ou qualquer linguagem de programação), você cometerá erros ao escrever o código. O compilador encontrará e relatar os erros. Verifique atentamente a saída de erro e o código que gerou o erro. O erro do compilador geralmente pode ajudá-lo a localizar o problema. 

Este primeiro exemplo mostra o poder do `if` e tipos boolianos. Um *booliano* é uma variável que pode ter um dos dois valores: `true` ou `false`. C# define um tipo especial, `bool` para variáveis Boolean. A instrução `if` verifica o valor de um `bool`. Quando o valor é `true`, a instrução após `if` é executada. Caso contrário, é ignorada. 

Esse processo de verificação de condições e execução de instruções com base nessas condições é muito eficiente.


## <a name="make-if-and-else-work-together"></a>Faça if e else funcionam juntas

Para executar um código diferente nos branches true e false, crie um branch `else` que será executado quando a condição for false. Tente fazer isso. Adicione as duas últimas linhas no código abaixo para o `Main` método (você já deve ter os quatro primeiros):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

A instrução após a palavra-chave `else` é executada somente quando a condição que estiver sendo testada for `false`. Combinando `if` e `else` com booliano condições fornece todos os recursos que você precisa lidar com ambos um `true` e um `false` condição.

> [!IMPORTANT]
> O recuo sob as instruções `if` e `else` é para leitores humanos.
> A linguagem C# não considera recuo ou espaço em branco como significativo. A instrução após a palavra-chave `if` ou `else` será executada com base na condição. Todos os exemplos neste guia rápido siga a prática comum para recuar as linhas com base em fluxo de controle de instruções.

Como o recuo não é significativo, você precisa usar `{` e `}` para indicar quando você quer que mais de uma instrução faça parte do bloco executado condicionalmente. Os programadores em C# normalmente usam essas chaves em todas as cláusulas `if` e `else`. O exemplo a seguir é o mesmo que você acabou de criar. Modifique o código acima para coincidir com o código a seguir:

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
> O restante deste início rápido, todos os exemplos de código incluem as chaves a seguir aceita práticas recomendadas.

Você pode testar condições mais complicadas. Adicione o seguinte código no seu `Main` método após o código que você escreveu até agora:

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

O `&&` representa "e". Isso significa que as duas condições devem ser verdadeiras para executar a instrução no branch verdadeiro.  Estes exemplos também mostram que você pode ter várias instruções em cada branch condicional, desde que você coloque-as entre `{` e `}`.

Você também pode usar `||` representar "ou". Adicione o seguinte código após o que você escreveu até agora:

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

Você terminou a primeira etapa. Antes de iniciar a próxima seção, vamos passar o código atual para um método separado. Isso facilita o começo do trabalho com um exemplo novo. Renomeie seu método `Main` como `ExploreIf` e escreva um novo método `Main` que chama `ExploreIf`. Quando você terminar, seu código deverá parecer com isto:

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

Comente a chamada para `ExploreIf()`. Fazer a saída que menor congestionado enquanto você trabalha nesta seção:

```csharp
//ExploreIf();
```

O `//` inicia um **comentário** em c#. Os comentários são qualquer texto que você deseja manter em seu código-fonte, mas não executado como código. O compilador não gera nenhum código executável de comentários.

## <a name="use-loops-to-repeat-operations"></a>Use loops para repetir operações

Nesta seção você usar **loops** repetir as instruções. Tente este código em seu `Main` método:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

O `while` instrução verifica uma condição e executa a instrução ou bloco de instruções a seguir o `while`. Repetidamente, ele verifica a condição e executar as instruções até que a condição for falsa.

Há outro operador novo neste exemplo. O `++` após a variável `counter` é o operador **increment**. Ele adiciona 1 para o valor de `counter` e armazena esse valor no `counter` variável.

> [!IMPORTANT]
> Verifique se o `while` loop alterações condição falsa ao executar o código. Caso contrário, crie um **loop infinito**, para que seu programa nunca termine. Que não será demonstrada neste exemplo, porque você tem que forçar o programa a encerrar o **CTRL-C** ou outros meios.

O loop `while` testa a condição antes de executar o código seguindo `while`. O loop `do` ... `while` executa o código primeiro e, em seguida, verifica a condição. A não enquanto o loop é mostrado no código a seguir:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Isso `do` loop e a anterior `while` loop produzem a mesma saída.

## <a name="work-with-the-for-loop"></a>Trabalhar com o loop for

O **para** loop é usado normalmente em c#. Tente este código no método Main ():

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Ele faz o mesmo trabalho que o loop `while` e o loop `do` que você já usou. A instrução `for` tem três partes que controlam o modo como ela funciona. 

A primeira parte é o **inicializador for**: `for index = 0;` declara que `index` é a variável do loop, e define seu valor inicial como `0`.

A parte central é a **condição for**: `index < 10` declara que este loop `for` continuará sendo executado desde que o valor do contador seja inferior a 10.

A parte final é o **iterador for**: `index++` especifica como modificar a variável de loop depois de executar o bloco após a instrução `for`. Aqui, ela especifica que `index` deve ser incrementado com 1 sempre que o bloco for executado.

Experimente você mesmo. Tente o seguinte:

- Altere o inicializador para iniciar em um valor diferente.
- Altere a condição para parar em um valor diferente.

Quando terminar, vamos escrever um código para usar o que você aprendeu.

## <a name="combine-branches-and-loops"></a>Combinar loops e ramificações

Agora que você viu a instrução `if` e as construções de loop na linguagem C#, verifique se você pode escrever o código C# para encontrar a soma de todos os inteiros de 1 a 20 divisíveis por 3.  Veja algumas dicas:

- O operador `%` retorna o restante de uma operação de divisão.
- O `if` instrução lhe dá a condição para ver se um número deve ser parte da soma.
- O loop `for` pode ajudar você a repetir uma série de etapas para todos os números de 1 a 20.

Tente você mesmo. Depois verifique como você fez. Você pode ver uma resposta possível por [exibindo o código completo no GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).

Você concluiu o início rápido "ramificações e loops".

Você pode continuar com a [matrizes e coleções](arrays-and-collections.md) início rápido em seu próprio ambiente de desenvolvimento.

Saiba mais sobre esses conceitos nestes tópicos:

[Instrução If e else](../language-reference/keywords/if-else.md)   
[Instrução while](../language-reference/keywords/while.md)   
[Instrução Do](../language-reference/keywords/do.md)   
[Instrução for](../language-reference/keywords/for.md)   
