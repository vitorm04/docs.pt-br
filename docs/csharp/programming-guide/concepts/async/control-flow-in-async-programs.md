---
title: Fluxo de controle em programas assíncronos (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 6a7b8f3f41b2096e3e7524d03217bdc123f26f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326197"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="93a29-102">Fluxo de controle em programas assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="93a29-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="93a29-103">Você pode escrever e manter programas assíncronos mais facilmente usando as palavras-chave `async` e `await`.</span><span class="sxs-lookup"><span data-stu-id="93a29-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="93a29-104">No entanto, os resultados podem surpreendê-lo se você não entender o funcionamento do seu programa.</span><span class="sxs-lookup"><span data-stu-id="93a29-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="93a29-105">Este tópico rastreia o fluxo de controle por meio de um programa assíncrono simples para mostrar quando o controle se move de um método para o outro e quais informações são transferidas a cada vez.</span><span class="sxs-lookup"><span data-stu-id="93a29-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="93a29-106">Em geral, você marca os métodos que contêm código assíncrono com o modificador [async (C#)](../../../../csharp/language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="93a29-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="93a29-107">Em um método marcado com um modificador assíncrono, você pode usar um operador [await (C#)](../../../../csharp/language-reference/keywords/await.md) para especificar o local em que o método faz uma pausa para esperar pela conclusão de um processo assíncrono que foi chamado.</span><span class="sxs-lookup"><span data-stu-id="93a29-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="93a29-108">Para obter mais informações, consulte [Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="93a29-108">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="93a29-109">O exemplo a seguir usa os métodos assíncronos para baixar o conteúdo de um site especificado como uma cadeia de caracteres e exibir o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="93a29-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="93a29-110">O exemplo contém os dois métodos a seguir.</span><span class="sxs-lookup"><span data-stu-id="93a29-110">The example contains the following two methods.</span></span>

-   `startButton_Click`<span data-ttu-id="93a29-111">, que chama `AccessTheWebAsync` e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="93a29-111">, which calls `AccessTheWebAsync` and displays the result.</span></span>

-   `AccessTheWebAsync`<span data-ttu-id="93a29-112">, que baixa o conteúdo de um site na forma de uma cadeia de caracteres e retorna o comprimento da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="93a29-112">, which downloads the contents of a website as a string and returns the length of the string.</span></span> `AccessTheWebAsync` <span data-ttu-id="93a29-113">usa um método <xref:System.Net.Http.HttpClient> assíncrono, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, para baixar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="93a29-113">uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="93a29-114">Linhas numeradas de exibição aparecem em pontos estratégicos em todo o programa para ajudá-lo a entender como o programa é executado e explicar o que acontece em cada ponto marcado.</span><span class="sxs-lookup"><span data-stu-id="93a29-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="93a29-115">As linhas de exibição são rotuladas como "UM"a "SEIS".</span><span class="sxs-lookup"><span data-stu-id="93a29-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="93a29-116">Os rótulos representam a ordem na qual o programa alcança essas linhas de código.</span><span class="sxs-lookup"><span data-stu-id="93a29-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="93a29-117">O código a seguir mostra uma estrutura de tópicos do programa.</span><span class="sxs-lookup"><span data-stu-id="93a29-117">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="93a29-118">Cada um dos locais rotulados, "UM"a "SEIS," exibe informações sobre o estado atual do programa.</span><span class="sxs-lookup"><span data-stu-id="93a29-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="93a29-119">A saída a seguir será produzida:</span><span class="sxs-lookup"><span data-stu-id="93a29-119">The following output is produced:</span></span>

```text
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

## <a name="set-up-the-program"></a><span data-ttu-id="93a29-120">Configurar o programa</span><span class="sxs-lookup"><span data-stu-id="93a29-120">Set up the program</span></span>

<span data-ttu-id="93a29-121">Você pode baixar o código usado nesse tópico no MSDN ou você mesmo pode criá-lo.</span><span class="sxs-lookup"><span data-stu-id="93a29-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="93a29-122">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="93a29-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="93a29-123">Baixar o programa</span><span class="sxs-lookup"><span data-stu-id="93a29-123">Download the program</span></span>

<span data-ttu-id="93a29-124">Você pode baixar o aplicativo para este tópico em [Amostra assíncrona: Fluxo de controle em programas assíncronos](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="93a29-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="93a29-125">As etapas a seguir abrem e executam o programa.</span><span class="sxs-lookup"><span data-stu-id="93a29-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="93a29-126">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93a29-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="93a29-127">Na barra de menus, escolha **Arquivo** > **Abrir** > **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="93a29-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="93a29-128">Navegue até a pasta que contém o código de exemplo descompactado, abra o arquivo da solução (.sln) e, em seguida, escolha a tecla **F5** para compilar e executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="93a29-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="93a29-129">Crie o programa sozinho</span><span class="sxs-lookup"><span data-stu-id="93a29-129">Create the program Yourself</span></span>

<span data-ttu-id="93a29-130">O projeto WPF (Windows Presentation Foundation) a seguir contém o exemplo de código deste tópico.</span><span class="sxs-lookup"><span data-stu-id="93a29-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="93a29-131">Para executar o projeto, realize as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="93a29-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="93a29-132">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93a29-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="93a29-133">Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="93a29-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="93a29-134">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="93a29-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="93a29-135">Escolha a categoria **Instalado** > **Visual C#** > **Área de Trabalho do Windows** e, em seguida, escolha **Aplicativo WPF** na lista de modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="93a29-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="93a29-136">Digite `AsyncTracer` como o nome do projeto e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="93a29-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="93a29-137">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="93a29-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="93a29-138">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="93a29-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="93a29-139">Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="93a29-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="93a29-140">Na exibição **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="93a29-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="93a29-141">Uma janela simples, contendo uma caixa de texto e um botão, aparecerá no modo de exibição de **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="93a29-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="93a29-142">Adicione uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="93a29-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="93a29-143">No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="93a29-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="93a29-144">Em MainWindow.xaml.cs, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="93a29-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="93a29-145">Escolha a tecla **F5** para executar o programa e, em seguida, o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="93a29-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="93a29-146">A saída a seguir é exibida:</span><span class="sxs-lookup"><span data-stu-id="93a29-146">The following output appears:</span></span>

    ```text
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

## <a name="trace-the-program"></a><span data-ttu-id="93a29-147">Rastrear o programa</span><span class="sxs-lookup"><span data-stu-id="93a29-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="93a29-148">Etapas UM e DOIS</span><span class="sxs-lookup"><span data-stu-id="93a29-148">Steps ONE and TWO</span></span>

<span data-ttu-id="93a29-149">As duas primeiras linhas de exibição rastreiam o caminho conforme `startButton_Click` chama `AccessTheWebAsync` e `AccessTheWebAsync` chama o método <xref:System.Net.Http.HttpClient> assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="93a29-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="93a29-150">A imagem a seguir delineia as chamadas de método a método.</span><span class="sxs-lookup"><span data-stu-id="93a29-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="93a29-151">![Etapas UM e DOIS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="93a29-151">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="93a29-152">O tipo de retorno de ambos `AccessTheWebAsync` e `client.GetStringAsync` é <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="93a29-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="93a29-153">Para `AccessTheWebAsync`, TResult é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="93a29-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="93a29-154">Para `GetStringAsync`, TResult é uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="93a29-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="93a29-155">Para obter mais informações sobre tipos de retorno de método assíncrono, consulte [Tipos de retorno assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="93a29-155">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="93a29-156">Um método assíncrono de retorno de tarefas retorna uma instância de tarefa, quando o controle volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="93a29-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="93a29-157">O controle retorna de um método assíncrono para seu chamador quando um operador `await` é encontrado no método chamado ou quando o método chamado termina.</span><span class="sxs-lookup"><span data-stu-id="93a29-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="93a29-158">As linhas de exibição rotuladas como "TRÊS"até "SEIS" rastreiam essa parte do processo.</span><span class="sxs-lookup"><span data-stu-id="93a29-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="93a29-159">Etapa TRÊS</span><span class="sxs-lookup"><span data-stu-id="93a29-159">Step THREE</span></span>

<span data-ttu-id="93a29-160">Em `AccessTheWebAsync`, o método assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> é chamado para baixar o conteúdo de página da Web de destino.</span><span class="sxs-lookup"><span data-stu-id="93a29-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="93a29-161">O controle retorna de `client.GetStringAsync` para `AccessTheWebAsync` quando `client.GetStringAsync` retornar.</span><span class="sxs-lookup"><span data-stu-id="93a29-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="93a29-162">O método `client.GetStringAsync` retorna uma tarefa de cadeia de caracteres que é atribuída à variável `getStringTask` em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="93a29-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="93a29-163">A linha do programa de exemplo a seguir mostra a chamada à `client.GetStringAsync` e a atribuição.</span><span class="sxs-lookup"><span data-stu-id="93a29-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="93a29-164">Você pode imaginar a tarefa como uma promessa de `client.GetStringAsync` para eventualmente produzir uma cadeia de caracteres real.</span><span class="sxs-lookup"><span data-stu-id="93a29-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="93a29-165">Enquanto isso, se `AccessTheWebAsync` tiver trabalho a fazer, que não dependa da cadeia de caracteres prometida de `client.GetStringAsync`, o trabalho poderá continuar enquanto `client.GetStringAsync` aguarda.</span><span class="sxs-lookup"><span data-stu-id="93a29-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="93a29-166">No exemplo, as linhas de saída seguintes, que são rotuladas como "TRÊS", representam a oportunidade para fazer o trabalho independente</span><span class="sxs-lookup"><span data-stu-id="93a29-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="93a29-167">A instrução a seguir suspende o andamento em `AccessTheWebAsync` quando `getStringTask` é aguardado.</span><span class="sxs-lookup"><span data-stu-id="93a29-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="93a29-168">A imagem a seguir mostra o fluxo de controle de `client.GetStringAsync` para a atribuição ao `getStringTask` e da criação de `getStringTask` para a aplicação de um operador de espera.</span><span class="sxs-lookup"><span data-stu-id="93a29-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="93a29-169">![Etapa TRÊS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="93a29-169">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="93a29-170">A expressão await suspende `AccessTheWebAsync` até que `client.GetStringAsync` retorne.</span><span class="sxs-lookup"><span data-stu-id="93a29-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="93a29-171">Enquanto isso, o controle retorna para o chamador de `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="93a29-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="93a29-172">Normalmente, você aguarda a chamada a um método assíncrono imediatamente.</span><span class="sxs-lookup"><span data-stu-id="93a29-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="93a29-173">Por exemplo, a atribuição a seguir poderia substituir o código anterior que cria e, em seguida, aguarda `getStringTask`:</span><span class="sxs-lookup"><span data-stu-id="93a29-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`:</span></span> `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> <span data-ttu-id="93a29-174">Neste tópico, o operador await é aplicado posteriormente para acomodar as linhas de saída que marcam o fluxo de controle em todo o programa.</span><span class="sxs-lookup"><span data-stu-id="93a29-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="93a29-175">Etapa QUATRO</span><span class="sxs-lookup"><span data-stu-id="93a29-175">Step FOUR</span></span>

<span data-ttu-id="93a29-176">O tipo de retorno declarado de `AccessTheWebAsync` é `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="93a29-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="93a29-177">Portanto, quando `AccessTheWebAsync` for suspenso, ele retornará uma tarefa de inteiro para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="93a29-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="93a29-178">Você deve compreender que a tarefa retornada não é `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="93a29-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="93a29-179">A tarefa retornada é uma nova tarefa de um inteiro que representa o que ainda precisa ser feito no método suspenso `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="93a29-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="93a29-180">A tarefa é uma promessa de `AccessTheWebAsync` para produzir um inteiro quando a tarefa for concluída.</span><span class="sxs-lookup"><span data-stu-id="93a29-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="93a29-181">A instrução a seguir atribui essa tarefa à variável `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="93a29-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="93a29-182">Como em `AccessTheWebAsync`, `startButton_Click` pode continuar com o trabalho que não dependa dos resultados da tarefa assíncrona (`getLengthTask`) até que a tarefa seja aguardada.</span><span class="sxs-lookup"><span data-stu-id="93a29-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="93a29-183">As seguintes linhas de saída representam esse trabalho.</span><span class="sxs-lookup"><span data-stu-id="93a29-183">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="93a29-184">O avanço em `startButton_Click` será suspenso quando `getLengthTask` for aguardada.</span><span class="sxs-lookup"><span data-stu-id="93a29-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="93a29-185">A seguinte instrução de atribuição suspende `startButton_Click` até que `AccessTheWebAsync` seja concluída.</span><span class="sxs-lookup"><span data-stu-id="93a29-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="93a29-186">Na ilustração a seguir, as setas mostram o fluxo de controle da expressão await em `AccessTheWebAsync` para a atribuição de um valor para `getLengthTask`, seguido pelo processamento normal de `startButton_Click` até que `getLengthTask` seja aguardada.</span><span class="sxs-lookup"><span data-stu-id="93a29-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="93a29-187">![Etapa QUATRO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="93a29-187">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="93a29-188">Etapa CINCO</span><span class="sxs-lookup"><span data-stu-id="93a29-188">Step FIVE</span></span>

<span data-ttu-id="93a29-189">Quando `client.GetStringAsync` sinaliza que está concluído, o processamento em `AccessTheWebAsync` é liberado da suspensão e pode continuar após a instrução await.</span><span class="sxs-lookup"><span data-stu-id="93a29-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="93a29-190">As seguintes linhas de saída representam a retomada do processamento.</span><span class="sxs-lookup"><span data-stu-id="93a29-190">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="93a29-191">O operando da instrução return, `urlContents.Length`, é armazenado na tarefa que `AccessTheWebAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="93a29-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="93a29-192">A expressão await recupera esse valor de `getLengthTask` em `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="93a29-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="93a29-193">A imagem a seguir mostra a transferência de controle após `client.GetStringAsync` (e `getStringTask`) estarem concluídas.</span><span class="sxs-lookup"><span data-stu-id="93a29-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="93a29-194">![Etapa CINCO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="93a29-194">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 `AccessTheWebAsync` <span data-ttu-id="93a29-195">é executado até a conclusão e o controle retorna ao `startButton_Click`, que está aguardando a conclusão.</span><span class="sxs-lookup"><span data-stu-id="93a29-195">runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="93a29-196">Etapa SEIS</span><span class="sxs-lookup"><span data-stu-id="93a29-196">Step SIX</span></span>

<span data-ttu-id="93a29-197">Quando `AccessTheWebAsync` sinaliza que está concluído, o processamento pode continuar após a instrução await em `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="93a29-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="93a29-198">Na verdade, o programa não tem mais nada para fazer.</span><span class="sxs-lookup"><span data-stu-id="93a29-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="93a29-199">As seguintes linhas de saída representam a retomada do processamento em `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="93a29-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="93a29-200">A expressão await recupera de `getLengthTask` o valor inteiro, que é o operando da instrução return em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="93a29-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="93a29-201">A instrução a seguir atribui esse valor à variável `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="93a29-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="93a29-202">A imagem a seguir mostra o retorno do controle de `AccessTheWebAsync` para `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="93a29-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="93a29-203">![Etapa SEIS](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="93a29-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="93a29-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93a29-204">See also</span></span>

- [<span data-ttu-id="93a29-205">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="93a29-205">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="93a29-206">Tipos de retorno assíncronos (C#)</span><span class="sxs-lookup"><span data-stu-id="93a29-206">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="93a29-207">Passo a passo: Acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="93a29-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="93a29-208">Amostra assíncrona: Fluxo de controle em programas assíncronos (C# e Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93a29-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
