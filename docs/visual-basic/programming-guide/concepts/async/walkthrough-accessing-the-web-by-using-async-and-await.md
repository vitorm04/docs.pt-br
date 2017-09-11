---
title: Acessando a Web com Async e Await (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="84fc6-102">Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84fc6-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="84fc6-103">Você pode escrever programas assíncronos intuitivamente e mais facilmente usando os recursos que foram introduzidos no [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span><span class="sxs-lookup"><span data-stu-id="84fc6-103">You can write asynchronous programs more easily and intuitively by using features that were introduced in [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span></span> <span data-ttu-id="84fc6-104">Você pode escrever código assíncrono que se parece com o código síncrono e deixar que o compilador lidar com as funções de retorno de chamada difícil e continuações normalmente envolve um código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="84fc6-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="84fc6-105">Para obter mais informações sobre o recurso Async, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="84fc6-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="84fc6-106">Este passo a passo começa com um aplicativo Windows Presentation Foundation (WPF) síncrono que some o número de bytes em uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="84fc6-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="84fc6-107">Passo a passo, em seguida, converte o aplicativo para uma solução assíncrona usando os novos recursos.</span><span class="sxs-lookup"><span data-stu-id="84fc6-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="84fc6-108">Se você não quiser criar os aplicativos por conta própria, você pode baixar "exemplo de assincronia: acessando o passo a passo da Web (c# e Visual Basic)" do [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="84fc6-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="84fc6-109">Neste passo a passo, você deve concluir as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="84fc6-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="84fc6-110">Para criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="84fc6-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="84fc6-111">Para criar um simples MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="84fc6-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="84fc6-112">Para adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="84fc6-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="84fc6-113">Para adicionar instruções Imports necessárias</span><span class="sxs-lookup"><span data-stu-id="84fc6-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="84fc6-114">Para criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="84fc6-115">Para testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="84fc6-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="84fc6-116">Para converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="84fc6-117">Para converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="84fc6-118">Para converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="84fc6-119">Para testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="84fc6-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="84fc6-120">Para substituir o método GetURLContentsAsync com um método do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84fc6-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="84fc6-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84fc6-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="84fc6-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="84fc6-122">Prerequisites</span></span>  
 <span data-ttu-id="84fc6-123">Visual Studio 2012 ou posterior deve ser instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="84fc6-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="84fc6-124">Para obter mais informações, consulte o [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="84fc6-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="84fc6-125"><a name="CreateWPFApp"></a>Para criar um aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="84fc6-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="84fc6-126">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="84fc6-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="84fc6-127">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="84fc6-128">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="84fc6-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="84fc6-129">No **modelos instalados** painel, escolha Visual Basic e, em seguida, escolha **aplicativo WPF** da lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="84fc6-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="84fc6-130">No **nome** texto, digite `AsyncExampleWPF`e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="84fc6-131">O novo projeto aparece na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="84fc6-132"><a name="MainWindow"></a>Para criar um simples MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="84fc6-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="84fc6-133">No código de Editor do Visual Studio, escolha o **MainWindow** guia.</span><span class="sxs-lookup"><span data-stu-id="84fc6-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="84fc6-134">Se o **Toolbox** janela não estiver visível, abra o **exibição** menu e, em seguida, escolha **ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="84fc6-135">Adicionar uma **botão** controle e um **TextBox** o controle para o **MainWindow** janela.</span><span class="sxs-lookup"><span data-stu-id="84fc6-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="84fc6-136">Realce o **TextBox** controle e, no **propriedades** janela, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="84fc6-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="84fc6-137">Definir o **nome** propriedade `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="84fc6-138">Definir o **altura** propriedade para 250.</span><span class="sxs-lookup"><span data-stu-id="84fc6-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="84fc6-139">Definir o **largura** propriedade a 500.</span><span class="sxs-lookup"><span data-stu-id="84fc6-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="84fc6-140">Sobre o **texto** , especifique uma fonte monoespaçada, como Lucida Console ou Monospace Global.</span><span class="sxs-lookup"><span data-stu-id="84fc6-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="84fc6-141">Realce o **botão** controle e, no **propriedades** janela, defina os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="84fc6-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="84fc6-142">Definir o **nome** propriedade `startButton`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="84fc6-143">Altere o valor da **conteúdo** propriedade **botão** para **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="84fc6-144">Posicione a caixa de texto e o botão para que ambos sejam exibidos no **MainWindow** janela.</span><span class="sxs-lookup"><span data-stu-id="84fc6-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="84fc6-145">Para obter mais informações sobre o WPF XAML Designer, consulte [criando uma interface do usuário usando o Designer XAML](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="84fc6-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="84fc6-146"><a name="AddRef"></a>Para adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="84fc6-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="84fc6-147">Em **Solution Explorer**, realce o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="84fc6-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="84fc6-148">Na barra de menus, escolha **projeto**, **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="84fc6-149">O **Gerenciador de referências** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="84fc6-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="84fc6-150">Na parte superior da caixa de diálogo, verifique se o seu projeto é voltado para o .NET Framework 4.5 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="84fc6-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="84fc6-151">No **Assemblies** área, escolha **Framework** se ele já não é escolhido.</span><span class="sxs-lookup"><span data-stu-id="84fc6-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="84fc6-152">Na lista de nomes, selecione o **System.Net.Http** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="84fc6-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="84fc6-153">Escolha o **Okey** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84fc6-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="84fc6-154"><a name="ImportsState"></a>Para adicionar instruções Imports necessárias</span><span class="sxs-lookup"><span data-stu-id="84fc6-154"><a name="ImportsState"></a> To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="84fc6-155">Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="84fc6-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="84fc6-156">Adicione o seguinte `Imports` instruções na parte superior do arquivo de código, se eles não ainda estiver presentes.</span><span class="sxs-lookup"><span data-stu-id="84fc6-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="84fc6-157"><a name="synchronous"></a>Para criar um aplicativo síncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="84fc6-158">Na janela de design, MainWindow. XAML, clique duas vezes o **iniciar** botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="84fc6-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="84fc6-159">Em MainWindow.xaml.vb, copie o seguinte código no corpo da `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="84fc6-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="84fc6-160">O código chama o método que acionam o aplicativo `SumPageSizes`e exibe uma mensagem quando o controle retorna para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="84fc6-161">O código para a solução síncrona contém os quatro métodos a seguir:</span><span class="sxs-lookup"><span data-stu-id="84fc6-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="84fc6-162">`SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e, em seguida, chama `GetURLContents` e `DisplayResults` para processar cada URL.</span><span class="sxs-lookup"><span data-stu-id="84fc6-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="84fc6-163">`SetUpURLList`, que cria e retorna uma lista de endereços da web.</span><span class="sxs-lookup"><span data-stu-id="84fc6-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="84fc6-164">`GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="84fc6-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="84fc6-165">`DisplayResults`, que exibe o número de bytes na matriz de bytes para cada URL.</span><span class="sxs-lookup"><span data-stu-id="84fc6-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="84fc6-166">Copie os quatro métodos e colá-los sob o `startButton_Click` manipulador de eventos MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="84fc6-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
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
###  <span data-ttu-id="84fc6-167"><a name="testSynch"></a>Para testar a solução síncrona</span><span class="sxs-lookup"><span data-stu-id="84fc6-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="84fc6-168">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="84fc6-169">Saída semelhante a lista a seguir deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="84fc6-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="84fc6-170">Observe que levará alguns segundos para exibir as contagens.</span><span class="sxs-lookup"><span data-stu-id="84fc6-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="84fc6-171">Durante esse tempo, o thread de interface do usuário é bloqueado enquanto aguarda recursos solicitados fazer o download.</span><span class="sxs-lookup"><span data-stu-id="84fc6-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="84fc6-172">Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição depois de escolher o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="84fc6-173">Esses esforços falham até que as contagens de byte começam a aparecer.</span><span class="sxs-lookup"><span data-stu-id="84fc6-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="84fc6-174">Se um site não estiver respondendo, você pode ter nenhuma indicação de qual site falhou.</span><span class="sxs-lookup"><span data-stu-id="84fc6-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="84fc6-175">É difícil até mesmo pare de esperar e fecha o programa.</span><span class="sxs-lookup"><span data-stu-id="84fc6-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="84fc6-176"><a name="GetURLContents"></a>Para converter GetURLContents em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="84fc6-177">Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents` porque as chamadas para o <xref:System.Net.HttpWebRequest>método <xref:System.Net.HttpWebRequest.GetResponse%2A>e o <xref:System.IO.Stream>método <xref:System.IO.Stream.CopyTo%2A>são onde o aplicativo acessa a web.</xref:System.IO.Stream.CopyTo%2A> </xref:System.IO.Stream> </xref:System.Net.HttpWebRequest.GetResponse%2A> </xref:System.Net.HttpWebRequest></span><span class="sxs-lookup"><span data-stu-id="84fc6-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="84fc6-178">O .NET Framework facilita a conversão ao fornecer versões assíncronas dos dois métodos.</span><span class="sxs-lookup"><span data-stu-id="84fc6-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="84fc6-179">Para obter mais informações sobre os métodos que são usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.</xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="84fc6-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="84fc6-180">Quando você seguir as etapas neste passo a passo, vários erros de compilador são exibidas.</span><span class="sxs-lookup"><span data-stu-id="84fc6-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="84fc6-181">Você pode ignorá-las e continuar com o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="84fc6-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="84fc6-182">Alterar o método é chamado na terceira linha da `GetURLContents` de `GetResponse` assíncrono, baseado em tarefa <xref:System.Net.WebRequest.GetResponseAsync%2A>método.</xref:System.Net.WebRequest.GetResponseAsync%2A></span><span class="sxs-lookup"><span data-stu-id="84fc6-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="84fc6-183">`GetResponseAsync`Retorna um <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="84fc6-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="84fc6-184">Nesse caso, o *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>.</xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="84fc6-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="84fc6-185">A tarefa é uma promessa de produzir um verdadeiro `WebResponse` depois que os dados solicitados foi baixados e a tarefa foi executada até a conclusão do objeto.</span><span class="sxs-lookup"><span data-stu-id="84fc6-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="84fc6-186">Para recuperar o `WebResponse` o valor da tarefa, aplique um [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador da chamada `GetResponseAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84fc6-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="84fc6-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="84fc6-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="84fc6-188">O `Await` operador suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="84fc6-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="84fc6-189">Enquanto isso, o controle retorna para o chamador do método atual.</span><span class="sxs-lookup"><span data-stu-id="84fc6-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="84fc6-190">Neste exemplo, o método atual é `GetURLContents`, e o chamador é `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="84fc6-191">Quando a tarefa é concluída, o prometido `WebResponse` objeto é produzido como o valor da tarefa awaited e atribuído à variável `response`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<span data-ttu-id="84fc6-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="84fc6-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="84fc6-193">A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="84fc6-194">Um `Await` operador é aplicado à tarefa para recuperar o `WebResponse` valor.</span><span class="sxs-lookup"><span data-stu-id="84fc6-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  <span data-ttu-id="84fc6-195">Como você adicionou o `Await` operador na etapa anterior, um erro do compilador ocorre.</span><span class="sxs-lookup"><span data-stu-id="84fc6-195">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="84fc6-196">O operador pode ser usado apenas nos métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="84fc6-196">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="84fc6-197">Ignorar o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` com uma chamada para `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-197">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="84fc6-198">Alterar o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.</xref:System.IO.Stream.CopyToAsync%2A></span><span class="sxs-lookup"><span data-stu-id="84fc6-198">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="84fc6-199">O `CopyTo` ou `CopyToAsync` método copia bytes para o argumento `content`e não retorna um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="84fc6-199">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="84fc6-200">Na versão síncrona, a chamada para `CopyTo` é uma simple instrução que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="84fc6-200">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="84fc6-201">A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="84fc6-201">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="84fc6-202">A tarefa funciona como "Task(void)" e permite que o método a ser aguardado.</span><span class="sxs-lookup"><span data-stu-id="84fc6-202">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="84fc6-203">Aplicar `Await` ou `await` da chamada `CopyToAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84fc6-203">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="84fc6-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="84fc6-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
         <span data-ttu-id="84fc6-205">A instrução anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84fc6-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
<span data-ttu-id="84fc6-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="84fc6-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="84fc6-207">Tudo o que resta a ser feito em `GetURLContents` é ajustar a assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="84fc6-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="84fc6-208">Você pode usar o `Await` operador apenas nos métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="84fc6-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="84fc6-209">Adicione o modificador para marcar o método como uma *método assíncrono*, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84fc6-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
<span data-ttu-id="84fc6-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="84fc6-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
5.  <span data-ttu-id="84fc6-211">O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="84fc6-211">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="84fc6-212">No Visual Basic, o método deve ser um `Function` que retorna um `Task` ou um `Task(Of T)`, ou o método deve ser um `Sub`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-212">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="84fc6-213">Normalmente, um `Sub` método é usado somente em um manipulador de eventos assíncronos, onde `Sub` é necessária.</span><span class="sxs-lookup"><span data-stu-id="84fc6-213">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="84fc6-214">Em outros casos, você usa `Task(T)` se o método concluído tiver uma [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) instrução que retorna um valor do tipo T, e você usar `Task` se o método concluído não retorna um valor significativo.</span><span class="sxs-lookup"><span data-stu-id="84fc6-214">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="84fc6-215">Para obter mais informações, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="84fc6-215">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="84fc6-216">Método `GetURLContents` possui uma instrução de retorno, e a instrução retorna uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="84fc6-216">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="84fc6-217">Portanto, o tipo de retorno da versão async é Task(T), onde T é uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="84fc6-217">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="84fc6-218">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="84fc6-218">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="84fc6-219">Alterar o tipo de retorno para `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-219">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="84fc6-220">Por convenção, os métodos assíncronos têm nomes que terminam em "Async", então renomear o método `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-220">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="84fc6-221">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="84fc6-221">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="84fc6-222">Com essas poucas alterações, a conversão de `GetURLContents` para um método assíncrono é concluído.</span><span class="sxs-lookup"><span data-stu-id="84fc6-222">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="84fc6-223"><a name="SumPageSizes"></a>Para converter SumPageSizes em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-223"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="84fc6-224">Repita as etapas do procedimento anterior para `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-224">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="84fc6-225">Primeiro, altere a chamada a `GetURLContents` para uma chamada assíncrona.</span><span class="sxs-lookup"><span data-stu-id="84fc6-225">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="84fc6-226">Alterar o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se você ainda não fez isso.</span><span class="sxs-lookup"><span data-stu-id="84fc6-226">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="84fc6-227">Aplicar `Await` para a tarefa que `GetURLContentsAsync` retorna o byte de obter o valor de matriz.</span><span class="sxs-lookup"><span data-stu-id="84fc6-227">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="84fc6-228">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="84fc6-228">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="84fc6-229">A atribuição anterior abrevia as duas linhas de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84fc6-229">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  <span data-ttu-id="84fc6-230">Faça as seguintes alterações na assinatura do método:</span><span class="sxs-lookup"><span data-stu-id="84fc6-230">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="84fc6-231">Marcar o método com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="84fc6-231">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="84fc6-232">Adicione "Async" para o nome do método.</span><span class="sxs-lookup"><span data-stu-id="84fc6-232">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="84fc6-233">Não há nenhuma variável de retorno de tarefa, T, neste momento porque `SumPageSizesAsync` não retorna um valor de T. (O método não tem `Return` instrução.) No entanto, o método deve retornar um `Task` para awaitable.</span><span class="sxs-lookup"><span data-stu-id="84fc6-233">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="84fc6-234">Portanto, altere o tipo de método de `Sub` para `Function`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-234">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="84fc6-235">O tipo de retorno da função é `Task`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-235">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="84fc6-236">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="84fc6-236">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="84fc6-237">A conversão de `SumPageSizes` para `SumPageSizesAsync` for concluída.</span><span class="sxs-lookup"><span data-stu-id="84fc6-237">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="84fc6-238"><a name="startButton"></a>Para converter startButton_Click em um método assíncrono</span><span class="sxs-lookup"><span data-stu-id="84fc6-238"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="84fc6-239">No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se você ainda não fez isso.</span><span class="sxs-lookup"><span data-stu-id="84fc6-239">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="84fc6-240">Porque `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.</span><span class="sxs-lookup"><span data-stu-id="84fc6-240">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="84fc6-241">A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-241">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="84fc6-242">A chamada retorna um `Task`, e não um `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-242">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="84fc6-243">Como em procedimentos anteriores, você pode converter a chamada por meio de uma instrução ou duas instruções.</span><span class="sxs-lookup"><span data-stu-id="84fc6-243">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="84fc6-244">O código a seguir mostra essas alterações.</span><span class="sxs-lookup"><span data-stu-id="84fc6-244">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="84fc6-245">Para evitar que acidentalmente redigitando a operação, adicione a seguinte instrução na parte superior do `startButton_Click` para desabilitar o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-245">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="84fc6-246">Você pode reabilitar o botão no final do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="84fc6-246">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="84fc6-247">Para obter mais informações sobre reentrância, consulte [tratando reentrada em aplicativos assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="84fc6-247">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="84fc6-248">Finalmente, adicione o `Async` modificador à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-248">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="84fc6-249">Normalmente, os nomes de manipuladores de eventos não são alterados.</span><span class="sxs-lookup"><span data-stu-id="84fc6-249">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="84fc6-250">O tipo de retorno não é alterado para `Task` como manipuladores de eventos devem ser `Sub` procedimentos no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84fc6-250">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="84fc6-251">A conversão do projeto de processamento síncrono para assíncrono é concluída.</span><span class="sxs-lookup"><span data-stu-id="84fc6-251">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="84fc6-252"><a name="testAsynch"></a>Para testar a solução assíncrona</span><span class="sxs-lookup"><span data-stu-id="84fc6-252"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="84fc6-253">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-253">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="84fc6-254">A saída que é semelhante à saída da solução síncrona deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="84fc6-254">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="84fc6-255">No entanto, observe as seguintes diferenças.</span><span class="sxs-lookup"><span data-stu-id="84fc6-255">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="84fc6-256">Os resultados não ocorrem ao mesmo tempo, após o processamento é concluído.</span><span class="sxs-lookup"><span data-stu-id="84fc6-256">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="84fc6-257">Por exemplo, os dois programas contêm uma linha no `startButton_Click` que desmarca a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="84fc6-257">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="84fc6-258">A intenção é desmarcar a caixa de texto entre as execuções, se você escolher o **iniciar** botão pela segunda vez, depois que um conjunto de resultados apareceu.</span><span class="sxs-lookup"><span data-stu-id="84fc6-258">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="84fc6-259">Na versão síncrona, a caixa de texto é limpo antes que as contagens são exibidos pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário está livre para executar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="84fc6-259">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="84fc6-260">A versão assíncrona, a caixa de texto limpa imediatamente depois que você escolher o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-260">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="84fc6-261">Mais importante, o thread de interface do usuário não é bloqueado durante os downloads.</span><span class="sxs-lookup"><span data-stu-id="84fc6-261">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="84fc6-262">Você pode mover ou redimensionar a janela enquanto os recursos da web estão sendo baixados, contados e exibido.</span><span class="sxs-lookup"><span data-stu-id="84fc6-262">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="84fc6-263">Se um dos sites está lento ou não responder, você pode cancelar a operação, escolhendo o **fechar** botão (o x no campo vermelho no canto superior direito).</span><span class="sxs-lookup"><span data-stu-id="84fc6-263">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="84fc6-264"><a name="GetURLContentsAsync"></a>Para substituir o método GetURLContentsAsync com um método do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84fc6-264"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="84fc6-265">O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="84fc6-265">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="84fc6-266">Um deles, o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, exatamente o que você precisa para este passo a passo.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="84fc6-266">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="84fc6-267">Você pode usá-lo em vez do `GetURLContentsAsync` método que você criou em um procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="84fc6-267">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="84fc6-268">A primeira etapa é criar um `HttpClient` objeto no método `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-268">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="84fc6-269">Adicione a seguinte declaração no início do método.</span><span class="sxs-lookup"><span data-stu-id="84fc6-269">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="84fc6-270">Em `SumPageSizesAsync,` substitua a chamada para o `GetURLContentsAsync` método com uma chamada para o `HttpClient` método.</span><span class="sxs-lookup"><span data-stu-id="84fc6-270">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="84fc6-271">Remova ou comente o `GetURLContentsAsync` método que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="84fc6-271">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="84fc6-272">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="84fc6-272">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="84fc6-273">O comportamento desta versão do projeto deve corresponder ao comportamento que descreve o procedimento "para testar a solução assíncrona" mas com o mesmo menos esforço do que você.</span><span class="sxs-lookup"><span data-stu-id="84fc6-273">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="84fc6-274"><a name="BKMK_CompleteCodeExamples"></a> Exemplo</span><span class="sxs-lookup"><span data-stu-id="84fc6-274"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="84fc6-275">O código a seguir contém o exemplo completo de conversão de um síncrono para uma solução assíncrona usando assíncrona `GetURLContentsAsync` método que você escreveu.</span><span class="sxs-lookup"><span data-stu-id="84fc6-275">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="84fc6-276">Observe que ele fortemente se assemelha a solução síncrona original.</span><span class="sxs-lookup"><span data-stu-id="84fc6-276">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="84fc6-277">O código a seguir contém o exemplo completo da solução que usa o `HttpClient` método `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="84fc6-277">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84fc6-278">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84fc6-278">See Also</span></span>  
 <span data-ttu-id="84fc6-279">[Exemplo de assincronia: Acessando o passo a passo da Web (c# e Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span><span class="sxs-lookup"><span data-stu-id="84fc6-279">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span></span>  
<span data-ttu-id="84fc6-280"> [Operador await](../../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="84fc6-280"> [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="84fc6-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span><span class="sxs-lookup"><span data-stu-id="84fc6-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span></span>  
<span data-ttu-id="84fc6-282"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="84fc6-282"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="84fc6-283"> [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="84fc6-283"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="84fc6-284"> [Programação assíncrona baseado em tarefa (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span><span class="sxs-lookup"><span data-stu-id="84fc6-284"> [Task-based Asynchronous Programming (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span></span>  
<span data-ttu-id="84fc6-285"> [Como: estender o passo a passo assíncronas usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span><span class="sxs-lookup"><span data-stu-id="84fc6-285"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span></span>  
<span data-ttu-id="84fc6-286"> [Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="84fc6-286"> [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span></span>
