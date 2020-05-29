---
title: Criar um aplicativo de console com o .NET Core usando Visual Studio Code
description: Saiba como criar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201695"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="547ec-103">Tutorial: criar um aplicativo de console com o .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="547ec-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="547ec-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core usando Visual Studio Code e o CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="547ec-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="547ec-105">Tarefas de projeto, como criar, compilar e executar um projeto, são feitas usando a CLI, para que você possa seguir este tutorial com um editor de código diferente e executar comandos em um terminal, se preferir.</span><span class="sxs-lookup"><span data-stu-id="547ec-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="547ec-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="547ec-106">Prerequisites</span></span>

1. <span data-ttu-id="547ec-107">[Visual Studio Code](https://code.visualstudio.com/) com a [extensão C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) instalada.</span><span class="sxs-lookup"><span data-stu-id="547ec-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="547ec-108">Para obter informações sobre como instalar extensões em Visual Studio Code, consulte [vs Code Marketplace de extensão](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="547ec-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="547ec-109">O [SDK do .NET Core 3,1 ou posterior](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="547ec-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="547ec-110">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="547ec-110">Create the app</span></span>

1. <span data-ttu-id="547ec-111">Abra o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="547ec-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="547ec-112">Criar um projeto.</span><span class="sxs-lookup"><span data-stu-id="547ec-112">Create a project.</span></span>

   1. <span data-ttu-id="547ec-113">Selecione **arquivo**  >  **abrir pasta** / **abrir...** no menu principal, crie uma pasta *HelloWorld* e clique em **Selecionar pasta** / **abrir**.</span><span class="sxs-lookup"><span data-stu-id="547ec-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="547ec-114">O nome da pasta torna-se o nome do projeto e o nome do namespace por padrão.</span><span class="sxs-lookup"><span data-stu-id="547ec-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="547ec-115">Você adicionará código posteriormente no tutorial que assume que o namespace do projeto é `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="547ec-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="547ec-116">Abra o **terminal** no Visual Studio Code selecionando **Exibir**  >  **terminal** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="547ec-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="547ec-117">O **terminal** é aberto com o prompt de comando na pasta *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="547ec-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="547ec-118">No **terminal**, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="547ec-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="547ec-119">O modelo de aplicativo de console para .NET Core define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento.</span><span class="sxs-lookup"><span data-stu-id="547ec-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="547ec-120">O arquivo *Program.cs* tem o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="547ec-120">The *Program.cs* file has the following code:</span></span>

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

<span data-ttu-id="547ec-121">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="547ec-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="547ec-122">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="547ec-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="547ec-123">O modelo cria um aplicativo simples que chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="547ec-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="547ec-124">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="547ec-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="547ec-125">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="547ec-125">Run the app</span></span>

<span data-ttu-id="547ec-126">Execute o seguinte comando no **terminal**:</span><span class="sxs-lookup"><span data-stu-id="547ec-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="547ec-127">O programa exibe "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="547ec-127">The program displays "Hello World!"</span></span> <span data-ttu-id="547ec-128">e termina.</span><span class="sxs-lookup"><span data-stu-id="547ec-128">and ends.</span></span>

![O comando de execução dotnet](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="547ec-130">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="547ec-130">Enhance the app</span></span>

<span data-ttu-id="547ec-131">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="547ec-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="547ec-132">Abra *Program.cs* clicando nele.</span><span class="sxs-lookup"><span data-stu-id="547ec-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="547ec-133">Na primeira vez que um arquivo do C# é aberto no Visual Studio Code, o [OmniSharp](https://www.omnisharp.net/) é carregado no editor.</span><span class="sxs-lookup"><span data-stu-id="547ec-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Abra o arquivo Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="547ec-135">Selecione **Sim** quando Visual Studio Code solicitar que você adicione os ativos ausentes para compilar e depurar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="547ec-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Prompt para ativos ausentes](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="547ec-137">Substitua o conteúdo do `Main` método em *Program.cs*, que atualmente é apenas a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="547ec-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="547ec-138">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="547ec-138">This code displays "What is your name?"</span></span> <span data-ttu-id="547ec-139">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida pela tecla **Enter** .</span><span class="sxs-lookup"><span data-stu-id="547ec-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="547ec-140">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="547ec-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="547ec-141">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="547ec-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="547ec-142">Por fim, ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="547ec-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="547ec-143">O `\n` representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="547ec-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="547ec-144">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="547ec-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="547ec-145">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="547ec-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="547ec-146">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="547ec-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="547ec-147">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="547ec-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="547ec-148">No Visual Studio Code, você precisa salvar explicitamente as alterações.</span><span class="sxs-lookup"><span data-stu-id="547ec-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="547ec-149">Ao contrário do Visual Studio, as alterações de arquivo não são salvas automaticamente quando você compila e executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="547ec-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="547ec-150">Execute o programa novamente:</span><span class="sxs-lookup"><span data-stu-id="547ec-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="547ec-151">Responda ao prompt digitando um nome e pressionando a tecla **Enter** .</span><span class="sxs-lookup"><span data-stu-id="547ec-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Janela do terminal com saída de programa modificada":::

1. <span data-ttu-id="547ec-153">Pressione qualquer tecla para sair do programa.</span><span class="sxs-lookup"><span data-stu-id="547ec-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="547ec-154">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="547ec-154">Additional resources</span></span>

- [<span data-ttu-id="547ec-155">Configurar o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="547ec-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="547ec-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="547ec-156">Next steps</span></span>

<span data-ttu-id="547ec-157">Neste tutorial, você criou um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="547ec-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="547ec-158">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="547ec-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="547ec-159">Depurar um aplicativo de console do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="547ec-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
