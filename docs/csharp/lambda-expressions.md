---
title: "Expressões lambda"
description: "Predisponha-se a usar expressões lambda, que são blocos de código executável que podem ser passados como argumentos."
keywords: ".NET, .NET Core, expressões lambda, lambdas, delegados"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.translationtype: HT
ms.sourcegitcommit: 2762cdc983465979a530192716c33de7044dd1ed
ms.openlocfilehash: 659a3366b00d6abe6598c31774d008c6b8f400fd
ms.contentlocale: pt-br
ms.lasthandoff: 08/04/2017

---

# <a name="lambda-expressions"></a>Expressões lambda #

Uma *expressão lambda* é um bloco de código (uma expressão ou um bloco de instruções) que é tratado como um objeto. Ela pode ser passada como um argumento para métodos e também pode ser retornada por chamadas de método. As expressões lambda são usadas amplamente para:

- Passar o código que deve ser executado por métodos assíncronos, como @System.Threading.Tasks.Task.Run(System.Action).

- Escrever [expressões de consulta LINQ](linq/index.md).

- Criar [árvores de expressão](expression-trees-building.md).

As expressões lambda são códigos que podem ser representados como um delegado ou como uma árvore de expressão que é compilada para um delegado. O tipo delegado específico de uma expressão lambda depende de seus parâmetros e do valor retornado. As expressões lambda que não retornam um valor correspondem a um delegado `Action` específico, dependendo de seu número de parâmetros. As expressões lambda que retornam um valor correspondem a um delegado `Func` específico, dependendo de seu número de parâmetros. Por exemplo, uma expressão lambda que tem dois parâmetros, mas não retorna nenhum valor, corresponde a um delegado @System.Action%602. Uma expressão lambda que tem um parâmetro e retorna um valor, corresponde ao delegado @System.Func%602.

Usa uma expressão lambda usa o `=>`, o [operador de declaração lambda](language-reference/operators/lambda-operator.md), para separar a lista de parâmetros de lambda de seu código executável. Para criar uma expressão lambda, você especifica os parâmetros de entrada (se houver) no lado esquerdo do operador lambda e coloca a expressão ou o bloco de instruções do outro lado. Por exemplo, a expressão lambda de linha única `x => x * x` especifica um parâmetro chamado `x` e retorna o valor de `x` ao quadrado. Você pode atribuir essa expressão a um tipo delegado como neste exemplo:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Ou pode passá-la diretamente como um argumento de método:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Lambdas de expressão ##

 Uma expressão lambda com uma expressão no lado direito do operador => é chamada de *lambda de expressão*. Os lambdas de expressão são usados amplamente na construção de [árvores de expressão](expression-trees.md). Uma expressão lambda retorna o resultado da expressão e tem o seguinte formato básico:

```csharp
(input parameters) => expression
```

Os parênteses serão opcionais somente se o lambda tiver um parâmetro de entrada; caso contrário, eles serão obrigatórios. Especifique parâmetros de entrada zero com parênteses vazios:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Dois ou mais parâmetros de entrada são separados por vírgulas e envolvidos por parênteses:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Normalmente, o compilador usa a inferência de tipos na determinação de tipos de parâmetro. No entanto, às vezes é difícil ou impossível para o compilador inferir os tipos de entrada. Quando isso ocorre, você pode especificar os tipos de maneira explícita, como no exemplo a seguir:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

Observe no exemplo anterior que o corpo de uma expressão lambda pode consistir de uma chamada de método. No entanto, se você estiver criando árvores de expressão que serão avaliadas fora do .NET Framework, como no SQL Server ou no EF (Entity Framework), você deverá evitar o uso de chamadas de método em expressões lambda, pois os métodos podem não ter significado fora do contexto da implementação do .NET. Se você optar por usar chamadas de método nesse caso, certifique-se de testá-las cuidadosamente para garantir que as chamadas de método possam ser resolvidas com êxito.

## <a name="statement-lambdas"></a>Lambdas de instrução ##

Um lambda de instrução lembra um lambda de expressão, exceto que as instruções estão incluídas entre chaves:

```csharp
(input parameters) => { statement; }
```

O corpo de uma instrução lambda pode consistir de qualquer número de instruções; no entanto, na prática, normalmente não há mais de duas ou três.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Lambdas de instrução, como métodos anônimos, não podem ser usados para criar árvores de expressão.

## <a name="async-lambdas"></a>Lambdas assíncronos ##

Você pode facilmente criar expressões e instruções lambda que incorporem processamento assíncrono, ao usar as palavras-chaves [async](language-reference/keywords/async.md) e [await](language-reference/keywords/await.md). Por exemplo, o exemplo chama um método `ShowSquares` que é executado de forma assíncrona.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [Programação assíncrona com async e await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Expressões lambda e tuplas ##

Começando com o C# 7.0, a linguagem C# fornece suporte interno para tuplas. Você pode fornecer uma tupla como um argumento para uma expressão lambda e a expressão lambda também pode retornar uma tupla. Em alguns casos, o compilador do C# usa a inferência de tipos para determinar os tipos dos componentes da tupla. 

Você pode definir uma tupla, colocando entre parênteses uma lista delimitada por vírgulas de seus componentes. O exemplo a seguir usa a tupla com cinco componentes para passar uma sequência de números para uma expressão lambda, que dobra cada valor e retorna uma tupla com cinco componentes que contêm o resultado das multiplicações.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Normalmente, os campos de uma tupla são chamados de `Item1`, `Item2`, etc. No entanto, você pode definir uma tupla com componentes nomeados, como é feito no exemplo a seguir.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Para obter mais informações sobre o suporte de tuplas no C#, consulte [Tipos de tupla do C#](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas com os operadores de consulta padrão ##

A LINQ to Objects, entre outras implementações, têm um parâmetro de entrada cujo tipo é um dos da família @System.Func%601 de delegados genéricos. Esses delegados usam parâmetros de tipo para definir o número e o tipo de parâmetros de entrada e o tipo de retorno do delegado. delegados `Func` são muito úteis para encapsular expressões definidas pelo usuário aplicadas a cada elemento em um conjunto de dados de origem. Por exemplo, considere o delegado @System.Func%601, cuja sintaxe é:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

O delegado pode ser instanciado com código semelhante ao seguinte

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

em que `int` é um parâmetro de entrada e `bool` é o valor retornado. O valor de retorno é sempre especificado no último parâmetro de tipo. Quando o delegado `Func` a seguir é invocado, ele retorna true ou false para indicar se o parâmetro de entrada é igual a 5:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Você também pode fornecer uma expressão lambda quando o tipo de argumento é um @System.Linq.Expressions.Expression%601, por exemplo, nos operadores de consulta padrão que são definidos no tipo @System.Linq.Queryable. Quando você especifica um argumento @System.Linq.Expressions.Expression%601, o lambda é compilado para uma árvore de expressão. O exemplo a seguir usa o operador de consulta padrão [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})).

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

O compilador pode inferir o tipo de parâmetro de entrada ou você também pode especificá-lo explicitamente. Essa expressão lambda em particular conta esses inteiros (`n`) que, quando divididos por dois, tem um resto igual a 1.

O exemplo a seguir gera uma sequência que contém todos os elementos da matriz `numbers` que precedem o 9, porque esse é o primeiro número na sequência que não satisfaz a condição.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

O exemplo a seguir especifica vários parâmetros de entrada, colocando-os entre parênteses. O método retorna todos os elementos na matriz de números até encontrar um número cujo valor é menor que sua posição ordinal na matriz.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Inferência de tipos em expressões lambda ##

Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo lambda, nos tipos de parâmetro e em outros fatores, conforme descrito na especificação da linguagem C#. Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem. Se você estiver consultando um `IEnumerable<Customer>`, a variável de entrada será inferida para ser um objeto `Customer`, o que significa que você terá acesso aos seus métodos e propriedades:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

As regras gerais para a inferência de tipos para lambdas são:

- O lambda deve conter o mesmo número de parâmetros do tipo delegado.

- Cada argumento de entrada no lambda deve ser implicitamente conversível em seu parâmetro delegado correspondente.

- O valor de retorno do lambda (se houver) deve ser implicitamente conversível para o tipo de retorno do delegado.

Observe que as expressões lambda em si não têm um tipo porque o sistema de tipo comum não possui conceito intrínseco da "expressão lambda". No entanto, às vezes é conveniente falar informalmente do "tipo" de uma expressão lambda. Nesses casos, o tipo se refere ao tipo delegado ou tipo @System.Linq.Expressions.Expression ao qual a expressão lambda é convertida.

## <a name="variable-scope-in-lambda-expressions"></a>Escopo variável em expressões lambda ##

As lambdas podem se referir a *variáveis externas* (consulte [Métodos anônimos](programming-guide/statements-expressions-operators/anonymous-methods.md)) que estão no escopo do método que define a função lambda ou no escopo do tipo que contém a expressão lambda. As variáveis que são capturadas dessa forma são armazenadas para uso na expressão lambda mesmo que de alguma outra forma elas saíssem do escopo e fossem coletadas como lixo. Uma variável externa deve ser definitivamente atribuída para que possa ser consumida em uma expressão lambda. O exemplo a seguir demonstra estas regras.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 As seguintes regras se aplicam ao escopo variável em expressões lambda:

- Uma variável capturada não será coletada do lixo até que o delegado que faz referência a ela se qualifique para coleta de lixo.

- As variáveis introduzidas em uma expressão lambda não são visíveis no método externo.

- Uma expressão lambda não pode capturar diretamente um parâmetro `ref` ou `out` de um método delimitador.

- Uma instrução return em uma expressão lambda não faz com que o método delimitador retorne.

- Uma expressão lambda não poderá conter uma instrução `goto`, `break` ou `continue` que está dentro da função lambda se o destino da instrução jump estiver fora do bloco. Também será um erro ter uma instrução jump fora do bloco da função lambda se o destino estiver dentro do bloco.

## <a name="see-also"></a>Consulte também ##

[LINQ (Consulta Integrada à Linguagem)](../standard/using-linq.md)   
[Métodos anônimos](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[Árvores de expressão](expression-trees.md)

