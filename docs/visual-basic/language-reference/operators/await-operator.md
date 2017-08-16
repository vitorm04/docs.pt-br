---
title: Operador await (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a>Operador Await (Visual Basic)
Aplicar o `Await` operador um operando em uma expressão lambda ou de método assíncrona para suspender a execução do método até que a tarefa aguardada seja concluída. A tarefa representa um trabalho em andamento.  
  
 O método no qual `Await` é usada deve ter uma [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador. Tal um método definido usando o `Async` modificador e geralmente contém um ou mais `Await` expressões, é conhecido como um *método assíncrono*.  
  
> [!NOTE]
>  O `Async` e `Await` palavras-chave foram introduzidas no Visual Studio 2012. Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Normalmente, a tarefa que você aplicar o `Await` operador é o valor retornado de uma chamada para um método que implementa o [padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/?LinkId=204847), ou seja, um <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 No código a seguir, o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>retorna `getContentsTask`, um `Task(Of Byte())`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient> A tarefa é uma promessa de produzir a matriz de bytes reais quando a operação for concluída. O `Await` operador é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até `getContentsTask` for concluída. Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`. Quando `getContentsTask` for concluído, o `Await` expressão é avaliada como uma matriz de bytes.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  Para o exemplo completo, consulte [passo a passo: acessando a Web, usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Você pode baixar o exemplo de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) no site da Microsoft. O exemplo é no projeto AsyncWalkthrough_HttpClient.  
  
 Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task(Of TResult)`, o tipo do `Await` expressão é TResult. Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task`, o `Await` expressão não retorna um valor. O exemplo a seguir ilustra a diferença.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Um `Await` expressão ou instrução não bloqueia o thread no qual ele está em execução. Em vez disso, ele faz com que o compilador inscrever-se o restante do método assíncrono, após o `Await` expressão, como uma continuação da tarefa awaited. Em seguida, o controle retorna para o chamador do método assíncrono. Quando a tarefa for concluída, ele chama sua continuação e a execução dos currículos de método assíncrono onde parou.  
  
 Um `Await` expressão pode ocorrer somente no corpo de uma expressão lambda ou de método delimitador imediatamente marcada por um `Async` modificador. O termo *Await* serve como uma palavra-chave somente nesse contexto. Em outro lugar, ele será interpretado como um identificador. Dentro da expressão de lambda ou de método assíncrono, um `Await` expressão não pode ocorrer em uma expressão de consulta, no `catch` ou `finally` bloco de um [Try... Catch... Por fim](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrução na expressão variável de controle de loop de uma `For` ou `For Each` loop, ou no corpo de uma [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrução.  
  
## <a name="exceptions"></a>Exceções  
 A maioria dos métodos assíncronos retornar uma <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> As propriedades da tarefa retornada transportam informações sobre seu status e o histórico, como se a tarefa for concluída, se o método assíncrono causou uma exceção ou foi cancelado e que o resultado final é. O `Await` operador acessa as propriedades.  
  
 Se você espera que um método assíncrono retorno de tarefas que faz com que uma exceção, o `Await` operador Relança a exceção.  
  
 Se você espera que um método assíncrono retornando a tarefa que é cancelado, o `Await` operador relança <xref:System.OperationCanceledException>.</xref:System.OperationCanceledException>  
  
 Uma única tarefa que está em um estado de falha pode refletir várias exceções.  Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> Quando você espera uma tarefa, a operação de espera relança apenas uma das exceções. No entanto, você não pode prever qual das exceções é emitida novamente.  
  
 Para obter exemplos de tratamento de erros em métodos assíncronos, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de formulários do Windows a seguir ilustra o uso do `Await` em um método assíncrono, `WaitAsynchronouslyAsync`. Compare o comportamento do método com o comportamento de `WaitSynchronously`. Sem um `Await` operador, `WaitSynchronously` é executado de forma síncrona apesar do uso do `Async` modificador em sua definição e uma chamada para <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>em seu corpo.</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Passo a passo: Acessando a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
