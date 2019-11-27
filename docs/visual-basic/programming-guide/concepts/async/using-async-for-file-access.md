---
title: Usando o Async para acessar arquivos
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: 803d182f5b0f3071feb7aae4945bc3c0a1fd82c3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349104"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="3b323-102">Usando Async para acesso a arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b323-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="3b323-103">Você pode usar o recurso assíncrono para acessar arquivos.</span><span class="sxs-lookup"><span data-stu-id="3b323-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="3b323-104">Usando o recurso Async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="3b323-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="3b323-105">Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicionar algumas palavras-chave ao código.</span><span class="sxs-lookup"><span data-stu-id="3b323-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="3b323-106">Você pode considerar seguintes motivos para adicionar a assincronia às chamadas de acesso ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="3b323-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="3b323-107">A assincronia torna os aplicativos de interface do usuário mais responsivos porque o thread de interface do usuário que inicia a operação pode executar outro trabalho.</span><span class="sxs-lookup"><span data-stu-id="3b323-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="3b323-108">Se o thread de interface do usuário precisar executar o código que leva muito tempo (por exemplo, mais de 50 milissegundos), a interface do usuário poderá congelar até que a E/S seja concluída e o thread da interface do usuário possa processar entradas do mouse e do teclado e outros eventos.</span><span class="sxs-lookup"><span data-stu-id="3b323-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="3b323-109">A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor reduzindo a necessidade de threads.</span><span class="sxs-lookup"><span data-stu-id="3b323-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="3b323-110">Se o aplicativo usar um thread dedicado por resposta e mil solicitações forem tratadas simultaneamente, serão necessários mil threads.</span><span class="sxs-lookup"><span data-stu-id="3b323-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="3b323-111">As operações assíncronas normalmente não precisam usar um thread durante a espera.</span><span class="sxs-lookup"><span data-stu-id="3b323-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="3b323-112">Elas podem usar o thread de conclusão de E/S existente rapidamente no final.</span><span class="sxs-lookup"><span data-stu-id="3b323-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="3b323-113">A latência de uma operação de acesso de arquivo pode ser muito baixa nas condições atuais, mas a latência pode aumentar consideravelmente no futuro.</span><span class="sxs-lookup"><span data-stu-id="3b323-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="3b323-114">Por exemplo, um arquivo pode ser movido para um servidor que está do outro lado do mundo.</span><span class="sxs-lookup"><span data-stu-id="3b323-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="3b323-115">A sobrecarga adicional de usar o recurso async é pequena.</span><span class="sxs-lookup"><span data-stu-id="3b323-115">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="3b323-116">As tarefas assíncronas podem facilmente ser executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="3b323-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="3b323-117">Executando os exemplos</span><span class="sxs-lookup"><span data-stu-id="3b323-117">Running the Examples</span></span>  
 <span data-ttu-id="3b323-118">Para executar os exemplos neste tópico, você pode criar um **Aplicativo WPF** ou um **Aplicativo do Windows Forms** e, em seguida, adicionar um **Botão**.</span><span class="sxs-lookup"><span data-stu-id="3b323-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="3b323-119">No evento `Click` do botão, adicione uma chamada para o primeiro método em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="3b323-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="3b323-120">Nos exemplos a seguir, inclua as seguintes instruções `Imports`.</span><span class="sxs-lookup"><span data-stu-id="3b323-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="3b323-121">Uso da classe FileStream</span><span class="sxs-lookup"><span data-stu-id="3b323-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="3b323-122">Os exemplos neste tópico usam a classe <xref:System.IO.FileStream>, que tem uma opção que faz com que a E/S assíncrona ocorra no nível do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="3b323-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="3b323-123">Usando essa opção, você pode evitar o bloqueio de um thread de ThreadPool em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="3b323-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="3b323-124">Para habilitar essa opção, você deve especificar o argumento `useAsync=true` ou `options=FileOptions.Asynchronous` na chamada do construtor.</span><span class="sxs-lookup"><span data-stu-id="3b323-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="3b323-125">Você não pode usar essa opção com <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> se você os abrir diretamente especificando um caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="3b323-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="3b323-126">No entanto, você poderá usar essa opção se fornecer um <xref:System.IO.Stream> que a classe <xref:System.IO.FileStream> abriu.</span><span class="sxs-lookup"><span data-stu-id="3b323-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="3b323-127">Observe que as chamadas assíncronas serão mais rápidas em aplicativos de interface do usuário mesmo se um thread de ThreadPool estiver bloqueado, porque o thread de interface do usuário não é bloqueado durante a espera.</span><span class="sxs-lookup"><span data-stu-id="3b323-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="3b323-128">Gravando texto</span><span class="sxs-lookup"><span data-stu-id="3b323-128">Writing Text</span></span>  
 <span data-ttu-id="3b323-129">O exemplo a seguir grava um texto em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="3b323-129">The following example writes text to a file.</span></span> <span data-ttu-id="3b323-130">A cada instrução await, o método sai imediatamente.</span><span class="sxs-lookup"><span data-stu-id="3b323-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="3b323-131">Quando o arquivo de E/S for concluído, o método continuará na instrução após a instrução await.</span><span class="sxs-lookup"><span data-stu-id="3b323-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="3b323-132">Observe que o modificador async é a definição de métodos que usam a instrução await.</span><span class="sxs-lookup"><span data-stu-id="3b323-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="3b323-133">O exemplo original tem a instrução `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, que é uma contração das duas instruções a seguir:</span><span class="sxs-lookup"><span data-stu-id="3b323-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="3b323-134">A primeira instrução retorna uma tarefa e faz com que o processamento do arquivo seja iniciado.</span><span class="sxs-lookup"><span data-stu-id="3b323-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="3b323-135">A segunda instrução com o await faz com que o método saia imediatamente e retorne uma tarefa diferente.</span><span class="sxs-lookup"><span data-stu-id="3b323-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="3b323-136">Quando o processamento do arquivo é concluído posteriormente, a execução retorna para a instrução após a await.</span><span class="sxs-lookup"><span data-stu-id="3b323-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="3b323-137">Para obter mais informações, consulte [fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="3b323-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="3b323-138">Lendo texto</span><span class="sxs-lookup"><span data-stu-id="3b323-138">Reading Text</span></span>  
 <span data-ttu-id="3b323-139">O exemplo a seguir lê o texto de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="3b323-139">The following example reads text from a file.</span></span> <span data-ttu-id="3b323-140">O texto é armazenado em buffer e, nesse caso, colocado em um <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="3b323-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="3b323-141">Diferentemente do exemplo anterior, a avaliação de await produz um valor.</span><span class="sxs-lookup"><span data-stu-id="3b323-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="3b323-142">O método <xref:System.IO.Stream.ReadAsync%2A> retorna um <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, portanto, a avaliação do await produz um valor `Int32` (`numRead`) após a conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="3b323-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="3b323-143">Para obter mais informações, consulte [tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="3b323-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="3b323-144">E/S assíncrona paralela</span><span class="sxs-lookup"><span data-stu-id="3b323-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="3b323-145">O exemplo a seguir demonstra o processamento paralelo escrevendo dez arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="3b323-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="3b323-146">Para cada arquivo, o método <xref:System.IO.Stream.WriteAsync%2A> retorna uma tarefa que é então adicionada a uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="3b323-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="3b323-147">A instrução `Await Task.WhenAll(tasks)` sai do método e retoma no método quando o processamento do arquivo é concluído para todas as tarefas.</span><span class="sxs-lookup"><span data-stu-id="3b323-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="3b323-148">O exemplo fecha todas as instâncias de <xref:System.IO.FileStream> em um bloco `Finally` após as tarefas serem concluídas.</span><span class="sxs-lookup"><span data-stu-id="3b323-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="3b323-149">Se cada `FileStream` foi criado em uma instrução `Imports`, o `FileStream` pode ter sido descartado antes de a tarefa ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="3b323-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="3b323-150">Observe que qualquer aumento de desempenho é quase que totalmente do processamento paralelo e não o processamento assíncrono.</span><span class="sxs-lookup"><span data-stu-id="3b323-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="3b323-151">As vantagens da assincronia são que ela não bloqueia vários threads e que ela não bloqueia o thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="3b323-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="3b323-152">Ao usar os métodos <xref:System.IO.Stream.WriteAsync%2A> e <xref:System.IO.Stream.ReadAsync%2A>, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usado para cancelar o fluxo intermediário da operação.</span><span class="sxs-lookup"><span data-stu-id="3b323-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="3b323-153">Para obter mais informações, consulte ajustar [seu aplicativo assíncrono (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) e o [cancelamento em threads gerenciados](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="3b323-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b323-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b323-154">See also</span></span>

- [<span data-ttu-id="3b323-155">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b323-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="3b323-156">Tipos de retorno assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b323-156">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="3b323-157">Fluxo de controle em programas assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b323-157">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
