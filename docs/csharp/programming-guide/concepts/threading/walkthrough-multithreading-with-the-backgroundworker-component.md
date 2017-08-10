---
title: "Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 541a1ec788c337eea9965b8a46155e5c6606ea2f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)
Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que pesquisa um arquivo de texto para ocorrências de uma palavra. Ele demonstra:  
  
-   Defina uma classe com um método que possa ser chamado pelo componente <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Manipular eventos gerados pelo componente <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Iniciar um componente <xref:System.ComponentModel.BackgroundWorker> para executar um método.  
  
-   Implementar um botão `Cancel` que interrompe o componente <xref:System.ComponentModel.BackgroundWorker>.  
  
### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário  
  
1.  Abra um novo projeto de Aplicativo do Windows Forms do C# e crie um formulário chamado `Form1`.  
  
2.  Adicione dois botões e quatro caixas de texto a `Form1`.  
  
3.  Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |Primeiro botão|`Name`, `Text`|Iniciar, Iniciar|  
    |Segundo botão|`Name`, `Text`|Cancelar, Cancelar|  
    |Primeira caixa de texto|`Name`, `Text`|SourceFile, ""|  
    |Segunda caixa de texto|`Name`, `Text`|CompareString, ""|  
    |Terceira caixa de texto|`Name`, `Text`|WordsCounted, "0"|  
    |Quarta caixa de texto|`Name`, `Text`|LinesCounted, "0"|  
  
4.  Adicione um rótulo ao lado de cada caixa de texto. Defina a propriedade `Text` para cada rótulo conforme mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |Primeiro rótulo|`Text`|Arquivo de Origem|  
    |Segundo rótulo|`Text`|Comparar cadeia de caracteres|  
    |Terceiro rótulo|`Text`|Palavras correspondentes|  
    |Quarto rótulo|`Text`|Linhas contadas|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>Para criar um componente BackgroundWorker e assinar seus eventos  
  
1.  Adicionar um componente <xref:System.ComponentModel.BackgroundWorker> da seção **Componentes** da **Caixa de ferramentas** ao formulário. Ele será exibido na bandeja de componentes do formulário.  
  
2.  Defina as propriedades a seguir ao objeto backgroundWorker1.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|verdadeiro|  
    |`WorkerSupportsCancellation`|verdadeiro|  
  
3.  Assine os eventos do objeto backgroundWorker1. Na parte superior da janela **Propriedades**, clique no ícone **Eventos**. Clique duas vezes no evento `RunWorkerCompleted` para criar um método de manipulador de eventos. Faça o mesmo para os eventos `ProgressChanged` e `DoWork`.  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Para definir o método que será executado em um thread separado  
  
1.  No menu **Projeto**, escolha **Adicionar Classe** para adicionar uma classe ao projeto. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
2.  Selecione **Classe** na janela de modelos e insira `Words.cs` no campo de nome.  
  
3.  Clique em **Adicionar**. A classe `Words` é exibida.  
  
4.  Adicione o seguinte código à classe `Words`:  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>Para manipular eventos do thread  
  
-   Adicione os seguintes manipuladores de eventos ao seu formulário principal:  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Para iniciar e chamar um novo thread que executa o método WordCount  
  
1.  Adicione os procedimentos a seguir ao programa:  
  
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
  
2.  Chame o método `StartThread` no botão `Start` no formulário:  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Para implementar um botão Cancelar que para o thread  
  
    -   Chame o procedimento `StopThread` do manipulador de eventos `Click` para o botão `Cancel`.  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a>Testes  
 Agora você pode testar o aplicativo para verificar se ele funciona corretamente.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Quando o formulário for exibido, insira o caminho do arquivo que deseja testar na caixa `sourceFile`. Por exemplo, supondo que o arquivo de teste seja chamado Test.txt, insira C:\Test.txt.  
  
3.  Na segunda caixa de texto, digite uma palavra ou frase para o aplicativo pesquisar no arquivo de texto.  
  
4.  Clique no botão `Start`. O botão `LinesCounted` deve começar a incrementar imediatamente. O aplicativo exibirá a mensagem "Contagem Finalizada" quando tiver terminado.  
  
#### <a name="to-test-the-cancel-button"></a>Para testar o botão Cancelar  
  
1.  Pressione F5 para iniciar o aplicativo e insira o nome do arquivo e a palavra de pesquisa conforme descrito no procedimento anterior. Certifique-se de que o arquivo escolhido seja grande o suficiente para garantir que você terá tempo para cancelar o procedimento antes de ele ser concluído.  
  
2.  Clique no botão `Start` para iniciar o aplicativo.  
  
3.  Clique no botão `Cancel`. O aplicativo deve parar de contar imediatamente.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este aplicativo contém um tratamento de erro básico. Ele detecta cadeias de caracteres de pesquisa em branco. Você pode tornar esse programa mais robusto tratando outros erros, como exceder o número máximo de palavras ou linhas que podem ser contadas.  
  
## <a name="see-also"></a>Consulte também  
 [Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 [Como realizar e cancelar a assinatura de eventos](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

