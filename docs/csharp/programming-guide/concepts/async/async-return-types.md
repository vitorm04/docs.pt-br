---
title: Tipos de retorno assíncrono (C#)
description: Saiba mais sobre os tipos de retorno que os métodos Async podem ter em C# com exemplos de código para cada tipo e recursos adicionais.
ms.date: 08/19/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 71e560ed8ee0cae14da396e5ea2f3ab29611ebab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811490"
---
# <a name="async-return-types-c"></a>Tipos de retorno assíncrono (C#)

Métodos assíncronos podem conter os seguintes tipos de retorno:

- <xref:System.Threading.Tasks.Task>, para um método assíncrono que executa uma operação, mas não retorna nenhum valor.
- <xref:System.Threading.Tasks.Task%601>, para um método assíncrono que retorna um valor.
- `void`, para um manipulador de eventos.
- Começando com o C# 7.0, qualquer tipo que tenha um método acessível `GetAwaiter`. O objeto retornado pelo método `GetAwaiter` deve implementar a interface <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType>.
- Começando com o C# 8,0, <xref:System.Collections.Generic.IAsyncEnumerable%601> , para um método assíncrono que retorna um *fluxo assíncrono*.

Para obter mais informações sobre métodos assíncronos, consulte [programação assíncrona com Async e Await (C#)](./index.md).

Vários outros tipos também existem que são específicos para cargas de trabalho do Windows:

- <xref:System.Windows.Threading.DispatcherOperation>, para operações assíncronas limitadas ao Windows.
- <xref:Windows.Foundation.IAsyncAction>, para ações assíncronas em UWP que não retornam um valor.
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>, para ações assíncronas em UWP que relatam o progresso, mas não retornam um valor.
- <xref:Windows.Foundation.IAsyncOperation%601>, para operações assíncronas em UWP que retornam um valor.
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>, para operações assíncronas em UWP que relatam o progresso e retornam um valor.

## <a name="task-return-type"></a>Tipo de retorno de tarefa

Os métodos assíncronos que não contêm uma instrução `return` ou que contêm uma instrução `return` que não retorna um operando, normalmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>. Esses métodos retornam `void` se eles são executados de forma síncrona. Se você usar um tipo de retorno <xref:System.Threading.Tasks.Task> para um método assíncrono, um método de chamada poderá usar um operador `await` para suspender a conclusão do chamador até que o método assíncrono chamado seja concluído.

No exemplo a seguir, o `WaitAndApologizeAsync` método não contém uma `return` instrução, portanto, o método retorna um <xref:System.Threading.Tasks.Task> objeto. Retornando uma `Task` habilitação `WaitAndApologizeAsync` a ser aguardada. O <xref:System.Threading.Tasks.Task> tipo não inclui uma `Result` propriedade porque não tem nenhum valor de retorno.

:::code language="csharp" source="snippets/async-return-types/async-returns2.cs" id="TaskReturn":::

O `WaitAndApologizeAsync` é aguardado, usando uma instrução await, em vez de uma expressão await, semelhante à instrução de chamada a um método síncrono de retorno void. A aplicação de um operador await, nesse caso, não produz um valor. Para esclarecer a declaração de termos e a expressão, consulte a tabela abaixo:

| Tipo Await | Exemplo                                      | Type                                   |
|------------|----------------------------------------------|----------------------------------------|
| de  | `await SomeTaskMethodAsync()`                | <xref:System.Threading.Tasks.Task>     |
| Expression | `T result = await SomeTaskMethodAsync<T>();` | <xref:System.Threading.Tasks.Task%601> |

Você pode separar a chamada para `WaitAndApologizeAsync` do aplicativo de um operador Await, como mostra o código a seguir. No entanto, lembre-se que uma `Task` não tem uma propriedade `Result` e que nenhum valor será produzido quando um operador await for aplicado a uma `Task`.

O código a seguir separa a chamada ao método `WaitAndApologizeAsync` da espera pela tarefa que o método retorna.

:::code language="csharp" source="snippets/async-return-types/async-returns2a.cs" id="AwaitTask":::

## <a name="tasktresult-return-type"></a>Tipo de retorno de tarefa \<TResult\>

O <xref:System.Threading.Tasks.Task%601> tipo de retorno é usado para um método assíncrono que contém uma instrução de [retorno](../../../language-reference/keywords/return.md) na qual o operando é `TResult` .

No exemplo a seguir, o `GetLeisureHoursAsync` método contém uma `return` instrução que retorna um inteiro. Portanto, a declaração do método deve especificar um tipo de retorno de `Task<int>`. O <xref:System.Threading.Tasks.Task.FromResult%2A> método Async é um espaço reservado para uma operação que retorna um <xref:System.DateTime.DayOfWeek> .

:::code language="csharp" source="snippets/async-return-types/async-returns1.cs" id="LeisureHours":::

Quando `GetLeisureHoursAsync` é chamado de dentro de uma expressão await no método `ShowTodaysInfo`, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que está armazenado na tarefa que é retornada pelo método `GetLeisureHours`. Para obter mais informações sobre expressões await, consulte [await](../../../language-reference/operators/await.md).

Você pode entender melhor como o `await` recupera o resultado de um `Task<T>` separando a chamada para `GetLeisureHoursAsync` do aplicativo do `await` , como mostra o código a seguir. Uma chamada ao método `GetLeisureHoursAsync` que não é aguardada imediatamente, retorna um `Task<int>`, como você esperaria da declaração do método. A tarefa é atribuída à variável `getLeisureHoursTask` no exemplo. Já que `getLeisureHoursTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém uma propriedade <xref:System.Threading.Tasks.Task%601.Result> do tipo `TResult`. Nesse caso, `TResult` representa um tipo inteiro. Quando `await` é aplicado à `getLeisureHoursTask`, a expressão await é avaliada como o conteúdo da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> de `getLeisureHoursTask`. O valor é atribuído à variável `ret`.

> [!IMPORTANT]
> A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é uma propriedade de bloqueio. Se você tentar acessá-la antes que sua tarefa seja concluída, o thread que está ativo no momento será bloqueado até que a tarefa seja concluída e o valor esteja disponível. Na maioria dos casos, você deve acessar o valor usando `await` em vez de acessar a propriedade diretamente.
>
> O exemplo anterior recuperou o valor da <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade para bloquear o thread principal para que o `Main` método pudesse imprimir o no `message` console antes de o aplicativo ser encerrado.

:::code language="csharp" source="snippets/async-return-types/async-returns1a.cs" id="StoreTask":::

## <a name="void-return-type"></a>Tipo de retorno void

O tipo de retorno `void` é usado em manipuladores de eventos assíncronos, que exigem um tipo de retorno `void`. Para métodos diferentes de manipuladores de eventos que não retornam um valor, você deve retornar um <xref:System.Threading.Tasks.Task>, porque não é possível esperar por um método assíncrono que retorna `void`. Qualquer chamador desse método deve continuar a conclusão sem esperar que o método assíncrono chamado seja concluído. O chamador deve ser independente de quaisquer valores ou exceções geradas pelo método Async.

O chamador de um método assíncrono de retorno nulo não pode capturar exceções lançadas do método, e essas exceções não tratadas provavelmente causarão a falha do aplicativo. Se um método que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> gera uma exceção, a exceção é armazenada na tarefa retornada. A exceção é relançada quando a tarefa é esperada. Portanto, verifique se qualquer método assíncrono que pode produzir uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> e que as chamadas ao método são aguardadas.

Para obter mais informações sobre como capturar exceções em métodos assíncronos, consulte a seção [Exceptions in Async Methods](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods) do artigo [try-catch](../../../language-reference/keywords/try-catch.md) .

O exemplo a seguir mostra o comportamento de um manipulador de eventos assíncrono. No código de exemplo, um manipulador de eventos assíncrono deve permitir que o thread principal saiba quando ele for concluído. Em seguida, o thread principal pode aguardar um manipulador de eventos assíncronos ser concluído antes de sair do programa.

:::code language="csharp" source="snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>Tipos de retorno assíncronos generalizados e ValueTask\<TResult\>

Começando com o C# 7.0, um método assíncrono pode retornar qualquer tipo que tenha um método `GetAwaiter` acessível.

Já que <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> são tipos de referência, a alocação de memória em caminhos críticos para o desempenho, especialmente quando alocações ocorrerem em loops estreitos, podem afetar o desempenho. Suporte para tipos de retorno generalizados significa que você pode retornar um tipo de valor leve em vez de um tipo de referência para evitar as alocações de memória adicionais.

O .NET fornece a estrutura <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> como uma implementação leve de um valor de retorno de tarefa generalizado. Para usar o tipo <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType>, você deve adicionar o pacote NuGet `System.Threading.Tasks.Extensions` ao seu projeto. O exemplo a seguir usa a estrutura <xref:System.Threading.Tasks.ValueTask%601> para recuperar o valor de dois lançamentos de dados.

:::code language="csharp" source="snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>Fluxos assíncronos com IAsyncEnumerable\<T\>

A partir do C# 8,0, um método assíncrono pode retornar um *fluxo assíncrono*, representado por <xref:System.Collections.Generic.IAsyncEnumerable%601> . Um fluxo assíncrono fornece uma maneira de enumerar itens lidos de um fluxo quando elementos são gerados em partes com chamadas assíncronas repetidas. O exemplo a seguir mostra um método assíncrono que gera um fluxo assíncrono:

:::code language="csharp" source="snippets/async-return-types/AsyncStreams.cs" id="GenerateAsyncStream":::

O exemplo anterior lê linhas de uma cadeia de caracteres de forma assíncrona. Depois que cada linha é lida, o código enumera cada palavra na cadeia de caracteres. Os chamadores enumerariam cada palavra usando a `await foreach` instrução. O método aguarda quando precisa ler de forma assíncrona a próxima linha da cadeia de caracteres de origem.

## <a name="see-also"></a>Confira também

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Processar tarefas assíncronas conforme elas são concluídas](start-multiple-async-tasks-and-process-them-as-they-complete.md)
- [Programação assíncrona com async e await (C#)](index.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
