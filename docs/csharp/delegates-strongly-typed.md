---
title: Delegados Fortemente Tipados
description: Delegados Fortemente Tipados
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ad73474ceb56f8610facd1668825bb0e71ccc7cb
ms.lasthandoff: 03/13/2017

---

# <a name="strongly-typed-delegates"></a>Delegados Fortemente Tipados

[Anterior](delegate-class.md)

No artigo anterior, você viu como criar tipos de delegado específicos usando a palavra-chave `delegate`. 

A classe de delegado abstrata fornece a infraestrutura para a invocação e acoplamento fraco. Os tipos de delegado concretos se tornam muito mais úteis adotando e impondo a segurança de tipos para os métodos que são adicionados à lista de invocação para um objeto delegado. Quando você usa a palavra-chave `delegate` e define um tipo de delegado concreto, o compilador gera esses métodos.

Na prática, isso poderia levar à criação de novos tipos de delegado sempre que precisar de uma assinatura de método diferente. Esse trabalho pode se tornar entediante depois de um tempo. Cada novo recurso exige novos tipos de delegado.

Felizmente, isso não é necessário. O .NET Core Framework contém vários tipos que podem ser reutilizados sempre que você precisar de tipos de delegado. Essas são definições [genéricas](programming-guide/generics/index.md) para que você possa declarar personalizações quando precisar de novas declarações de método. 

O primeiro desses tipos é o tipo @System.Action e diversas variações:

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

O modificador `in` no argumento de tipo genérico é abordado neste artigo sobre covariância.

Há variações do delegado `Action` que contêm até 16 argumentos como @System.Action%6016.
É importante que essas definições usem argumentos genéricos diferentes para cada um dos argumentos do delegado: isso proporciona a máxima flexibilidade. Os argumentos de método não precisam ser, mas podem ser, do mesmo tipo.

Use um dos tipos `Action` para qualquer tipo de delegado que tenha um tipo de retorno nulo.

A estrutura também inclui vários tipos de delegado genérico que você pode usar para tipos de delegado que retornam valores:

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

O modificador `out` no argumento de tipo genérico de resultado é abordado neste artigo sobre covariância.

Há variações do delegado `Func` com até 16 argumentos de entrada como @System.Func%6017.
O tipo do resultado é sempre o último parâmetro de tipo em todas as declarações `Func`, por convenção.

Use um dos tipos `Func` para qualquer tipo de delegado que retorna um valor.

Há também um tipo @System.Predicate%601 especializado para um delegado que retorna um teste em um único valor:

```csharp
public delegate bool Predicate<in T>(T obj);
```

Você pode observar que para qualquer tipo `Predicate`, há um tipo `Func` estruturalmente equivalente, por exemplo:

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

Você pode pensar que esses dois tipos são equivalentes. Eles não são.
Essas duas variáveis não podem ser usadas alternadamente. Uma variável de um tipo não pode ser atribuída o outro tipo. O sistema de tipo do C# usa os nomes dos tipos definidos, não a estrutura.

Todas essas definições de tipo de delegado na Biblioteca do .NET Core devem significar que você não precisa definir um novo tipo de delegado para qualquer novo recurso criado que exige delegados. Essas definições genéricas devem fornecer todos os tipos de delegado necessários na maioria das situações. Você pode simplesmente instanciar um desses tipos com os parâmetros de tipo necessários. No caso de algoritmos que podem ser tornados genéricos, esses delegados podem ser usados como tipos genéricos. 

Isso deve economizar tempo e minimizar o número de novos tipos de que você precisa criar a fim de trabalhar com delegados.

No próximo artigo, você verá vários padrões comuns para trabalhar com delegados na prática.

[Avançar](delegates-patterns.md)

