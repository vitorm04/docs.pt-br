---
title: "await (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "await_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "await [C#]"
  - "palavra-chave await [C#]"
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
caps.handback.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# await (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `await` operador é aplicado a uma tarefa em um método assíncrono para suspender a execução do método até que a tarefa aguardada seja concluída.  A tarefa representa o trabalho em andamento.  
  
 O método assíncrono no qual `await` é usado deve ser modificado pelo [async](../../../visual-basic/language-reference/modifiers/async.md) palavra\-chave.  Esse método, definido usando o `async` modificador e geralmente contém um ou mais `await` expressões, é conhecido como um *método assíncrono*.  
  
> [!NOTE]
>  O `async` e `await` palavras\-chave foram introduzidas no Visual Studio 2012.  Para obter uma introdução à programação assíncrona, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 A tarefa à qual a `await` operador é aplicado normalmente é o valor de retorno de uma chamada para um método que implementa o [padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/?LinkId=204847).  Os exemplos incluem valores do tipo <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  
  
 No código a seguir, o <xref:System.Net.Http.HttpClient> método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retorna um `Task\<byte[]>`, `getContentsTask`.  A tarefa é uma promessa de produzir a matriz de bytes real quando a tarefa for concluída.  O `await` operador é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até `getContentsTask` for concluída.  Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`.  Quando `getContentsTask` é concluído, o `await` expressão é avaliada como uma matriz de bytes.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  Para o exemplo completo, consulte [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Você pode baixar o exemplo de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) no site da Microsoft.  O exemplo é no projeto AsyncWalkthrough\_HttpClient.  
  
 Conforme mostrado no exemplo anterior, se `await` é aplicada ao resultado de uma chamada de método que retorna um `Task<TResult>`, em seguida, o tipo do `await` expressão é TResult.  Se `await` é aplicada ao resultado de uma chamada de método que retorna um `Task`, em seguida, o tipo do `await` expressão é nulo.  O exemplo a seguir ilustra a diferença.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Um `await` expressão não bloqueia o thread no qual ele está em execução.  Em vez disso, ele faz com que o compilador assinar o restante do método assíncrono como uma continuação da tarefa awaited.  Controle retorna para o chamador do método assíncrono.  Quando a tarefa for concluída, ele chama sua continuação e execução dos currículos de método assíncrono onde parou.  
  
 Um `await` expressão pode ocorrer somente no corpo de um delimitador imediatamente método, expressão lambda ou método anônimo é marcado por um `async` modificador.  O termo *await* serve como uma palavra\-chave somente nesse contexto.  Em outro lugar, ele será interpretado como um identificador.  Dentro do método, uma expressão lambda ou um método anônimo, um `await` expressão não pode ocorrer no corpo de uma função síncrona, em uma expressão de consulta, no bloco de um [instrução lock](../../../csharp/language-reference/keywords/lock-statement.md), ou em um [unsafe](../../../csharp/language-reference/keywords/unsafe.md) contexto.  
  
## Exceções  
 A maioria dos métodos assíncronos retornam um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  As propriedades da tarefa retornada transportam informações sobre seu status e o histórico, como se a tarefa for concluída, se o método assíncrono causou uma exceção ou foi cancelado e que o resultado final é.  O `await` operador acessa as propriedades.  
  
 Se você espera que um método assíncrono retorno de tarefas que causa uma exceção, o  `await` operador Relança a exceção.  
  
 Se você espera que um método assíncrono retorno de tarefas que é cancelado, o `await` operador relança um <xref:System.OperationCanceledException>.  
  
 Uma única tarefa que está em um estado de falha pode refletir várias exceções.  Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Quando você espera que essa tarefa, a operação de espera relança apenas uma das exceções.  No entanto, você não pode prever qual das exceções é emitida novamente.  
  
 Para obter exemplos de tratamento de erros em métodos assíncronos, consulte [try\-catch](../../../csharp/language-reference/keywords/try-catch.md).  
  
## Exemplo  
 O exemplo de formulários do Windows a seguir ilustra o uso do `await` em um método assíncrono, `WaitAsynchronouslyAsync`.  Compare o comportamento do método com o comportamento de `WaitSynchronously`.  Sem um `await` operador aplicado a uma tarefa, `WaitSynchronously` é executado de forma síncrona apesar do uso do `async` modificador em sua definição e uma chamada para <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> em seu corpo.  
  
```c#  
  
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
  
## Consulte também  
 [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [async](../../../visual-basic/language-reference/modifiers/async.md)