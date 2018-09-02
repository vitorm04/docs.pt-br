---
title: 'Passo a passo: Acessando a Web usando Async e Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: e00798a5e591ed8621cd0b5dbb4adfd1d41989bd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399672"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="92f31-102">Passo a passo: Acessando a Web usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="92f31-103">É possível escrever programas assíncronos de forma mais fácil e intuitiva usando funcionalidades async/await.</span><span class="sxs-lookup"><span data-stu-id="92f31-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="92f31-104">Você pode escrever código assíncrono que se parece com código síncrono e deixar que o compilador trate das complicadas continuações e funções de retorno de chamada que um código assíncrono normalmente envolve.</span><span class="sxs-lookup"><span data-stu-id="92f31-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="92f31-105">Para obter mais informações sobre o recurso Async, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="92f31-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="92f31-106">Este passo a passo começa com um aplicativo WPF (Windows Presentation Foundation) síncrono que soma o número de bytes em uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="92f31-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="92f31-107">Em seguida, converte o aplicativo em uma solução assíncrona usando os novos recursos.</span><span class="sxs-lookup"><span data-stu-id="92f31-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="92f31-108">Se não quiser compilar os aplicativos, você poderá baixar "Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)" nas [Amostras de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="92f31-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="92f31-109">Neste passo a passo, você realizará as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="92f31-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="92f31-110">Criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="92f31-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="92f31-111">Projetar um MainWindow WPF simples</span><span class="sxs-lookup"><span data-stu-id="92f31-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="92f31-112">Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="92f31-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="92f31-113">Para adicionar instruções Imports necessárias</span><span class="sxs-lookup"><span data-stu-id="92f31-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="92f31-114">Criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="92f31-115">Testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="92f31-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="92f31-116">Converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="92f31-117">Converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="92f31-118">Converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="92f31-119">Testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="92f31-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="92f31-120">Substituir o método GetURLContentsAsync por um método .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92f31-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="92f31-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92f31-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="92f31-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="92f31-122">Prerequisites</span></span>  
 <span data-ttu-id="92f31-123">O Visual Studio 2012 ou posterior deve estar instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="92f31-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="92f31-124">Para obter mais informações, consulte o [site da Microsoft](https://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="92f31-124">For more information, see the [Microsoft website](https://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="92f31-125">Criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="92f31-125">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="92f31-126">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92f31-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="92f31-127">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="92f31-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="92f31-128">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="92f31-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="92f31-129">No **modelos instalados** painel, escolha Visual Basic e, em seguida, escolha **aplicativo WPF** na lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="92f31-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="92f31-130">Na caixa de texto **Nome**, insira `AsyncExampleWPF` e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="92f31-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="92f31-131">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="92f31-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="92f31-132">Projetar um MainWindow WPF simples</span><span class="sxs-lookup"><span data-stu-id="92f31-132">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="92f31-133">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="92f31-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="92f31-134">Se a janela **Caixa de Ferramentas** não estiver visível, abra o menu **Exibir** e, em seguida, escolha **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="92f31-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="92f31-135">Adicione um controle **Botão** e um controle **Caixa de Texto** à janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="92f31-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="92f31-136">Realce o controle **Caixa de Texto** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="92f31-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="92f31-137">Defina a propriedade **Nome** como `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="92f31-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="92f31-138">Defina a propriedade **Altura** como 250.</span><span class="sxs-lookup"><span data-stu-id="92f31-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="92f31-139">Defina a propriedade **Largura** como 500.</span><span class="sxs-lookup"><span data-stu-id="92f31-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="92f31-140">Na guia **Texto**, especifique uma fonte com espaçamento uniforme, como Lucida Console ou Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="92f31-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="92f31-141">Realce o controle **Botão** e, na janela **Propriedades**, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="92f31-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="92f31-142">Defina a propriedade **Nome** como `startButton`.</span><span class="sxs-lookup"><span data-stu-id="92f31-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="92f31-143">Altere o valor da propriedade **Conteúdo** de **Botão** para **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="92f31-144">Posicione a caixa de texto e o botão de modo que ambos sejam exibidos na janela **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="92f31-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="92f31-145">Para obter mais informações sobre o Designer XAML do WPF, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="92f31-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="92f31-146">Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="92f31-146">To add a reference</span></span>  
  
1.  <span data-ttu-id="92f31-147">No **Gerenciador de Soluções**, realce o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="92f31-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="92f31-148">Na barra de menus, escolha **Projeto**, **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="92f31-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="92f31-149">A caixa de diálogo **Gerenciador de Referências** é exibida.</span><span class="sxs-lookup"><span data-stu-id="92f31-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="92f31-150">Na parte superior da caixa de diálogo, verifique se seu projeto é voltado para o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="92f31-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="92f31-151">Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.</span><span class="sxs-lookup"><span data-stu-id="92f31-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="92f31-152">Na lista de nomes, marque a caixa de seleção **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="92f31-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="92f31-153">Escolha o botão **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="92f31-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a> <span data-ttu-id="92f31-154">Para adicionar instruções Imports necessárias</span><span class="sxs-lookup"><span data-stu-id="92f31-154">To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="92f31-155">Na **Gerenciador de soluções**, abra o menu de atalho para XAML. vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="92f31-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="92f31-156">Adicione o seguinte `Imports` instruções na parte superior do arquivo de código se eles não ainda estiver presentes.</span><span class="sxs-lookup"><span data-stu-id="92f31-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="92f31-157">Criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-157">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="92f31-158">Na janela de design, MainWindow. XAML, clique duas vezes o **inicie** botão para criar o `startButton_Click` manipulador de eventos no XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="92f31-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="92f31-159">No XAML. vb, copie o seguinte código no corpo da `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="92f31-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="92f31-160">O código chama o método que aciona o aplicativo, `SumPageSizes` e exibe uma mensagem quando o controle retorna para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="92f31-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="92f31-161">O código para a solução síncrona contém os quatro métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="92f31-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="92f31-162">`SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e chama `GetURLContents` e `DisplayResults` para processar cada URL.</span><span class="sxs-lookup"><span data-stu-id="92f31-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="92f31-163">`SetUpURLList`, que cria e retorna uma lista de endereços web.</span><span class="sxs-lookup"><span data-stu-id="92f31-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="92f31-164">`GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="92f31-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="92f31-165">`DisplayResults`, que exibe o número de bytes na matriz de bytes de cada URL.</span><span class="sxs-lookup"><span data-stu-id="92f31-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="92f31-166">Copie os quatro métodos a seguir e, em seguida, cole-os no `startButton_Click` manipulador de eventos no XAML. vb:</span><span class="sxs-lookup"><span data-stu-id="92f31-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> <span data-ttu-id="92f31-167">Testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="92f31-167">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="92f31-168">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="92f31-169">Uma saída semelhante à lista a seguir deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="92f31-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="92f31-170">Observe que são necessários alguns segundos para exibir as contagens.</span><span class="sxs-lookup"><span data-stu-id="92f31-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="92f31-171">Durante esse tempo, o thread da interface do usuário é bloqueado enquanto espera que os recursos solicitados sejam baixados.</span><span class="sxs-lookup"><span data-stu-id="92f31-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="92f31-172">Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição após escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="92f31-173">Esses esforços falham até que as contagens de bytes comecem a aparecer.</span><span class="sxs-lookup"><span data-stu-id="92f31-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="92f31-174">Se um site não estiver respondendo, você não terá nenhuma indicação de qual site falhou.</span><span class="sxs-lookup"><span data-stu-id="92f31-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="92f31-175">É difícil até mesmo parar de esperar e fechar o programa.</span><span class="sxs-lookup"><span data-stu-id="92f31-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="92f31-176">Converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="92f31-177">Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents`, porque é pelas chamadas para o método <xref:System.Net.HttpWebRequest.GetResponse%2A> de <xref:System.Net.HttpWebRequest> e para o método <xref:System.IO.Stream.CopyTo%2A> de <xref:System.IO.Stream> que o aplicativo acessa a Web.</span><span class="sxs-lookup"><span data-stu-id="92f31-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="92f31-178">O .NET Framework facilita a conversão fornecendo versões assíncronas dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="92f31-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="92f31-179">Para obter mais informações sobre os métodos usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="92f31-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92f31-180">Conforme você seguir as etapas neste passo a passo, vários erros de compilador serão exibidos.</span><span class="sxs-lookup"><span data-stu-id="92f31-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="92f31-181">Você pode ignorá-los e continuar com o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="92f31-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="92f31-182">Altere o método chamado na terceira linha de `GetURLContents` de `GetResponse` para o método <xref:System.Net.WebRequest.GetResponseAsync%2A> assíncrono, baseado em tarefas.</span><span class="sxs-lookup"><span data-stu-id="92f31-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="92f31-183">`GetResponseAsync` retorna um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="92f31-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="92f31-184">Nesse caso, a *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="92f31-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="92f31-185">A tarefa é uma promessa de produzir um objeto `WebResponse` verdadeiro após os dados solicitados terem sido baixados e a tarefa ter sido executada até a conclusão.</span><span class="sxs-lookup"><span data-stu-id="92f31-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="92f31-186">Para recuperar o `WebResponse` o valor da tarefa, aplique um [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador para a chamada para `GetResponseAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="92f31-187">O operador `Await` suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="92f31-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="92f31-188">Enquanto isso, o controle retorna para o chamador do método atual.</span><span class="sxs-lookup"><span data-stu-id="92f31-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="92f31-189">Neste exemplo, o método atual é `GetURLContents` e o chamador é `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="92f31-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="92f31-190">Quando a tarefa é concluída, o objeto `WebResponse` prometido é produzido como o valor da tarefa aguardada e é atribuído à variável `response`.</span><span class="sxs-lookup"><span data-stu-id="92f31-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="92f31-191">A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.</span><span class="sxs-lookup"><span data-stu-id="92f31-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="92f31-192">A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="92f31-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="92f31-193">Em seguida, uma `Await` operador é aplicado à tarefa para recuperar o `WebResponse` valor.</span><span class="sxs-lookup"><span data-stu-id="92f31-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="92f31-194">Se seu método assíncrono tiver trabalho a fazer que não depende da conclusão da tarefa, o método poderá continuar com esse trabalho entre essas duas instruções, após a chamada para o método assíncrono e antes do operador await é aplicado.</span><span class="sxs-lookup"><span data-stu-id="92f31-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="92f31-195">Para obter exemplos, consulte [como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) e [como: estender a Async Walkthrough usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="92f31-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="92f31-196">Como você adicionou o operador `Await` na etapa anterior, um erro do compilador ocorre.</span><span class="sxs-lookup"><span data-stu-id="92f31-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="92f31-197">O operador pode ser usado apenas em métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="92f31-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="92f31-198">Ignore o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` por uma chamada para `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="92f31-199">Altere o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="92f31-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="92f31-200">O método `CopyTo` ou `CopyToAsync` copia bytes para seu argumento, `content` e não retorna um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="92f31-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="92f31-201">Na versão síncrona, a chamada para `CopyTo` é uma instrução simples que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="92f31-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="92f31-202">A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="92f31-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="92f31-203">A tarefa funciona como "Task(void)" e permite que o método seja aguardado.</span><span class="sxs-lookup"><span data-stu-id="92f31-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="92f31-204">Aplique `Await` ou `await` à chamada para `CopyToAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="92f31-205">A instrução anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  <span data-ttu-id="92f31-206">Tudo o que resta fazer em `GetURLContents` é ajustar a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="92f31-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="92f31-207">Você pode usar o `Await` operador apenas em métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="92f31-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="92f31-208">Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  <span data-ttu-id="92f31-209">O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="92f31-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="92f31-210">No Visual Basic, o método deve ser um `Function` que retorna um `Task` ou um `Task(Of T)`, ou o método deve ser um `Sub`.</span><span class="sxs-lookup"><span data-stu-id="92f31-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="92f31-211">Normalmente, uma `Sub` método é usado somente em um manipulador de eventos assíncronos, onde `Sub` é necessária.</span><span class="sxs-lookup"><span data-stu-id="92f31-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="92f31-212">Em outros casos, você deve usar `Task(T)` se o método concluído tiver uma [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) instrução que retorna um valor do tipo T, e você usar `Task` se o método concluído não retornar um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="92f31-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="92f31-213">Para obter mais informações, consulte [tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="92f31-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="92f31-214">O método `GetURLContents` tem uma instrução de retorno e a instrução retorna uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="92f31-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="92f31-215">Portanto, o tipo de retorno da versão assíncrona é Task(T), em que T é uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="92f31-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="92f31-216">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="92f31-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="92f31-217">Altere o tipo de retorno para `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="92f31-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="92f31-218">Por convenção, métodos assíncronos têm nomes que terminam em "Async", então renomeie o método `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="92f31-219">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="92f31-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="92f31-220">Com essas poucas alterações, a conversão de `GetURLContents` em um método assíncrono é concluída.</span><span class="sxs-lookup"><span data-stu-id="92f31-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="92f31-221">Converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="92f31-222">Repita as etapas do procedimento anterior para `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="92f31-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="92f31-223">Primeiro, altere a chamada para `GetURLContents` para uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="92f31-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="92f31-224">Altere o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="92f31-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="92f31-225">Aplique `Await` à tarefa que `GetURLContentsAsync` retorna para obter o valor da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="92f31-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="92f31-226">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="92f31-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="92f31-227">A atribuição anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  <span data-ttu-id="92f31-228">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="92f31-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="92f31-229">Marque o método com o modificador `Async`.</span><span class="sxs-lookup"><span data-stu-id="92f31-229">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="92f31-230">Acrescente "Async" ao nome do método.</span><span class="sxs-lookup"><span data-stu-id="92f31-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="92f31-231">Não há nenhuma variável de retorno de tarefa, T, desta vez porque `SumPageSizesAsync` não retorna um valor para T. (O método não tem uma instrução `Return`.) No entanto, o método deve retornar um `Task` para que possa ser aguardado.</span><span class="sxs-lookup"><span data-stu-id="92f31-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="92f31-232">Portanto, alterar o tipo de método de `Sub` para `Function`.</span><span class="sxs-lookup"><span data-stu-id="92f31-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="92f31-233">O tipo de retorno da função é `Task`.</span><span class="sxs-lookup"><span data-stu-id="92f31-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="92f31-234">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="92f31-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="92f31-235">A conversão de `SumPageSizes` em `SumPageSizesAsync` está concluída.</span><span class="sxs-lookup"><span data-stu-id="92f31-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="92f31-236">Converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="92f31-236">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="92f31-237">No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se ainda não tiver feito isso.</span><span class="sxs-lookup"><span data-stu-id="92f31-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="92f31-238">Como `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.</span><span class="sxs-lookup"><span data-stu-id="92f31-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="92f31-239">A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="92f31-240">A chamada retorna um `Task` e não um `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="92f31-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="92f31-241">Assim como nos procedimentos anteriores, você pode converter a chamada usando uma instrução ou duas instruções.</span><span class="sxs-lookup"><span data-stu-id="92f31-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="92f31-242">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="92f31-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="92f31-243">Para evitar inserir novamente a operação por acidente, adicione a seguinte instrução à parte superior de `startButton_Click` para desabilitar o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="92f31-244">É possível reabilitar o botão no final do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="92f31-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="92f31-245">Para obter mais informações sobre a reentrada, consulte [tratando a reentrada em aplicativos assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="92f31-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="92f31-246">Por fim, adicione o modificador `Async` à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="92f31-247">Normalmente, os nomes dos manipuladores de eventos não são alterados.</span><span class="sxs-lookup"><span data-stu-id="92f31-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="92f31-248">O tipo de retorno não é alterado para `Task` porque os manipuladores de eventos devem ser `Sub` procedimentos no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="92f31-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="92f31-249">A conversão do projeto de um processamento síncrono em um assíncrono está concluída.</span><span class="sxs-lookup"><span data-stu-id="92f31-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="92f31-250">Testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="92f31-250">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="92f31-251">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="92f31-252">Uma saída semelhante à saída da solução síncrona deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="92f31-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="92f31-253">No entanto, observe as diferenças a seguir.</span><span class="sxs-lookup"><span data-stu-id="92f31-253">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="92f31-254">Os resultados não ocorrem todos ao mesmo tempo, após a conclusão do processamento.</span><span class="sxs-lookup"><span data-stu-id="92f31-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="92f31-255">Por exemplo, os dois programas contêm uma linha em `startButton_Click` que desmarca a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="92f31-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="92f31-256">A intenção é desmarcar a caixa de texto entre as execuções se você escolher o botão **Iniciar** pela segunda vez, após um conjunto de resultados ter aparecido.</span><span class="sxs-lookup"><span data-stu-id="92f31-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="92f31-257">Na versão síncrona, a caixa de texto é desmarcada logo antes das contagens aparecerem pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário fica livre para executar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="92f31-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="92f31-258">Na versão assíncrona, a caixa de texto é limpa imediatamente após você escolher o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="92f31-259">Mais importante, o thread da interface do usuário não é bloqueado durante os downloads.</span><span class="sxs-lookup"><span data-stu-id="92f31-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="92f31-260">Você pode mover ou redimensionar a janela enquanto os recursos da Web estão sendo baixados, contados e exibido.</span><span class="sxs-lookup"><span data-stu-id="92f31-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="92f31-261">Se um dos sites estiver lento ou não estiver respondendo, você poderá cancelar a operação escolhendo o botão **Fechar** (o x no campo vermelho no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="92f31-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="92f31-262">Substituir o método GetURLContentsAsync por um método .NET Framework</span><span class="sxs-lookup"><span data-stu-id="92f31-262">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="92f31-263">O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="92f31-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="92f31-264">Um deles, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> de <xref:System.Net.Http.HttpClient>, faz exatamente o que é necessário para este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="92f31-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="92f31-265">Você pode usá-lo em vez do método `GetURLContentsAsync` que criou em um procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="92f31-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="92f31-266">A primeira etapa é criar um objeto `HttpClient` no método `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="92f31-267">Adicione a declaração a seguir ao início do método.</span><span class="sxs-lookup"><span data-stu-id="92f31-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="92f31-268">Em `SumPageSizesAsync,`, substitua a chamada para seu método `GetURLContentsAsync` por uma chamada para o método `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="92f31-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="92f31-269">Remova ou comente o método `GetURLContentsAsync` que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="92f31-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="92f31-270">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="92f31-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="92f31-271">O comportamento desta versão do projeto deve corresponder ao comportamento que o procedimento "Testar a solução assíncrona" descreve, mas com ainda menos esforço para você.</span><span class="sxs-lookup"><span data-stu-id="92f31-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="92f31-272">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92f31-272">Example</span></span>  
 <span data-ttu-id="92f31-273">O código a seguir contém o exemplo completo da conversão de uma solução síncrona em uma solução assíncrona usando o método `GetURLContentsAsync` assíncrono que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="92f31-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="92f31-274">Observe que ele se assemelha muito à solução síncrona original.</span><span class="sxs-lookup"><span data-stu-id="92f31-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="92f31-275">O código a seguir contém o exemplo completo da solução que usa o método `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="92f31-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="92f31-276">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92f31-276">See Also</span></span>  
 [<span data-ttu-id="92f31-277">Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [<span data-ttu-id="92f31-278">Operador Await</span><span class="sxs-lookup"><span data-stu-id="92f31-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="92f31-279">Async</span><span class="sxs-lookup"><span data-stu-id="92f31-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="92f31-280">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="92f31-281">Tipos de retorno assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="92f31-282">TAP (programação assíncrona baseada em tarefas)</span><span class="sxs-lookup"><span data-stu-id="92f31-282">Task-based Asynchronous Programming (TAP)</span></span>](https://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="92f31-283">Como estender as instruções passo a passo assíncronas usando Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="92f31-284">Como fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92f31-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
