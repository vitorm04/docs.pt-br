---
title: "Como esta chamada n&#227;o &#233; aguardada, o m&#233;todo atual continua sendo executado antes da chamada ser conclu&#237;da | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42358"
  - "vbc42358"
helpviewer_keywords: 
  - "BC42358"
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como esta chamada n&#227;o &#233; aguardada, o m&#233;todo atual continua sendo executado antes da chamada ser conclu&#237;da
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como esta chamada não é aguardada, a execução do método atual continua antes da chamada é concluída. Considere a possibilidade de aplicar o operador 'Await' para o resultado da chamada.  
  
 O método atual chama um método async que retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601> e não se aplica a [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador para o resultado. A chamada para o método assíncrono inicia uma tarefa assíncrona. No entanto, porque nenhum `Await` operador é aplicado, o programa continua sem esperar que a tarefa seja concluída. Na maioria dos casos, esse comportamento não é esperado. Geralmente os outros aspectos do método de chamada dependem dos resultados da chamada ou, no mínimo, o método chamado é esperado para ser concluída antes de retornar do método que contém a chamada.  
  
 Igualmente importante é o que acontece com exceções que são geradas em um método assíncrono chamado. Uma exceção é acionada em um método que retorna um <xref:System.Threading.Tasks.Task> ou  <xref:System.Threading.Tasks.Task%601> é armazenado na tarefa retornada. Se você não esperar a tarefa ou verificar explicitamente se há exceções, a exceção será perdida. Se você esperar a tarefa, sua exceção será emitida novamente.  
  
 Como prática recomendada, você deve sempre espera a chamada.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42358  
  
### Para resolver este aviso  
  
-   Você deve considerar suprimir o aviso somente se você tiver certeza de que você não deseja aguardar a chamada assíncrona seja concluída e que o método chamado não gera nenhuma exceção. Nesse caso, você pode suprimir o aviso atribuindo o resultado da tarefa da chamada para uma variável.  
  
     O exemplo a seguir mostra como fazer com que o aviso, como suprimir a ele e a espera a chamada.  
  
    ```vb  
    Async Function CallingMethodAsync() As Task  
  
        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
        ' Variable delay is used to slow down the called method so that you  
        ' can distinguish between awaiting and not awaiting in the program's output.   
        ' You can adjust the value to produce the output that this topic shows   
        ' after the code.  
        Dim delay = 5000  
  
        ' Call #1.  
        ' Call an async method. Because you don't await it, its completion isn't   
        ' coordinated with the current method, CallingMethodAsync.  
        ' The following line causes the warning.  
        CalledMethodAsync(delay)  
  
        ' Call #2.  
        ' To suppress the warning without awaiting, you can assign the   
        ' returned task to a variable. The assignment doesn't change how  
        ' the program runs. However, the recommended practice is always to  
        ' await a call to an async method.  
        ' Replace Call #1 with the following line.  
        'Task delayTask = CalledMethodAsync(delay)  
  
        ' Call #3  
        ' To contrast with an awaited call, replace the unawaited call   
        ' (Call #1 or Call #2) with the following awaited call. The best   
        ' practice is to await the call.  
  
        'Await CalledMethodAsync(delay)  
  
        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
        ' continues to run and, in this example, finishes its work and returns  
        ' to its caller.  
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
    End Function  
  
    Async Function CalledMethodAsync(howLong As Integer) As Task  
  
        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
        ' Slow the process down a little so you can distinguish between awaiting  
        ' and not awaiting. Adjust the value for howLong if necessary.  
        Await Task.Delay(howLong)  
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
    End Function  
  
    ```  
  
     No exemplo, se você escolher chamar n º 1 ou chamar n º 2, o método assíncrono unawaited \(`CalledMethodAsync`\) é concluída após os dois seu chamador \(`CallingMethodAsync`\) e o chamador do chamador \(`StartButton_Click`\) forem concluídas. A última linha na saída a seguir mostra quando termina o método chamado. Entrada e saída do manipulador de eventos chama `CallingMethodAsync` no exemplo completo está marcado na saída.  
  
    ```  
  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## Exemplo  
 O seguinte aplicativo do Windows Presentation Foundation \(WPF\) contém os métodos do exemplo anterior. As etapas a seguir configuram o aplicativo.  
  
1.  Criar um aplicativo WPF e nomeie\-o `AsyncWarning`.  
  
2.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
     Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**, e, em seguida, escolha **Exibir código**.  
  
3.  Substitua o código no **XAML** exibição de MainWindow. XAML com o código a seguir.  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />  
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
        </Grid>  
    </Window>  
  
    ```  
  
     Uma janela simple que contém um botão e uma caixa de texto aparece no **Design** exibição de MainWindow. XAML.  
  
     Para obter mais informações sobre o Designer XAML, consulte [Criando uma interface de usuário usando o Designer XAML](/visual-studio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Para obter informações sobre como criar sua própria interface do usuário simple, consulte o "para criar um aplicativo WPF" e "para criar um simples MainWindow WPF" seções de [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
4.  Substitua o código em MainWindow.xaml.vb com o código a seguir.  
  
    ```vb  
  
    Class MainWindow   
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."  
            Await CallingMethodAsync()  
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."  
        End Sub  
  
        Async Function CallingMethodAsync() As Task  
  
            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
            ' Variable delay is used to slow down the called method so that you  
            ' can distinguish between awaiting and not awaiting in the program's output.   
            ' You can adjust the value to produce the output that this topic shows   
            ' after the code.  
            Dim delay = 5000  
  
            ' Call #1.  
            ' Call an async method. Because you don't await it, its completion isn't   
            ' coordinated with the current method, CallingMethodAsync.  
            ' The following line causes the warning.  
            CalledMethodAsync(delay)  
  
            ' Call #2.  
            ' To suppress the warning without awaiting, you can assign the   
            ' returned task to a variable. The assignment doesn't change how  
            ' the program runs. However, the recommended practice is always to  
            ' await a call to an async method.  
  
            ' Replace Call #1 with the following line.  
            'Task delayTask = CalledMethodAsync(delay)  
  
            ' Call #3  
            ' To contrast with an awaited call, replace the unawaited call   
            ' (Call #1 or Call #2) with the following awaited call. The best   
            ' practice is to await the call.  
  
            'Await CalledMethodAsync(delay)  
  
            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
            ' continues to run and, in this example, finishes its work and returns  
            ' to its caller.  
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
        End Function  
  
        Async Function CalledMethodAsync(howLong As Integer) As Task  
  
            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
            ' Slow the process down a little so you can distinguish between awaiting  
            ' and not awaiting. Adjust the value for howLong if necessary.  
            Await Task.Delay(howLong)  
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
        End Function  
  
    End Class  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    '     Task.Delay is finished--returning from called method.  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '     Task.Delay is finished--returning from called method.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    ```  
  
5.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
     A saída esperada é exibido no final do código.  
  
## Consulte também  
 [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)