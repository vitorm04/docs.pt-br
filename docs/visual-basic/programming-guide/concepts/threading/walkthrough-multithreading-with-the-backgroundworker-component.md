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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3686eb230349876f6cfffd2ad94ed1f547779ab1
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>Passo a passo: Multithreading com o componente BackgroundWorker (Visual Basic)
Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que procura um arquivo de texto por ocorrências de uma palavra. Ele demonstra:  
  
-   Definir uma classe com um método que pode ser chamado pelo <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Manipulação de eventos gerados pelo <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Iniciando um <xref:System.ComponentModel.BackgroundWorker>componentes para executar um método.</xref:System.ComponentModel.BackgroundWorker>  
  
-   Implementando um `Cancel` botão que interrompe o <xref:System.ComponentModel.BackgroundWorker>componente.</xref:System.ComponentModel.BackgroundWorker>  
  
### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário  
  
1.  Abra um novo projeto de aplicativo do Windows Forms do Visual Basic e crie um formulário chamado `Form1`.  
  
2.  Adicione dois botões e quatro caixas de texto para `Form1`.  
  
3.  Nomeie os objetos como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |Primeiro botão|`Name`, `Text`|Iniciar, início|  
    |Segundo botão|`Name`, `Text`|Cancelar, cancelar|  
    |Primeira caixa de texto|`Name`, `Text`|Arquivo de origem, ""|  
    |Segunda caixa de texto|`Name`, `Text`|CompareString, ""|  
    |Terceira caixa de texto|`Name`, `Text`|WordsCounted, "0"|  
    |Quarta caixa de texto|`Name`, `Text`|LinesCounted, "0"|  
  
4.  Adicione um rótulo ao lado de cada caixa de texto. Definir o `Text` propriedade para cada rótulo como mostrado na tabela a seguir.  
  
    |Objeto|Propriedade|Configuração|  
    |------------|--------------|-------------|  
    |Primeiro rótulo|`Text`|Arquivo de Origem|  
    |Segundo rótulo|`Text`|Comparação de cadeia de caracteres|  
    |Terceiro rótulo|`Text`|Correspondência de palavras|  
    |Rótulo|`Text`|Linhas contadas|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>Para criar um componente BackgroundWorker e assinar seus eventos  
  
1.  Adicionar um <xref:System.ComponentModel.BackgroundWorker>componente do **componentes** seção o **ToolBox** ao formulário.</xref:System.ComponentModel.BackgroundWorker> Ele será exibido na bandeja de componentes do formulário.  
  
2.  Defina as seguintes propriedades para o objeto BackgroundWorker1.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|verdadeiro|  
    |`WorkerSupportsCancellation`|verdadeiro|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Para definir o método que será executado em um thread separado  
  
1.  Do **projeto** menu, escolha **Adicionar classe** para adicionar uma classe ao projeto. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
2.  Selecione **classe** da janela de modelos e digite `Words.vb` no campo nome.  
  
3.  Clique em **Adicionar**. O `Words` classe é exibida.  
  
4.  Adicione o seguinte código à classe `Words`:  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>Para manipular eventos do encadeamento  
  
-   Adicione os seguintes manipuladores de eventos ao seu formulário principal:  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Para iniciar e chamar um novo encadeamento que executa o método WordCount  
  
1.  Adicione os seguintes procedimentos para o seu programa:  
  
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
  
2.  Chamar o `StartThread` método a partir de `Start` botão no formulário:  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Para implementar um botão Cancelar que para o encadeamento  
  
-   Chamar o `StopThread` procedimento o `Click` manipulador de eventos para o `Cancel` botão.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>Testes  
 Agora você pode testar o aplicativo para verificar se que ele funciona corretamente.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5 para executar o aplicativo.  
  
2.  Quando o formulário for exibido, insira o caminho para o arquivo que você deseja testar a `sourceFile` caixa. Por exemplo, supondo que o arquivo de teste é chamado Test. txt, entre c:\test.txt..  
  
3.  Na segunda caixa de texto, digite uma palavra ou frase para o aplicativo procurar o arquivo de texto.  
  
4.  Clique o `Start` botão. O `LinesCounted` botão deve começar a incrementar imediatamente. O aplicativo exibirá a mensagem "Finished Counting" quando estiver pronto.  
  
#### <a name="to-test-the-cancel-button"></a>Para testar o botão Cancelar  
  
1.  Pressione F5 para iniciar o aplicativo e insira a arquivo nome e procure uma palavra como descrito no procedimento anterior. Certifique-se de que o arquivo escolhido é grande o suficiente para garantir que você tenha tempo para cancelar o procedimento antes de ser concluído.  
  
2.  Clique o `Start` botão para iniciar o aplicativo.  
  
3.  Clique o `Cancel` botão. O aplicativo deve parar de contar imediatamente.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este aplicativo contém um tratamento de erros básicos. Ele detecta cadeias de caracteres de pesquisa em branco. Você pode fazer esse programa mais robusto manipulando outros erros, como exceder o número máximo de palavras ou linhas que podem ser contadas.  
  
## <a name="see-also"></a>Consulte também  
 [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [Passo a passo: Criando um componente Multithreaded simples com o Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)   
 [Como realizar e cancelar a assinatura de eventos](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
