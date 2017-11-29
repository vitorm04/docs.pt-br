---
title: Multithreading com o componente BackgroundWorker (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb0734b4bbf3f8bf5b27305754829f1a9f29f42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>Passo a passo: Multithreading com o componente BackgroundWorker (Visual Basic)
Este passo a passo demonstra como criar um aplicativo Windows Forms com multithread que pesquisa um arquivo de texto para ocorrências de uma palavra. Ele demonstra:  
  
-   Defina uma classe com um método que possa ser chamado pelo componente <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Manipular eventos gerados pelo componente <xref:System.ComponentModel.BackgroundWorker>.  
  
-   Iniciar um componente <xref:System.ComponentModel.BackgroundWorker> para executar um método.  
  
-   Implementar um botão `Cancel` que interrompe o componente <xref:System.ComponentModel.BackgroundWorker>.  
  
### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário  
  
1.  Abra um novo projeto de aplicativo Windows Forms Visual Basic e crie um formulário denominado `Form1`.  
  
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
  
2.  Defina as seguintes propriedades para o objeto BackgroundWorker1.  
  
    |Propriedade|Configuração|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|verdadeiro|  
    |`WorkerSupportsCancellation`|verdadeiro|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>Para definir o método que será executado em um thread separado  
  
1.  No menu **Projeto**, escolha **Adicionar Classe** para adicionar uma classe ao projeto. A caixa de diálogo **Adicionar Novo Item** é exibida.  
  
2.  Selecione **Classe** na janela de modelos e insira `Words.vb` no campo de nome.  
  
3.  Clique em **Adicionar**. A classe `Words` é exibida.  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>Para manipular eventos do thread  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>Para iniciar e chamar um novo thread que executa o método WordCount  
  
1.  Adicione os procedimentos a seguir ao programa:  
  
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
  
2.  Chame o método `StartThread` no botão `Start` no formulário:  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>Para implementar um botão Cancelar que para o thread  
  
-   Chame o procedimento `StopThread` do manipulador de eventos `Click` para o botão `Cancel`.  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
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
 [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [Passo a passo: Criação de um componente Multithreaded simples com o Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [Como realizar e cancelar a assinatura de eventos](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
