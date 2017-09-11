---
title: Multithreading com o componente BackgroundWorker (Visual Basic) | Documentos do Microsoft
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
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
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
ms.openlocfilehash: 88d0711c8e417ae5c95b0e109504b69882015241
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="33db1-102">Passo a passo: Multithreading com o componente BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33db1-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="33db1-103">Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que procura um arquivo de texto por ocorrências de uma palavra.</span><span class="sxs-lookup"><span data-stu-id="33db1-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="33db1-104">Ele demonstra:</span><span class="sxs-lookup"><span data-stu-id="33db1-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="33db1-105">Definir uma classe com um método que pode ser chamado pelo <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="33db1-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="33db1-106">Manipulação de eventos gerados pelo <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="33db1-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="33db1-107">Iniciando um <xref:System.ComponentModel.BackgroundWorker>componentes para executar um método.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="33db1-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="33db1-108">Implementando um `Cancel` botão que interrompe o <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="33db1-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="33db1-109">Para criar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="33db1-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="33db1-110">Abra um novo projeto de aplicativo do Windows Forms do Visual Basic e crie um formulário chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="33db1-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="33db1-111">Adicione dois botões e quatro caixas de texto para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="33db1-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="33db1-112">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="33db1-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="33db1-113">Objeto</span><span class="sxs-lookup"><span data-stu-id="33db1-113">Object</span></span>|<span data-ttu-id="33db1-114">Propriedade</span><span class="sxs-lookup"><span data-stu-id="33db1-114">Property</span></span>|<span data-ttu-id="33db1-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="33db1-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="33db1-116">Primeiro botão</span><span class="sxs-lookup"><span data-stu-id="33db1-116">First button</span></span>|<span data-ttu-id="33db1-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-117">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-118">Iniciar, início</span><span class="sxs-lookup"><span data-stu-id="33db1-118">Start, Start</span></span>|  
    |<span data-ttu-id="33db1-119">Segundo botão</span><span class="sxs-lookup"><span data-stu-id="33db1-119">Second button</span></span>|<span data-ttu-id="33db1-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-120">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-121">Cancelar, cancelar</span><span class="sxs-lookup"><span data-stu-id="33db1-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="33db1-122">Primeira caixa de texto</span><span class="sxs-lookup"><span data-stu-id="33db1-122">First text box</span></span>|<span data-ttu-id="33db1-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-123">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-124">Arquivo de origem, ""</span><span class="sxs-lookup"><span data-stu-id="33db1-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="33db1-125">Segunda caixa de texto</span><span class="sxs-lookup"><span data-stu-id="33db1-125">Second text box</span></span>|<span data-ttu-id="33db1-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-126">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="33db1-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="33db1-128">Terceira caixa de texto</span><span class="sxs-lookup"><span data-stu-id="33db1-128">Third text box</span></span>|<span data-ttu-id="33db1-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-129">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="33db1-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="33db1-131">Quarta caixa de texto</span><span class="sxs-lookup"><span data-stu-id="33db1-131">Fourth text box</span></span>|<span data-ttu-id="33db1-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="33db1-132">`Name`, `Text`</span></span>|<span data-ttu-id="33db1-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="33db1-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="33db1-134">Adicione um rótulo ao lado de cada caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="33db1-134">Add a label next to each text box.</span></span> <span data-ttu-id="33db1-135">Definir o `Text` propriedade para cada rótulo como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="33db1-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="33db1-136">Objeto</span><span class="sxs-lookup"><span data-stu-id="33db1-136">Object</span></span>|<span data-ttu-id="33db1-137">Propriedade</span><span class="sxs-lookup"><span data-stu-id="33db1-137">Property</span></span>|<span data-ttu-id="33db1-138">Configuração</span><span class="sxs-lookup"><span data-stu-id="33db1-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="33db1-139">Primeiro rótulo</span><span class="sxs-lookup"><span data-stu-id="33db1-139">First label</span></span>|`Text`|<span data-ttu-id="33db1-140">Arquivo de Origem</span><span class="sxs-lookup"><span data-stu-id="33db1-140">Source File</span></span>|  
    |<span data-ttu-id="33db1-141">Segundo rótulo</span><span class="sxs-lookup"><span data-stu-id="33db1-141">Second label</span></span>|`Text`|<span data-ttu-id="33db1-142">Comparação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="33db1-142">Compare String</span></span>|  
    |<span data-ttu-id="33db1-143">Terceiro rótulo</span><span class="sxs-lookup"><span data-stu-id="33db1-143">Third label</span></span>|`Text`|<span data-ttu-id="33db1-144">Correspondência de palavras</span><span class="sxs-lookup"><span data-stu-id="33db1-144">Matching Words</span></span>|  
    |<span data-ttu-id="33db1-145">Rótulo</span><span class="sxs-lookup"><span data-stu-id="33db1-145">Fourth label</span></span>|`Text`|<span data-ttu-id="33db1-146">Linhas contadas</span><span class="sxs-lookup"><span data-stu-id="33db1-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="33db1-147">Para criar um componente BackgroundWorker e assinar seus eventos</span><span class="sxs-lookup"><span data-stu-id="33db1-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="33db1-148">Adicionar um <xref:System.ComponentModel.BackgroundWorker>componente do **componentes** seção o **ToolBox** ao formulário.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="33db1-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="33db1-149">Ele será exibido na bandeja de componentes do formulário.</span><span class="sxs-lookup"><span data-stu-id="33db1-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="33db1-150">Defina as seguintes propriedades para o objeto BackgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="33db1-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="33db1-151">Propriedade</span><span class="sxs-lookup"><span data-stu-id="33db1-151">Property</span></span>|<span data-ttu-id="33db1-152">Configuração</span><span class="sxs-lookup"><span data-stu-id="33db1-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="33db1-153">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="33db1-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="33db1-154">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="33db1-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="33db1-155">Para definir o método que será executado em um thread separado</span><span class="sxs-lookup"><span data-stu-id="33db1-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="33db1-156">Do **projeto** menu, escolha **Adicionar classe** para adicionar uma classe ao projeto.</span><span class="sxs-lookup"><span data-stu-id="33db1-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="33db1-157">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="33db1-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="33db1-158">Selecione **classe** da janela de modelos e digite `Words.vb` no campo nome.</span><span class="sxs-lookup"><span data-stu-id="33db1-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="33db1-159">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="33db1-159">Click **Add**.</span></span> <span data-ttu-id="33db1-160">O `Words` classe é exibida.</span><span class="sxs-lookup"><span data-stu-id="33db1-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="33db1-161">Adicione o seguinte código à classe `Words`:</span><span class="sxs-lookup"><span data-stu-id="33db1-161">Add the following code to the `Words` class:</span></span>  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="33db1-162">Para manipular eventos do encadeamento</span><span class="sxs-lookup"><span data-stu-id="33db1-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="33db1-163">Adicione os seguintes manipuladores de eventos ao seu formulário principal:</span><span class="sxs-lookup"><span data-stu-id="33db1-163">Add the following event handlers to your main form:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="33db1-164">Para iniciar e chamar um novo encadeamento que executa o método WordCount</span><span class="sxs-lookup"><span data-stu-id="33db1-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="33db1-165">Adicione os seguintes procedimentos para o seu programa:</span><span class="sxs-lookup"><span data-stu-id="33db1-165">Add the following procedures to your program:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="33db1-166">Chamar o `StartThread` método a partir de `Start` botão no formulário:</span><span class="sxs-lookup"><span data-stu-id="33db1-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="33db1-167">Para implementar um botão Cancelar que para o encadeamento</span><span class="sxs-lookup"><span data-stu-id="33db1-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="33db1-168">Chamar o `StopThread` procedimento o `Click` manipulador de eventos para o `Cancel` botão.</span><span class="sxs-lookup"><span data-stu-id="33db1-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="33db1-169">Testes</span><span class="sxs-lookup"><span data-stu-id="33db1-169">Testing</span></span>  
 <span data-ttu-id="33db1-170">Agora você pode testar o aplicativo para verificar se que ele funciona corretamente.</span><span class="sxs-lookup"><span data-stu-id="33db1-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="33db1-171">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="33db1-171">To test the application</span></span>  
  
1.  <span data-ttu-id="33db1-172">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33db1-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="33db1-173">Quando o formulário for exibido, insira o caminho para o arquivo que você deseja testar a `sourceFile` caixa.</span><span class="sxs-lookup"><span data-stu-id="33db1-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="33db1-174">Por exemplo, supondo que o arquivo de teste é chamado Test. txt, entre c:\test.txt..</span><span class="sxs-lookup"><span data-stu-id="33db1-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="33db1-175">Na segunda caixa de texto, digite uma palavra ou frase para o aplicativo procurar o arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="33db1-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="33db1-176">Clique o `Start` botão.</span><span class="sxs-lookup"><span data-stu-id="33db1-176">Click the `Start` button.</span></span> <span data-ttu-id="33db1-177">O `LinesCounted` botão deve começar a incrementar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="33db1-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="33db1-178">O aplicativo exibirá a mensagem "Finished Counting" quando estiver pronto.</span><span class="sxs-lookup"><span data-stu-id="33db1-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="33db1-179">Para testar o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="33db1-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="33db1-180">Pressione F5 para iniciar o aplicativo e insira a arquivo nome e procure uma palavra como descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="33db1-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="33db1-181">Certifique-se de que o arquivo escolhido é grande o suficiente para garantir que você tenha tempo para cancelar o procedimento antes de ser concluído.</span><span class="sxs-lookup"><span data-stu-id="33db1-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="33db1-182">Clique o `Start` botão para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33db1-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="33db1-183">Clique o `Cancel` botão.</span><span class="sxs-lookup"><span data-stu-id="33db1-183">Click the `Cancel` button.</span></span> <span data-ttu-id="33db1-184">O aplicativo deve parar de contar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="33db1-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="33db1-185">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="33db1-185">Next Steps</span></span>  
 <span data-ttu-id="33db1-186">Este aplicativo contém um tratamento de erros básicos.</span><span class="sxs-lookup"><span data-stu-id="33db1-186">This application contains some basic error handling.</span></span> <span data-ttu-id="33db1-187">Ele detecta cadeias de caracteres de pesquisa em branco.</span><span class="sxs-lookup"><span data-stu-id="33db1-187">It detects blank search strings.</span></span> <span data-ttu-id="33db1-188">Você pode fazer esse programa mais robusto manipulando outros erros, como exceder o número máximo de palavras ou linhas que podem ser contadas.</span><span class="sxs-lookup"><span data-stu-id="33db1-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33db1-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33db1-189">See Also</span></span>  
 <span data-ttu-id="33db1-190">[Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="33db1-190">[Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="33db1-191"> [Passo a passo: Criando um componente Multithreaded simples com o Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span><span class="sxs-lookup"><span data-stu-id="33db1-191"> [Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span></span>  
<span data-ttu-id="33db1-192"> [Como realizar e cancelar a assinatura de eventos](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="33db1-192"> [How to: Subscribe to and Unsubscribe from Events](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span></span>
