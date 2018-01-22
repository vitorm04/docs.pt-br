---
title: "Tratando a reentrada em aplicativos assíncronos (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07157057d7ae94d3c6017544ff654ca0ed7b7cf2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="989be-102">Tratando a reentrada em aplicativos assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="989be-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="989be-103">Ao incluir código assíncrono em seu aplicativo, você deve considerar e, possivelmente, evitar a reentrância, que se refere à reinserção de uma operação assíncrona antes de ela ser concluída.</span><span class="sxs-lookup"><span data-stu-id="989be-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="989be-104">Se você não identificar e tratar as possibilidades de reentrância, isso poderá causar resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="989be-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="989be-105">**Neste tópico**</span><span class="sxs-lookup"><span data-stu-id="989be-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="989be-106">Reconhecendo a reentrância</span><span class="sxs-lookup"><span data-stu-id="989be-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="989be-107">Tratando a reentrância</span><span class="sxs-lookup"><span data-stu-id="989be-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="989be-108">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="989be-108">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="989be-109">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="989be-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="989be-110">Executar várias operações e colocar a saída na fila</span><span class="sxs-lookup"><span data-stu-id="989be-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="989be-111">Examinar e executar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="989be-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="989be-112">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="989be-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="989be-113">Reconhecendo a reentrância</span><span class="sxs-lookup"><span data-stu-id="989be-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="989be-114">No exemplo deste tópico, os usuários escolhem um botão **Iniciar** para iniciar um aplicativo assíncrono que baixa uma série de sites e calcula o número total de bytes baixados.</span><span class="sxs-lookup"><span data-stu-id="989be-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="989be-115">Uma versão síncrona do exemplo responderia da mesma forma, independentemente de quantas vezes um usuário escolhesse o botão porque, após a primeira vez, o thread da interface do usuário ignora esses eventos até que o aplicativo conclua a execução.</span><span class="sxs-lookup"><span data-stu-id="989be-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="989be-116">Em um aplicativo assíncrono, no entanto, o thread da interface do usuário continua a responder e você pode reinserir a operação assíncrona antes que ele seja concluído.</span><span class="sxs-lookup"><span data-stu-id="989be-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="989be-117">O exemplo a seguir mostra a saída esperada, caso o usuário escolha o botão **Iniciar** apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="989be-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="989be-118">É exibida uma lista dos sites baixados com o tamanho, em bytes, de cada site.</span><span class="sxs-lookup"><span data-stu-id="989be-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="989be-119">O número total de bytes é exibido no final.</span><span class="sxs-lookup"><span data-stu-id="989be-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="989be-120">No entanto, se o usuário escolhe o botão mais de uma vez, o manipulador de eventos é invocado repetidamente e o processo de download é reinserido a cada vez.</span><span class="sxs-lookup"><span data-stu-id="989be-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="989be-121">Como resultado, várias operações assíncronas estarão em execução ao mesmo tempo, a saída intercalará os resultados e o número total de bytes será confuso.</span><span class="sxs-lookup"><span data-stu-id="989be-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
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
  
 <span data-ttu-id="989be-122">Você pode examinar o código que produz esta saída fazendo a rolagem até o final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="989be-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="989be-123">Você pode fazer experimentos com o código baixando a solução em seu computador local e, em seguida, executar o projeto WebsiteDownload ou usar o código no final deste tópico para criar seu próprio projeto. Para obter mais informações e instruções, consulte [Examinar e executar o aplicativo de exemplo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="989be-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="989be-124">Tratando a reentrância</span><span class="sxs-lookup"><span data-stu-id="989be-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="989be-125">É possível tratar a reentrância de várias maneiras, dependendo do que você deseja que seu aplicativo faça.</span><span class="sxs-lookup"><span data-stu-id="989be-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="989be-126">Este tópico apresenta os exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="989be-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="989be-127">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="989be-127">Disable the Start Button</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="989be-128">Desabilitar o botão **Iniciar** enquanto a operação estiver em execução para que o usuário não possa interrompê-la.</span><span class="sxs-lookup"><span data-stu-id="989be-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="989be-129">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="989be-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="989be-130">Cancelar qualquer operação que ainda estiver em execução quando o usuário escolher o botão **Iniciar** novamente e, em seguida, permitir que a operação solicitada mais recentemente continue.</span><span class="sxs-lookup"><span data-stu-id="989be-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="989be-131">Executar várias operações e colocar a saída na fila</span><span class="sxs-lookup"><span data-stu-id="989be-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="989be-132">Permitir que todas as operações solicitadas sejam executadas de forma assíncrona, mas coordenar a exibição da saída, de forma que os resultados de cada operação apareçam juntos e em ordem.</span><span class="sxs-lookup"><span data-stu-id="989be-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="989be-133">Desabilitar o botão Iniciar</span><span class="sxs-lookup"><span data-stu-id="989be-133">Disable the Start Button</span></span>  
 <span data-ttu-id="989be-134">Você pode bloquear o botão **Iniciar** enquanto uma operação estiver em execução, desabilitando o botão na parte superior do manipulador de eventos `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="989be-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="989be-135">Você pode reativar o botão de dentro um bloco `finally` quando a operação for concluída para que os usuários possam executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="989be-135">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="989be-136">O código a seguir mostra essas alterações, que estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="989be-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="989be-137">Você pode adicionar as alterações ao código no final deste tópico ou você pode baixar o aplicativo concluído em [Exemplos assíncronos: reentrância em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="989be-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="989be-138">O nome do projeto é DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="989be-138">The project name is DisableStartButton.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 <span data-ttu-id="989be-139">Como resultado das alterações, o botão não responderá enquanto `AccessTheWebAsync` estiver baixando os sites, para que o processo não possa ser reinserido.</span><span class="sxs-lookup"><span data-stu-id="989be-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="989be-140">Cancelar e reiniciar a operação</span><span class="sxs-lookup"><span data-stu-id="989be-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="989be-141">Em vez de desabilitar o botão **Iniciar**, você pode manter o botão ativo, mas, se o usuário escolher esse botão novamente, cancele a operação que já está em execução e permita que a operação iniciada mais recentemente continue.</span><span class="sxs-lookup"><span data-stu-id="989be-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="989be-142">Para obter mais informações sobre o cancelamento, consulte [Ajuste fino de seu aplicativo assíncrono (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="989be-142">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="989be-143">Para configurar esse cenário, faça as seguintes alterações no código básico que é fornecido em [Examinar e executar o aplicativo de exemplo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="989be-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="989be-144">Você também pode baixar o aplicativo finalizado de [Exemplos assíncronos: reentrância em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="989be-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="989be-145">O nome do projeto é CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="989be-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="989be-146">Declare uma variável <xref:System.Threading.CancellationTokenSource>, `cts`, que está no escopo para todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="989be-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="989be-147">Em `StartButton_Click`, determine se uma operação já está em andamento.</span><span class="sxs-lookup"><span data-stu-id="989be-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="989be-148">Se o valor de `cts` for nulo, nenhuma operação estará ativa.</span><span class="sxs-lookup"><span data-stu-id="989be-148">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="989be-149">Se o valor não for nulo, a operação que já está em execução será cancelada.</span><span class="sxs-lookup"><span data-stu-id="989be-149">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="989be-150">Defina `cts` para um valor diferente que represente o processo atual.</span><span class="sxs-lookup"><span data-stu-id="989be-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="989be-151">Ao final de `StartButton_Click`, o processo atual estará concluído, então, defina o valor de `cts` novamente como nulo.</span><span class="sxs-lookup"><span data-stu-id="989be-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="989be-152">O código a seguir mostra todas as alterações em `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="989be-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="989be-153">As adições estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="989be-153">The additions are marked with asterisks.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 <span data-ttu-id="989be-154">Em `AccessTheWebAsync`, faça as seguintes alterações.</span><span class="sxs-lookup"><span data-stu-id="989be-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="989be-155">Adicione um parâmetro para aceitar o token de cancelamento de `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="989be-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="989be-156">Use o método <xref:System.Net.Http.HttpClient.GetAsync%2A> para baixar os sites porque `GetAsync` aceita um argumento <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="989be-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="989be-157">Antes de chamar `DisplayResults` para exibir os resultados para cada site baixado, verifique `ct` para ver se a operação atual não foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="989be-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="989be-158">O código a seguir mostra essas alterações, que estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="989be-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 <span data-ttu-id="989be-159">Se você escolher o botão **Iniciar** várias vezes enquanto este aplicativo estiver em execução, ele deverá produzir resultados semelhantes à saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="989be-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="989be-160">Para eliminar as listas parciais, remova a marca de comentário da primeira linha de código em `StartButton_Click`, para limpar a caixa de texto sempre que o usuário reiniciar a operação.</span><span class="sxs-lookup"><span data-stu-id="989be-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="989be-161">Executar várias operações e colocar a saída na fila</span><span class="sxs-lookup"><span data-stu-id="989be-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="989be-162">Este terceiro exemplo é mais complicado pois o aplicativo iniciará outra operação assíncrona a cada vez que o usuário escolher o botão **Iniciar** e todas as operações serão executadas até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="989be-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="989be-163">Todas as operações solicitadas baixam sites da lista de maneira assíncrona, mas a saída das operações será apresentada sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="989be-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="989be-164">Ou seja, a atividade de download real é intercalada, conforme mostrado na saída em [Reconhecendo a reentrância](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), mas a lista de resultados para cada grupo é apresentada separadamente.</span><span class="sxs-lookup"><span data-stu-id="989be-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="989be-165">As operações compartilham uma <xref:System.Threading.Tasks.Task> global, `pendingWork`, que serve como um gatekeeper para o processo de exibição.</span><span class="sxs-lookup"><span data-stu-id="989be-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="989be-166">Você pode executar esse exemplo, colando as alterações no código em [Compilando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ou pode seguir as instruções em [Baixando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para baixar o exemplo e executar o projeto QueueResults.</span><span class="sxs-lookup"><span data-stu-id="989be-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="989be-167">A saída a seguir mostra o resultado, caso o usuário escolha o botão **Iniciar** apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="989be-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="989be-168">O rótulo de letra A indica que o resultado é da primeira vez que o botão **Iniciar** foi escolhido.</span><span class="sxs-lookup"><span data-stu-id="989be-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="989be-169">Os números mostram a ordem das URLs na lista de destinos de download.</span><span class="sxs-lookup"><span data-stu-id="989be-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="989be-170">Se o usuário escolher o botão **Iniciar** três vezes, o aplicativo produzirá uma saída semelhante à das linhas a seguir.</span><span class="sxs-lookup"><span data-stu-id="989be-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="989be-171">As linhas de informações que começam com um sinal de jogo da velha (#) rastreiam o progresso do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989be-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="989be-172">Os grupos B e C iniciam antes da conclusão do grupo A, mas a saída para cada grupo é exibida separadamente.</span><span class="sxs-lookup"><span data-stu-id="989be-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="989be-173">Toda a saída para o grupo A aparece em primeiro, seguida por toda a saída para o grupo B e, em seguida, toda a saída para o grupo C. O aplicativo sempre exibe os grupos em ordem e, para cada grupo, sempre exibe as informações sobre os sites individuais na ordem em que as URLs aparecem na lista de URLs.</span><span class="sxs-lookup"><span data-stu-id="989be-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="989be-174">No entanto, não é possível prever a ordem na qual os downloads realmente acontecem.</span><span class="sxs-lookup"><span data-stu-id="989be-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="989be-175">Depois que vários grupos tiverem sido iniciados, as tarefas de download que eles geram estarão todos ativas.</span><span class="sxs-lookup"><span data-stu-id="989be-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="989be-176">Você não pode presumir que A-1 será baixado antes de B-1 e não pode presumir que A-1 será baixado antes de A-2.</span><span class="sxs-lookup"><span data-stu-id="989be-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="989be-177">Definições Globais</span><span class="sxs-lookup"><span data-stu-id="989be-177">Global Definitions</span></span>  
 <span data-ttu-id="989be-178">O código de exemplo contém as duas declarações globais a seguir, que estão visíveis em todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="989be-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="989be-179">A variável `Task`, `pendingWork`, supervisiona o processo de exibição e impede que qualquer grupo interrompa a operação de exibição do outro grupo.</span><span class="sxs-lookup"><span data-stu-id="989be-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="989be-180">A variável de caractere, `group`, rotula a saída de grupos diferentes para verificar se os resultados aparecem na ordem esperada.</span><span class="sxs-lookup"><span data-stu-id="989be-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="989be-181">O manipulador de eventos Click</span><span class="sxs-lookup"><span data-stu-id="989be-181">The Click Event Handler</span></span>  
 <span data-ttu-id="989be-182">O manipulador de eventos `StartButton_Click`, incrementa a letra de grupo sempre que o usuário escolhe o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="989be-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="989be-183">Em seguida, o manipulador chama `AccessTheWebAsync` para executar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="989be-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="989be-184">O método AccessTheWebAsync</span><span class="sxs-lookup"><span data-stu-id="989be-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="989be-185">Este exemplo divide o `AccessTheWebAsync` em dois métodos.</span><span class="sxs-lookup"><span data-stu-id="989be-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="989be-186">O primeiro método, `AccessTheWebAsync`, inicia todas as tarefas de download de um grupo e configura `pendingWork` para controlar o processo de exibição.</span><span class="sxs-lookup"><span data-stu-id="989be-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="989be-187">O método usa uma LINQ (consulta integrada à linguagem) e um <xref:System.Linq.Enumerable.ToArray%2A> para iniciar todas as tarefas de download ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="989be-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="989be-188">Em seguida, o `AccessTheWebAsync` chama `FinishOneGroupAsync` para aguardar a conclusão de cada download e exibir seu comprimento.</span><span class="sxs-lookup"><span data-stu-id="989be-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="989be-189">O `FinishOneGroupAsync` retorna uma tarefa que é atribuída a `pendingWork` em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="989be-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="989be-190">Esse valor impede a interrupção por outra operação antes que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="989be-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="989be-191">O método FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="989be-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="989be-192">Esse método percorre as tarefas de download em um grupo, aguardando cada uma delas, exibindo o comprimento do site baixado e adicionando o comprimento ao total.</span><span class="sxs-lookup"><span data-stu-id="989be-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="989be-193">A primeira instrução em `FinishOneGroupAsync` usa `pendingWork` para verificar se o método de inserção não interfere com uma operação que já está no processo de exibição ou que já está aguardando.</span><span class="sxs-lookup"><span data-stu-id="989be-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="989be-194">Se houver uma operação dessas em andamento, a operação de inserção deverá esperar por sua vez.</span><span class="sxs-lookup"><span data-stu-id="989be-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
 <span data-ttu-id="989be-195">Você pode executar esse exemplo, colando as alterações no código em [Compilando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ou pode seguir as instruções em [Baixando o aplicativo](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para baixar o exemplo e executar o projeto QueueResults.</span><span class="sxs-lookup"><span data-stu-id="989be-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="989be-196">Pontos de Interesse</span><span class="sxs-lookup"><span data-stu-id="989be-196">Points of Interest</span></span>  
 <span data-ttu-id="989be-197">As linhas de informações que começam com um sinal de jogo da velha (#) na saída esclarecem o funcionamento deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="989be-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="989be-198">A saída mostra os padrões a seguir.</span><span class="sxs-lookup"><span data-stu-id="989be-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="989be-199">Um grupo pode ser iniciado enquanto um grupo anterior estiver exibindo a saída, mas a exibição da saída do grupo anterior não será interrompida.</span><span class="sxs-lookup"><span data-stu-id="989be-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="989be-200">O tarefa `pendingWork` é nula no início de `FinishOneGroupAsync` somente para o grupo A, que foi iniciado primeiro.</span><span class="sxs-lookup"><span data-stu-id="989be-200">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="989be-201">O grupo A ainda não concluiu uma expressão await quando alcança o `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="989be-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="989be-202">Portanto, o controle não foi retornado ao `AccessTheWebAsync` e a primeira atribuição para `pendingWork` não ocorreu.</span><span class="sxs-lookup"><span data-stu-id="989be-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="989be-203">As duas linhas a seguir sempre aparecem juntas na saída.</span><span class="sxs-lookup"><span data-stu-id="989be-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="989be-204">O código nunca é interrompido entre o início de uma operação de um grupo em `StartButton_Click` e a atribuição de uma tarefa para o grupo para `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="989be-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="989be-205">Depois que um grupo insere o `StartButton_Click`, a operação não conclui uma expressão await até que a operação insira `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="989be-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="989be-206">Portanto, nenhuma outra operação pode obter controle durante esse segmento de código.</span><span class="sxs-lookup"><span data-stu-id="989be-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="989be-207">Examinar e executar o aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="989be-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="989be-208">Para entender melhor o aplicativo de exemplo, você pode baixá-lo, compilá-lo ou examinar o código ao final deste tópico sem implementar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="989be-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="989be-209">Para executar o exemplo como um aplicativo da área de trabalho do WPF (Windows Presentation Foundation), você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="989be-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="989be-210">Baixar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="989be-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="989be-211">Baixe o aplicativo compactado em [Exemplos assíncronos: reentrância em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).</span><span class="sxs-lookup"><span data-stu-id="989be-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="989be-212">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="989be-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="989be-213">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="989be-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="989be-214">Navegue até a pasta que contém o código de exemplo descompactado e, em seguida, abra o arquivo de solução (.sln).</span><span class="sxs-lookup"><span data-stu-id="989be-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="989be-215">No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja executar e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="989be-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="989be-216">Escolha as teclas CTRL+F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="989be-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="989be-217">Compilando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="989be-217">Building the App</span></span>  
 <span data-ttu-id="989be-218">A seção a seguir fornece o código para compilar o exemplo como um aplicativo do WPF.</span><span class="sxs-lookup"><span data-stu-id="989be-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="989be-219">Para compilar um aplicativo do WPF</span><span class="sxs-lookup"><span data-stu-id="989be-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="989be-220">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="989be-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="989be-221">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="989be-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="989be-222">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="989be-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="989be-223">No painel **Modelos Instalados**, expanda **Visual C#** e, em seguida, expanda **Windows**.</span><span class="sxs-lookup"><span data-stu-id="989be-223">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="989be-224">Na lista de tipos de projeto, escolha **Aplicativo WPF**.</span><span class="sxs-lookup"><span data-stu-id="989be-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="989be-225">Nomeie o projeto como `WebsiteDownloadWPF` e escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="989be-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="989be-226">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="989be-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="989be-227">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="989be-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="989be-228">Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="989be-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="989be-229">Na exibição **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="989be-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
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
  
     <span data-ttu-id="989be-230">Uma janela simples, contendo uma caixa de texto e um botão, aparecerá no modo de exibição de **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="989be-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="989be-231">Adicione uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="989be-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="989be-232">No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="989be-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="989be-233">Em MainWindow.xaml.cs, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="989be-233">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    // Add the following using directives, and add a reference for System.Net.Http.  
    using System.Net.Http;  
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="989be-234">Escolha a tecla CTRL+F5 para executar o programa e, em seguida, escolha o botão **Iniciar** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="989be-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="989be-235">Faça as alterações de [Desabilitar o botão Iniciar](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancelar e reiniciar a operação](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) ou [Executar várias operações e colocar a saída em fila](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) para tratar a reentrância.</span><span class="sxs-lookup"><span data-stu-id="989be-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989be-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="989be-236">See Also</span></span>  
 [<span data-ttu-id="989be-237">Passo a passo: acessando a Web e usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="989be-237">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="989be-238">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="989be-238">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
