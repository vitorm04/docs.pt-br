---
title: Criar um aplicativo de console do .NET Core usando Visual Studio Code
description: Saiba como criar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: 466a1353b574711a73570428569b58eab7ad8135
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84811694"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="c4939-103">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c4939-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="c4939-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4939-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="c4939-105">Tarefas de projeto, como criar, compilar e executar um projeto, são feitas usando o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4939-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="c4939-106">Você pode seguir este tutorial com um editor de código diferente e executar comandos em um terminal, se preferir.</span><span class="sxs-lookup"><span data-stu-id="c4939-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c4939-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c4939-107">Prerequisites</span></span>

1. <span data-ttu-id="c4939-108">[Visual Studio Code](https://code.visualstudio.com/) com a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="c4939-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="c4939-109">Para obter informações sobre como instalar extensões em Visual Studio Code, consulte [vs Code Marketplace de extensão](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="c4939-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="c4939-110">O [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="c4939-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c4939-111">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c4939-111">Create the app</span></span>

<span data-ttu-id="c4939-112">Crie um projeto de aplicativo de console do .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="c4939-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="c4939-113">Inicie o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c4939-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="c4939-114">Selecione **arquivo**  >  **abrir pasta** (**arquivo**  >  **aberto...** no MacOS) no menu principal.</span><span class="sxs-lookup"><span data-stu-id="c4939-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="c4939-115">Na caixa de diálogo **abrir pasta** , crie uma pasta *HelloWorld* e clique em **Selecionar pasta** (**aberta** no MacOS).</span><span class="sxs-lookup"><span data-stu-id="c4939-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="c4939-116">O nome da pasta torna-se o nome do projeto e o nome do namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="c4939-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="c4939-117">Você adicionará código posteriormente no tutorial que assume que o namespace do projeto é `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="c4939-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="c4939-118">Abra o **terminal** no Visual Studio Code selecionando **Exibir**  >  **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="c4939-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="c4939-119">O **terminal** é aberto com o prompt de comando na pasta *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="c4939-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="c4939-120">No **terminal**, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c4939-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="c4939-121">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="c4939-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c4939-122">Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="c4939-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="c4939-123">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="c4939-123">in the console window.</span></span>

<span data-ttu-id="c4939-124">O código de modelo define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento:</span><span class="sxs-lookup"><span data-stu-id="c4939-124">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="c4939-125">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4939-125">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c4939-126">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="c4939-126">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c4939-127">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c4939-127">Run the app</span></span>

<span data-ttu-id="c4939-128">Execute o seguinte comando no **terminal**:</span><span class="sxs-lookup"><span data-stu-id="c4939-128">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="c4939-129">O programa exibe "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="c4939-129">The program displays "Hello World!"</span></span> <span data-ttu-id="c4939-130">e termina.</span><span class="sxs-lookup"><span data-stu-id="c4939-130">and ends.</span></span>

![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="c4939-132">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="c4939-132">Enhance the app</span></span>

<span data-ttu-id="c4939-133">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="c4939-133">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="c4939-134">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="c4939-134">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="c4939-135">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="c4939-135">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="c4939-137">Selecione **Sim** quando Visual Studio Code solicitar que você adicione os ativos ausentes para compilar e depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4939-137">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="c4939-139">Substitua o conteúdo do `Main` método em *Program.cs*, que é a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="c4939-139">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="c4939-140">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="c4939-140">This code displays "What is your name?"</span></span> <span data-ttu-id="c4939-141">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida pela tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="c4939-141">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="c4939-142">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="c4939-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="c4939-143">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="c4939-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c4939-144">Por fim, ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="c4939-144">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="c4939-145">O `\n` representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="c4939-145">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="c4939-146">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c4939-146">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="c4939-147">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="c4939-147">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="c4939-148">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="c4939-148">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="c4939-149">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="c4939-149">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="c4939-150">No Visual Studio Code, você precisa salvar explicitamente as alterações.</span><span class="sxs-lookup"><span data-stu-id="c4939-150">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="c4939-151">Ao contrário do Visual Studio, as alterações de arquivo não são salvas automaticamente quando você compila e executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4939-151">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="c4939-152">Execute o programa novamente:</span><span class="sxs-lookup"><span data-stu-id="c4939-152">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="c4939-153">Responda ao prompt digitando um nome e pressionando a tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="c4939-153">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Janela do terminal com saída de programa modificada":::

1. <span data-ttu-id="c4939-155">Pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="c4939-155">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c4939-156">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="c4939-156">Additional resources</span></span>

- [<span data-ttu-id="c4939-157">Configurar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c4939-157">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="c4939-158">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c4939-158">Next steps</span></span>

<span data-ttu-id="c4939-159">Neste tutorial, você criou um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4939-159">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="c4939-160">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c4939-160">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c4939-161">Depurar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c4939-161">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
