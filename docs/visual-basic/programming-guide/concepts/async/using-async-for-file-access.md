---
title: Usando o Async para acesso a arquivos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e0e548989b1d2c32b9faf5ce0dd90ae371dfc028
ms.lasthandoff: 03/13/2017

---
# <a name="using-async-for-file-access-visual-basic"></a>Usando o Async para acesso a arquivos (Visual Basic)
Você pode usar o recurso Async para acessar arquivos. Usando o recurso Async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda. Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicione algumas palavras-chave no código.  
  
 Você pode considerar os motivos para a adição de assincronia para chamadas de acesso do arquivo:  
  
-   Assincronia torna os aplicativos de interface do usuário mais responsiva porque o thread de interface do usuário que inicia a operação pode executar outro trabalho. Se o thread de interface do usuário deve executar o código que leva muito tempo (por exemplo, mais de 50 milissegundos), a interface do usuário pode congelar até que a e/s é concluída e o thread da interface do usuário pode processar teclado e entrados e outros eventos de mouse novamente.  
  
-   A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor, reduzindo a necessidade de threads. Se o aplicativo usa um thread dedicado por resposta e mil solicitações são tratadas simultaneamente, mil threads são necessários. Operações assíncronas normalmente não precisam usar um thread durante a espera. Eles usam o thread de conclusão de e/s existente brevemente no final.  
  
-   A latência de uma operação de acesso de arquivo pode ser muito baixa em condições atuais, mas a latência pode aumentar consideravelmente no futuro. Por exemplo, um arquivo pode ser movido para um servidor que esteja em todo o mundo.  
  
-   A sobrecarga de usar o recurso Async é pequena.  
  
-   Tarefas assíncronas facilmente podem ser executadas em paralelo.  
  
## <a name="running-the-examples"></a>Executando os exemplos  
 Para executar os exemplos neste tópico, você pode criar um **aplicativo WPF** ou um **Windows Forms Application** e, em seguida, adicione um **botão**. O botão `Click` evento, adicione uma chamada para o primeiro método em cada exemplo.  
  
 Nos exemplos a seguir, incluem o seguinte `Imports` instruções.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Uso da classe FileStream  
 Os exemplos neste tópico usam o <xref:System.IO.FileStream>classe, que tem uma opção que faz com que a e/s assíncrona ocorrer no nível do sistema operacional.</xref:System.IO.FileStream> Usando essa opção, você pode evitar o bloqueio de um thread de ThreadPool em muitos casos. Para habilitar essa opção, você deve especificar o `useAsync=true` ou `options=FileOptions.Asynchronous` argumento na chamada do construtor.  
  
 Você não pode usar essa opção com <xref:System.IO.StreamReader>e <xref:System.IO.StreamWriter>se você abri-los diretamente, especificando um caminho de arquivo.</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader> No entanto, você pode usar essa opção se você fornecer um <xref:System.IO.Stream>que o <xref:System.IO.FileStream>classe aberto.</xref:System.IO.FileStream> </xref:System.IO.Stream> Observe que chamadas assíncronas são mais rápidas em aplicativos de interface do usuário mesmo se um thread de ThreadPool é bloqueado, pois o thread de interface do usuário não é bloqueado durante a espera.  
  
## <a name="writing-text"></a>Escrevendo texto  
 O exemplo a seguir grava um arquivo de texto. Cada instrução de espera, o método sai imediatamente. Quando o arquivo de e/s for concluído, o método continua a instrução que segue a instrução de espera. Observe que o modificador async é a definição de métodos que usam a instrução de espera.  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 O exemplo original tem a instrução `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, que é uma contração das duas instruções a seguir:  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 A primeira instrução retorna uma tarefa e faz com que o processamento de arquivos iniciar. A segunda instrução com o await faz com que o método sair imediatamente e retornar uma tarefa diferente. Ao concluir o processamento posterior de arquivos, execução retornará para a instrução que segue a espera. Para obter mais informações, consulte [fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Lendo texto  
 O exemplo a seguir lê o texto de um arquivo. O texto é armazenada em buffer e, nesse caso, colocado em <xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder> Diferentemente do exemplo anterior, a avaliação de esperar o produz um valor. O <xref:System.IO.Stream.ReadAsync%2A>método retorna um <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, portanto, a avaliação de await produz uma `Int32` valor (`numRead`) após a conclusão da operação.</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A> Para obter mais informações, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>E/s assíncrona paralela  
 O exemplo a seguir demonstra o processamento paralelo escrevendo 10 arquivos de texto. Para cada arquivo, o <xref:System.IO.Stream.WriteAsync%2A>método retorna uma tarefa que é adicionada a uma lista de tarefas.</xref:System.IO.Stream.WriteAsync%2A> O `Await Task.WhenAll(tasks)` instrução sai do método e currículos dentro do método quando o processamento de arquivo é concluída para todas as tarefas.  
  
 O exemplo fecha todos <xref:System.IO.FileStream>instâncias em um `Finally` bloco depois que as tarefas sejam concluídas.</xref:System.IO.FileStream> Se cada `FileStream` foi criado em uma `Imports` instrução, o `FileStream` pode ser descartado antes que a tarefa foi concluída.  
  
 Observe que qualquer aumento de desempenho é quase que totalmente do processamento paralelo e não o processamento assíncrono. As vantagens de assincronia são que não bloqueia vários threads, e que não bloqueia o thread de interface do usuário.  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 Ao usar o <xref:System.IO.Stream.WriteAsync%2A>e <xref:System.IO.Stream.ReadAsync%2A>métodos, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usada para cancelar o fluxo intermediário da operação.</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A> Para obter mais informações, consulte [ajuste seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) e [cancelamento em Threads gerenciados](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [Fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
