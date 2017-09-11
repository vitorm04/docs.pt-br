---
title: "Como esta chamada não é aguardada, o método atual continua sendo executado antes da chamada é concluída | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: acee06829c246fbff866bfe188d6685f7cd8a263
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="d0083-102">Como esta chamada não é aguardada, o método atual continua sendo executado antes da chamada ser concluída</span><span class="sxs-lookup"><span data-stu-id="d0083-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="d0083-103">Como esta chamada não era esperada, a execução do método atual continua antes da chamada ser concluída.</span><span class="sxs-lookup"><span data-stu-id="d0083-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="d0083-104">Considere a possibilidade de aplicar o operador 'Await' para o resultado da chamada.</span><span class="sxs-lookup"><span data-stu-id="d0083-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="d0083-105">O método atual chama um método async que retorna um <xref:System.Threading.Tasks.Task>ou um <xref:System.Threading.Tasks.Task%601>e não se aplica a [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador para o resultado.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="d0083-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="d0083-106">A chamada para o método assíncrono inicia uma tarefa assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d0083-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="d0083-107">No entanto, porque nenhum `Await` operador é aplicado, o programa continua sem esperar que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="d0083-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="d0083-108">Na maioria dos casos, esse comportamento não é esperado.</span><span class="sxs-lookup"><span data-stu-id="d0083-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="d0083-109">Geralmente os outros aspectos do método de chamada dependem dos resultados da chamada ou, no mínimo, o método chamado é esperado para ser concluída antes de retornar do método que contém a chamada.</span><span class="sxs-lookup"><span data-stu-id="d0083-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="d0083-110">Igualmente importante é o que acontece com exceções que são geradas em um método assíncrono chamado.</span><span class="sxs-lookup"><span data-stu-id="d0083-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="d0083-111">Uma exceção é acionada em um método que retorna um <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>é armazenado na tarefa retornada.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="d0083-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="d0083-112">Se você não esperar a tarefa ou verificar explicitamente se há exceções, a exceção será perdida.</span><span class="sxs-lookup"><span data-stu-id="d0083-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="d0083-113">Se você esperar a tarefa, sua exceção será emitida novamente.</span><span class="sxs-lookup"><span data-stu-id="d0083-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="d0083-114">Como prática recomendada, você deve sempre espera a chamada.</span><span class="sxs-lookup"><span data-stu-id="d0083-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="d0083-115">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d0083-115">By default, this message is a warning.</span></span> <span data-ttu-id="d0083-116">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d0083-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d0083-117">**ID do erro:** BC42358</span><span class="sxs-lookup"><span data-stu-id="d0083-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="d0083-118">Para resolver este aviso</span><span class="sxs-lookup"><span data-stu-id="d0083-118">To address this warning</span></span>  
  
-   <span data-ttu-id="d0083-119">Você deve considerar suprimir o aviso somente se você tiver certeza de que você não deseja aguardar a chamada assíncrona seja concluída e que o método chamado não gera nenhuma exceção.</span><span class="sxs-lookup"><span data-stu-id="d0083-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="d0083-120">Nesse caso, você pode suprimir o aviso atribuindo o resultado da tarefa da chamada para uma variável.</span><span class="sxs-lookup"><span data-stu-id="d0083-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="d0083-121">O exemplo a seguir mostra como fazer com que o aviso, como suprimir a ele e a espera a chamada.</span><span class="sxs-lookup"><span data-stu-id="d0083-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
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
  
     <span data-ttu-id="d0083-122">No exemplo, se você escolher chamar n º 1 ou chamar n º 2, o método assíncrono unawaited (`CalledMethodAsync`) é concluída após os dois seu chamador (`CallingMethodAsync`) e o chamador do chamador (`StartButton_Click`) forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="d0083-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="d0083-123">A última linha na saída a seguir mostra quando termina o método chamado.</span><span class="sxs-lookup"><span data-stu-id="d0083-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="d0083-124">Entrada e saída do manipulador de eventos chama `CallingMethodAsync` no exemplo completo está marcado na saída.</span><span class="sxs-lookup"><span data-stu-id="d0083-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="d0083-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0083-125">Example</span></span>  
 <span data-ttu-id="d0083-126">O seguinte aplicativo do Windows Presentation Foundation (WPF) contém os métodos do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d0083-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="d0083-127">As etapas a seguir configuram o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0083-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="d0083-128">Criar um aplicativo WPF e nomeie-o `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="d0083-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="d0083-129">No código de Editor do Visual Studio, escolha o **MainWindow** guia.</span><span class="sxs-lookup"><span data-stu-id="d0083-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="d0083-130">Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="d0083-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="d0083-131">Substitua o código no **XAML** exibição de MainWindow. XAML com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0083-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
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
  
     <span data-ttu-id="d0083-132">Uma janela simple que contém um botão e uma caixa de texto aparece no **Design** exibição de MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="d0083-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="d0083-133">Para obter mais informações sobre o Designer XAML, consulte [criando uma interface do usuário usando o Designer XAML](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d0083-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="d0083-134">Para obter informações sobre como criar sua própria interface do usuário simple, consulte o "para criar um aplicativo WPF" e "para criar um simples MainWindow WPF" seções de [passo a passo: acessando a Web, usando Async e Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span><span class="sxs-lookup"><span data-stu-id="d0083-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="d0083-135">Substitua o código em MainWindow.xaml.vb com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0083-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
5.  <span data-ttu-id="d0083-136">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="d0083-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="d0083-137">A saída esperada é exibido no final do código.</span><span class="sxs-lookup"><span data-stu-id="d0083-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0083-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0083-138">See Also</span></span>  
 <span data-ttu-id="d0083-139">[Operador await](../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="d0083-139">[Await Operator](../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="d0083-140"> [Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="d0083-140"> [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md)</span></span>

