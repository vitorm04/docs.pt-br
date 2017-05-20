---
title: "await (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 3656141c32a04e3a32a2992185f4c418c6915482
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="await-c-reference"></a>await (Referência de C#)
O operador `await` é aplicado a uma tarefa em um método assíncrono para suspender a execução do método até que a tarefa aguardada seja concluída. A tarefa representa um trabalho em andamento.  
  
 O método assíncrono no qual `await` é usado deve ser modificado pela palavra-chave [async](../../../csharp/language-reference/keywords/async.md). Esse tipo de método, definido pelo uso do modificador `async` e, geralmente, contendo uma ou mais expressões `await`, é conhecido como um *método assíncrono*.  
  
> [!NOTE]
>  As palavras-chave `async` e `await` foram introduzidas no Visual Studio 2012. Para uma introdução à programação assíncrona, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).  
  
 A tarefa à qual o operador `await` é aplicado, normalmente é o valor retornado de uma chamada a um método que implementa o [Padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/?LinkId=204847). Os exemplos incluem valores de tipo <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  
  
 No código a seguir, o método <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, retorna um `Task\<byte[]>`, `getContentsTask`. A tarefa é uma promessa de produzir a matriz de bytes real quando a tarefa for concluída. O operador `await` é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até que `getContentsTask` seja concluída. Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`. Quando `getContentsTask` for concluído, a expressão `await` resulta em uma matriz de bytes.  
  
```csharp  
  
private async Task SumPageSizesAsync()  
{  
    // To use the HttpClient type in desktop apps, you must include a using directive and add a   
    // reference for the System.Net.Http namespace.  
    HttpClient client = new HttpClient();  
    // . . .  
    Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
    byte[] urlContents = await getContentsTask;  
  
    // Equivalently, now that you see how it works, you can write the same thing in a single line.  
    //byte[] urlContents = await client.GetByteArrayAsync(url);  
    // . . .  
}  
  
```  
  
> [!IMPORTANT]
>  Para obter o exemplo completo, consulte [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Você pode baixar o exemplo em [Exemplos de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) no site da Microsoft. O exemplo está no projeto AsyncWalkthrough_HttpClient.  
  
 Conforme mostrado no exemplo anterior, se `await` for aplicado ao resultado de uma chamada de método que retorna uma `Task<TResult>`, o tipo da expressão `await` será TResult. Se `await` for aplicado ao resultado de uma chamada de método que retorna uma `Task`, o tipo da expressão `await` será nula. O exemplo a seguir ilustra a diferença.  
  
```csharp  
// Keyword await used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// Keyword await used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  
  
```  
  
 Um expressão `await` não bloqueia o thread no qual ela está em execução. Em vez disso, ela faz com que o compilador inscreva o restante do método assíncrono como uma continuação da tarefa aguardada. Em seguida, o controle retorna para o chamador do método assíncrono. Quando a tarefa for concluída, ela invoca a sua continuação e a execução do método assíncrono continua de onde parou.  
  
 Uma expressão `await` só pode ocorrer no corpo de um método imediatamente delimitador, uma expressão lambda ou um método anônimo que esteja marcado por um modificador `async`. O termo *await* só serve como uma palavra-chave nesse contexto. Em outro local, ele será interpretado como um identificador. No método, na expressão lambda ou no método anônimo, uma expressão `await` não pode ocorrer no corpo de uma função síncrona, em uma expressão de consulta, no bloco de uma [instrução lock](../../../csharp/language-reference/keywords/lock-statement.md) ou em um contexto [inseguro](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exceptions"></a>Exceções  
 A maioria dos métodos assíncronos retorna uma <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. As propriedades da tarefa retornada transportam informações sobre seu status e histórico como: se a tarefa foi concluída, se o método assíncrono causou uma exceção ou se foi cancelado e qual foi o resultado final. O operador `await` acessa essas propriedades.  
  
 Se você aguarda um método assíncrono de retorno de tarefa que causou uma exceção, o operador `await` relançará a exceção.  
  
 Se você aguarda um método assíncrono de retorno de tarefa que foi cancelado, o operador `await` relançará a <xref:System.OperationCanceledException>.  
  
 Uma tarefa única que está em um estado com falha pode refletir várias exceções. Por exemplo, a tarefa pode ser o resultado de uma chamada ao <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>. Quando você aguarda essa tarefa, a operação de aguardar relança apenas uma das exceções. No entanto, você não pode prever qual das exceções será relançada.  
  
 Para obter exemplos de tratamento de erro em métodos assíncronos, consulte [try-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo do Windows Forms a seguir ilustra o uso do `await` em um método assíncrono `WaitAsynchronouslyAsync`. Compare o comportamento desse método com o comportamento de `WaitSynchronously`. Sem um operador `await` aplicado a uma tarefa, `WaitSynchronously` é executado de forma síncrona, apesar do uso do modificador `async` em sua definição e de uma chamada ao <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> em seu corpo.  
  
```csharp  
  
private async void button1_Click(object sender, EventArgs e)  
{  
    // Call the method that runs asynchronously.  
    string result = await WaitAsynchronouslyAsync();  
  
    // Call the method that runs synchronously.  
    //string result = await WaitSynchronously ();  
  
    // Display the result.  
    textBox1.Text += result;  
}  
  
// The following method runs asynchronously. The UI thread is not  
// blocked during the delay. You can move or resize the Form1 window   
// while Task.Delay is running.  
public async Task<string> WaitAsynchronouslyAsync()  
{  
    await Task.Delay(10000);  
    return "Finished";  
}  
  
// The following method runs synchronously, despite the use of async.  
// You cannot move or resize the Form1 window while Thread.Sleep  
// is running because the UI thread is blocked.  
public async Task<string> WaitSynchronously()  
{  
    // Add a using directive for System.Threading.  
    Thread.Sleep(10000);  
    return "Finished";  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md)   
 [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [async](../../../csharp/language-reference/keywords/async.md)
