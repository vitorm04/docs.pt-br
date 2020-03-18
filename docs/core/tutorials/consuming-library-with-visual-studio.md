---
title: Consumir uma biblioteca .NET Standard no Visual Studio
description: Crie um aplicativo .NET Core que chama os membros de outra biblioteca de classe com o Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920451"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="5760c-103">Consumir uma biblioteca .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5760c-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="5760c-104">Depois de criar uma biblioteca de classe .NET Standard, testá-la e construir uma versão de versão da biblioteca, o próximo passo é disponibilizá-la aos chamadores.</span><span class="sxs-lookup"><span data-stu-id="5760c-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="5760c-105">É possível fazer isso de duas formas:</span><span class="sxs-lookup"><span data-stu-id="5760c-105">You can do this in two ways:</span></span>

- <span data-ttu-id="5760c-106">Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.</span><span class="sxs-lookup"><span data-stu-id="5760c-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="5760c-107">Se a biblioteca estiver disponível publicamente, você pode distribuí-la como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="5760c-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="5760c-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="5760c-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5760c-109">Adicione um aplicativo de console à sua solução que faz referência a um projeto de biblioteca .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5760c-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="5760c-110">Crie um pacote NuGet que contenha um projeto de biblioteca padrão .NET.</span><span class="sxs-lookup"><span data-stu-id="5760c-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="5760c-111">Adicione um aplicativo de console à sua solução</span><span class="sxs-lookup"><span data-stu-id="5760c-111">Add a console app to your solution</span></span>

<span data-ttu-id="5760c-112">Assim como você incluiu testes unitários na mesma solução que sua biblioteca de classe no [Teste de uma biblioteca .NET Standard no Visual Studio,](testing-library-with-visual-studio.md)você pode incluir seu aplicativo como parte dessa solução.</span><span class="sxs-lookup"><span data-stu-id="5760c-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="5760c-113">Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:</span><span class="sxs-lookup"><span data-stu-id="5760c-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="5760c-114">Abra `ClassLibraryProjects` a solução criada na [biblioteca Build a .NET Standard no](library-with-visual-studio.md) artigo do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5760c-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="5760c-115">Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.</span><span class="sxs-lookup"><span data-stu-id="5760c-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="5760c-116">Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5760c-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5760c-117">Na **página Adicionar uma nova** página de projeto, digite console na caixa de pesquisa. **console**</span><span class="sxs-lookup"><span data-stu-id="5760c-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="5760c-118">Escolha **C#** ou **Visual Basic** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma.</span><span class="sxs-lookup"><span data-stu-id="5760c-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5760c-119">Escolha o modelo **do Aplicativo de console (.NET Core)** e escolha **Next**.</span><span class="sxs-lookup"><span data-stu-id="5760c-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5760c-120">Na **página Configurar sua nova** página de projeto, digite **ShowCase** na caixa **nome do Projeto.**</span><span class="sxs-lookup"><span data-stu-id="5760c-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="5760c-121">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="5760c-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="5760c-122">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="5760c-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu de contexto do projeto Visual Studio para definir projeto de startup](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="5760c-124">Inicialmente, seu projeto não tem acesso à sua biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="5760c-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="5760c-125">Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="5760c-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="5760c-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="5760c-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Adicionar menu de contexto de referência no Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="5760c-128">Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="5760c-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Caixa de diálogo gerenciador de referência com stringlibrary selecionado](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="5760c-130">Na janela de código para o *arquivo Program.cs* ou *Program.vb,* substitua todo o código pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5760c-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="5760c-131">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="5760c-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5760c-132">Sempre que é maior ou igual a 25, o código limpa a janela do console e exibe uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="5760c-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5760c-133">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5760c-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5760c-134">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="5760c-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5760c-135">Se o usuário pressionar a tecla Enter sem inserir uma seqüência, o aplicativo será fechado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="5760c-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="5760c-136">Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="5760c-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="5760c-137">Compile e execute o programa selecionando a seta verde no botão **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="5760c-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Barra de ferramentas do projeto Visual Studio mostrando botão Debug](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="5760c-139">Você pode depurar e publicar o aplicativo que usa esta biblioteca seguindo os passos em [Debug your C# ou Visual Basic .NET Core Hello World aplicativo usando Visual Studio](debugging-with-visual-studio.md) e Publicar seu aplicativo [.NET Core Hello World com o Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5760c-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="5760c-140">Criar um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="5760c-140">Create a NuGet package</span></span>

<span data-ttu-id="5760c-141">Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="5760c-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="5760c-142">O Visual Studio não suporta a criação de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5760c-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="5760c-143">Para criar um, você precisa usar os comandos .NET Core CLI:</span><span class="sxs-lookup"><span data-stu-id="5760c-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="5760c-144">Abra uma janela do console.</span><span class="sxs-lookup"><span data-stu-id="5760c-144">Open a console window.</span></span>

   <span data-ttu-id="5760c-145">Por exemplo, **digite 'Prompt'** de comando na caixa de pesquisa na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="5760c-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="5760c-146">Selecione o aplicativo de desktop **Command Prompt** ou **pressione Enter** se ele já estiver selecionado nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="5760c-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="5760c-147">Navegue até o diretório do projeto da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="5760c-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="5760c-148">O diretório contém seu código-fonte e um arquivo de projeto, *StringLibrary.csproj* ou *StringLibrary.vbproj*.</span><span class="sxs-lookup"><span data-stu-id="5760c-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="5760c-149">Execute o comando [dotnet pack](../tools/dotnet-pack.md) para gerar um pacote com uma extensão *.nupkg:*</span><span class="sxs-lookup"><span data-stu-id="5760c-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="5760c-150">Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="5760c-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="5760c-151">Para obter mais informações sobre a criação de pacotes NuGet, consulte [Como criar um pacote NuGet com o .NET Core CLI](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="5760c-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
