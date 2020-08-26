---
title: Criar um aplicativo de console do .NET Core usando Visual Studio para Mac
description: Saiba como criar um aplicativo de console do .NET Core usando Visual Studio para Mac.
ms.date: 06/02/2020
ms.openlocfilehash: 8ffcb05ad85f53180ca1aaefbd2dfc7496946142
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867653"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="0f02f-103">Tutorial: criar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="0f02f-103">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="0f02f-104">Este tutorial mostra como criar e executar um aplicativo de console do .NET Core usando Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="0f02f-104">This tutorial shows how to create and run a .NET Core console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="0f02f-105">Seus comentários são muito importantes.</span><span class="sxs-lookup"><span data-stu-id="0f02f-105">Your feedback is highly valued.</span></span> <span data-ttu-id="0f02f-106">Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="0f02f-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="0f02f-107">Em Visual Studio para Mac, selecione **ajuda**para  >  **relatar um problema** no menu ou **relatar um problema** na tela de boas-vindas, que abrirá uma janela para o arquivamento de um relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="0f02f-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="0f02f-108">Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://developercommunity.visualstudio.com/spaces/8/index.html).</span><span class="sxs-lookup"><span data-stu-id="0f02f-108">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="0f02f-109">Para fazer uma sugestão, selecione **ajuda**  >  **fornecer uma sugestão** no menu ou **forneça uma sugestão** na tela de boas-vindas, que levará você para a [página da Web do Visual Studio para Mac Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span><span class="sxs-lookup"><span data-stu-id="0f02f-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f02f-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f02f-110">Prerequisites</span></span>

* <span data-ttu-id="0f02f-111">[Visual Studio para Mac versão 8,6 ou posterior](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="0f02f-111">[Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="0f02f-112">Selecione a opção para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f02f-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="0f02f-113">A instalação do Xamarin é opcional para o desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f02f-113">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="0f02f-114">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f02f-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="0f02f-115">[Tutorial: instalar o Visual Studio para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="0f02f-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="0f02f-116">[Versões do MacOS com suporte](../install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="0f02f-116">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="0f02f-117">[Versões do .NET Core com suporte pelo Visual Studio para Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="0f02f-117">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="0f02f-118">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f02f-118">Create the app</span></span>

<span data-ttu-id="0f02f-119">Crie um projeto de aplicativo de console do .NET Core chamado "HelloWorld".</span><span class="sxs-lookup"><span data-stu-id="0f02f-119">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="0f02f-120">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="0f02f-120">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="0f02f-121">Selecione **novo** na janela iniciar.</span><span class="sxs-lookup"><span data-stu-id="0f02f-121">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="O botão Novo na tela de Boas-vindas do Visual Studio para Mac":::

1. <span data-ttu-id="0f02f-123">Na caixa de diálogo **novo projeto** , selecione **aplicativo** no nó **Web e console** .</span><span class="sxs-lookup"><span data-stu-id="0f02f-123">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="0f02f-124">Selecione o modelo de **aplicativo de console** e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0f02f-124">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="Lista de modelos de novo projeto":::

1. <span data-ttu-id="0f02f-126">Na lista **suspensa estrutura de destino** da caixa de diálogo **configurar seu novo aplicativo de console** , selecione **.NET Core 3,1**e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="0f02f-126">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET Core 3.1**, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="Selecionar estrutura de destino":::

1. <span data-ttu-id="0f02f-128">Digite "HelloWorld" para o **nome do projeto**e selecione **criar**.</span><span class="sxs-lookup"><span data-stu-id="0f02f-128">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="Configurar a caixa de diálogo Novo Aplicativo de Console":::

<span data-ttu-id="0f02f-130">O modelo cria um simples aplicativo “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="0f02f-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="0f02f-131">Ele chama o <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> método para exibir "Olá, mundo!"</span><span class="sxs-lookup"><span data-stu-id="0f02f-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="0f02f-132">na janela do terminal.</span><span class="sxs-lookup"><span data-stu-id="0f02f-132">in the terminal window.</span></span>

<span data-ttu-id="0f02f-133">O código de modelo define uma classe, `Program` , com um único método, `Main` , que usa uma <xref:System.String> matriz como um argumento:</span><span class="sxs-lookup"><span data-stu-id="0f02f-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="0f02f-134">`Main` é o ponto de entrada do aplicativo, o método que é chamado automaticamente pelo runtime quando ele inicia o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f02f-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="0f02f-135">Todos os argumentos de linha de comando fornecidos quando o aplicativo é iniciado estão disponíveis na `args` matriz.</span><span class="sxs-lookup"><span data-stu-id="0f02f-135">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="0f02f-136">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f02f-136">Run the app</span></span>

1. <span data-ttu-id="0f02f-137">Pressione <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>comando</kbd>Option + <kbd>Enter</kbd>) para executar o aplicativo sem depuração.</span><span class="sxs-lookup"><span data-stu-id="0f02f-137">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="O terminal mostra Olá, Mundo!":::

1. <span data-ttu-id="0f02f-139">Feche a janela do **terminal** .</span><span class="sxs-lookup"><span data-stu-id="0f02f-139">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="0f02f-140">Aprimorar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f02f-140">Enhance the app</span></span>

<span data-ttu-id="0f02f-141">Aprimore o aplicativo para solicitar ao usuário seu nome e exibi-lo junto com a data e hora.</span><span class="sxs-lookup"><span data-stu-id="0f02f-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="0f02f-142">No *Program.cs*, substitua o conteúdo do `Main` método, que é a linha que chama `Console.WriteLine` , com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0f02f-142">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="0f02f-143">Esse código exibe um prompt na janela do console e aguarda até que o usuário insira uma cadeia de caracteres seguida pela tecla <kbd>Enter</kbd> .</span><span class="sxs-lookup"><span data-stu-id="0f02f-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="0f02f-144">Ele armazena essa cadeia de caracteres em uma variável chamada `name` .</span><span class="sxs-lookup"><span data-stu-id="0f02f-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="0f02f-145">Ele também recupera o valor da propriedade <xref:System.DateTime.Now?displayProperty=nameWithType>, que contém a hora local atual e o atribui a uma variável chamada `date`.</span><span class="sxs-lookup"><span data-stu-id="0f02f-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="0f02f-146">E ele exibe esses valores na janela do console.</span><span class="sxs-lookup"><span data-stu-id="0f02f-146">And it displays these values in the console window.</span></span> <span data-ttu-id="0f02f-147">Por fim, ele exibe um prompt na janela do console e chama o <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> método para aguardar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="0f02f-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="0f02f-148">O `\n` representa um caractere de nova linha.</span><span class="sxs-lookup"><span data-stu-id="0f02f-148">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="0f02f-149">O cifrão ( `$` ) na frente de uma cadeia de caracteres permite que você coloque expressões como nomes de variáveis entre chaves na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0f02f-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="0f02f-150">O valor da expressão é inserido na cadeia de caracteres no lugar da expressão.</span><span class="sxs-lookup"><span data-stu-id="0f02f-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="0f02f-151">Essa sintaxe é conhecida como [cadeias de caracteres interpoladas](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="0f02f-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="0f02f-152">Pressione <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>comando</kbd>Option + <kbd>Enter</kbd>) para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f02f-152">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="0f02f-153">Responda ao prompt digitando um nome e pressionando <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0f02f-153">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="Terminal mostra a saída de programa modificada":::

1. <span data-ttu-id="0f02f-155">Feche o terminal.</span><span class="sxs-lookup"><span data-stu-id="0f02f-155">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0f02f-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="0f02f-156">Next steps</span></span>

<span data-ttu-id="0f02f-157">Neste tutorial, você criou um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f02f-157">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="0f02f-158">No próximo tutorial, você depurará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f02f-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0f02f-159">Depurar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="0f02f-159">Debug a .NET Core console application using Visual Studio for Mac</span></span>](debugging-with-visual-studio-mac.md)
