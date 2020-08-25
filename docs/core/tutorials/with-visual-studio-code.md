---
title: Criar um aplicativo de console do .NET Core usando Visual Studio Code
description: Saiba como criar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: e936c23d8525e42a9d2781cc680067c9da2ce42f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811920"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="4bfac-103">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bfac-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="4bfac-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bfac-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="4bfac-105">Tarefas de projeto, como criar, compilar e executar um projeto, são feitas usando o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bfac-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="4bfac-106">Você pode seguir este tutorial com um editor de código diferente e executar comandos em um terminal, se preferir.</span><span class="sxs-lookup"><span data-stu-id="4bfac-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4bfac-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4bfac-107">Prerequisites</span></span>

1. <span data-ttu-id="4bfac-108">[Visual Studio Code](https://code.visualstudio.com/) com a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="4bfac-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="4bfac-109">Para obter informações sobre como instalar extensões em Visual Studio Code, consulte [vs Code Marketplace de extensão](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="4bfac-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="4bfac-110">O [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="4bfac-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4bfac-111">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4bfac-111">Create the app</span></span>

<span data-ttu-id="4bfac-112">Crie um projeto de aplicativo de console do .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="4bfac-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="4bfac-113">Iniciar o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4bfac-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="4bfac-114">Selecione **arquivo**  >  **abrir pasta** (**arquivo**  >  **aberto...** no MacOS) no menu principal.</span><span class="sxs-lookup"><span data-stu-id="4bfac-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="4bfac-115">Na caixa de diálogo **abrir pasta** , crie uma pasta *HelloWorld* e clique em **Selecionar pasta** (**aberta** no MacOS).</span><span class="sxs-lookup"><span data-stu-id="4bfac-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="4bfac-116">O nome da pasta torna-se o nome do projeto e o nome do namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="4bfac-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="4bfac-117">Você adicionará código posteriormente no tutorial que assume que o namespace do projeto é `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="4bfac-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="4bfac-118">Abra o **terminal** no Visual Studio Code selecionando **Exibir**  >  **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="4bfac-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="4bfac-119">O **terminal** é aberto com o prompt de comando na pasta *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="4bfac-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="4bfac-120">No **terminal**, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4bfac-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="4bfac-121">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="4bfac-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="4bfac-122">Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir " :::no-loc text="Hello World!"::: " na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4bfac-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="4bfac-123">O código de modelo define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento:</span><span class="sxs-lookup"><span data-stu-id="4bfac-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="4bfac-124">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4bfac-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4bfac-125">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="4bfac-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4bfac-126">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4bfac-126">Run the app</span></span>

<span data-ttu-id="4bfac-127">Execute o seguinte comando no **terminal**:</span><span class="sxs-lookup"><span data-stu-id="4bfac-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="4bfac-128">O programa exibe "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="4bfac-128">The program displays "Hello World!"</span></span> <span data-ttu-id="4bfac-129">e termina.</span><span class="sxs-lookup"><span data-stu-id="4bfac-129">and ends.</span></span>

![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="4bfac-131">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4bfac-131">Enhance the app</span></span>

<span data-ttu-id="4bfac-132">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="4bfac-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="4bfac-133">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="4bfac-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="4bfac-134">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="4bfac-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="4bfac-136">Selecione **Sim** quando Visual Studio Code solicitar que você adicione os ativos ausentes para compilar e depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4bfac-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="4bfac-138">Substitua o conteúdo do `Main` método em *Program.cs*, que é a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4bfac-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="4bfac-139">Esse código exibe um prompt na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida pela tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="4bfac-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="4bfac-140">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="4bfac-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4bfac-141">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="4bfac-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="4bfac-142">E ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4bfac-142">And it displays these values in the console window.</span></span> <span data-ttu-id="4bfac-143">Por fim, ele exibe um prompt na janela do console e chama o <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> método para aguardar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="4bfac-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="4bfac-144">O `\n` representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="4bfac-144">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="4bfac-145">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4bfac-145">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4bfac-146">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="4bfac-146">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4bfac-147">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4bfac-147">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4bfac-148">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="4bfac-148">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="4bfac-149">No Visual Studio Code, você precisa salvar explicitamente as alterações.</span><span class="sxs-lookup"><span data-stu-id="4bfac-149">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="4bfac-150">Ao contrário do Visual Studio, as alterações de arquivo não são salvas automaticamente quando você compila e executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4bfac-150">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="4bfac-151">Execute o programa novamente:</span><span class="sxs-lookup"><span data-stu-id="4bfac-151">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="4bfac-152">Responda ao prompt digitando um nome e pressionando a tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="4bfac-152">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Janela do terminal com saída de programa modificada":::

1. <span data-ttu-id="4bfac-154">Pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="4bfac-154">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4bfac-155">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="4bfac-155">Additional resources</span></span>

- [<span data-ttu-id="4bfac-156">Configurar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bfac-156">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="4bfac-157">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4bfac-157">Next steps</span></span>

<span data-ttu-id="4bfac-158">Neste tutorial, você criou um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bfac-158">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="4bfac-159">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4bfac-159">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4bfac-160">Depurar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bfac-160">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
