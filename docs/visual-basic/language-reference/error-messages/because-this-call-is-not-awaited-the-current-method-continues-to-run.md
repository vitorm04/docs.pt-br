---
title: Como esta chamada não é aguardada, o método atual continua sendo executado antes da chamada ser concluída
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0d0a5e7c50bacc657a3f54a7f08036ede59cbfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="28442-102">Como esta chamada não é aguardada, o método atual continua sendo executado antes da chamada ser concluída</span><span class="sxs-lookup"><span data-stu-id="28442-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="28442-103">Como esta chamada não era esperada, a execução do método atual continua antes da chamada ser concluída.</span><span class="sxs-lookup"><span data-stu-id="28442-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="28442-104">Considere a possibilidade de aplicar o operador 'Await' para o resultado da chamada.</span><span class="sxs-lookup"><span data-stu-id="28442-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="28442-105">O método atual chama um método assíncrono que retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601> e não se aplica a [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador para o resultado.</span><span class="sxs-lookup"><span data-stu-id="28442-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="28442-106">A chamada ao método assíncrono inicia uma tarefa assíncrona.</span><span class="sxs-lookup"><span data-stu-id="28442-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="28442-107">No entanto, como nenhum operador `Await` é aplicado, o programa continua sem esperar que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="28442-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="28442-108">Na maioria dos casos, esse comportamento não é esperado.</span><span class="sxs-lookup"><span data-stu-id="28442-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="28442-109">Geralmente, os outros aspectos do método de chamada dependem dos resultados da chamada ou, no mínimo, é esperado que o método chamado seja concluído antes de retornar do método que contém a chamada.</span><span class="sxs-lookup"><span data-stu-id="28442-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="28442-110">Igualmente importante é o que acontece com as exceções que são geradas no método assíncrono chamado.</span><span class="sxs-lookup"><span data-stu-id="28442-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="28442-111">Uma exceção que é gerada em um método que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> é armazenado na tarefa retornada.</span><span class="sxs-lookup"><span data-stu-id="28442-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="28442-112">Se você não aguardar a tarefa ou verificar explicitamente se há exceções, a exceção será perdida.</span><span class="sxs-lookup"><span data-stu-id="28442-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="28442-113">Se você aguardar a tarefa, a exceção será relançada.</span><span class="sxs-lookup"><span data-stu-id="28442-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="28442-114">Como uma melhor prática, você sempre deve aguardar a chamada.</span><span class="sxs-lookup"><span data-stu-id="28442-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="28442-115">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="28442-115">By default, this message is a warning.</span></span> <span data-ttu-id="28442-116">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="28442-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="28442-117">**ID do erro:** BC42358</span><span class="sxs-lookup"><span data-stu-id="28442-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="28442-118">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="28442-118">To address this warning</span></span>  
  
-   <span data-ttu-id="28442-119">Considere suprimir o aviso somente se você tiver certeza de que não deseja aguardar que a chamada assíncrona seja concluída e que o método chamado não gerará nenhuma exceção.</span><span class="sxs-lookup"><span data-stu-id="28442-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="28442-120">Nesse caso, você pode suprimir o aviso atribuindo o resultado da tarefa da chamada a uma variável.</span><span class="sxs-lookup"><span data-stu-id="28442-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="28442-121">O exemplo a seguir mostra como causar o aviso, como suprimi-lo e como aguardar a chamada.</span><span class="sxs-lookup"><span data-stu-id="28442-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
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
  
     <span data-ttu-id="28442-122">No exemplo, se você escolher a Chamada nº 1 ou Chamada nº 2, o método assíncrono não aguardado (`CalledMethodAsync`) será concluído após o chamador (`CallingMethodAsync`) e o chamador do chamador (`StartButton_Click`) serem concluídos.</span><span class="sxs-lookup"><span data-stu-id="28442-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="28442-123">A última linha na saída a seguir mostra quando o método chamado termina.</span><span class="sxs-lookup"><span data-stu-id="28442-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="28442-124">A entrada e a saída do manipulador de eventos que chama `CallingMethodAsync` no exemplo completo estão marcadas na saída.</span><span class="sxs-lookup"><span data-stu-id="28442-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="28442-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28442-125">Example</span></span>  
 <span data-ttu-id="28442-126">O seguinte aplicativo do WPF (Windows Presentation Foundation) contém os métodos do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="28442-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="28442-127">As etapas a seguir configuram o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28442-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="28442-128">Crie um aplicativo WPF e nomeie-o `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="28442-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="28442-129">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="28442-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="28442-130">Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="28442-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="28442-131">Substitua o código na exibição **XAML** de MainWindow.xaml pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="28442-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
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
  
     <span data-ttu-id="28442-132">Uma janela simples, contendo um botão e uma caixa de texto, aparecerá no modo de exibição de **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="28442-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="28442-133">Para obter mais informações sobre o Designer XAML, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="28442-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="28442-134">Para obter informações sobre como criar sua própria interface do usuário simples, consulte as seções "Para criar um aplicativo WPF" e "Para criar uma simples MainWindow do WPF" do [Passo a passo: acessando a Web usando async e await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span><span class="sxs-lookup"><span data-stu-id="28442-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="28442-135">Substitua o código em MainWindow.xaml.vb com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="28442-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
5.  <span data-ttu-id="28442-136">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="28442-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="28442-137">A saída esperada será exibida no final do código.</span><span class="sxs-lookup"><span data-stu-id="28442-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28442-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28442-138">See Also</span></span>  
 [<span data-ttu-id="28442-139">Operador Await</span><span class="sxs-lookup"><span data-stu-id="28442-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="28442-140">Programação assíncrona com Async e Await</span><span class="sxs-lookup"><span data-stu-id="28442-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
