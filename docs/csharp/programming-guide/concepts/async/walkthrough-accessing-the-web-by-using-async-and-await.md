---
title: 'Passo a passo: acessando a Web usando async e await (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="25ba4-102">Passo a passo: acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="25ba4-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="25ba4-103">É possível escrever programas assíncronos de forma mais fácil e intuitiva usando funcionalidades async/await.</span><span class="sxs-lookup"><span data-stu-id="25ba4-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="25ba4-104">Você pode escrever código assíncrono que se parece com código síncrono e deixar que o compilador trate das complicadas continuações e funções de retorno de chamada que um código assíncrono normalmente envolve.</span><span class="sxs-lookup"><span data-stu-id="25ba4-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="25ba4-105">Para obter mais informações sobre o recurso Assíncrono, consulte [Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="25ba4-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="25ba4-106">Este passo a passo começa com um aplicativo WPF (Windows Presentation Foundation) síncrono que soma o número de bytes em uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="25ba4-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="25ba4-107">Em seguida, converte o aplicativo em uma solução assíncrona usando os novos recursos.</span><span class="sxs-lookup"><span data-stu-id="25ba4-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="25ba4-108">Se não quiser compilar os aplicativos, você poderá baixar "Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)" nas [Amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="25ba4-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="25ba4-109">Neste passo a passo, você realizará as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="25ba4-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="25ba4-110">Criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="25ba4-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="25ba4-111">Projetar um MainWindow WPF simples</span><span class="sxs-lookup"><span data-stu-id="25ba4-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="25ba4-112">Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="25ba4-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="25ba4-113">Adicionar as diretivas de uso necessárias</span><span class="sxs-lookup"><span data-stu-id="25ba4-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="25ba4-114">Criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="25ba4-115">Testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="25ba4-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="25ba4-116">Converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="25ba4-117">Converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="25ba4-118">Converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="25ba4-119">Testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="25ba4-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="25ba4-120">Substituir o método GetURLContentsAsync por um método .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25ba4-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="25ba4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25ba4-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="25ba4-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="25ba4-122">Prerequisites</span></span>  
 <span data-ttu-id="25ba4-123">O Visual Studio 2012 ou posterior deve estar instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="25ba4-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="25ba4-124">Para obter mais informações, consulte o [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="25ba4-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="25ba4-125"><a name="CreateWPFApp"></a> Criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="25ba4-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="25ba4-126">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25ba4-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="25ba4-127">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="25ba4-128">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="25ba4-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="25ba4-129">No painel **Modelos Instalados**, escolha Visual C# e, em seguida, escolha **Aplicativo WPF** na lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="25ba4-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="25ba4-130">Na caixa de texto **Nome**, insira `AsyncExampleWPF` e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="25ba4-131">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="25ba4-132"><a name="MainWindow"></a> Projetar um MainWindow WPF simples</span><span class="sxs-lookup"><span data-stu-id="25ba4-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="25ba4-133">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="25ba4-134">Se a janela **Caixa de Ferramentas** não estiver visível, abra o menu **Exibir** e, em seguida, escolha **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="25ba4-135">Adicione um controle **Botão** e um controle **Caixa de Texto** à janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="25ba4-136">Realce o controle **Caixa de Texto** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="25ba4-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="25ba4-137">Defina a propriedade **Nome** como `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="25ba4-138">Defina a propriedade **Altura** como 250.</span><span class="sxs-lookup"><span data-stu-id="25ba4-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="25ba4-139">Defina a propriedade **Largura** como 500.</span><span class="sxs-lookup"><span data-stu-id="25ba4-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="25ba4-140">Na guia **Texto**, especifique uma fonte com espaçamento uniforme, como Lucida Console ou Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="25ba4-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="25ba4-141">Realce o controle **Botão** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="25ba4-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="25ba4-142">Defina a propriedade **Nome** como `startButton`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="25ba4-143">Altere o valor da propriedade **Conteúdo** de **Botão** para **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="25ba4-144">Posicione a caixa de texto e o botão de modo que ambos sejam exibidos na janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="25ba4-145">Para obter mais informações sobre o Designer XAML do WPF, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="25ba4-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="25ba4-146"><a name="AddRef"></a> Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="25ba4-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="25ba4-147">No **Gerenciador de Soluções**, realce o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="25ba4-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="25ba4-148">Na barra de menus, escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="25ba4-149">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="25ba4-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="25ba4-150">Na parte superior da caixa de diálogo, verifique se seu projeto é voltado para o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="25ba4-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="25ba4-151">Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.</span><span class="sxs-lookup"><span data-stu-id="25ba4-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="25ba4-152">Na lista de nomes, marque a caixa de seleção **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="25ba4-153">Escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="25ba4-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="25ba4-154"><a name="usingDir"></a> Adicionar as diretivas de uso necessárias</span><span class="sxs-lookup"><span data-stu-id="25ba4-154"><a name="usingDir"></a> To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="25ba4-155">No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="25ba4-156">Adicione as seguintes diretivas `using` na parte superior do arquivo de código, se elas ainda não estiverem presentes.</span><span class="sxs-lookup"><span data-stu-id="25ba4-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="25ba4-157"><a name="synchronous"></a> Criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="25ba4-158">Na janela de design, MainWindow.xaml, clique duas vezes no botão **Iniciar** para criar o manipulador de eventos `startButton_Click` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="25ba4-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="25ba4-159">Em MainWindow.xaml.cs, copie o seguinte código para o corpo de `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="25ba4-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="25ba4-160">O código chama o método que aciona o aplicativo, `SumPageSizes` e exibe uma mensagem quando o controle retorna para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="25ba4-161">O código para a solução síncrona contém os quatro métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="25ba4-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="25ba4-162">`SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e chama `GetURLContents` e `DisplayResults` para processar cada URL.</span><span class="sxs-lookup"><span data-stu-id="25ba4-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="25ba4-163">`SetUpURLList`, que cria e retorna uma lista de endereços web.</span><span class="sxs-lookup"><span data-stu-id="25ba4-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="25ba4-164">`GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="25ba4-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="25ba4-165">`DisplayResults`, que exibe o número de bytes na matriz de bytes de cada URL.</span><span class="sxs-lookup"><span data-stu-id="25ba4-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="25ba4-166">Copie os quatro métodos a seguir e cole-os no manipulador de eventos `startButton_Click` em MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="25ba4-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290136.aspx",  
            "http://msdn.microsoft.com/library/ee256749.aspx",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="25ba4-167"><a name="testSynch"></a> Testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="25ba4-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="25ba4-168">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="25ba4-169">Uma saída semelhante à lista a seguir deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="25ba4-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     <span data-ttu-id="25ba4-170">Observe que são necessários alguns segundos para exibir as contagens.</span><span class="sxs-lookup"><span data-stu-id="25ba4-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="25ba4-171">Durante esse tempo, o thread da interface do usuário é bloqueado enquanto espera que os recursos solicitados sejam baixados.</span><span class="sxs-lookup"><span data-stu-id="25ba4-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="25ba4-172">Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição após escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="25ba4-173">Esses esforços falham até que as contagens de bytes comecem a aparecer.</span><span class="sxs-lookup"><span data-stu-id="25ba4-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="25ba4-174">Se um site não estiver respondendo, você não terá nenhuma indicação de qual site falhou.</span><span class="sxs-lookup"><span data-stu-id="25ba4-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="25ba4-175">É difícil até mesmo parar de esperar e fechar o programa.</span><span class="sxs-lookup"><span data-stu-id="25ba4-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="25ba4-176"><a name="GetURLContents"></a> Converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="25ba4-177">Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents`, porque é pelas chamadas para o método <xref:System.Net.HttpWebRequest.GetResponse%2A> de <xref:System.Net.HttpWebRequest> e para o método <xref:System.IO.Stream.CopyTo%2A> de <xref:System.IO.Stream> que o aplicativo acessa a Web.</span><span class="sxs-lookup"><span data-stu-id="25ba4-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="25ba4-178">O .NET Framework facilita a conversão fornecendo versões assíncronas dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="25ba4-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="25ba4-179">Para obter mais informações sobre os métodos usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="25ba4-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25ba4-180">Conforme você seguir as etapas neste passo a passo, vários erros de compilador serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="25ba4-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="25ba4-181">Você pode ignorá-los e continuar com o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="25ba4-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="25ba4-182">Altere o método chamado na terceira linha de `GetURLContents` de `GetResponse` para o método <xref:System.Net.WebRequest.GetResponseAsync%2A> assíncrono, baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="25ba4-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="25ba4-183">`GetResponseAsync` retorna um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="25ba4-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="25ba4-184">Nesse caso, a *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="25ba4-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="25ba4-185">A tarefa é uma promessa de produzir um objeto `WebResponse` verdadeiro após os dados solicitados terem sido baixados e a tarefa ter sido executada até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="25ba4-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="25ba4-186">Para recuperar o valor `WebResponse` da tarefa, aplique um operador [await](../../../../csharp/language-reference/keywords/await.md) à chamada para `GetResponseAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="25ba4-187">O operador `await` suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="25ba4-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="25ba4-188">Enquanto isso, o controle retorna para o chamador do método atual.</span><span class="sxs-lookup"><span data-stu-id="25ba4-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="25ba4-189">Neste exemplo, o método atual é `GetURLContents` e o chamador é `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="25ba4-190">Quando a tarefa é concluída, o objeto `WebResponse` prometido é produzido como o valor da tarefa aguardada e é atribuído à variável `response`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="25ba4-191">A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.</span><span class="sxs-lookup"><span data-stu-id="25ba4-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="25ba4-192">A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="25ba4-193">Em seguida, um operador await é aplicado à tarefa para recuperar o valor `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="25ba4-194">Se seu método assíncrono tiver trabalho a fazer que não depende da conclusão da tarefa, o método poderá continuar com esse trabalho entre essas duas instruções, após a chamada para o método assíncrono e antes do operador `await` ser aplicado.</span><span class="sxs-lookup"><span data-stu-id="25ba4-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="25ba4-195">Para obter exemplos, consulte [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) (Como fazer várias solicitações da Web em paralelo usando async e await (C#)) e [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) (Como estender as instruções passo a passo async usando Task.WhenAll (C#)).</span><span class="sxs-lookup"><span data-stu-id="25ba4-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="25ba4-196">Como você adicionou o operador `await` na etapa anterior, um erro do compilador ocorre.</span><span class="sxs-lookup"><span data-stu-id="25ba4-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="25ba4-197">O operador pode ser usado apenas em métodos que são marcados com o modificador [async](../../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="25ba4-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="25ba4-198">Ignore o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` por uma chamada para `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="25ba4-199">Altere o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="25ba4-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="25ba4-200">O método `CopyTo` ou `CopyToAsync` copia bytes para seu argumento, `content` e não retorna um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="25ba4-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="25ba4-201">Na versão síncrona, a chamada para `CopyTo` é uma instrução simples que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="25ba4-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="25ba4-202">A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="25ba4-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="25ba4-203">A tarefa funciona como "Task(void)" e permite que o método seja aguardado.</span><span class="sxs-lookup"><span data-stu-id="25ba4-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="25ba4-204">Aplique `Await` ou `await` à chamada para `CopyToAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="25ba4-205">A instrução anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="25ba4-206">Tudo o que resta fazer em `GetURLContents` é ajustar a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="25ba4-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="25ba4-207">Você pode usar o operador `await` apenas em métodos que são marcados com o modificador [async](../../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="25ba4-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="25ba4-208">Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="25ba4-209">O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou `void` em C#.</span><span class="sxs-lookup"><span data-stu-id="25ba4-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="25ba4-210">Normalmente, um tipo de retorno de `void` é usado somente em um manipulador de eventos assíncrono, em que `void` é necessário.</span><span class="sxs-lookup"><span data-stu-id="25ba4-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="25ba4-211">Em outros casos, você usa `Task(T)` se o método concluído tiver uma instrução [return](../../../../csharp/language-reference/keywords/return.md) que retorna um valor do tipo T e usa `Task` se o método concluído não retornar um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="25ba4-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="25ba4-212">Você pode considerar que o tipo de retorno `Task` significa "Task(void)".</span><span class="sxs-lookup"><span data-stu-id="25ba4-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="25ba4-213">Para obter mais informações, consulte [Tipos de retorno assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="25ba4-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="25ba4-214">O método `GetURLContents` tem uma instrução de retorno e a instrução retorna uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="25ba4-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="25ba4-215">Portanto, o tipo de retorno da versão assíncrona é Task(T), em que T é uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="25ba4-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="25ba4-216">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="25ba4-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="25ba4-217">Altere o tipo de retorno para `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="25ba4-218">Por convenção, métodos assíncronos têm nomes que terminam em "Async", então renomeie o método `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="25ba4-219">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="25ba4-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="25ba4-220">Com essas poucas alterações, a conversão de `GetURLContents` em um método assíncrono é concluída.</span><span class="sxs-lookup"><span data-stu-id="25ba4-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="25ba4-221"><a name="SumPageSizes"></a> Converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-221"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="25ba4-222">Repita as etapas do procedimento anterior para `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="25ba4-223">Primeiro, altere a chamada para `GetURLContents` para uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="25ba4-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="25ba4-224">Altere o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="25ba4-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="25ba4-225">Aplique `await` à tarefa que `GetURLContentsAsync` retorna para obter o valor da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="25ba4-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="25ba4-226">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="25ba4-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="25ba4-227">A atribuição anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="25ba4-228">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="25ba4-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="25ba4-229">Marque o método com o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="25ba4-230">Acrescente "Async" ao nome do método.</span><span class="sxs-lookup"><span data-stu-id="25ba4-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="25ba4-231">Não há nenhuma variável de retorno de tarefa, T, desta vez porque `SumPageSizesAsync` não retorna um valor para T. (O método não tem uma instrução `return`.) No entanto, o método deve retornar um `Task` para que possa ser aguardado.</span><span class="sxs-lookup"><span data-stu-id="25ba4-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="25ba4-232">Portanto, altere o tipo de retorno do método de `void` para `Task`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="25ba4-233">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="25ba4-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="25ba4-234">A conversão de `SumPageSizes` em `SumPageSizesAsync` está concluída.</span><span class="sxs-lookup"><span data-stu-id="25ba4-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="25ba4-235"><a name="startButton"></a> Converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="25ba4-235"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="25ba4-236">No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="25ba4-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="25ba4-237">Como `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.</span><span class="sxs-lookup"><span data-stu-id="25ba4-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="25ba4-238">A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="25ba4-239">A chamada retorna um `Task` e não um `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="25ba4-240">Assim como nos procedimentos anteriores, você pode converter a chamada usando uma instrução ou duas instruções.</span><span class="sxs-lookup"><span data-stu-id="25ba4-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="25ba4-241">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="25ba4-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="25ba4-242">Para evitar inserir novamente a operação por acidente, adicione a seguinte instrução à parte superior de `startButton_Click` para desabilitar o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="25ba4-243">É possível reabilitar o botão no final do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="25ba4-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="25ba4-244">Para obter mais informações sobre a reentrada, consulte [Tratando a reentrada em aplicativos assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="25ba4-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="25ba4-245">Por fim, adicione o modificador `async` à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="25ba4-246">Normalmente, os nomes dos manipuladores de eventos não são alterados.</span><span class="sxs-lookup"><span data-stu-id="25ba4-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="25ba4-247">O tipo de retorno não é alterado para `Task` porque os manipuladores de eventos devem retornar `void`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="25ba4-248">A conversão do projeto de um processamento síncrono em um assíncrono está concluída.</span><span class="sxs-lookup"><span data-stu-id="25ba4-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="25ba4-249"><a name="testAsynch"></a> Testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="25ba4-249"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="25ba4-250">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="25ba4-251">Uma saída semelhante à saída da solução síncrona deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="25ba4-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="25ba4-252">No entanto, observe as diferenças a seguir.</span><span class="sxs-lookup"><span data-stu-id="25ba4-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="25ba4-253">Os resultados não ocorrem todos ao mesmo tempo, após a conclusão do processamento.</span><span class="sxs-lookup"><span data-stu-id="25ba4-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="25ba4-254">Por exemplo, os dois programas contêm uma linha em `startButton_Click` que desmarca a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="25ba4-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="25ba4-255">A intenção é desmarcar a caixa de texto entre as execuções se você escolher o botão **Iniciar** pela segunda vez, após um conjunto de resultados ter aparecido.</span><span class="sxs-lookup"><span data-stu-id="25ba4-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="25ba4-256">Na versão síncrona, a caixa de texto é desmarcada logo antes das contagens aparecerem pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário fica livre para executar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="25ba4-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="25ba4-257">Na versão assíncrona, a caixa de texto é limpa imediatamente após você escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="25ba4-258">Mais importante, o thread da interface do usuário não é bloqueado durante os downloads.</span><span class="sxs-lookup"><span data-stu-id="25ba4-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="25ba4-259">Você pode mover ou redimensionar a janela enquanto os recursos da Web estão sendo baixados, contados e exibido.</span><span class="sxs-lookup"><span data-stu-id="25ba4-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="25ba4-260">Se um dos sites estiver lento ou não estiver respondendo, você poderá cancelar a operação escolhendo o botão **Fechar** (o x no campo vermelho no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="25ba4-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="25ba4-261"><a name="GetURLContentsAsync"></a> Substituir o método GetURLContentsAsync por um método .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25ba4-261"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="25ba4-262">O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="25ba4-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="25ba4-263">Um deles, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> de <xref:System.Net.Http.HttpClient>, faz exatamente o que é necessário para este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="25ba4-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="25ba4-264">Você pode usá-lo em vez do método `GetURLContentsAsync` que criou em um procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="25ba4-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="25ba4-265">A primeira etapa é criar um objeto `HttpClient` no método `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="25ba4-266">Adicione a declaração a seguir ao início do método.</span><span class="sxs-lookup"><span data-stu-id="25ba4-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="25ba4-267">Em `SumPageSizesAsync,`, substitua a chamada para seu método `GetURLContentsAsync` por uma chamada para o método `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="25ba4-268">Remova ou comente o método `GetURLContentsAsync` que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="25ba4-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="25ba4-269">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="25ba4-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="25ba4-270">O comportamento desta versão do projeto deve corresponder ao comportamento que o procedimento "Testar a solução assíncrona" descreve, mas com ainda menos esforço para você.</span><span class="sxs-lookup"><span data-stu-id="25ba4-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="25ba4-271"><a name="BKMK_CompleteCodeExamples"></a> Exemplo</span><span class="sxs-lookup"><span data-stu-id="25ba4-271"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="25ba4-272">O código a seguir contém o exemplo completo da conversão de uma solução síncrona em uma solução assíncrona usando o método `GetURLContentsAsync` assíncrono que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="25ba4-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="25ba4-273">Observe que ele se assemelha muito à solução síncrona original.</span><span class="sxs-lookup"><span data-stu-id="25ba4-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="25ba4-274">O código a seguir contém o exemplo completo da solução que usa o método `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="25ba4-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25ba4-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25ba4-275">See Also</span></span>  
 [<span data-ttu-id="25ba4-276">Exemplo de assíncrono: Acessando o passo a passo da Web (c# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25ba4-276">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="25ba4-277">async</span><span class="sxs-lookup"><span data-stu-id="25ba4-277">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="25ba4-278">await</span><span class="sxs-lookup"><span data-stu-id="25ba4-278">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="25ba4-279">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="25ba4-279">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="25ba4-280">Tipos de retorno assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="25ba4-280">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="25ba4-281">Programação assíncrona com base em tarefa (TAP)</span><span class="sxs-lookup"><span data-stu-id="25ba4-281">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="25ba4-282">Como estender as instruções passo a passo assíncronas usando Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="25ba4-282">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="25ba4-283">Como fazer várias solicitações da Web em paralelo, usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="25ba4-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
