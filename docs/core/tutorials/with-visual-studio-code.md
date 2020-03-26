---
title: Introdução ao C# e ao Visual Studio Code
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.date: 12/05/2018
ms.openlocfilehash: 49a1271f2bf74224e189e70bebf0d22c49408e5d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111056"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="194c2-103">Introdução ao C# e ao Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="194c2-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="194c2-104">O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="194c2-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="194c2-105">Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.</span><span class="sxs-lookup"><span data-stu-id="194c2-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="194c2-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="194c2-106">Prerequisites</span></span>

1. <span data-ttu-id="194c2-107">Instale [o Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="194c2-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="194c2-108">Instale o [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="194c2-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="194c2-109">Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="194c2-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="194c2-110">Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="194c2-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="194c2-111">Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="194c2-111">Hello World</span></span>

<span data-ttu-id="194c2-112">Vamos começar com um simples programa "Olá, Mundo" no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="194c2-112">Let's get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="194c2-113">Abra um projeto:</span><span class="sxs-lookup"><span data-stu-id="194c2-113">Open a project:</span></span>

    - <span data-ttu-id="194c2-114">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="194c2-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="194c2-115">Clique no ícone do Explorer no menu à esquerda e, em seguida, clique em **Abrir Pasta**.</span><span class="sxs-lookup"><span data-stu-id="194c2-115">Click on the Explorer icon on the left menu and then click **Open Folder**.</span></span>
    - <span data-ttu-id="194c2-116">Selecione >  **''Abrir'pasta**de**arquivos'** no menu principal para abrir a pasta que deseja que seu projeto C# esteja dentro e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="194c2-116">Select **File** > **Open Folder** from the main menu to open the folder you want your C# project to be in and click **Select Folder**.</span></span> <span data-ttu-id="194c2-117">Para nosso exemplo, estamos criando uma pasta para nosso projeto chamado *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="194c2-117">For our example, we're creating a folder for our project named *HelloWorld*.</span></span>

      ![Pasta aberta do Visual Studio Code](media/with-visual-studio-code/vs-code-open-folder.png)

2. <span data-ttu-id="194c2-119">Inicialize um projeto em C#:</span><span class="sxs-lookup"><span data-stu-id="194c2-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="194c2-120">Abra o Terminal Integrado do Visual Studio Code selecionando **Exibir** > **Terminal Integrado** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="194c2-120">Open the Integrated Terminal from Visual Studio Code by selecting **View** > **Integrated Terminal** from the main menu.</span></span>
    - <span data-ttu-id="194c2-121">Na janela do terminal, digite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="194c2-121">In the terminal window, type `dotnet new console`.</span></span>
    - <span data-ttu-id="194c2-122">Este comando cria um arquivo *Program.cs* em sua pasta com um simples programa "Hello World" já escrito, juntamente com um arquivo de projeto C# chamado *HelloWorld.csproj*.</span><span class="sxs-lookup"><span data-stu-id="194c2-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![O novo comando dotnet](media/with-visual-studio-code/dotnet-new-command.png)

3. <span data-ttu-id="194c2-124">Resolva os ativos do build:</span><span class="sxs-lookup"><span data-stu-id="194c2-124">Resolve the build assets:</span></span>

    - <span data-ttu-id="194c2-125">Para o **.NET Core 1.x**, digite `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="194c2-125">For **.NET Core 1.x**, type `dotnet restore`.</span></span> <span data-ttu-id="194c2-126">Executar `dotnet restore` fornece acesso a pacotes .NET Core que são necessários para compilar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="194c2-126">Running `dotnet restore` gives you access to the  required .NET Core packages that are needed to build your project.</span></span>

      ![O comando de restauração dotnet](media/with-visual-studio-code/dotnet-restore-command.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. <span data-ttu-id="194c2-128">Execute o programa "Olá, Mundo":</span><span class="sxs-lookup"><span data-stu-id="194c2-128">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="194c2-129">Digite `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="194c2-129">Type `dotnet run`.</span></span>

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

<span data-ttu-id="194c2-131">Você também pode assistir a um tutorial breve em vídeo para obter ajuda na instalação em [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) ou [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="194c2-131">You can also watch a short video tutorial for further setup help on [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), or [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

## <a name="debug"></a><span data-ttu-id="194c2-132">Depurar</span><span class="sxs-lookup"><span data-stu-id="194c2-132">Debug</span></span>

1. <span data-ttu-id="194c2-133">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="194c2-133">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="194c2-134">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="194c2-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

2. <span data-ttu-id="194c2-136">O Visual Studio Code deverá solicitar que você adicione os ativos ausentes para compilar e depurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="194c2-136">Visual Studio Code should prompt you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="194c2-137">Selecione **Sim**.</span><span class="sxs-lookup"><span data-stu-id="194c2-137">Select **Yes**.</span></span>

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

3. <span data-ttu-id="194c2-139">Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="194c2-139">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Abrir a guia Depurar no Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

4. <span data-ttu-id="194c2-141">Localize a seta verde na parte superior do painel.</span><span class="sxs-lookup"><span data-stu-id="194c2-141">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="194c2-142">Certifique-se de que a queda ao lado dele tenha **o .NET Core Launch (console)** selecionado.</span><span class="sxs-lookup"><span data-stu-id="194c2-142">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Selecionando o .NET Core no Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

5. <span data-ttu-id="194c2-144">Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="194c2-144">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/set-breakpoint-vs-code.png)

6. <span data-ttu-id="194c2-146">Para iniciar a depuração, pressione <kbd>F5</kbd> ou selecione a seta verde.</span><span class="sxs-lookup"><span data-stu-id="194c2-146">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="194c2-147">O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="194c2-147">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="194c2-148">Durante a depuração, você pode visualizar suas variáveis locais no painel superior esquerdo ou usar o console de depuração.</span><span class="sxs-lookup"><span data-stu-id="194c2-148">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

7. <span data-ttu-id="194c2-149">Selecione a seta azul na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interromper o processamento.</span><span class="sxs-lookup"><span data-stu-id="194c2-149">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Execução e depuração no Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="194c2-151">Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="194c2-151">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="194c2-152">Adicionar uma classe</span><span class="sxs-lookup"><span data-stu-id="194c2-152">Add a class</span></span>

1. <span data-ttu-id="194c2-153">Para adicionar uma nova classe, clique com o botão direito do mouse no VSCode Explorer e selecione **Novo Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="194c2-153">To add a new class, right-click in the VSCode Explorer and select **New File**.</span></span> <span data-ttu-id="194c2-154">Isso adiciona um novo arquivo à pasta que você abriu no VSCode.</span><span class="sxs-lookup"><span data-stu-id="194c2-154">This adds a new file to the folder you have open in VSCode.</span></span>
2. <span data-ttu-id="194c2-155">Nomeie seu arquivo *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="194c2-155">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="194c2-156">Salve-o com uma extensão `.cs` no final para que ele seja reconhecido como um arquivo csharp.</span><span class="sxs-lookup"><span data-stu-id="194c2-156">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
3. <span data-ttu-id="194c2-157">Adicione o código a seguir para criar sua primeira classe.</span><span class="sxs-lookup"><span data-stu-id="194c2-157">Add the code below to create your first class.</span></span> <span data-ttu-id="194c2-158">Certifique-se de incluir o namespace correto para que você possa referencia-lo a partir de seu arquivo *Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="194c2-158">Make sure to include the correct namespace so you can reference it from your *Program.cs* file:</span></span>

    ``` csharp
    using System;

    namespace HelloWorld
    {
        public class MyClass
        {
            public string ReturnMessage()
            {
                return "Happy coding!";
            }
        }
    }
    ```

4. <span data-ttu-id="194c2-159">Ligue para sua nova classe a partir do seu método principal em *Program.cs* adicionando o código abaixo:</span><span class="sxs-lookup"><span data-stu-id="194c2-159">Call your new class from your main method in *Program.cs* by adding the code below:</span></span>

    ```csharp
    using System;

    namespace HelloWorld
    {
        class Program
        {
            static void Main(string[] args)
            {
                var c1 = new MyClass();
                Console.WriteLine($"Hello World! {c1.ReturnMessage()}");
            }
        }
    }
    ```

5. <span data-ttu-id="194c2-160">Salve as alterações e execute o programa novamente.</span><span class="sxs-lookup"><span data-stu-id="194c2-160">Save your changes and run your program again.</span></span> <span data-ttu-id="194c2-161">A nova mensagem deve aparecer com a cadeia de caracteres acrescentada.</span><span class="sxs-lookup"><span data-stu-id="194c2-161">The new message should appear with the appended string.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="194c2-162">Você obterá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="194c2-162">You get the following output:</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="194c2-163">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="194c2-163">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="194c2-164">Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="194c2-164">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="194c2-165">Meu depurador diz: "Nenhuma configuração".</span><span class="sxs-lookup"><span data-stu-id="194c2-165">My debugger says "No Configuration."</span></span>

<span data-ttu-id="194c2-166">A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você.</span><span class="sxs-lookup"><span data-stu-id="194c2-166">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="194c2-167">O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="194c2-167">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="194c2-168">Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug".</span><span class="sxs-lookup"><span data-stu-id="194c2-168">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="194c2-169">A seleção disso gera os arquivos de configuração *.vscode,* *launch.json*e *tasks.json* que você precisa.</span><span class="sxs-lookup"><span data-stu-id="194c2-169">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="194c2-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="194c2-170">See also</span></span>

- [<span data-ttu-id="194c2-171">Configurar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="194c2-171">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="194c2-172">Depurar no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="194c2-172">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
