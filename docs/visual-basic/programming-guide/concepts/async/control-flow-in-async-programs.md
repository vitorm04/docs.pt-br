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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="05b20-102">Fluxo de controle em programas assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05b20-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="05b20-103">Você pode escrever e manter assíncronos programas mais facilmente usando o `Async` e `Await` palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="05b20-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="05b20-104">No entanto, os resultados podem surpreendê-lo se você não entender o funcionamento do seu programa.</span><span class="sxs-lookup"><span data-stu-id="05b20-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="05b20-105">Este rastreamentos de tópico o fluxo de controle por meio de um programa assíncrono simples para mostrar a você quando o controle se move de um método para outro e quais informações é transferido de cada vez.</span><span class="sxs-lookup"><span data-stu-id="05b20-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b20-106">O `Async` e `Await` palavras-chave foram introduzidas no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="05b20-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="05b20-107">Em geral, você pode marcar métodos que contêm código assíncrono com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="05b20-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="05b20-108">Em um método marcado com um modificador assíncrono, você pode usar um [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operador para especificar onde o método faz uma pausa para esperar por um processo assíncrono chamado concluir.</span><span class="sxs-lookup"><span data-stu-id="05b20-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="05b20-109">Para obter mais informações, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="05b20-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="05b20-110">O exemplo a seguir usa os métodos assíncronos para baixar o conteúdo de um site especificado como uma cadeia de caracteres e exibir o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="05b20-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="05b20-111">O exemplo contém dois métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="05b20-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="05b20-112">`startButton_Click`, que chama `AccessTheWebAsync` e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="05b20-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="05b20-113">`AccessTheWebAsync`, que baixa o conteúdo de um site como uma cadeia de caracteres e retorna o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="05b20-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="05b20-114">`AccessTheWebAsync`usa assíncrona <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, para baixar o conteúdo.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="05b20-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="05b20-115">Numeradas exibição linhas aparecem em pontos estratégicos em todo o programa para ajudá-lo a entender como o programa é executado e explicar o que acontece em cada ponto marcado.</span><span class="sxs-lookup"><span data-stu-id="05b20-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="05b20-116">Exibir linhas são rotulados como "Um"a "seis."</span><span class="sxs-lookup"><span data-stu-id="05b20-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="05b20-117">Os rótulos de representam a ordem na qual o programa atingir estas linhas de código.</span><span class="sxs-lookup"><span data-stu-id="05b20-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="05b20-118">O código a seguir mostra uma estrutura de tópicos do programa.</span><span class="sxs-lookup"><span data-stu-id="05b20-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="05b20-119">Todos os locais de rotulado, "Um"a "seis," exibe informações sobre o estado atual do programa.</span><span class="sxs-lookup"><span data-stu-id="05b20-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="05b20-120">A seguinte saída é produzida.</span><span class="sxs-lookup"><span data-stu-id="05b20-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="05b20-121">Configurar o Programa</span><span class="sxs-lookup"><span data-stu-id="05b20-121">Set Up the Program</span></span>  
 <span data-ttu-id="05b20-122">Você pode baixar o código que usa este tópico do MSDN, ou você pode criá-la sozinho.</span><span class="sxs-lookup"><span data-stu-id="05b20-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b20-123">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="05b20-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="05b20-124">Baixar o Programa</span><span class="sxs-lookup"><span data-stu-id="05b20-124">Download the Program</span></span>  
 <span data-ttu-id="05b20-125">Você pode baixar o aplicativo para este tópico de [exemplo de assincronia: fluxo de controle em programas assíncronos](http://go.microsoft.com/fwlink/?LinkId=255285).</span><span class="sxs-lookup"><span data-stu-id="05b20-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="05b20-126">As etapas a seguir abrirem e executam o programa.</span><span class="sxs-lookup"><span data-stu-id="05b20-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="05b20-127">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05b20-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="05b20-128">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="05b20-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="05b20-129">Navegue até a pasta que contém o código de exemplo descompactado, abra o arquivo de solução (. sln) e pressione a tecla F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="05b20-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="05b20-130">Compilar o Programa Sozinho</span><span class="sxs-lookup"><span data-stu-id="05b20-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="05b20-131">O projeto Windows Presentation Foundation (WPF) a seguir contém o código de exemplo neste tópico.</span><span class="sxs-lookup"><span data-stu-id="05b20-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="05b20-132">Para executar o projeto, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="05b20-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="05b20-133">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05b20-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="05b20-134">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="05b20-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="05b20-135">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="05b20-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="05b20-136">No **modelos instalados** painel, escolha **Visual Basic**e, em seguida, escolha **aplicativo WPF** da lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="05b20-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="05b20-137">Digite `AsyncTracer` como o nome do projeto e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="05b20-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="05b20-138">O novo projeto aparece na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="05b20-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="05b20-139">No código de Editor do Visual Studio, escolha o **MainWindow** guia.</span><span class="sxs-lookup"><span data-stu-id="05b20-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="05b20-140">Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="05b20-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="05b20-141">No **XAML** exibir de MainWindow. XAML, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="05b20-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="05b20-142">Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** exibição de MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="05b20-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="05b20-143">Adicione uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="05b20-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="05b20-144">Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="05b20-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="05b20-145">Em MainWindow.xaml.vb, substitua o código com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="05b20-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="05b20-146">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="05b20-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="05b20-147">A saída a seguir deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="05b20-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="05b20-148">Rastrear o Programa</span><span class="sxs-lookup"><span data-stu-id="05b20-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="05b20-149">Etapas UM e DOIS</span><span class="sxs-lookup"><span data-stu-id="05b20-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="05b20-150">As duas primeiras exibir linhas rastrear o caminho como `startButton_Click` chamadas `AccessTheWebAsync`, e `AccessTheWebAsync` chama o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient> de assíncrono</span><span class="sxs-lookup"><span data-stu-id="05b20-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="05b20-151">A imagem a seguir descreve as chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="05b20-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="05b20-152">![As etapas um e dois](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="05b20-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="05b20-153">O tipo de retorno de ambos `AccessTheWebAsync` e `client.GetStringAsync` é <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="05b20-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="05b20-154">Para `AccessTheWebAsync`, TResult é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="05b20-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="05b20-155">Para `GetStringAsync`, TResult é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="05b20-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="05b20-156">Para obter mais informações sobre tipos de retorno de método assíncrono, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="05b20-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="05b20-157">Um método assíncrono de retorno de tarefas retorna uma instância de tarefa quando o controle passa para o chamador.</span><span class="sxs-lookup"><span data-stu-id="05b20-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="05b20-158">O controle retorna de um método assíncrono para seu chamador quando um `Await` operador é encontrado no método chamado ou quando termina o método chamado.</span><span class="sxs-lookup"><span data-stu-id="05b20-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="05b20-159">Exibir linhas que são rotulados como "Três"através de "seis" Esta parte do processo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="05b20-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="05b20-160">Etapa TRÊS</span><span class="sxs-lookup"><span data-stu-id="05b20-160">Step THREE</span></span>  
 <span data-ttu-id="05b20-161">Em `AccessTheWebAsync`, o método assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>é chamado para baixar o conteúdo de página da Web de destino.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="05b20-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="05b20-162">O controle retorna de `client.GetStringAsync` para `AccessTheWebAsync` quando `client.GetStringAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="05b20-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="05b20-163">O `client.GetStringAsync` método retorna uma tarefa de cadeia de caracteres que é atribuída para a `getStringTask` variável em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="05b20-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="05b20-164">A linha do programa de exemplo a seguir mostra a chamada para `client.GetStringAsync` e a atribuição.</span><span class="sxs-lookup"><span data-stu-id="05b20-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
<span data-ttu-id="05b20-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-166">Você pode imaginar a tarefa como uma promessa por `client.GetStringAsync` para produzir uma cadeia de caracteres real eventualmente.</span><span class="sxs-lookup"><span data-stu-id="05b20-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="05b20-167">Enquanto isso, se `AccessTheWebAsync` tem trabalho a fazer que não depende da cadeia de caracteres prometida de `client.GetStringAsync`, que o trabalho possa continuar enquanto `client.GetStringAsync` espera.</span><span class="sxs-lookup"><span data-stu-id="05b20-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="05b20-168">No exemplo, as seguintes linhas de saída, que são rotuladas "Três", representam a oportunidade de fazer o trabalho independente</span><span class="sxs-lookup"><span data-stu-id="05b20-168">In the example, the following lines of output, which are labeled "THREE,” represent the opportunity to do independent work</span></span>  
  
<span data-ttu-id="05b20-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-170">A instrução a seguir suspende o andamento em `AccessTheWebAsync` quando `getStringTask` é esperado.</span><span class="sxs-lookup"><span data-stu-id="05b20-170">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
<span data-ttu-id="05b20-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-172">A imagem a seguir mostra o fluxo de controle de `client.GetStringAsync` para a atribuição ao `getStringTask` e da criação de `getStringTask` para a aplicação de um operador de espera.</span><span class="sxs-lookup"><span data-stu-id="05b20-172">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="05b20-173">![Etapa três](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-três")</span><span class="sxs-lookup"><span data-stu-id="05b20-173">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="05b20-174">A expressão await suspende `AccessTheWebAsync` até `client.GetStringAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="05b20-174">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="05b20-175">Enquanto isso, o controle retorna para o chamador de `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="05b20-175">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b20-176">Normalmente, você aguarda a chamada para um método assíncrono imediatamente.</span><span class="sxs-lookup"><span data-stu-id="05b20-176">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="05b20-177">Por exemplo, a atribuição a seguir poderia substituir o código anterior que cria e, em seguida, aguarda `getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="05b20-177">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="05b20-178">Neste tópico, o operador de espera é aplicado posteriormente para acomodar as linhas de saída que marca o fluxo de controle por meio do programa.</span><span class="sxs-lookup"><span data-stu-id="05b20-178">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="05b20-179">Etapa QUATRO</span><span class="sxs-lookup"><span data-stu-id="05b20-179">Step FOUR</span></span>  
 <span data-ttu-id="05b20-180">O declarados retornam o tipo de `AccessTheWebAsync` é `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="05b20-180">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="05b20-181">Portanto, quando `AccessTheWebAsync` é suspenso, ele retorna uma tarefa de inteiro para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="05b20-181">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="05b20-182">Você deve compreender que a tarefa retornada não é `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="05b20-182">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="05b20-183">A tarefa retornada é uma nova tarefa de número inteiro que representa o que resta a ser feito no método suspenso, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="05b20-183">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="05b20-184">A tarefa é uma promessa de `AccessTheWebAsync` para produzir um número inteiro, quando a tarefa for concluída.</span><span class="sxs-lookup"><span data-stu-id="05b20-184">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="05b20-185">A instrução a seguir atribui essa tarefa para o `getLengthTask` variável.</span><span class="sxs-lookup"><span data-stu-id="05b20-185">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
<span data-ttu-id="05b20-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-187">Como em `AccessTheWebAsync`, `startButton_Click` pode continuar com o trabalho que não depende dos resultados da tarefa assíncrona (`getLengthTask`) até que a tarefa é esperada.</span><span class="sxs-lookup"><span data-stu-id="05b20-187">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="05b20-188">As seguintes linhas de saída representam esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="05b20-188">The following output lines represent that work.</span></span>  
  
<span data-ttu-id="05b20-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-190">Avançar na `startButton_Click` é suspensa quando `getLengthTask` é esperado.</span><span class="sxs-lookup"><span data-stu-id="05b20-190">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="05b20-191">A seguinte instrução de atribuição suspende `startButton_Click` até `AccessTheWebAsync` for concluída.</span><span class="sxs-lookup"><span data-stu-id="05b20-191">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
<span data-ttu-id="05b20-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-193">Na ilustração a seguir, as setas mostram o fluxo de controle da expressão await em `AccessTheWebAsync` para a atribuição de um valor para `getLengthTask`, seguido pelo processamento normal de `startButton_Click` até `getLengthTask` é esperado.</span><span class="sxs-lookup"><span data-stu-id="05b20-193">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="05b20-194">![Etapa quatro](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace quatro")</span><span class="sxs-lookup"><span data-stu-id="05b20-194">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="05b20-195">Etapa CINCO</span><span class="sxs-lookup"><span data-stu-id="05b20-195">Step FIVE</span></span>  
 <span data-ttu-id="05b20-196">Quando `client.GetStringAsync` sinaliza que está concluída, o processamento em `AccessTheWebAsync` é liberado da suspensão e pode continuar após a instrução de espera.</span><span class="sxs-lookup"><span data-stu-id="05b20-196">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="05b20-197">As seguintes linhas de saída representam a continuação do processamento.</span><span class="sxs-lookup"><span data-stu-id="05b20-197">The following lines of output represent the resumption of processing.</span></span>  
  
<span data-ttu-id="05b20-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-199">O operando da instrução return, `urlContents.Length`, é armazenado na tarefa que `AccessTheWebAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="05b20-199">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="05b20-200">A expressão await recupera o valor de `getLengthTask` em `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="05b20-200">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="05b20-201">A imagem a seguir mostra a transferência de controle após `client.GetStringAsync` (e `getStringTask`) forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="05b20-201">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="05b20-202">![Etapa cinco](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace cinco")</span><span class="sxs-lookup"><span data-stu-id="05b20-202">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="05b20-203">`AccessTheWebAsync`é executado para conclusão e o controle retorna ao `startButton_Click`, que está aguardando a conclusão.</span><span class="sxs-lookup"><span data-stu-id="05b20-203">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="05b20-204">Etapa SEIS</span><span class="sxs-lookup"><span data-stu-id="05b20-204">Step SIX</span></span>  
 <span data-ttu-id="05b20-205">Quando `AccessTheWebAsync` sinais for concluído, o processamento podem continuar após a instrução de espera em `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="05b20-205">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="05b20-206">Na verdade, o programa não tem mais nada para fazer.</span><span class="sxs-lookup"><span data-stu-id="05b20-206">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="05b20-207">As seguintes linhas de saída representam a continuação do processamento no `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="05b20-207">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
<span data-ttu-id="05b20-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-209">A expressão await recupera de `getLengthTask` o valor inteiro que é o operando da instrução return no `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="05b20-209">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="05b20-210">A instrução a seguir atribui o valor para o `contentLength` variável.</span><span class="sxs-lookup"><span data-stu-id="05b20-210">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
<span data-ttu-id="05b20-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="05b20-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="05b20-212">A imagem a seguir mostra o retorno do controle de `AccessTheWebAsync` para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="05b20-212">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="05b20-213">![Etapa seis](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace seis")</span><span class="sxs-lookup"><span data-stu-id="05b20-213">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b20-214">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05b20-214">See Also</span></span>  
 <span data-ttu-id="05b20-215">[Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="05b20-215">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="05b20-216"> [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="05b20-216"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="05b20-217"> [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="05b20-217"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="05b20-218"> [Exemplo de assincronia: Fluxo de controle em programas assíncronos (c# e Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span><span class="sxs-lookup"><span data-stu-id="05b20-218"> [Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span></span>
