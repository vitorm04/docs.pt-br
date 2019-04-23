---
title: Fluxo de controle em programas assíncronos (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: ed993943bcf7341f900c575744a1faa53a4a8a2e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300925"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="814e8-102">Fluxo de controle em programas assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814e8-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="814e8-103">Você pode escrever e manter programas assíncronos mais facilmente usando as palavras-chave `Async` e `Await`.</span><span class="sxs-lookup"><span data-stu-id="814e8-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="814e8-104">No entanto, os resultados podem surpreendê-lo se você não entender o funcionamento do seu programa.</span><span class="sxs-lookup"><span data-stu-id="814e8-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="814e8-105">Este tópico rastreia o fluxo de controle por meio de um programa assíncrono simples para mostrar quando o controle se move de um método para o outro e quais informações são transferidas a cada vez.</span><span class="sxs-lookup"><span data-stu-id="814e8-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="814e8-106">As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="814e8-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="814e8-107">Em geral, você marca métodos que contêm código assíncrono com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="814e8-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="814e8-108">Em um método marcado com um modificador assíncrono, você pode usar um [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operador para especificar onde o método pausa para aguardar um processo assíncrono chamado concluir.</span><span class="sxs-lookup"><span data-stu-id="814e8-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="814e8-109">Para obter mais informações, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="814e8-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="814e8-110">O exemplo a seguir usa os métodos assíncronos para baixar o conteúdo de um site especificado como uma cadeia de caracteres e exibir o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="814e8-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="814e8-111">O exemplo contém os dois métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="814e8-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="814e8-112">`startButton_Click`, que chama `AccessTheWebAsync` e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="814e8-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="814e8-113">`AccessTheWebAsync`, que baixa o conteúdo de um site na forma de uma cadeia de caracteres e retorna o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="814e8-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="814e8-114">`AccessTheWebAsync` usa um método <xref:System.Net.Http.HttpClient> assíncrono, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, para baixar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="814e8-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="814e8-115">Linhas numeradas de exibição aparecem em pontos estratégicos em todo o programa para ajudá-lo a entender como o programa é executado e explicar o que acontece em cada ponto marcado.</span><span class="sxs-lookup"><span data-stu-id="814e8-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="814e8-116">As linhas de exibição são rotuladas como "UM"a "SEIS".</span><span class="sxs-lookup"><span data-stu-id="814e8-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="814e8-117">Os rótulos representam a ordem na qual o programa alcança essas linhas de código.</span><span class="sxs-lookup"><span data-stu-id="814e8-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="814e8-118">O código a seguir mostra uma estrutura de tópicos do programa.</span><span class="sxs-lookup"><span data-stu-id="814e8-118">The following code shows an outline of the program.</span></span>  
  
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
            client.GetStringAsync("https://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="814e8-119">Cada um dos locais rotulados, "UM"a "SEIS," exibe informações sobre o estado atual do programa.</span><span class="sxs-lookup"><span data-stu-id="814e8-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="814e8-120">A saída a seguir será produzida.</span><span class="sxs-lookup"><span data-stu-id="814e8-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="814e8-121">Configurar o Programa</span><span class="sxs-lookup"><span data-stu-id="814e8-121">Set Up the Program</span></span>  
 <span data-ttu-id="814e8-122">Você pode baixar o código usado nesse tópico no MSDN ou você mesmo pode criá-lo.</span><span class="sxs-lookup"><span data-stu-id="814e8-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="814e8-123">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="814e8-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="814e8-124">Baixar o Programa</span><span class="sxs-lookup"><span data-stu-id="814e8-124">Download the Program</span></span>  
 <span data-ttu-id="814e8-125">Você pode baixar o aplicativo para este tópico em [exemplo assíncrono: Controlar fluxo em programas assíncronos](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="814e8-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="814e8-126">As etapas a seguir abrem e executam o programa.</span><span class="sxs-lookup"><span data-stu-id="814e8-126">The following steps open and run the program.</span></span>  
  
1. <span data-ttu-id="814e8-127">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="814e8-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="814e8-128">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="814e8-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="814e8-129">Navegue até a pasta que contém o código de exemplo descompactado, abra o arquivo da solução (.sln) e, em seguida, escolha a tecla F5 para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="814e8-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="814e8-130">Compilar o Programa Sozinho</span><span class="sxs-lookup"><span data-stu-id="814e8-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="814e8-131">O projeto WPF (Windows Presentation Foundation) a seguir contém o exemplo de código deste tópico.</span><span class="sxs-lookup"><span data-stu-id="814e8-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="814e8-132">Para executar o projeto, realize as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="814e8-132">To run the project, perform the following steps:</span></span>  
  
1. <span data-ttu-id="814e8-133">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="814e8-133">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="814e8-134">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="814e8-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="814e8-135">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="814e8-135">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="814e8-136">No **modelos instalados** painel, escolha **Visual Basic**e, em seguida, escolha **aplicativo WPF** na lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="814e8-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="814e8-137">Digite `AsyncTracer` como o nome do projeto e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="814e8-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="814e8-138">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="814e8-138">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="814e8-139">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="814e8-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="814e8-140">Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="814e8-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6. <span data-ttu-id="814e8-141">Na exibição **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="814e8-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="814e8-142">Uma janela simples, contendo uma caixa de texto e um botão, aparecerá no modo de exibição de **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="814e8-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7. <span data-ttu-id="814e8-143">Adicione uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="814e8-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8. <span data-ttu-id="814e8-144">Na **Gerenciador de soluções**, abra o menu de atalho para XAML. vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="814e8-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="814e8-145">No XAML. vb, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="814e8-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
  
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
  
10. <span data-ttu-id="814e8-146">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="814e8-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="814e8-147">A saída a seguir deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="814e8-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="814e8-148">Rastrear o Programa</span><span class="sxs-lookup"><span data-stu-id="814e8-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="814e8-149">Etapas UM e DOIS</span><span class="sxs-lookup"><span data-stu-id="814e8-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="814e8-150">As duas primeiras linhas de exibição rastreiam o caminho conforme `startButton_Click` chama `AccessTheWebAsync` e `AccessTheWebAsync` chama o método <xref:System.Net.Http.HttpClient> assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="814e8-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="814e8-151">A imagem a seguir delineia as chamadas de método a método.</span><span class="sxs-lookup"><span data-stu-id="814e8-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="814e8-152">![Etapas UM e DOIS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="814e8-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="814e8-153">O tipo de retorno de ambos `AccessTheWebAsync` e `client.GetStringAsync` é <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="814e8-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="814e8-154">Para `AccessTheWebAsync`, TResult é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="814e8-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="814e8-155">Para `GetStringAsync`, TResult é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="814e8-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="814e8-156">Para obter mais informações sobre tipos de retorno de método assíncrono, consulte [tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="814e8-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="814e8-157">Um método assíncrono de retorno de tarefas retorna uma instância de tarefa, quando o controle volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="814e8-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="814e8-158">O controle retorna de um método assíncrono para seu chamador quando um operador `Await` é encontrado no método chamado ou quando o método chamado termina.</span><span class="sxs-lookup"><span data-stu-id="814e8-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="814e8-159">As linhas de exibição rotuladas como "TRÊS"até "SEIS" rastreiam essa parte do processo.</span><span class="sxs-lookup"><span data-stu-id="814e8-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="814e8-160">Etapa TRÊS</span><span class="sxs-lookup"><span data-stu-id="814e8-160">Step THREE</span></span>  
 <span data-ttu-id="814e8-161">Em `AccessTheWebAsync`, o método assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> é chamado para baixar o conteúdo de página da Web de destino.</span><span class="sxs-lookup"><span data-stu-id="814e8-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="814e8-162">O controle retorna de `client.GetStringAsync` para `AccessTheWebAsync` quando `client.GetStringAsync` retornar.</span><span class="sxs-lookup"><span data-stu-id="814e8-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="814e8-163">O método `client.GetStringAsync` retorna uma tarefa de cadeia de caracteres que é atribuída à variável `getStringTask` em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="814e8-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="814e8-164">A linha do programa de exemplo a seguir mostra a chamada à `client.GetStringAsync` e a atribuição.</span><span class="sxs-lookup"><span data-stu-id="814e8-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 <span data-ttu-id="814e8-165">Você pode imaginar a tarefa como uma promessa de `client.GetStringAsync` para eventualmente produzir uma cadeia de caracteres real.</span><span class="sxs-lookup"><span data-stu-id="814e8-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="814e8-166">Enquanto isso, se `AccessTheWebAsync` tiver trabalho a fazer, que não dependa da cadeia de caracteres prometida de `client.GetStringAsync`, o trabalho poderá continuar enquanto `client.GetStringAsync` aguarda.</span><span class="sxs-lookup"><span data-stu-id="814e8-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="814e8-167">No exemplo, as linhas de saída seguintes, que são rotuladas como "TRÊS", representam a oportunidade para fazer o trabalho independente</span><span class="sxs-lookup"><span data-stu-id="814e8-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="814e8-168">A instrução a seguir suspende o andamento em `AccessTheWebAsync` quando `getStringTask` é aguardado.</span><span class="sxs-lookup"><span data-stu-id="814e8-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 <span data-ttu-id="814e8-169">A imagem a seguir mostra o fluxo de controle de `client.GetStringAsync` para a atribuição ao `getStringTask` e da criação de `getStringTask` para o aplicativo de um operador Await.</span><span class="sxs-lookup"><span data-stu-id="814e8-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="814e8-170">![Etapa TRÊS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="814e8-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="814e8-171">A expressão await suspende `AccessTheWebAsync` até que `client.GetStringAsync` retorne.</span><span class="sxs-lookup"><span data-stu-id="814e8-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="814e8-172">Enquanto isso, o controle retorna para o chamador de `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="814e8-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="814e8-173">Normalmente, você aguarda a chamada a um método assíncrono imediatamente.</span><span class="sxs-lookup"><span data-stu-id="814e8-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="814e8-174">Por exemplo, a atribuição a seguir poderia substituir o código anterior que cria e, em seguida, aguarda `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="814e8-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="814e8-175">Neste tópico, o operador await é aplicado posteriormente para acomodar as linhas de saída que marcam o fluxo de controle em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="814e8-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="814e8-176">Etapa QUATRO</span><span class="sxs-lookup"><span data-stu-id="814e8-176">Step FOUR</span></span>  
 <span data-ttu-id="814e8-177">O tipo de retorno declarado de `AccessTheWebAsync` é `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="814e8-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="814e8-178">Portanto, quando `AccessTheWebAsync` for suspenso, ele retornará uma tarefa de inteiro para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="814e8-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="814e8-179">Você deve compreender que a tarefa retornada não é `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="814e8-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="814e8-180">A tarefa retornada é uma nova tarefa de um inteiro que representa o que ainda precisa ser feito no método suspenso `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="814e8-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="814e8-181">A tarefa é uma promessa de `AccessTheWebAsync` para produzir um inteiro quando a tarefa for concluída.</span><span class="sxs-lookup"><span data-stu-id="814e8-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="814e8-182">A instrução a seguir atribui essa tarefa à variável `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="814e8-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 <span data-ttu-id="814e8-183">Como em `AccessTheWebAsync`, `startButton_Click` pode continuar com o trabalho que não dependa dos resultados da tarefa assíncrona (`getLengthTask`) até que a tarefa seja aguardada.</span><span class="sxs-lookup"><span data-stu-id="814e8-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="814e8-184">As seguintes linhas de saída representam esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="814e8-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="814e8-185">O avanço em `startButton_Click` será suspenso quando `getLengthTask` for aguardada.</span><span class="sxs-lookup"><span data-stu-id="814e8-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="814e8-186">A seguinte instrução de atribuição suspende `startButton_Click` até que `AccessTheWebAsync` seja concluída.</span><span class="sxs-lookup"><span data-stu-id="814e8-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="814e8-187">Na ilustração a seguir, as setas mostram o fluxo de controle da expressão await em `AccessTheWebAsync` para a atribuição de um valor para `getLengthTask`, seguido pelo processamento normal de `startButton_Click` até que `getLengthTask` seja aguardada.</span><span class="sxs-lookup"><span data-stu-id="814e8-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="814e8-188">![Etapa QUATRO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="814e8-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="814e8-189">Etapa CINCO</span><span class="sxs-lookup"><span data-stu-id="814e8-189">Step FIVE</span></span>  
 <span data-ttu-id="814e8-190">Quando `client.GetStringAsync` sinaliza que está concluído, o processamento em `AccessTheWebAsync` é liberado da suspensão e pode continuar após a instrução await.</span><span class="sxs-lookup"><span data-stu-id="814e8-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="814e8-191">As seguintes linhas de saída representam a retomada do processamento.</span><span class="sxs-lookup"><span data-stu-id="814e8-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="814e8-192">O operando da instrução return, `urlContents.Length`, é armazenado na tarefa que `AccessTheWebAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="814e8-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="814e8-193">A expressão await recupera esse valor de `getLengthTask` em `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="814e8-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="814e8-194">A imagem a seguir mostra a transferência de controle após `client.GetStringAsync` (e `getStringTask`) estarem concluídas.</span><span class="sxs-lookup"><span data-stu-id="814e8-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="814e8-195">![Etapa CINCO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="814e8-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="814e8-196">`AccessTheWebAsync` é executado até a conclusão e o controle retorna ao `startButton_Click`, que está aguardando a conclusão.</span><span class="sxs-lookup"><span data-stu-id="814e8-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="814e8-197">Etapa SEIS</span><span class="sxs-lookup"><span data-stu-id="814e8-197">Step SIX</span></span>  
 <span data-ttu-id="814e8-198">Quando `AccessTheWebAsync` sinaliza que está concluído, o processamento pode continuar após a instrução await em `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="814e8-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="814e8-199">Na verdade, o programa não tem mais nada para fazer.</span><span class="sxs-lookup"><span data-stu-id="814e8-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="814e8-200">As seguintes linhas de saída representam a retomada do processamento em `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="814e8-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="814e8-201">A expressão await recupera de `getLengthTask` o valor inteiro, que é o operando da instrução return em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="814e8-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="814e8-202">A instrução a seguir atribui esse valor à variável `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="814e8-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="814e8-203">A imagem a seguir mostra o retorno do controle de `AccessTheWebAsync` para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="814e8-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="814e8-204">![Etapa SEIS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="814e8-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814e8-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="814e8-205">See also</span></span>

- [<span data-ttu-id="814e8-206">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814e8-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="814e8-207">Tipos de retorno assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814e8-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="814e8-208">Passo a passo: Acessando a Web usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814e8-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="814e8-209">Exemplo de Async: Controlar fluxo em programas assíncronos (C# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="814e8-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
