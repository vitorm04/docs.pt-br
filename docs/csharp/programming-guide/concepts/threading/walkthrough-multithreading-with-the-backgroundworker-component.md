---
title: "Passo a passo: Multithreading com o componente BackgroundWorker (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passo a passo: Multithreading com o componente BackgroundWorker (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que procura um arquivo de texto por ocorrências de uma palavra. Ele demonstra:  
  
-   Definir uma classe com um método que pode ser chamado pelo <xref:System.ComponentModel.BackgroundWorker> componente.  
  
-   Manipulação de eventos gerados pelo <xref:System.ComponentModel.BackgroundWorker> componente.  
  
-   Iniciando um <xref:System.ComponentModel.BackgroundWorker> componentes para executar um método.  
  
-   Implementando um `Cancel` botão que interrompe o <xref:System.ComponentModel.BackgroundWorker> componente.  
  
### Para criar a interface do usuário  
  
1.  Abra um novo projeto de aplicativo do c\# Windows Forms e criar um formulário chamado `Form1`.  
  
2.  Adicione dois botões e quatro caixas de texto para `Form1`.  
  
3.  Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|-----------------|------------------|  
    |Primeiro botão|`Name`, `Text`|Iniciar, início|  
    |Segundo botão|`Name`, `Text`|Cancelar, cancelar|  
    |Primeira caixa de texto|`Name`, `Text`|Arquivo de origem, ""|  
    |Segunda caixa de texto|`Name`, `Text`|CompareString, ""|  
    |Terceira caixa de texto|`Name`, `Text`|WordsCounted, "0"|  
    |Quarta caixa de texto|`Name`, `Text`|LinesCounted, "0"|  
  
4.  Adicione um rótulo ao lado de cada caixa de texto. Definir o `Text` propriedade para cada rótulo como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|-----------------|------------------|  
    |Primeiro rótulo|`Text`|Arquivo de Origem|  
    |Segundo rótulo|`Text`|Comparação de cadeia de caracteres|  
    |Terceiro rótulo|`Text`|Correspondência de palavras|  
    |Rótulo|`Text`|Linhas contadas|  
  
### Para criar um componente BackgroundWorker e assinar seus eventos  
  
1.  Adicionar um <xref:System.ComponentModel.BackgroundWorker> componente do **componentes** seção o **ToolBox** ao formulário. Ele será exibido na bandeja de componentes do formulário.  
  
2.  Defina as seguintes propriedades para o objeto backgroundWorker1.  
  
    |Propriedade|Configuração|  
    |-----------------|------------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
3.  Assine os eventos do objeto backgroundWorker1. Na parte superior do **propriedades** janela, clique o **eventos** ícone. Clique duas vezes o `RunWorkerCompleted` evento para criar um método de manipulador de eventos. Faça o mesmo para o `ProgressChanged` e `DoWork` eventos.  
  
### Para definir o método que será executado em um thread separado  
  
1.  Do **projeto** menu, escolha **Add Class** para adicionar uma classe ao projeto. O **Add New Item** caixa de diálogo é exibida.  
  
2.  Selecione **classe** da janela de modelos e digite `Words.cs` no campo nome.  
  
3.  Clique em **Adicionar**. O `Words` classe é exibida.  
  
4.  Adicione o seguinte código para o `Words` classe:  
  
    ```c#  
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
  
### Para manipular eventos do encadeamento  
  
-   Adicione os seguintes manipuladores de eventos ao seu formulário principal:  
  
    ```c#  
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
  
### Para iniciar e chamar um novo encadeamento que executa o método WordCount  
  
1.  Adicione os seguintes procedimentos para o seu programa:  
  
    ```c#  
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
  
2.  Chamar o `StartThread` método a partir de `Start` botão no formulário:  
  
    ```c#  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### Para implementar um botão Cancelar que para o encadeamento  
  
    -   Chamar o `StopThread` procedimento o `Click` manipulador de eventos para o `Cancel` botão.  
  
        ```c#  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## Teste  
 Agora você pode testar o aplicativo para verificar se que ele funciona corretamente.  
  
#### Para testar o aplicativo  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Quando o formulário for exibido, insira o caminho para o arquivo que você deseja testar a `sourceFile` caixa. Por exemplo, supondo que o arquivo de teste é chamado Test. txt, entre c:\\test.txt..  
  
3.  Na segunda caixa de texto, digite uma palavra ou frase para o aplicativo procurar o arquivo de texto.  
  
4.  Clique o `Start` botão. O `LinesCounted` botão deve começar a incrementar imediatamente. O aplicativo exibirá a mensagem "Finished Counting" quando estiver pronto.  
  
#### Para testar o botão Cancelar  
  
1.  Pressione F5 para iniciar o aplicativo e insira a arquivo nome e procure uma palavra como descrito no procedimento anterior. Certifique\-se de que o arquivo escolhido é grande o suficiente para garantir que você tenha tempo para cancelar o procedimento antes de ser concluído.  
  
2.  Clique o `Start` botão para iniciar o aplicativo.  
  
3.  Clique o `Cancel` botão. O aplicativo deve parar de contar imediatamente.  
  
## Próximas etapas  
 Este aplicativo contém um tratamento de erros básicos. Ele detecta cadeias de caracteres de pesquisa em branco. Você pode fazer esse programa mais robusto manipulando outros erros, como exceder o número máximo de palavras ou linhas que podem ser contadas.  
  
## Consulte também  
 [Threading \(c\#\)](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como realizar e cancelar a assinatura de eventos](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)