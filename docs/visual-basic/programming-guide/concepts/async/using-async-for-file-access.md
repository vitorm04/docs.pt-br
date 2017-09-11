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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 85f5fe17a012402c406eed972debd1f5889dd393
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="e098f-102">Usando o Async para acesso a arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e098f-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="e098f-103">Você pode usar o recurso Async para acessar arquivos.</span><span class="sxs-lookup"><span data-stu-id="e098f-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="e098f-104">Usando o recurso Async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="e098f-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="e098f-105">Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicione algumas palavras-chave no código.</span><span class="sxs-lookup"><span data-stu-id="e098f-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="e098f-106">Você pode considerar os motivos para a adição de assincronia para chamadas de acesso do arquivo:</span><span class="sxs-lookup"><span data-stu-id="e098f-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="e098f-107">Assincronia torna os aplicativos de interface do usuário mais responsiva porque o thread de interface do usuário que inicia a operação pode executar outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="e098f-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="e098f-108">Se o thread de interface do usuário deve executar o código que leva muito tempo (por exemplo, mais de 50 milissegundos), a interface do usuário pode congelar até que a e/s é concluída e o thread da interface do usuário pode processar teclado e entrados e outros eventos de mouse novamente.</span><span class="sxs-lookup"><span data-stu-id="e098f-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="e098f-109">A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor, reduzindo a necessidade de threads.</span><span class="sxs-lookup"><span data-stu-id="e098f-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="e098f-110">Se o aplicativo usa um thread dedicado por resposta e mil solicitações são tratadas simultaneamente, mil threads são necessários.</span><span class="sxs-lookup"><span data-stu-id="e098f-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="e098f-111">Operações assíncronas normalmente não precisam usar um thread durante a espera.</span><span class="sxs-lookup"><span data-stu-id="e098f-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="e098f-112">Eles usam o thread de conclusão de e/s existente brevemente no final.</span><span class="sxs-lookup"><span data-stu-id="e098f-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="e098f-113">A latência de uma operação de acesso de arquivo pode ser muito baixa em condições atuais, mas a latência pode aumentar consideravelmente no futuro.</span><span class="sxs-lookup"><span data-stu-id="e098f-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="e098f-114">Por exemplo, um arquivo pode ser movido para um servidor que esteja em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="e098f-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="e098f-115">A sobrecarga de usar o recurso Async é pequena.</span><span class="sxs-lookup"><span data-stu-id="e098f-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="e098f-116">Tarefas assíncronas facilmente podem ser executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="e098f-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="e098f-117">Executando os exemplos</span><span class="sxs-lookup"><span data-stu-id="e098f-117">Running the Examples</span></span>  
 <span data-ttu-id="e098f-118">Para executar os exemplos neste tópico, você pode criar um **aplicativo WPF** ou um **Windows Forms Application** e, em seguida, adicione um **botão**.</span><span class="sxs-lookup"><span data-stu-id="e098f-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="e098f-119">O botão `Click` evento, adicione uma chamada para o primeiro método em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="e098f-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="e098f-120">Nos exemplos a seguir, incluem o seguinte `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="e098f-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="e098f-121">Uso da classe FileStream</span><span class="sxs-lookup"><span data-stu-id="e098f-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="e098f-122">Os exemplos neste tópico usam o <xref:System.IO.FileStream>classe, que tem uma opção que faz com que a e/s assíncrona ocorrer no nível do sistema operacional.</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="e098f-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="e098f-123">Usando essa opção, você pode evitar o bloqueio de um thread de ThreadPool em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="e098f-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="e098f-124">Para habilitar essa opção, você deve especificar o `useAsync=true` ou `options=FileOptions.Asynchronous` argumento na chamada do construtor.</span><span class="sxs-lookup"><span data-stu-id="e098f-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="e098f-125">Você não pode usar essa opção com <xref:System.IO.StreamReader>e <xref:System.IO.StreamWriter>se você abri-los diretamente, especificando um caminho de arquivo.</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="e098f-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="e098f-126">No entanto, você pode usar essa opção se você fornecer um <xref:System.IO.Stream>que o <xref:System.IO.FileStream>classe aberto.</xref:System.IO.FileStream> </xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="e098f-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="e098f-127">Observe que chamadas assíncronas são mais rápidas em aplicativos de interface do usuário mesmo se um thread de ThreadPool é bloqueado, pois o thread de interface do usuário não é bloqueado durante a espera.</span><span class="sxs-lookup"><span data-stu-id="e098f-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="e098f-128">Escrevendo texto</span><span class="sxs-lookup"><span data-stu-id="e098f-128">Writing Text</span></span>  
 <span data-ttu-id="e098f-129">O exemplo a seguir grava um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="e098f-129">The following example writes text to a file.</span></span> <span data-ttu-id="e098f-130">Cada instrução de espera, o método sai imediatamente.</span><span class="sxs-lookup"><span data-stu-id="e098f-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="e098f-131">Quando o arquivo de e/s for concluído, o método continua a instrução que segue a instrução de espera.</span><span class="sxs-lookup"><span data-stu-id="e098f-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="e098f-132">Observe que o modificador async é a definição de métodos que usam a instrução de espera.</span><span class="sxs-lookup"><span data-stu-id="e098f-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="e098f-133">O exemplo original tem a instrução `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, que é uma contração das duas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="e098f-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="e098f-134">A primeira instrução retorna uma tarefa e faz com que o processamento de arquivos iniciar.</span><span class="sxs-lookup"><span data-stu-id="e098f-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="e098f-135">A segunda instrução com o await faz com que o método sair imediatamente e retornar uma tarefa diferente.</span><span class="sxs-lookup"><span data-stu-id="e098f-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="e098f-136">Ao concluir o processamento posterior de arquivos, execução retornará para a instrução que segue a espera.</span><span class="sxs-lookup"><span data-stu-id="e098f-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="e098f-137">Para obter mais informações, consulte [fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="e098f-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="e098f-138">Lendo texto</span><span class="sxs-lookup"><span data-stu-id="e098f-138">Reading Text</span></span>  
 <span data-ttu-id="e098f-139">O exemplo a seguir lê o texto de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e098f-139">The following example reads text from a file.</span></span> <span data-ttu-id="e098f-140">O texto é armazenada em buffer e, nesse caso, colocado em <xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="e098f-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="e098f-141">Diferentemente do exemplo anterior, a avaliação de esperar o produz um valor.</span><span class="sxs-lookup"><span data-stu-id="e098f-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="e098f-142">O <xref:System.IO.Stream.ReadAsync%2A>método retorna um <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, portanto, a avaliação de await produz uma `Int32` valor (`numRead`) após a conclusão da operação.</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A></span><span class="sxs-lookup"><span data-stu-id="e098f-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="e098f-143">Para obter mais informações, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e098f-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="e098f-144">E/s assíncrona paralela</span><span class="sxs-lookup"><span data-stu-id="e098f-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="e098f-145">O exemplo a seguir demonstra o processamento paralelo escrevendo 10 arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="e098f-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="e098f-146">Para cada arquivo, o <xref:System.IO.Stream.WriteAsync%2A>método retorna uma tarefa que é adicionada a uma lista de tarefas.</xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="e098f-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="e098f-147">O `Await Task.WhenAll(tasks)` instrução sai do método e currículos dentro do método quando o processamento de arquivo é concluída para todas as tarefas.</span><span class="sxs-lookup"><span data-stu-id="e098f-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="e098f-148">O exemplo fecha todos <xref:System.IO.FileStream>instâncias em um `Finally` bloco depois que as tarefas sejam concluídas.</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="e098f-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="e098f-149">Se cada `FileStream` foi criado em uma `Imports` instrução, o `FileStream` pode ser descartado antes que a tarefa foi concluída.</span><span class="sxs-lookup"><span data-stu-id="e098f-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="e098f-150">Observe que qualquer aumento de desempenho é quase que totalmente do processamento paralelo e não o processamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="e098f-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="e098f-151">As vantagens de assincronia são que não bloqueia vários threads, e que não bloqueia o thread de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="e098f-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="e098f-152">Ao usar o <xref:System.IO.Stream.WriteAsync%2A>e <xref:System.IO.Stream.ReadAsync%2A>métodos, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usada para cancelar o fluxo intermediário da operação.</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="e098f-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="e098f-153">Para obter mais informações, consulte [ajuste seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) e [cancelamento em Threads gerenciados](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span><span class="sxs-lookup"><span data-stu-id="e098f-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e098f-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e098f-154">See Also</span></span>  
 <span data-ttu-id="e098f-155">[Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="e098f-155">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="e098f-156"> [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="e098f-156"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="e098f-157"> [Fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span><span class="sxs-lookup"><span data-stu-id="e098f-157"> [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span></span>
