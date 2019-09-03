---
title: Operador await – referência de C#
ms.custom: seodec18
ms.date: 08/30/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c2172f651dd106825680de3195e26f032225a9ab
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169324"
---
# <a name="await-operator-c-reference"></a>Operador await (referência de C#)

O operador `await` suspende a avaliação do método [async](../keywords/async.md) delimitador enquanto a operação assíncrona representada por seu operando não é concluída. Quando a operação assíncrona for concluída, o operador `await` retornará o resultado da operação, se houver. Quando o operador `await` é aplicado ao operando que representa a operação já concluída, ele retorna o resultado da operação imediatamente sem a suspensão do método delimitador. O operador `await` não bloqueia o thread que avalia o método assíncrono. Quando o operador `await` suspende o método delimitador, o controle é retornado ao chamador do método.

No exemplo a seguir, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retorna a instância `Task<byte[]>`, que representa uma operação assíncrona que produz uma matriz de bytes quando é concluída. O operador `await` suspende o método `DownloadDocsMainPageAsync` até que a operação seja concluída. Quando `DownloadDocsMainPageAsync` é suspenso, o controle é retornado ao método `Main`, que é o chamador de `DownloadDocsMainPageAsync`. O método `Main` é executado até precisar do resultado da operação assíncrona executada pelo método `DownloadDocsMainPageAsync`. Quando <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> obtém todos os bytes, o restante do método `DownloadDocsMainPageAsync` é avaliado. Depois disso, o restante do método `Main` é avaliado.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

O exemplo anterior usa o [método `Main` assíncrono](../../programming-guide/main-and-command-args/index.md), que é possível no C# 7.1 em diante. Para obter mais informações, confira a seção [Operador await no método Main](#await-operator-in-the-main-method).

> [!NOTE]
> Para obter uma introdução à programação assíncrona, confira [Programação assíncrona com async e await](../../programming-guide/concepts/async/index.md). A programação assíncrona com `async` e `await` segue o [padrão assíncrono baseado em tarefas](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Use o operador `await` somente em um método, uma [expressão lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou um [método anônimo](delegate-operator.md) que seja modificado pela palavra-chave [async](../keywords/async.md). Em um método assíncrono, não é possível usar o operador `await` no corpo de uma função síncrona, dentro do bloco de uma [instrução lock](../keywords/lock-statement.md) e em um contexto [desprotegido](../keywords/unsafe.md).
  
O operando `await` do operador geralmente é de um dos seguintes tipos .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. No entanto, qualquer expressão aguardável pode ser o operando do operador `await`. Para obter mais informações, confira a seção [Expressões aguardáveis](~/_csharplang/spec/expressions.md#awaitable-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

O tipo de expressão `await t` é `TResult` se o tipo de expressão `t` é <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.ValueTask%601>. Se o tipo de `t` é <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.ValueTask>, o tipo de `await t` é `void`. Em ambos os casos, se `t` gera uma exceção, `await t` gera a exceção novamente. Para obter mais informações sobre o tratamento de exceções, confira a seção [Exceções em métodos assíncronos](../keywords/try-catch.md#exceptions-in-async-methods) do artigo [Instrução try-catch](../keywords/try-catch.md).

As palavras-chave `async` e `await` estão disponíveis no C# 5 em diante.

## <a name="await-operator-in-the-main-method"></a>Operador await no método Main

No C# 7.1 em diante, o [método `Main`](../../programming-guide/main-and-command-args/index.md), que é o ponto de entrada do aplicativo, pode retornar `Task` ou `Task<int>`, permitindo que ele seja assíncrono, de modo que você possa usar o operador `await` no corpo. Em versões anteriores do C#, para garantir que o método `Main` aguarde a conclusão de uma operação assíncrona, você pode recuperar o valor da propriedade <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> da instância <xref:System.Threading.Tasks.Task%601> retornada pelo método assíncrono correspondente. Para operações assíncronas que não produzem um valor, você pode chamar o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Para saber mais sobre como selecionar a versão da linguagem, consulte [Selecionar a versão da linguagem C#](../configure-language-version.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira a seção [Expressões await](~/_csharplang/spec/expressions.md#await-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [async](../keywords/async.md)
- [Programação assíncrona com async e await](../../programming-guide/concepts/async/index.md)
- [Modelo de programação assíncrona de tarefa](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Programação assíncrona](../../async.md)
- [Padrão assíncrono baseado em tarefas](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Assincronia detalhada](../../../standard/async-in-depth.md)
- [Passo a passo: Como acessar a Web usando async e await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
