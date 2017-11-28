---
title: "Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72d6e9ab42ca270ebe0691be23ebe181b973620d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="c8353-102">Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="c8353-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="c8353-103">Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que pesquisa um arquivo de texto para ocorrências de uma palavra.</span><span class="sxs-lookup"><span data-stu-id="c8353-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="c8353-104">Ele demonstra:</span><span class="sxs-lookup"><span data-stu-id="c8353-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="c8353-105">Defina uma classe com um método que possa ser chamado pelo componente <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="c8353-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="c8353-106">Manipular eventos gerados pelo componente <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="c8353-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="c8353-107">Iniciar um componente <xref:System.ComponentModel.BackgroundWorker> para executar um método.</span><span class="sxs-lookup"><span data-stu-id="c8353-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="c8353-108">Implementar um botão `Cancel` que interrompe o componente <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="c8353-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="c8353-109">Para criar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="c8353-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="c8353-110">Abra um novo projeto de Aplicativo do Windows Forms do C# e crie um formulário chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c8353-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="c8353-111">Adicione dois botões e quatro caixas de texto a `Form1`.</span><span class="sxs-lookup"><span data-stu-id="c8353-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="c8353-112">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8353-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c8353-113">Objeto</span><span class="sxs-lookup"><span data-stu-id="c8353-113">Object</span></span>|<span data-ttu-id="c8353-114">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c8353-114">Property</span></span>|<span data-ttu-id="c8353-115">Configuração</span><span class="sxs-lookup"><span data-stu-id="c8353-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="c8353-116">Primeiro botão</span><span class="sxs-lookup"><span data-stu-id="c8353-116">First button</span></span>|<span data-ttu-id="c8353-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-117">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-118">Iniciar, Iniciar</span><span class="sxs-lookup"><span data-stu-id="c8353-118">Start, Start</span></span>|  
    |<span data-ttu-id="c8353-119">Segundo botão</span><span class="sxs-lookup"><span data-stu-id="c8353-119">Second button</span></span>|<span data-ttu-id="c8353-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-120">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-121">Cancelar, Cancelar</span><span class="sxs-lookup"><span data-stu-id="c8353-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="c8353-122">Primeira caixa de texto</span><span class="sxs-lookup"><span data-stu-id="c8353-122">First text box</span></span>|<span data-ttu-id="c8353-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-123">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="c8353-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="c8353-125">Segunda caixa de texto</span><span class="sxs-lookup"><span data-stu-id="c8353-125">Second text box</span></span>|<span data-ttu-id="c8353-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-126">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="c8353-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="c8353-128">Terceira caixa de texto</span><span class="sxs-lookup"><span data-stu-id="c8353-128">Third text box</span></span>|<span data-ttu-id="c8353-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-129">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="c8353-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="c8353-131">Quarta caixa de texto</span><span class="sxs-lookup"><span data-stu-id="c8353-131">Fourth text box</span></span>|<span data-ttu-id="c8353-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="c8353-132">`Name`, `Text`</span></span>|<span data-ttu-id="c8353-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="c8353-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="c8353-134">Adicione um rótulo ao lado de cada caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="c8353-134">Add a label next to each text box.</span></span> <span data-ttu-id="c8353-135">Defina a propriedade `Text` para cada rótulo conforme mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8353-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="c8353-136">Objeto</span><span class="sxs-lookup"><span data-stu-id="c8353-136">Object</span></span>|<span data-ttu-id="c8353-137">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c8353-137">Property</span></span>|<span data-ttu-id="c8353-138">Configuração</span><span class="sxs-lookup"><span data-stu-id="c8353-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="c8353-139">Primeiro rótulo</span><span class="sxs-lookup"><span data-stu-id="c8353-139">First label</span></span>|`Text`|<span data-ttu-id="c8353-140">Arquivo de Origem</span><span class="sxs-lookup"><span data-stu-id="c8353-140">Source File</span></span>|  
    |<span data-ttu-id="c8353-141">Segundo rótulo</span><span class="sxs-lookup"><span data-stu-id="c8353-141">Second label</span></span>|`Text`|<span data-ttu-id="c8353-142">Comparar cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8353-142">Compare String</span></span>|  
    |<span data-ttu-id="c8353-143">Terceiro rótulo</span><span class="sxs-lookup"><span data-stu-id="c8353-143">Third label</span></span>|`Text`|<span data-ttu-id="c8353-144">Palavras correspondentes</span><span class="sxs-lookup"><span data-stu-id="c8353-144">Matching Words</span></span>|  
    |<span data-ttu-id="c8353-145">Quarto rótulo</span><span class="sxs-lookup"><span data-stu-id="c8353-145">Fourth label</span></span>|`Text`|<span data-ttu-id="c8353-146">Linhas contadas</span><span class="sxs-lookup"><span data-stu-id="c8353-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="c8353-147">Para criar um componente BackgroundWorker e assinar seus eventos</span><span class="sxs-lookup"><span data-stu-id="c8353-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="c8353-148">Adicionar um componente <xref:System.ComponentModel.BackgroundWorker> da seção **Componentes** da **Caixa de ferramentas** ao formulário.</span><span class="sxs-lookup"><span data-stu-id="c8353-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="c8353-149">Ele será exibido na bandeja de componentes do formulário.</span><span class="sxs-lookup"><span data-stu-id="c8353-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="c8353-150">Defina as propriedades a seguir ao objeto backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="c8353-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="c8353-151">Propriedade</span><span class="sxs-lookup"><span data-stu-id="c8353-151">Property</span></span>|<span data-ttu-id="c8353-152">Configuração</span><span class="sxs-lookup"><span data-stu-id="c8353-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="c8353-153">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8353-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="c8353-154">verdadeiro</span><span class="sxs-lookup"><span data-stu-id="c8353-154">True</span></span>|  
  
3.  <span data-ttu-id="c8353-155">Assine os eventos do objeto backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="c8353-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="c8353-156">Na parte superior da janela **Propriedades**, clique no ícone **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="c8353-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="c8353-157">Clique duas vezes no evento `RunWorkerCompleted` para criar um método de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c8353-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="c8353-158">Faça o mesmo para os eventos `ProgressChanged` e `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="c8353-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="c8353-159">Para definir o método que será executado em um thread separado</span><span class="sxs-lookup"><span data-stu-id="c8353-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="c8353-160">No menu **Projeto**, escolha **Adicionar Classe** para adicionar uma classe ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c8353-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="c8353-161">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="c8353-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="c8353-162">Selecione **Classe** na janela de modelos e insira `Words.cs` no campo de nome.</span><span class="sxs-lookup"><span data-stu-id="c8353-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="c8353-163">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="c8353-163">Click **Add**.</span></span> <span data-ttu-id="c8353-164">A classe `Words` é exibida.</span><span class="sxs-lookup"><span data-stu-id="c8353-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="c8353-165">Adicione o seguinte código à classe `Words`:</span><span class="sxs-lookup"><span data-stu-id="c8353-165">Add the following code to the `Words` class:</span></span>  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="c8353-166">Para manipular eventos do thread</span><span class="sxs-lookup"><span data-stu-id="c8353-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="c8353-167">Adicione os seguintes manipuladores de eventos ao seu formulário principal:</span><span class="sxs-lookup"><span data-stu-id="c8353-167">Add the following event handlers to your main form:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="c8353-168">Para iniciar e chamar um novo thread que executa o método WordCount</span><span class="sxs-lookup"><span data-stu-id="c8353-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="c8353-169">Adicione os procedimentos a seguir ao programa:</span><span class="sxs-lookup"><span data-stu-id="c8353-169">Add the following procedures to your program:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  <span data-ttu-id="c8353-170">Chame o método `StartThread` no botão `Start` no formulário:</span><span class="sxs-lookup"><span data-stu-id="c8353-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="c8353-171">Para implementar um botão Cancelar que para o thread</span><span class="sxs-lookup"><span data-stu-id="c8353-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="c8353-172">Chame o procedimento `StopThread` do manipulador de eventos `Click` para o botão `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="c8353-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="c8353-173">Testes</span><span class="sxs-lookup"><span data-stu-id="c8353-173">Testing</span></span>  
 <span data-ttu-id="c8353-174">Agora você pode testar o aplicativo para verificar se ele funciona corretamente.</span><span class="sxs-lookup"><span data-stu-id="c8353-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="c8353-175">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8353-175">To test the application</span></span>  
  
1.  <span data-ttu-id="c8353-176">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8353-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="c8353-177">Quando o formulário for exibido, insira o caminho do arquivo que deseja testar na caixa `sourceFile`.</span><span class="sxs-lookup"><span data-stu-id="c8353-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="c8353-178">Por exemplo, supondo que o arquivo de teste seja chamado Test.txt, insira C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="c8353-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="c8353-179">Na segunda caixa de texto, digite uma palavra ou frase para o aplicativo pesquisar no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="c8353-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="c8353-180">Clique no botão `Start`.</span><span class="sxs-lookup"><span data-stu-id="c8353-180">Click the `Start` button.</span></span> <span data-ttu-id="c8353-181">O botão `LinesCounted` deve começar a incrementar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="c8353-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="c8353-182">O aplicativo exibirá a mensagem "Contagem Finalizada" quando tiver terminado.</span><span class="sxs-lookup"><span data-stu-id="c8353-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="c8353-183">Para testar o botão Cancelar</span><span class="sxs-lookup"><span data-stu-id="c8353-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="c8353-184">Pressione F5 para iniciar o aplicativo e insira o nome do arquivo e a palavra de pesquisa conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="c8353-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="c8353-185">Certifique-se de que o arquivo escolhido seja grande o suficiente para garantir que você terá tempo para cancelar o procedimento antes de ele ser concluído.</span><span class="sxs-lookup"><span data-stu-id="c8353-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="c8353-186">Clique no botão `Start` para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8353-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="c8353-187">Clique no botão `Cancel`.</span><span class="sxs-lookup"><span data-stu-id="c8353-187">Click the `Cancel` button.</span></span> <span data-ttu-id="c8353-188">O aplicativo deve parar de contar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="c8353-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c8353-189">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c8353-189">Next Steps</span></span>  
 <span data-ttu-id="c8353-190">Este aplicativo contém um tratamento de erro básico.</span><span class="sxs-lookup"><span data-stu-id="c8353-190">This application contains some basic error handling.</span></span> <span data-ttu-id="c8353-191">Ele detecta cadeias de caracteres de pesquisa em branco.</span><span class="sxs-lookup"><span data-stu-id="c8353-191">It detects blank search strings.</span></span> <span data-ttu-id="c8353-192">Você pode tornar esse programa mais robusto tratando outros erros, como exceder o número máximo de palavras ou linhas que podem ser contadas.</span><span class="sxs-lookup"><span data-stu-id="c8353-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8353-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8353-193">See Also</span></span>  
 [<span data-ttu-id="c8353-194">Threading (C#)</span><span class="sxs-lookup"><span data-stu-id="c8353-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="c8353-195">Como realizar e cancelar a assinatura de eventos</span><span class="sxs-lookup"><span data-stu-id="c8353-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
