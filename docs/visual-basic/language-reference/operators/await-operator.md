---
title: "Operador Await (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Await"
helpviewer_keywords: 
  - "Espera [Visual Basic]"
  - "Operador Await [Visual Basic]"
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Await (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você aplica o operador de `Await` a um operando em um método assíncrono ou na expressão lambda para suspender a execução do método até que a tarefa deve terminar.  A tarefa representa um trabalho em andamento.  
  
 O método no qual `Await` é usado deve ter um modificador de [Async](../../../visual-basic/language-reference/modifiers/async.md) .  Esse método, definido usando o modificador de `Async` , e geralmente contendo uma ou mais expressões de `Await` , é conhecido como *um método assíncrono*.  
  
> [!NOTE]
>  As palavras\-chave de `Async` e de `Await` foram introduzidas no Visual Studio 2012.  Para uma introdução de programação async, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Normalmente, a tarefa para que você aplica o operador de `Await` é o valor de retorno de uma chamada a um método que implementa [Padrão assíncrono baseado chave](http://go.microsoft.com/fwlink/?LinkId=204847), isto é, <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  
  
 No código a seguir, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> de <xref:System.Net.Http.HttpClient> retorna `getContentsTask`, `Task(Of Byte())`.  A tarefa é uma promessa de gerar a matriz real de bytes quando a operação é concluída.  O operador de `Await` é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até que `getContentsTask` seja concluída.  Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`.  Quando `getContentsTask` termina, a expressão `Await` é avaliada como uma matriz de bytes.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  Para um exemplo completo, consulte [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  Você pode baixar o exemplo de [Exemplos de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) no site da Microsoft.  O exemplo está no projeto de AsyncWalkthrough\_HttpClient.  
  
 Se `Await` é aplicado ao resultado de uma chamada de método que retorna `Task(Of TResult)`, o tipo da expressão de `Await` é TResult.  Se `Await` é aplicado ao resultado de uma chamada de método que retorna `Task`, a expressão de `Await` não retorna um valor.  O exemplo a seguir ilustra a diferença.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Uma expressão ou uma declaração de `Await` não bloco o thread em que está executando.  Em vez disso, faz com que o compilador assine anterior o restante do método de async, após a expressão de `Await` , como uma continuação na tarefa esperada.  Então, o controle retorna para o chamador do método async.  Quando a tarefa termina, ela chama sua continuação, e a execução do método de async continua onde parou.  
  
 Uma expressão de `Await` pode ocorrer apenas no corpo de um método imediatamente incluindo ou de expressão lambda que é sinalizado por um modificador de `Async` .  O termo *espera* serve como uma palavra\-chave somente nesse contexto.  Em outro lugar, é interpretado como um identificador.  No método de async ou da expressão lambda, uma expressão de `Await` não pode ocorrer em uma expressão de consulta, no bloco de `catch` ou de `finally` de uma instrução de [Try… catch… finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , na expressão variável de controle de loop de um loop de `For` ou de `For Each` , ou no corpo de uma instrução de [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .  
  
## Exceções  
 A maioria dos métodos assíncronos retornam <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  As propriedades da tarefa retornada transportam informações sobre seus status e histórico como, por exemplo, se a tarefa está concluída, se o método de async causou uma exceção ou foi cancelado, e o qual é o resultado final.  O operador de `Await` acessa essas propriedades.  
  
 Se você aguardar um método assíncrono de retorno de tarefa que cause uma exceção, o operador `Await` relançará a exceção.  
  
 Se você pretende ajustar retornando um método de async que foi cancelado, a qual o operador de `Await`<xref:System.OperationCanceledException>.  
  
 Uma única tarefa que apresentar defeito pode refletir em diversas exceções.  Por exemplo, a tarefa pode ser resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.  Quando você espera uma tarefa, a operação de espera relança apenas uma das exceções.  No entanto, não é possível prever qual das exceções será lançada novamente.  
  
 Para exemplos de tratamento de erro em métodos assíncronos, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Exemplo  
 O seguinte exemplo do Windows Forms ilustra o uso de `Await` em um método assíncrono, `WaitAsynchronouslyAsync`.  Destaque o comportamento do método com o comportamento de `WaitSynchronously`.  Sem um operador de `Await` , `WaitSynchronously` executa forma independentemente do modificador de `Async` em sua definição e em uma chamada a <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> no corpo.  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## Consulte também  
 [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)