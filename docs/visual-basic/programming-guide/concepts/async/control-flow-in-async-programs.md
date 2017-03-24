---
title: "Controle de fluxo em programas assíncronos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
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
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a>Fluxo de controle em programas assíncronos (Visual Basic)
Você pode escrever e manter assíncronos programas mais facilmente usando o `Async` e `Await` palavras-chave. No entanto, os resultados podem surpreendê-lo se você não entender o funcionamento do seu programa. Este rastreamentos de tópico o fluxo de controle por meio de um programa assíncrono simples para mostrar a você quando o controle se move de um método para outro e quais informações é transferido de cada vez.  
  
> [!NOTE]
>  O `Async` e `Await` palavras-chave foram introduzidas no Visual Studio 2012.  
  
 Em geral, você pode marcar métodos que contêm código assíncrono com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Em um método marcado com um modificador assíncrono, você pode usar um [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operador para especificar onde o método faz uma pausa para esperar por um processo assíncrono chamado concluir. Para obter mais informações, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 O exemplo a seguir usa os métodos assíncronos para baixar o conteúdo de um site especificado como uma cadeia de caracteres e exibir o comprimento da cadeia de caracteres. O exemplo contém dois métodos a seguir.  
  
-   `startButton_Click`, que chama `AccessTheWebAsync` e exibe o resultado.  
  
-   `AccessTheWebAsync`, que baixa o conteúdo de um site como uma cadeia de caracteres e retorna o comprimento da cadeia de caracteres. `AccessTheWebAsync`usa assíncrona <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, para baixar o conteúdo.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient>  
  
 Numeradas exibição linhas aparecem em pontos estratégicos em todo o programa para ajudá-lo a entender como o programa é executado e explicar o que acontece em cada ponto marcado. Exibir linhas são rotulados como "Um"a "seis." Os rótulos de representam a ordem na qual o programa atingir estas linhas de código.  
  
 O código a seguir mostra uma estrutura de tópicos do programa.  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
    End Sub  
  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' TWO  
        Dim client As HttpClient = New HttpClient()   
        Dim getStringTask As Task(Of String) =   
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
  
```  
  
 Todos os locais de rotulado, "Um"a "seis," exibe informações sobre o estado atual do programa. A seguinte saída é produzida.  
  
```  
  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a>Configurar o Programa  
 Você pode baixar o código que usa este tópico do MSDN, ou você pode criá-la sozinho.  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
### <a name="download-the-program"></a>Baixar o Programa  
 Você pode baixar o aplicativo para este tópico de [exemplo de assincronia: fluxo de controle em programas assíncronos](http://go.microsoft.com/fwlink/?LinkId=255285). As etapas a seguir abrirem e executam o programa.  
  
1.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.  
  
3.  Navegue até a pasta que contém o código de exemplo descompactado, abra o arquivo de solução (. sln) e pressione a tecla F5 para compilar e executar o projeto.  
  
### <a name="build-the-program-yourself"></a>Compilar o Programa Sozinho  
 O projeto Windows Presentation Foundation (WPF) a seguir contém o código de exemplo neste tópico.  
  
 Para executar o projeto, execute as seguintes etapas:  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **modelos instalados** painel, escolha **Visual Basic**e, em seguida, escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  Digite `AsyncTracer` como o nome do projeto e, em seguida, escolha o **Okey** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
5.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
     Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **Exibir código**.  
  
6.  No **XAML** exibir de MainWindow. XAML, substitua o código pelo código a seguir.  
  
    ```vb  
    <Window  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"  
        Title="Control Flow Trace" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** exibição de MainWindow. XAML.  
  
7.  Adicione uma referência para <xref:System.Net.Http>.</xref:System.Net.Http>  
  
8.  Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.  
  
9. Em MainWindow.xaml.vb, substitua o código com o código a seguir.  
  
    ```vb  
    ' Add an Imports statement and a reference for System.Net.Http.  
    Imports System.Net.Http  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
            ' The display lines in the example lead you through the control shifts.  
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &  
                "           Calling AccessTheWebAsync." & vbCrLf  
  
            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is started." & vbCrLf &  
                "           About to await getLengthTask -- no caller to return to." & vbCrLf  
  
            Dim contentLength As Integer = Await getLengthTask  
  
            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is finished." & vbCrLf &  
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &  
                "           About to display contentLength and exit." & vbCrLf  
  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
        End Sub  
  
        Async Function AccessTheWebAsync() As Task(Of Integer)  
  
            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."  
  
            ' Declare an HttpClient object.  
            Dim client As HttpClient = New HttpClient()  
  
            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf  
  
            ' GetStringAsync returns a Task(Of String).   
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &  
                "           Task getStringTask is started."  
  
            ' AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
            ResultsTextBox.Text &=  
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf  
  
            ' Retrieve the website contents when task is complete.  
            Dim urlContents As String = Await getStringTask  
  
            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &  
                vbCrLf & "           Task getStringTask is complete." &  
                vbCrLf & "           Processing the return statement." &  
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf  
  
            Return urlContents.Length  
        End Function  
  
    End Class  
    ```  
  
10. Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.  
  
     A saída a seguir deve aparecer.  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a>Rastrear o Programa  
  
### <a name="steps-one-and-two"></a>Etapas UM e DOIS  
 As duas primeiras exibir linhas rastrear o caminho como `startButton_Click` chamadas `AccessTheWebAsync`, e `AccessTheWebAsync` chama o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient> de assíncrono A imagem a seguir descreve as chamadas de método.  
  
 ![As etapas um e dois](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 O tipo de retorno de ambos `AccessTheWebAsync` e `client.GetStringAsync` é <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> Para `AccessTheWebAsync`, TResult é um inteiro. Para `GetStringAsync`, TResult é uma cadeia de caracteres. Para obter mais informações sobre tipos de retorno de método assíncrono, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Um método assíncrono de retorno de tarefas retorna uma instância de tarefa quando o controle passa para o chamador. O controle retorna de um método assíncrono para seu chamador quando um `Await` operador é encontrado no método chamado ou quando termina o método chamado. Exibir linhas que são rotulados como "Três"através de "seis" Esta parte do processo de rastreamento.  
  
### <a name="step-three"></a>Etapa TRÊS  
 Em `AccessTheWebAsync`, o método assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>é chamado para baixar o conteúdo de página da Web de destino.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> O controle retorna de `client.GetStringAsync` para `AccessTheWebAsync` quando `client.GetStringAsync` retorna.  
  
 O `client.GetStringAsync` método retorna uma tarefa de cadeia de caracteres que é atribuída para a `getStringTask` variável em `AccessTheWebAsync`. A linha do programa de exemplo a seguir mostra a chamada para `client.GetStringAsync` e a atribuição.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Você pode imaginar a tarefa como uma promessa por `client.GetStringAsync` para produzir uma cadeia de caracteres real eventualmente. Enquanto isso, se `AccessTheWebAsync` tem trabalho a fazer que não depende da cadeia de caracteres prometida de `client.GetStringAsync`, que o trabalho possa continuar enquanto `client.GetStringAsync` espera. No exemplo, as seguintes linhas de saída, que são rotuladas "Três", representam a oportunidade de fazer o trabalho independente  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 A instrução a seguir suspende o andamento em `AccessTheWebAsync` quando `getStringTask` é esperado.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 A imagem a seguir mostra o fluxo de controle de `client.GetStringAsync` para a atribuição ao `getStringTask` e da criação de `getStringTask` para a aplicação de um operador de espera.  
  
 ![Etapa três](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-três")  
  
 A expressão await suspende `AccessTheWebAsync` até `client.GetStringAsync` retorna. Enquanto isso, o controle retorna para o chamador de `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Normalmente, você aguarda a chamada para um método assíncrono imediatamente. Por exemplo, a atribuição a seguir poderia substituir o código anterior que cria e, em seguida, aguarda `getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  Neste tópico, o operador de espera é aplicado posteriormente para acomodar as linhas de saída que marca o fluxo de controle por meio do programa.  
  
### <a name="step-four"></a>Etapa QUATRO  
 O declarados retornam o tipo de `AccessTheWebAsync` é `Task(Of Integer)`. Portanto, quando `AccessTheWebAsync` é suspenso, ele retorna uma tarefa de inteiro para `startButton_Click`. Você deve compreender que a tarefa retornada não é `getStringTask`. A tarefa retornada é uma nova tarefa de número inteiro que representa o que resta a ser feito no método suspenso, `AccessTheWebAsync`. A tarefa é uma promessa de `AccessTheWebAsync` para produzir um número inteiro, quando a tarefa for concluída.  
  
 A instrução a seguir atribui essa tarefa para o `getLengthTask` variável.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Como em `AccessTheWebAsync`, `startButton_Click` pode continuar com o trabalho que não depende dos resultados da tarefa assíncrona (`getLengthTask`) até que a tarefa é esperada. As seguintes linhas de saída representam esse trabalho.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Avançar na `startButton_Click` é suspensa quando `getLengthTask` é esperado. A seguinte instrução de atribuição suspende `startButton_Click` até `AccessTheWebAsync` for concluída.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 Na ilustração a seguir, as setas mostram o fluxo de controle da expressão await em `AccessTheWebAsync` para a atribuição de um valor para `getLengthTask`, seguido pelo processamento normal de `startButton_Click` até `getLengthTask` é esperado.  
  
 ![Etapa quatro](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace quatro")  
  
### <a name="step-five"></a>Etapa CINCO  
 Quando `client.GetStringAsync` sinaliza que está concluída, o processamento em `AccessTheWebAsync` é liberado da suspensão e pode continuar após a instrução de espera. As seguintes linhas de saída representam a continuação do processamento.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
 O operando da instrução return, `urlContents.Length`, é armazenado na tarefa que `AccessTheWebAsync` retorna. A expressão await recupera o valor de `getLengthTask` em `startButton_Click`.  
  
 A imagem a seguir mostra a transferência de controle após `client.GetStringAsync` (e `getStringTask`) forem concluídas.  
  
 ![Etapa cinco](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace cinco")  
  
 `AccessTheWebAsync`é executado para conclusão e o controle retorna ao `startButton_Click`, que está aguardando a conclusão.  
  
### <a name="step-six"></a>Etapa SEIS  
 Quando `AccessTheWebAsync` sinais for concluído, o processamento podem continuar após a instrução de espera em `startButton_Async`. Na verdade, o programa não tem mais nada para fazer.  
  
 As seguintes linhas de saída representam a continuação do processamento no `startButton_Async`:  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
 A expressão await recupera de `getLengthTask` o valor inteiro que é o operando da instrução return no `AccessTheWebAsync`. A instrução a seguir atribui o valor para o `contentLength` variável.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
 A imagem a seguir mostra o retorno do controle de `AccessTheWebAsync` para `startButton_Click`.  
  
 ![Etapa seis](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace seis")  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Exemplo de assincronia: Fluxo de controle em programas assíncronos (c# e Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)
