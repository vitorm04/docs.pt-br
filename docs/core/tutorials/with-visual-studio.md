---
title: Criar um aplicativo de console do .NET Core usando o Visual Studio
description: Saiba como criar um aplicativo de console .NET Core com C# ou Visual Basic usando o Visual Studio.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4cd18aca4396f902268d59867760424d65ddcf6d
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867627"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="ebdb4-103">Tutorial: criar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ebdb4-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="ebdb4-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ebdb4-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ebdb4-105">Prerequisites</span></span>

- <span data-ttu-id="ebdb4-106">[Visual Studio 2019 versão 16,6 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="ebdb4-107">O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="ebdb4-108">Para obter mais informações, consulte [instalar o SDK do .NET Core com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ebdb4-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="ebdb4-109">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ebdb4-109">Create the app</span></span>

<span data-ttu-id="ebdb4-110">Crie um projeto de aplicativo de console do .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="ebdb4-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="ebdb4-111">Inicie o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="ebdb4-112">Na página inicial, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-112">On the start page, choose **Create a new project**.</span></span>

   ![Criar um novo botão de projeto selecionado na página inicial do Visual Studio](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="ebdb4-114">Na página **criar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="ebdb4-115">Em seguida, escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="ebdb4-116">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![Criar uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="ebdb4-118">Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="ebdb4-119">Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** .</span><span class="sxs-lookup"><span data-stu-id="ebdb4-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="ebdb4-120">O Instalador do Visual Studio é aberto.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="ebdb4-121">Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="ebdb4-122">No diálogo **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="ebdb4-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="ebdb4-123">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-123">Then choose **Create**.</span></span>

   ![Configurar sua nova janela de projeto com os campos nome do projeto, local e nome da solução](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="ebdb4-125">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="ebdb4-126">Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="ebdb4-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="ebdb4-127">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-127">in the console window.</span></span>

<span data-ttu-id="ebdb4-128">O código de modelo define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento:</span><span class="sxs-lookup"><span data-stu-id="ebdb4-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

<span data-ttu-id="ebdb4-129">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="ebdb4-130">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="ebdb4-131">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="ebdb4-132">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ebdb4-132">Run the app</span></span>

1. <span data-ttu-id="ebdb4-133">Pressione <kbd>Ctrl</kbd> + <kbd>F5</kbd> para executar o programa sem depuração.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-133">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="ebdb4-134">Uma janela de console é aberta com o texto "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="ebdb4-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="ebdb4-135">impresso na tela e algumas informações de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="ebdb4-137">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="ebdb4-138">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ebdb4-138">Enhance the app</span></span>

<span data-ttu-id="ebdb4-139">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="ebdb4-140">Em *Program.cs* ou *Program. vb*, substitua o conteúdo do `Main` método, que é a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ebdb4-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="ebdb4-141">Esse código exibe um prompt na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida pela tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="ebdb4-141">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="ebdb4-142">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="ebdb4-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="ebdb4-143">Ele também recupera o valor da <xref:System.DateTime.Now?displayProperty=nameWithType> propriedade, que contém a hora local atual e a atribui a uma variável chamada `date` ( `currentDate` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ebdb4-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="ebdb4-144">E ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-144">And it displays these values in the console window.</span></span> <span data-ttu-id="ebdb4-145">Por fim, ele exibe um prompt na janela do console e chama o <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> método para aguardar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-145">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="ebdb4-146">O `\n` ( `vbCrLf` em Visual Basic) representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="ebdb4-147">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="ebdb4-148">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="ebdb4-149">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="ebdb4-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="ebdb4-150">Pressione <kbd>Ctrl</kbd> + <kbd>F5</kbd> para executar o programa sem depuração.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-150">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="ebdb4-151">Responda ao prompt digitando um nome e pressionando a tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="ebdb4-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="ebdb4-153">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ebdb4-154">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ebdb4-154">Next steps</span></span>

<span data-ttu-id="ebdb4-155">Neste tutorial, você criou um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="ebdb4-156">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebdb4-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ebdb4-157">Depurar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ebdb4-157">Debug a .NET Core console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
