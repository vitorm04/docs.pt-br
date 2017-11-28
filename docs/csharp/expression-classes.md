---
title: "Tipos de Framework com suporte a árvores de expressão"
description: "Saiba mais sobre tipos de estrutura com suporte a árvores de expressão, criando árvores de expressão e técnicas para trabalhar com APIs de árvore de expressão."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: ed89b286eee9b4c2e11bb27d18e50f777f94f33e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="framework-types-supporting-expression-trees"></a>Tipos de Framework com suporte a árvores de expressão

[Anterior – Árvores de expressão explicadas](expression-trees-explained.md)

Há uma grande lista de classes do .NET Core Framework que funcionam com árvores de expressão.
Você pode ver a lista completa [aqui](/dotnet/core/api/System.Linq.Expressions).
Em vez de percorrer a lista completa, vamos entender como as classes de estrutura foram projetadas.

No design de linguagem, uma expressão é um corpo de código que calcula e retorna um valor. As expressões podem ser muito simples: a expressão constante `1` retorna o valor constante de 1. Elas podem ser mais complicados: a expressão `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` retorna uma raiz de uma equação quadrática (no caso em que a equação tem uma solução).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Tudo começa com System.Linq.Expression

Uma das complexidades de se trabalhar com árvores de expressão é que muitos tipos diferentes de expressões são válidos em muitos locais nos programas. Considere uma expressão de atribuição. O lado direito de uma atribuição pode ser um valor constante, uma variável, uma expressão de chamada de método ou outros. Essa flexibilidade de linguagem significa que você poderá encontrar muitos tipos diferentes de expressão em qualquer lugar nos nós de uma árvore ao percorrer uma árvore de expressão. Portanto, a maneira mais simples de se trabalhar é quando você pode trabalhar com o tipo de expressão de base. No entanto, às vezes você precisa saber mais.
A classe Expressão de base contém uma propriedade `NodeType` para essa finalidade.
Ela retorna um `ExpressionType` que é uma enumeração dos tipos de expressão possíveis.
Uma vez que você souber qual o tipo do nó, poderá convertê-la para esse tipo e executar ações específicas, conhecendo o tipo do nó de expressão. Você pode pesquisar determinados tipos de nó e trabalhar com as propriedades específicas desse tipo de expressão.

Por exemplo, esse código imprimirá o nome de uma variável para uma expressão de acesso variável. Eu segui a prática de verificar o tipo de nó, converter em uma expressão de acesso variável e verificar as propriedades do tipo de expressão específico:

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>Criando árvores de expressão

A classe `System.Linq.Expression` também contém vários métodos estáticos para criar expressões. Esses métodos criam um nó de expressão usando os argumentos fornecidos para seus filhos. Dessa forma, você cria uma expressão de seus nós folha. Por exemplo, esse código cria uma expressão de Adicionar:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Você pode ver neste exemplo simples que há muitos tipos envolvidos na criação e no trabalho com árvores de expressão. Essa complexidade é necessária para fornecer os recursos do vocabulário avançado fornecido pela linguagem C#.

## <a name="navigating-the-apis"></a>Navegando nas APIs
Há tipos de Nó de expressão que mapeiam para quase todos os elementos de sintaxe da linguagem C#. Cada tipo tem métodos específicos para esse tipo de elemento de linguagem. É muita coisa para guardar na memória ao mesmo tempo. Em vez de tentar memorizar tudo, aqui estão as técnicas que eu uso para trabalhar com Árvores de expressão:
1. Observar os membros da enumeração `ExpressionType` para determinar possíveis nós que devem ser examinados. Isso é realmente útil se você deseja percorrer e entender uma árvore de expressão.
2. Observar os membros estáticos da classe `Expression` para compilar uma expressão. Esses métodos podem compilar qualquer tipo de expressão em um conjunto de seu nós filho.
3. Examinar a classe `ExpressionVisitor` para compilar uma árvore de expressão modificada.

Você encontrará mais ao examinar cada uma dessas três áreas. Invariavelmente, você encontrará o que precisa ao começar com uma dessas três etapas.
 
 [Próximo – Executar árvores de expressão](expression-trees-execution.md)
 
