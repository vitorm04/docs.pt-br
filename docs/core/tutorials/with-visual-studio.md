---
title: Criar um aplicativo de console com o .NET Core no Visual Studio
description: Saiba como criar um aplicativo de console .NET Core com C# ou Visual Basic usando o Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201592"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="4249b-103">Tutorial: criar um aplicativo de console do .NET Core no Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4249b-103">Tutorial: Create a .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="4249b-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="4249b-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4249b-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4249b-105">Prerequisites</span></span>

- <span data-ttu-id="4249b-106">[Visual Studio 2019 versão 16,6 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="4249b-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="4249b-107">O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4249b-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="4249b-108">Para obter mais informações, consulte a seção [instalar com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) no artigo [instalar o SDK do .NET Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="4249b-108">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4249b-109">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4249b-109">Create the app</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="4249b-110">Abra o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="4249b-110">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="4249b-111">Crie um novo projeto de aplicativo de console do .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="4249b-111">Create a new .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="4249b-112">Na página inicial, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="4249b-112">On the start page, choose **Create a new project**.</span></span>

      ![Criar um novo botão de projeto selecionado na página inicial do Visual Studio](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="4249b-114">Na página **criar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="4249b-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="4249b-115">Em seguida, escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="4249b-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="4249b-116">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="4249b-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Criar uma nova janela de projeto com filtros selecionados](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="4249b-118">Se você não vir os modelos do .NET Core, provavelmente está faltando a carga de trabalho necessária.</span><span class="sxs-lookup"><span data-stu-id="4249b-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="4249b-119">Na mensagem **não localizando o que você está procurando?** , escolha o link **instalar mais ferramentas e recursos** .</span><span class="sxs-lookup"><span data-stu-id="4249b-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="4249b-120">O Instalador do Visual Studio é aberto.</span><span class="sxs-lookup"><span data-stu-id="4249b-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="4249b-121">Verifique se você tem a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="4249b-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="4249b-122">Na página **configurar seu novo projeto** , digite **HelloWorld** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="4249b-122">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="4249b-123">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="4249b-123">Then choose **Create**.</span></span>

      ![Configurar sua nova janela de projeto com os campos nome do projeto, local e nome da solução](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="4249b-125">O modelo de aplicativo de console para .NET Core define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento.</span><span class="sxs-lookup"><span data-stu-id="4249b-125">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="4249b-126">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4249b-126">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4249b-127">Quaisquer argumentos de linha de comando fornecidos quando o aplicativo for iniciado estão disponíveis na matriz *args*.</span><span class="sxs-lookup"><span data-stu-id="4249b-127">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   <span data-ttu-id="4249b-128">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="4249b-128">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="4249b-129">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="4249b-129">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="4249b-130">Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="4249b-130">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="4249b-131">na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4249b-131">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4249b-132">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4249b-132">Run the app</span></span>

1. <span data-ttu-id="4249b-133">Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="4249b-133">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![Barra de ferramentas do Visual Studio com o botão execução HelloWorld selecionado](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="4249b-135">Uma janela de console é aberta com o texto "Olá, Mundo!"</span><span class="sxs-lookup"><span data-stu-id="4249b-135">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="4249b-136">impresso na tela e algumas informações de depuração do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4249b-136">printed on the screen and some Visual Studio debug information.</span></span>

   ![Janela de console mostrando Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="4249b-138">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="4249b-138">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="4249b-139">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4249b-139">Enhance the app</span></span>

<span data-ttu-id="4249b-140">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="4249b-140">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="4249b-141">As instruções a seguir modificam o aplicativo e executam novamente:</span><span class="sxs-lookup"><span data-stu-id="4249b-141">The following instructions modify the app and run it again:</span></span>

1. <span data-ttu-id="4249b-142">Substitua o conteúdo do `Main` método, que atualmente é apenas a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4249b-142">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   <span data-ttu-id="4249b-143">Esse código exibe "Qual é o seu nome?"</span><span class="sxs-lookup"><span data-stu-id="4249b-143">This code displays "What is your name?"</span></span> <span data-ttu-id="4249b-144">na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida da tecla Enter.</span><span class="sxs-lookup"><span data-stu-id="4249b-144">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="4249b-145">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="4249b-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4249b-146">Ele também recupera o valor da <xref:System.DateTime.Now?displayProperty=nameWithType> propriedade, que contém a hora local atual e a atribui a uma variável chamada `date` ( `currentDate` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4249b-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="4249b-147">Por fim, ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="4249b-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="4249b-148">O `\n` ( `vbCrLf` em Visual Basic) representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="4249b-148">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="4249b-149">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4249b-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4249b-150">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="4249b-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4249b-151">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4249b-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4249b-152">Para executar o programa, escolha **HelloWorld** na barra de ferramentas ou pressione **F5**.</span><span class="sxs-lookup"><span data-stu-id="4249b-152">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="4249b-153">Responda ao prompt digitando um nome e pressionando a tecla **Enter** .</span><span class="sxs-lookup"><span data-stu-id="4249b-153">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Janela de console com saída de programa modificada](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="4249b-155">Pressione qualquer tecla para fechar a janela do console.</span><span class="sxs-lookup"><span data-stu-id="4249b-155">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4249b-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4249b-156">Next steps</span></span>

<span data-ttu-id="4249b-157">Neste tutorial, você criou um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4249b-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="4249b-158">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4249b-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4249b-159">Depurar um aplicativo de console do .NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4249b-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
