---
title: Introdução ao C# e ao Visual Studio Code
description: Saiba como criar e depurar seu primeiro aplicativo .NET Core no C# usando o Visual Studio Code.
author: kendrahavens
ms.date: 04/23/2020
ms.openlocfilehash: 3dd7c4602fbb27e29bad977f8d3df34b6061bc23
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506864"
---
# <a name="get-started-with-c-and-visual-studio-code"></a><span data-ttu-id="dc81a-103">Introdução ao C# e ao Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc81a-103">Get started with C# and Visual Studio Code</span></span>

<span data-ttu-id="dc81a-104">O .NET Core oferece uma plataforma modular e rápida para a criação de aplicativos que são executados no Windows, Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="dc81a-104">.NET Core gives you a fast and modular platform for creating applications that run on Windows, Linux, and macOS.</span></span> <span data-ttu-id="dc81a-105">Use o Visual Studio Code com a extensão do C# para obter uma excelente experiência de edição com suporte completo para IntelliSense em C# (conclusão de código inteligente) e depuração.</span><span class="sxs-lookup"><span data-stu-id="dc81a-105">Use Visual Studio Code with the C# extension to get a powerful editing experience with full support for C# IntelliSense (smart code completion) and debugging.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc81a-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dc81a-106">Prerequisites</span></span>

1. <span data-ttu-id="dc81a-107">Instale o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="dc81a-107">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
2. <span data-ttu-id="dc81a-108">Instale o [SDK do .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="dc81a-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>
3. <span data-ttu-id="dc81a-109">Instale a [extensão de C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) para o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc81a-109">Install the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) for Visual Studio Code.</span></span> <span data-ttu-id="dc81a-110">Para saber mais sobre como instalar extensões no Visual Studio Code, confira [Marketplace de extensão de código do VS](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="dc81a-110">For more information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>

## <a name="hello-world"></a><span data-ttu-id="dc81a-111">Olá, Mundo</span><span class="sxs-lookup"><span data-stu-id="dc81a-111">Hello World</span></span>

<span data-ttu-id="dc81a-112">Comece com um programa simples de "Olá, Mundo" no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="dc81a-112">Get started with a simple "Hello World" program on .NET Core:</span></span>

1. <span data-ttu-id="dc81a-113">Abra um projeto:</span><span class="sxs-lookup"><span data-stu-id="dc81a-113">Open a project:</span></span>

    - <span data-ttu-id="dc81a-114">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc81a-114">Open Visual Studio Code.</span></span>
    - <span data-ttu-id="dc81a-115">Selecione **arquivo** > **abrir pasta** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc81a-115">Select **File** > **Open Folder** from the main menu.</span></span>
    - <span data-ttu-id="dc81a-116">Crie uma pasta chamada *HelloWorld*e clique em **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="dc81a-116">Create a folder named *HelloWorld*, and click **Select Folder**.</span></span> <span data-ttu-id="dc81a-117">O nome da pasta torna-se o nome do projeto e o nome do namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="dc81a-117">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="dc81a-118">Você adicionará código posteriormente no tutorial que assume que o namespace do projeto `HelloWorld`é.</span><span class="sxs-lookup"><span data-stu-id="dc81a-118">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="dc81a-119">Inicialize um projeto em C#:</span><span class="sxs-lookup"><span data-stu-id="dc81a-119">Initialize a C# project:</span></span>

    - <span data-ttu-id="dc81a-120">Abra o terminal de Visual Studio Code selecionando **Exibir** > **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc81a-120">Open the Terminal from Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>
    - <span data-ttu-id="dc81a-121">Na janela do terminal, digite `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="dc81a-121">In the terminal window, enter `dotnet new console`.</span></span>

      <span data-ttu-id="dc81a-122">Este comando cria um arquivo *Program.cs* em sua pasta com um programa simples de "Olá, mundo" já gravado, juntamente com um arquivo de projeto C# chamado *HelloWorld. csproj*.</span><span class="sxs-lookup"><span data-stu-id="dc81a-122">This command creates a *Program.cs* file in your folder with a simple "Hello World" program already written, along with a C# project file named *HelloWorld.csproj*.</span></span>

      ![O novo comando dotnet](media/with-visual-studio-code/dotnet-new-command.png)

1. <span data-ttu-id="dc81a-124">Execute o programa "Olá, Mundo":</span><span class="sxs-lookup"><span data-stu-id="dc81a-124">Run the "Hello World" program:</span></span>

    - <span data-ttu-id="dc81a-125">Na janela do terminal, digite `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="dc81a-125">In the terminal window, enter `dotnet run`.</span></span>

      ![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="debug"></a><span data-ttu-id="dc81a-127">Depurar</span><span class="sxs-lookup"><span data-stu-id="dc81a-127">Debug</span></span>

1. <span data-ttu-id="dc81a-128">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="dc81a-128">Open *Program.cs* by clicking on it.</span></span> <span data-ttu-id="dc81a-129">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="dc81a-129">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

    ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="dc81a-131">Visual Studio Code solicita que você adicione os ativos ausentes para compilar e depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dc81a-131">Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span> <span data-ttu-id="dc81a-132">Selecione **Sim** na barra superior.</span><span class="sxs-lookup"><span data-stu-id="dc81a-132">Select **Yes**.</span></span>

    ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="dc81a-134">Para abrir e exibição Depuração, clique no ícone Depuração no menu do lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="dc81a-134">To open the Debug view, click on the Debugging icon on the left side menu.</span></span>

    ![Abrir a guia Depurar no Visual Studio Code](media/with-visual-studio-code/open-debug-tab.png)

1. <span data-ttu-id="dc81a-136">Localize a seta verde na parte superior do painel.</span><span class="sxs-lookup"><span data-stu-id="dc81a-136">Locate the green arrow at the top of the pane.</span></span> <span data-ttu-id="dc81a-137">Certifique-se de que a lista suspensa ao lado dele tenha a **inicialização do .NET Core (console)** selecionada.</span><span class="sxs-lookup"><span data-stu-id="dc81a-137">Make sure the drop-down next to it has **.NET Core Launch (console)** selected.</span></span>

    ![Selecionando o .NET Core no Visual Studio Code](media/with-visual-studio-code/select-net-core.png)

1. <span data-ttu-id="dc81a-139">Adicione um ponto de interrupção ao seu projeto. Para isso, clique na **margem do editor** logo à esquerda dos números de linha no editor, próximo à linha 9, ou mova o cursor do texto na linha 9 no editor e pressione <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="dc81a-139">Add a breakpoint to your project by clicking on the **editor margin**, which is the space on the left of the line numbers in the editor, next to line 9, or move the text cursor onto line 9 in the editor and  press <kbd>F9</kbd>.</span></span>

    ![Definindo um ponto de interrupção](media/with-visual-studio-code/set-breakpoint-vs-code.png)

1. <span data-ttu-id="dc81a-141">Para iniciar a depuração, pressione <kbd>F5</kbd> ou selecione a seta verde.</span><span class="sxs-lookup"><span data-stu-id="dc81a-141">To start debugging, press <kbd>F5</kbd> or select the green arrow.</span></span> <span data-ttu-id="dc81a-142">O depurador interrompe a execução do programa quando ele atinge o ponto de interrupção definido na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="dc81a-142">The debugger stops execution of your program when it reaches the breakpoint you set in the previous step.</span></span>
    - <span data-ttu-id="dc81a-143">Durante a depuração, você pode exibir suas variáveis locais no painel superior esquerdo ou usar o console de depuração.</span><span class="sxs-lookup"><span data-stu-id="dc81a-143">While debugging, you can view your local variables in the top-left pane or use the debug console.</span></span>

1. <span data-ttu-id="dc81a-144">Selecione a seta azul na parte superior para continuar a depuração ou escolha o quadrado vermelho na parte superior para interromper o processamento.</span><span class="sxs-lookup"><span data-stu-id="dc81a-144">Select the blue arrow at the top to continue debugging, or select the red square at the top to stop.</span></span>

    ![Execução e depuração no Visual Studio Code](media/with-visual-studio-code/run-debug-vs-code.png)

> [!TIP]
> <span data-ttu-id="dc81a-146">Para obter mais informações e dicas sobre solução de problemas de depuração do .NET Core com o OmniSharp no Visual Studio Code, consulte [Instruções para configurar o depurador .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="dc81a-146">For more information and troubleshooting tips on .NET Core debugging with OmniSharp in Visual Studio Code, see [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="add-a-class"></a><span data-ttu-id="dc81a-147">Adicionar uma classe</span><span class="sxs-lookup"><span data-stu-id="dc81a-147">Add a class</span></span>

1. <span data-ttu-id="dc81a-148">Para adicionar uma nova classe, clique com o botão direito do mouse no VSCode Explorer abaixo de *Program.cs* e selecione **novo arquivo**.</span><span class="sxs-lookup"><span data-stu-id="dc81a-148">To add a new class, right-click in the VSCode Explorer below *Program.cs* and select **New File**.</span></span> <span data-ttu-id="dc81a-149">Isso adiciona um novo arquivo à pasta que você abriu no VSCode.</span><span class="sxs-lookup"><span data-stu-id="dc81a-149">This adds a new file to the folder you have open in VSCode.</span></span>
1. <span data-ttu-id="dc81a-150">Nomeie o arquivo *MyClass.cs*.</span><span class="sxs-lookup"><span data-stu-id="dc81a-150">Name your file *MyClass.cs*.</span></span> <span data-ttu-id="dc81a-151">Salve-o com uma extensão `.cs` no final para que ele seja reconhecido como um arquivo csharp.</span><span class="sxs-lookup"><span data-stu-id="dc81a-151">You must save it with a `.cs` extension at the end for it to be recognized as a csharp file.</span></span>
1. <span data-ttu-id="dc81a-152">Adicione o código a seguir para criar sua primeira classe.</span><span class="sxs-lookup"><span data-stu-id="dc81a-152">Add the following code to create your first class.</span></span>

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

1. <span data-ttu-id="dc81a-153">Chame sua nova classe do seu `Main` método substituindo o código em *Program.cs* pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="dc81a-153">Call your new class from your `Main` method by replacing the code in *Program.cs* with the following code:</span></span>

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

1. <span data-ttu-id="dc81a-154">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="dc81a-154">Save your changes.</span></span>

1. <span data-ttu-id="dc81a-155">Execute o programa novamente.</span><span class="sxs-lookup"><span data-stu-id="dc81a-155">Run the program again.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="dc81a-156">A nova mensagem é exibida com a cadeia de caracteres acrescentada.</span><span class="sxs-lookup"><span data-stu-id="dc81a-156">The new message appears with the appended string.</span></span>

    ```console
    Hello World! Happy coding!
    ```

## <a name="faq"></a><span data-ttu-id="dc81a-157">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="dc81a-157">FAQ</span></span>

### <a name="im-missing-required-assets-to-build-and-debug-c-in-visual-studio-code-my-debugger-says-no-configuration"></a><span data-ttu-id="dc81a-158">Faltam os ativos necessários para compilar e depurar C# no Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="dc81a-158">I'm missing required assets to build and debug C# in Visual Studio Code.</span></span> <span data-ttu-id="dc81a-159">Meu depurador diz: "Nenhuma configuração".</span><span class="sxs-lookup"><span data-stu-id="dc81a-159">My debugger says "No Configuration."</span></span>

<span data-ttu-id="dc81a-160">A extensão C# do Visual Studio Code pode gerar ativos para compilar e depurar para você.</span><span class="sxs-lookup"><span data-stu-id="dc81a-160">The Visual Studio Code C# extension can generate assets to build and debug for you.</span></span> <span data-ttu-id="dc81a-161">O Visual Studio Code solicita que você gere esses ativos ao abrir um projeto C# pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="dc81a-161">Visual Studio Code prompts you to generate these assets when you first open a C# project.</span></span> <span data-ttu-id="dc81a-162">Se você não gerar os ativos em seguida, você ainda poderá executar esse comando abrindo a paleta de comandos (**Exibição > Paleta de comandos**) e digitando">.NET: Generate Assets for Build and Debug".</span><span class="sxs-lookup"><span data-stu-id="dc81a-162">If you didn't generate assets then, you can still run this command by opening the Command Palette (**View > Command Palette**) and typing ">.NET: Generate Assets for Build and Debug".</span></span> <span data-ttu-id="dc81a-163">Selecionar isso gera os arquivos de configuração *. vscode*, *Launch. JSON*e *Tasks. JSON* necessários.</span><span class="sxs-lookup"><span data-stu-id="dc81a-163">Selecting this generates the *.vscode*, *launch.json*, and *tasks.json* configuration files that you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc81a-164">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc81a-164">See also</span></span>

- [<span data-ttu-id="dc81a-165">Configurar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc81a-165">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)
- [<span data-ttu-id="dc81a-166">Depurar no Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc81a-166">Debugging in Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/editor/debugging)
