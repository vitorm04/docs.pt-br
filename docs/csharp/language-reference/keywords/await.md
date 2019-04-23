---
title: await – Referência de C#
ms.custom: seodec18
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 91d76309fedb2a6f3d877a47f230fda74060107e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122883"
---
# <a name="await-c-reference"></a>await (Referência de C#)
O operador `await` é aplicado a uma tarefa em um método assíncrono para inserir um ponto de suspensão na execução do método até que a tarefa aguardada seja concluída. A tarefa representa um trabalho em andamento.  
  
`await` só pode ser usado em um método assíncrono modificado pela palavra-chave [async](../../../csharp/language-reference/keywords/async.md). Esse tipo de método, definido pelo uso do modificador `async` e, geralmente, contendo uma ou mais expressões `await`, é conhecido como um *método assíncrono*.  
  
> [!NOTE]
> As palavras-chave `async` e `await` foram introduzidas no C# 5. Para uma introdução à programação assíncrona, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).  
  
A tarefa à qual o operador `await` é aplicado, normalmente é retornada por uma chamada a um método que implementa o [Padrão assíncrono baseado em tarefa](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md). Eles incluem métodos que retornam objetos<xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask> e <xref:System.Threading.Tasks.ValueTask%601>.  

No exemplo a seguir, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> retorna um `Task<byte[]>`. A tarefa é uma promessa de produzir a matriz de bytes real quando a tarefa for concluída. O operador `await` suspende a execução até que o trabalho do método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> esteja concluído. Enquanto isso, o controle é retornado ao chamador de `GetPageSizeAsync`. Quando a tarefa termina a execução, a expressão `await` é avaliada para uma matriz de bytes.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
> Para o exemplo completo, confira o [Passo a passo: Como acessar a Web usando Async e Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Você pode baixar o exemplo em [Exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) no site da Microsoft. O exemplo está no projeto AsyncWalkthrough_HttpClient.  
  
Conforme mostrado no exemplo anterior, se `await` for aplicado ao resultado de uma chamada de método que retorna uma `Task<TResult>`, o tipo da expressão `await` será `TResult`. Se `await` for aplicado ao resultado de uma chamada de método que retorna uma `Task`, o tipo da expressão `await` será `void`. O exemplo a seguir ilustra a diferença.  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
Um expressão `await` não bloqueia o thread no qual ela está em execução. Em vez disso, ela faz com que o compilador inscreva o restante do método assíncrono como uma continuação da tarefa aguardada. Em seguida, o controle retorna para o chamador do método assíncrono. Quando a tarefa for concluída, ela invoca a sua continuação e a execução do método assíncrono continua de onde parou.  
  
Uma expressão `await` só pode ocorrer no corpo do respectivo método delimitador, de uma expressão lambda ou de um método anônimo que deve estar marcado com um modificador `async`. O termo *await* só serve como uma palavra-chave nesse contexto. Em outro local, ele será interpretado como um identificador. No método, na expressão lambda ou no método anônimo, uma expressão `await` não pode ocorrer no corpo de uma função síncrona, em uma expressão de consulta, no bloco de uma [instrução lock](../../../csharp/language-reference/keywords/lock-statement.md) ou em um contexto [inseguro](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exceptions"></a>Exceções  
A maioria dos métodos assíncronos retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601>. As propriedades da tarefa retornada transportam informações sobre seu status e histórico como: se a tarefa foi concluída, se o método assíncrono causou uma exceção ou se foi cancelado e qual foi o resultado final. O operador `await` acessa essas propriedades chamando métodos no objeto retornado pelo método `GetAwaiter`.  
  
Se você aguarda um método assíncrono de retorno de tarefa que causou uma exceção, o operador `await` relança a exceção.  
  
Se você aguarda um método assíncrono de retorno de tarefa que está cancelado, o operador `await` relança uma <xref:System.OperationCanceledException>.  
  
Uma tarefa única que está em um estado com falha pode refletir várias exceções. Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quando você aguarda essa tarefa, a operação de aguardar relança apenas uma das exceções. No entanto, você não pode prever qual das exceções será relançada.  
  
Para obter exemplos de tratamento de erro em métodos assíncronos, consulte [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir retorna o número total de caracteres nas páginas cujas URLs são passadas para ele como argumentos de linha de comando. O exemplo chama o método `GetPageLengthsAsync`, que é marcado com a palavra-chave `async`. O método `GetPageLengthsAsync`, por sua vez, utiliza a palavra-chave `await` para aguardar chamadas para o método <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType>.  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

O exemplo anterior usa o C# 7.1, que oferece suporte ao método [`async` `Main`](../../programming-guide/main-and-command-args/index.md). Como as versões anteriores de C# não dão suporte a pontos de entrada do aplicativo que retornam <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, não é possível aplicar o modificador `async` ao método `Main` e esperar a chamada do método `GetPageLengthsAsync`. Nesse caso, podemos assegurar que o método `Main` aguarde a conclusão da operação assíncrona por meio da recuperação do valor da propriedade <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>. Para tarefas que não retornam um valor, você pode chamar o método <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Para saber mais sobre como selecionar a versão da linguagem, consulte [Selecionar a versão da linguagem C#](../configure-language-version.md).

## <a name="see-also"></a>Consulte também

- [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md)
- [Passo a passo: acessar a Web usando Async e Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [async](../../../csharp/language-reference/keywords/async.md)
