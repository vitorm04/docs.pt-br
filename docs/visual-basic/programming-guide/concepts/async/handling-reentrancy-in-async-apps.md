---
title: "Tratando a reentrada em aplicativos assíncronos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 8c35f0b393f38ea32f456a60ebd520065d16c6eb
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="bcac3-102">Tratando a reentrada em aplicativos assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcac3-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="bcac3-103">Quando você inclui o código assíncrono em seu aplicativo, você deve considerar e possivelmente evitar reentrância, que se refere ao redigitando uma operação assíncrona, antes de ser concluído.</span><span class="sxs-lookup"><span data-stu-id="bcac3-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="bcac3-104">Se você não identificar e lidar com possibilidades de reentrância, ele pode causar resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="bcac3-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="bcac3-105">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="bcac3-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="bcac3-106">Reconhecendo reentrada</span><span class="sxs-lookup"><span data-stu-id="bcac3-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="bcac3-107">Tratando a reentrada</span><span class="sxs-lookup"><span data-stu-id="bcac3-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="bcac3-108">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="bcac3-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="bcac3-109">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bcac3-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="bcac3-110">Executar várias operações e a fila de saída</span><span class="sxs-lookup"><span data-stu-id="bcac3-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="bcac3-111">Examinar e executar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="bcac3-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="bcac3-112">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="bcac3-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="bcac3-113"><a name="BKMK_RecognizingReentrancy"></a>Reconhecendo reentrada</span><span class="sxs-lookup"><span data-stu-id="bcac3-113"><a name="BKMK_RecognizingReentrancy"></a> Recognizing Reentrancy</span></span>  
 <span data-ttu-id="bcac3-114">O exemplo neste tópico, os usuários escolhem um **iniciar** botão para iniciar um aplicativo assíncrono que baixa uma série de sites e calcula o número total de bytes baixados.</span><span class="sxs-lookup"><span data-stu-id="bcac3-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="bcac3-115">Uma versão síncrona do exemplo responderia a mesma forma independentemente de quantas vezes um usuário escolhe o botão porque, após a primeira vez, o thread de interface do usuário ignora esses eventos até que o aplicativo é encerrado.</span><span class="sxs-lookup"><span data-stu-id="bcac3-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="bcac3-116">Em um aplicativo assíncrono, no entanto, o thread de interface do usuário continua a responder e você pode digitar novamente a operação assíncrona antes de ser concluído.</span><span class="sxs-lookup"><span data-stu-id="bcac3-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="bcac3-117">O exemplo a seguir mostra a esperada de saída se o usuário escolhe o **iniciar** botão apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="bcac3-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="bcac3-118">É exibida uma lista dos sites baixados com o tamanho, em bytes, de cada site.</span><span class="sxs-lookup"><span data-stu-id="bcac3-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="bcac3-119">O número total de bytes é exibida no final.</span><span class="sxs-lookup"><span data-stu-id="bcac3-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="bcac3-120">No entanto, se o usuário clica no botão de mais de uma vez, o manipulador de eventos é chamado repetidamente, e o processo de download é reinserido cada vez.</span><span class="sxs-lookup"><span data-stu-id="bcac3-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="bcac3-121">Como resultado, várias operações assíncronas estão em execução ao mesmo tempo, a saída intercala os resultados e o número total de bytes é confuso.</span><span class="sxs-lookup"><span data-stu-id="bcac3-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="bcac3-122">Você pode examinar o código que produz esta saída navegado até o final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bcac3-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="bcac3-123">Você pode experimentar o código baixando a solução em seu computador local e, em seguida, executando o projeto WebsiteDownload ou usando o código no final deste tópico para criar seu próprio projeto para obter mais informações e instruções, consulte [revisando e executar o aplicativo de exemplo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="bcac3-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <span data-ttu-id="bcac3-124"><a name="BKMK_HandlingReentrancy"></a>Tratando a reentrada</span><span class="sxs-lookup"><span data-stu-id="bcac3-124"><a name="BKMK_HandlingReentrancy"></a> Handling Reentrancy</span></span>  
 <span data-ttu-id="bcac3-125">Você pode manipular reentrância de várias maneiras, dependendo do que você deseja que seu aplicativo faça.</span><span class="sxs-lookup"><span data-stu-id="bcac3-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="bcac3-126">Este tópico apresenta os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="bcac3-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="bcac3-127">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="bcac3-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="bcac3-128">Desabilitar o **iniciar** botão enquanto a operação está em execução para que o usuário não é possível interrompê-lo.</span><span class="sxs-lookup"><span data-stu-id="bcac3-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="bcac3-129">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bcac3-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="bcac3-130">Cancelar qualquer operação que ainda está em execução quando o usuário escolhe o **iniciar** novamente e, em seguida, continuar a permitir que a operação solicitada mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="bcac3-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="bcac3-131">Executar várias operações e a fila de saída</span><span class="sxs-lookup"><span data-stu-id="bcac3-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="bcac3-132">Permitir que todos os solicitados operações executadas de forma assíncrona, mas coordenar a exibição da saída de forma que os resultados de cada operação aparecem juntos e na ordem.</span><span class="sxs-lookup"><span data-stu-id="bcac3-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <span data-ttu-id="bcac3-133"><a name="BKMK_DisableTheStartButton"></a>Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="bcac3-133"><a name="BKMK_DisableTheStartButton"></a> Disable the Start Button</span></span>  
 <span data-ttu-id="bcac3-134">Você pode bloquear o **iniciar** botão enquanto uma operação está em execução, desativando o botão na parte superior do `StartButton_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="bcac3-135">Você pode reativar o botão de dentro um `Finally` bloquear quando a operação é concluída para que os usuários podem executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="bcac3-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="bcac3-136">O código a seguir mostra essas alterações, que são marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="bcac3-137">Você pode adicionar as alterações ao código no final deste tópico, ou você pode baixar o aplicativo concluído de [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="bcac3-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="bcac3-138">O nome do projeto é DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="bcac3-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="bcac3-139">Como resultado das alterações, o botão não responde enquanto `AccessTheWebAsync` está baixando os sites da Web, para que o processo não pode ser restabelecido.</span><span class="sxs-lookup"><span data-stu-id="bcac3-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <span data-ttu-id="bcac3-140"><a name="BKMK_CancelAndRestart"></a>Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="bcac3-140"><a name="BKMK_CancelAndRestart"></a> Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="bcac3-141">Em vez de desativar o **iniciar** botão, você pode manter o botão ativa, mas, se o usuário escolher o botão novamente, cancele a operação que já está em execução e permitir que a operação iniciada mais recentemente continuar.</span><span class="sxs-lookup"><span data-stu-id="bcac3-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="bcac3-142">Para obter mais informações sobre cancelamento, consulte [ajuste seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="bcac3-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="bcac3-143">Para configurar esse cenário, faça as seguintes alterações para o código básico que é fornecido no [revisando e executar o aplicativo de exemplo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="bcac3-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="bcac3-144">Você também pode baixar o aplicativo concluído de [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="bcac3-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="bcac3-145">O nome do projeto é CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="bcac3-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="bcac3-146">Declarar uma <xref:System.Threading.CancellationTokenSource>variável, `cts`, que está no escopo para todos os métodos.</xref:System.Threading.CancellationTokenSource></span><span class="sxs-lookup"><span data-stu-id="bcac3-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="bcac3-147">Em `StartButton_Click`, determinar se uma operação já está em andamento.</span><span class="sxs-lookup"><span data-stu-id="bcac3-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="bcac3-148">Se o valor de `cts` é `Nothing`, nenhuma operação já está ativa.</span><span class="sxs-lookup"><span data-stu-id="bcac3-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="bcac3-149">Se o valor não for `Nothing`, a operação já está em execução foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="bcac3-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="bcac3-150">Definir `cts` para um valor diferente que representa o processo atual.</span><span class="sxs-lookup"><span data-stu-id="bcac3-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="bcac3-151">No final da `StartButton_Click`, o processo atual for concluído, então, defina o valor de `cts` para `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="bcac3-152">O código a seguir mostra todas as alterações na `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="bcac3-153">As adições são marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="bcac3-154">Em `AccessTheWebAsync`, faça as seguintes alterações.</span><span class="sxs-lookup"><span data-stu-id="bcac3-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="bcac3-155">Adicionar um parâmetro para aceitar o token de cancelamento de `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="bcac3-156">Use o <xref:System.Net.Http.HttpClient.GetAsync%2A>método para baixar os sites porque `GetAsync` aceita um <xref:System.Threading.CancellationToken>argumento.</xref:System.Threading.CancellationToken> </xref:System.Net.Http.HttpClient.GetAsync%2A></span><span class="sxs-lookup"><span data-stu-id="bcac3-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="bcac3-157">Antes de chamar `DisplayResults` para exibir os resultados para cada site baixado, verifique `ct` para verificar que a operação atual não foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="bcac3-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="bcac3-158">O código a seguir mostra essas alterações, que são marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="bcac3-159">Se você escolher o **iniciar** botão várias vezes enquanto este aplicativo é executado, ele deve produzir resultados semelhantes a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="bcac3-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="bcac3-160">Para eliminar as listas parciais, remova a primeira linha do código em `StartButton_Click` desmarcar a caixa de texto sempre que o usuário reinicia a operação.</span><span class="sxs-lookup"><span data-stu-id="bcac3-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <span data-ttu-id="bcac3-161"><a name="BKMK_RunMultipleOperations"></a>Executar várias operações e a fila de saída</span><span class="sxs-lookup"><span data-stu-id="bcac3-161"><a name="BKMK_RunMultipleOperations"></a> Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="bcac3-162">Este exemplo terceiro é mais complicado que o aplicativo inicia outra operação assíncrona cada vez que o usuário escolhe o **iniciar** botão e todas as operações executadas até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="bcac3-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="bcac3-163">Todas as operações solicitadas baixar sites da lista de forma assíncrona, mas a saída das operações é apresentada em sequência.</span><span class="sxs-lookup"><span data-stu-id="bcac3-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="bcac3-164">Ou seja, a atividade de download real é intercalada, como a saída em [reconhecendo reentrada](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) mostra, mas a lista de resultados para cada grupo é apresentado separadamente.</span><span class="sxs-lookup"><span data-stu-id="bcac3-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="bcac3-165">As operações de compartilham um global <xref:System.Threading.Tasks.Task>, `pendingWork`, que serve como um gatekeeper para o processo de exibição.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="bcac3-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="bcac3-166">Você pode executar esse exemplo, colando as alterações no código no [criando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou você pode seguir as instruções em [baixados do aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para baixar o exemplo e execute o projeto QueueResults.</span><span class="sxs-lookup"><span data-stu-id="bcac3-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="bcac3-167">A saída a seguir mostra o resultado se o usuário escolhe o **iniciar** botão apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="bcac3-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="bcac3-168">O rótulo de letra A, indica que o resultado é a primeira vez o **iniciar** botão for escolhido.</span><span class="sxs-lookup"><span data-stu-id="bcac3-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="bcac3-169">Os números mostram a ordem das URLs na lista de destinos de download.</span><span class="sxs-lookup"><span data-stu-id="bcac3-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="bcac3-170">Se o usuário escolhe o **iniciar** botão três vezes, o aplicativo produz uma saída semelhante das linhas a seguir.</span><span class="sxs-lookup"><span data-stu-id="bcac3-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="bcac3-171">Inscreva-as linhas de informações que começam com um sustenido (#) rastrear o progresso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcac3-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="bcac3-172">Grupos de B e C iniciado antes de um grupo é concluída, mas a saída para cada grupo será exibido separadamente.</span><span class="sxs-lookup"><span data-stu-id="bcac3-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="bcac3-173">Toda a saída para um grupo aparece primeira, seguido por toda a saída para o grupo B e, em seguida, toda a saída para o grupo C. O aplicativo sempre exibe os grupos em ordem e, para cada grupo, sempre exibe as informações sobre os sites individuais na ordem em que as URLs aparecem na lista de URLs.</span><span class="sxs-lookup"><span data-stu-id="bcac3-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="bcac3-174">No entanto, é possível prever a ordem na qual os downloads realmente acontecem.</span><span class="sxs-lookup"><span data-stu-id="bcac3-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="bcac3-175">Depois que tiverem sido iniciados vários grupos, as tarefas de download que elas geram estão todos ativas.</span><span class="sxs-lookup"><span data-stu-id="bcac3-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="bcac3-176">Você não pode presumir que-1 será baixado antes de B-1, e você não pode presumir que-1 será baixado antes de A-2.</span><span class="sxs-lookup"><span data-stu-id="bcac3-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="bcac3-177">Definições Globais</span><span class="sxs-lookup"><span data-stu-id="bcac3-177">Global Definitions</span></span>  
 <span data-ttu-id="bcac3-178">O código de exemplo contém as seguintes declarações globais dois que são visíveis a partir de todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="bcac3-179">O `Task` variável, `pendingWork`, supervisiona o processo de exibição e impede que qualquer grupo de interromper a operação de exibição do outro grupo.</span><span class="sxs-lookup"><span data-stu-id="bcac3-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="bcac3-180">A variável de caractere, `group`, rótulos a saída de grupos diferentes para verificar se os resultados aparecem na ordem esperada.</span><span class="sxs-lookup"><span data-stu-id="bcac3-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="bcac3-181">O manipulador de eventos de clique</span><span class="sxs-lookup"><span data-stu-id="bcac3-181">The Click Event Handler</span></span>  
 <span data-ttu-id="bcac3-182">O manipulador de eventos, `StartButton_Click`, a letra de grupo é incrementado toda vez que o usuário escolhe o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="bcac3-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="bcac3-183">Em seguida, chama o manipulador `AccessTheWebAsync` para executar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="bcac3-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="bcac3-184">O método AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="bcac3-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="bcac3-185">Este exemplo divide `AccessTheWebAsync` em dois métodos.</span><span class="sxs-lookup"><span data-stu-id="bcac3-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="bcac3-186">O primeiro método, `AccessTheWebAsync`, inicia todas as tarefas de download de um grupo e configura `pendingWork` para controlar o processo de exibição.</span><span class="sxs-lookup"><span data-stu-id="bcac3-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="bcac3-187">O método usa uma consulta integrada à linguagem (consulta LINQ) e <xref:System.Linq.Enumerable.ToArray%2A>para iniciar todas as tarefas de download ao mesmo tempo.</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="bcac3-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="bcac3-188">`AccessTheWebAsync`em seguida, chama `FinishOneGroupAsync` para esperar pela conclusão de cada download e exibir seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="bcac3-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="bcac3-189">`FinishOneGroupAsync`Retorna uma tarefa que é atribuída a `pendingWork` em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="bcac3-190">Que valor impede a interrupção por outra operação antes que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="bcac3-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="bcac3-191">O método FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="bcac3-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="bcac3-192">Esse método percorre as tarefas de download em um grupo, aguardando a cada uma delas, exibindo o comprimento do site baixado e adicionando o comprimento para o total.</span><span class="sxs-lookup"><span data-stu-id="bcac3-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="bcac3-193">A primeira instrução em `FinishOneGroupAsync` usa `pendingWork` para certificar-se de que inserindo o método não interfere com uma operação que já está no processo de exibição ou que já está aguardando.</span><span class="sxs-lookup"><span data-stu-id="bcac3-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="bcac3-194">Se essa operação está em andamento, a operação de inserção deve esperar sua vez.</span><span class="sxs-lookup"><span data-stu-id="bcac3-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="bcac3-195">Você pode executar esse exemplo, colando as alterações no código no [criando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou você pode seguir as instruções em [baixados do aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para baixar o exemplo e execute o projeto QueueResults.</span><span class="sxs-lookup"><span data-stu-id="bcac3-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="bcac3-196">Pontos de Interesse</span><span class="sxs-lookup"><span data-stu-id="bcac3-196">Points of Interest</span></span>  
 <span data-ttu-id="bcac3-197">As linhas de informações que começam com um sinal de libra (#) na saída esclarecem como este exemplo funciona.</span><span class="sxs-lookup"><span data-stu-id="bcac3-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="bcac3-198">A saída mostra os padrões a seguir.</span><span class="sxs-lookup"><span data-stu-id="bcac3-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="bcac3-199">Um grupo pode ser iniciado enquanto um grupo anterior está exibindo a saída, mas a exibição da saída do grupo anterior não é interrompida.</span><span class="sxs-lookup"><span data-stu-id="bcac3-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="bcac3-200">O `pendingWork` tarefa é `Nothing` no início de `FinishOneGroupAsync` apenas para um grupo, que foi iniciado primeiro.</span><span class="sxs-lookup"><span data-stu-id="bcac3-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="bcac3-201">Um grupo ainda não tiver concluído uma expressão await quando ele atinge `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="bcac3-202">Portanto, o controle não foi retornado ao `AccessTheWebAsync`e a primeira atribuição para `pendingWork` não ocorreu.</span><span class="sxs-lookup"><span data-stu-id="bcac3-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="bcac3-203">As duas linhas a seguir sempre aparecem juntos na saída.</span><span class="sxs-lookup"><span data-stu-id="bcac3-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="bcac3-204">O código nunca é interrompido entre iniciando a operação de um grupo `StartButton_Click` e atribuir uma tarefa para o grupo de `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="bcac3-205">Depois de insere um grupo de `StartButton_Click`, a operação não conclui uma expressão await, até que a operação entre `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="bcac3-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="bcac3-206">Portanto, nenhuma outra operação pode obter controle durante esse segmento de código.</span><span class="sxs-lookup"><span data-stu-id="bcac3-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <span data-ttu-id="bcac3-207"><a name="BKMD_SettingUpTheExample"></a>Examinar e executar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="bcac3-207"><a name="BKMD_SettingUpTheExample"></a> Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="bcac3-208">Para entender melhor o aplicativo de exemplo, você pode baixá-lo, compilá-lo ou examinar o código no final deste tópico sem implementar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bcac3-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcac3-209">Para executar o exemplo como um aplicativo de desktop do Windows Presentation Foundation (WPF), você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="bcac3-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <span data-ttu-id="bcac3-210"><a name="BKMK_DownloadingTheApp"></a>Baixar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bcac3-210"><a name="BKMK_DownloadingTheApp"></a> Downloading the App</span></span>  
  
1.  <span data-ttu-id="bcac3-211">Baixe o arquivo compactado em [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="bcac3-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="bcac3-212">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcac3-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="bcac3-213">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="bcac3-214">Navegue até a pasta que contém o código de exemplo descompactado e, em seguida, abra o arquivo de solução (. sln).</span><span class="sxs-lookup"><span data-stu-id="bcac3-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="bcac3-215">Em **Solution Explorer**, abra o menu de atalho para o projeto que você deseja executar e, em seguida, escolha **definida como StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="bcac3-216">Escolha as teclas CTRL + F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="bcac3-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <span data-ttu-id="bcac3-217"><a name="BKMK_BuildingTheApp"></a>Criando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="bcac3-217"><a name="BKMK_BuildingTheApp"></a> Building the App</span></span>  
 <span data-ttu-id="bcac3-218">A seção a seguir fornece o código para criar o exemplo como um aplicativo WPF.</span><span class="sxs-lookup"><span data-stu-id="bcac3-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="bcac3-219">Para criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="bcac3-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="bcac3-220">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bcac3-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="bcac3-221">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="bcac3-222">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="bcac3-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bcac3-223">No **modelos instalados** painel, expanda **Visual Basic**e, em seguida, expanda **Windows**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="bcac3-224">Na lista de tipos de projeto, escolha **aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="bcac3-225">Nomeie o projeto `WebsiteDownloadWPF`e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="bcac3-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="bcac3-226">O novo projeto aparece na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="bcac3-227">No código de Editor do Visual Studio, escolha o **MainWindow** guia.</span><span class="sxs-lookup"><span data-stu-id="bcac3-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="bcac3-228">Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="bcac3-229">No **XAML** exibir de MainWindow. XAML, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bcac3-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="bcac3-230">Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** exibição de MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="bcac3-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="bcac3-231">Adicione uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="bcac3-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="bcac3-232">Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="bcac3-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="bcac3-233">Em MainWindow.xaml.vb, substitua o código com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bcac3-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="bcac3-234">Escolha as teclas CTRL + F5 para executar o programa e, em seguida, escolha o **iniciar** botão várias vezes.</span><span class="sxs-lookup"><span data-stu-id="bcac3-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="bcac3-235">Faça as alterações de [desabilitar o botão Iniciar](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancelar e reiniciar a operação](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), ou [executar várias operações e a fila de saída](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para lidar com a reentrância.</span><span class="sxs-lookup"><span data-stu-id="bcac3-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcac3-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bcac3-236">See Also</span></span>  
 <span data-ttu-id="bcac3-237">[Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="bcac3-237">[Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="bcac3-238"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="bcac3-238"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)</span></span>

