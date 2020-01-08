---
title: Consumir uma biblioteca .NET Standard no Visual Studio
description: Crie um aplicativo .NET Core que chama membros de outra biblioteca de classes com o Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 9fcfb2e0c664186feda24c2a12daacb38769a68e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75339994"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="37763-103">Consumir uma biblioteca .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="37763-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="37763-104">Depois de criar uma biblioteca de classes .NET Standard, testá-la e criar uma versão de lançamento da biblioteca, a próxima etapa é disponibilizá-la para os chamadores.</span><span class="sxs-lookup"><span data-stu-id="37763-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="37763-105">Você pode fazer isso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="37763-105">You can do this in two ways:</span></span>

- <span data-ttu-id="37763-106">Se a biblioteca for usada por uma única solução (por exemplo, se for um componente em um único aplicativo grande), você poderá incluí-la como um projeto de sua solução.</span><span class="sxs-lookup"><span data-stu-id="37763-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="37763-107">Se a biblioteca estiver disponível publicamente, você poderá distribuí-la como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="37763-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="37763-108">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="37763-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="37763-109">Adicione um aplicativo de console à sua solução que faz referência a um projeto de biblioteca .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="37763-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="37763-110">Crie um pacote NuGet que contenha um projeto de biblioteca .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="37763-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="37763-111">Adicionar um aplicativo de console à sua solução</span><span class="sxs-lookup"><span data-stu-id="37763-111">Add a console app to your solution</span></span>

<span data-ttu-id="37763-112">Assim como você inclui testes de unidade na mesma solução que a biblioteca de classes em [testar uma biblioteca de .net Standard no Visual Studio](testing-library-with-visual-studio.md), você pode incluir seu aplicativo como parte dessa solução.</span><span class="sxs-lookup"><span data-stu-id="37763-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="37763-113">Por exemplo, você pode usar a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e informe se o primeiro caractere é maiúsculo:</span><span class="sxs-lookup"><span data-stu-id="37763-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="37763-114">Abra a solução `ClassLibraryProjects` que você criou no artigo [criar uma biblioteca de .net Standard no Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="37763-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="37763-115">Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.</span><span class="sxs-lookup"><span data-stu-id="37763-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="37763-116">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="37763-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="37763-117">Na página **Adicionar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="37763-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="37763-118">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="37763-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="37763-119">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="37763-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="37763-120">Na página **configurar seu novo projeto** , insira **Showcase** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="37763-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="37763-121">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="37763-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="37763-122">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="37763-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu de contexto do projeto do Visual Studio para definir o projeto de inicialização](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="37763-124">Inicialmente, seu projeto não tem acesso à sua biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="37763-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="37763-125">Para permitir que ele chame métodos na biblioteca de classes, você cria uma referência à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="37763-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="37763-126">No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Dependências** do projeto `ShowCase` e selecione **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="37763-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Adicionar menu de contexto de referência no Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="37763-128">Na caixa de diálogo **Gerenciador de Referências**, selecione **StringLibrary**, seu projeto de biblioteca de classes, e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="37763-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Caixa de diálogo Gerenciador de referências com StringLibrary selecionado](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="37763-130">Na janela de código do arquivo *Program.cs* ou *Program. vb* , substitua todo o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="37763-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="37763-131">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="37763-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="37763-132">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="37763-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="37763-133">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="37763-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="37763-134">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="37763-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="37763-135">Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="37763-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="37763-136">Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="37763-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="37763-137">Compile e execute o programa selecionando a seta verde no botão **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="37763-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Barra de ferramentas do projeto do Visual Studio mostrando botão de depuração](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="37763-139">Você pode depurar e publicar o aplicativo que usa essa biblioteca seguindo as etapas em [depurar seu C# ou Visual Basic aplicativo .NET Core Olá, mundo usando o Visual Studio](debugging-with-visual-studio.md) e [publicar seu aplicativo do .NET Core Olá, mundo com o Visual Studio](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="37763-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="37763-140">Criar um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="37763-140">Create a NuGet package</span></span>

<span data-ttu-id="37763-141">Você pode fazer com que sua biblioteca de classes esteja amplamente disponível ao publicá-la como um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="37763-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="37763-142">O Visual Studio não dá suporte à criação de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="37763-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="37763-143">Para criar um, você precisa usar os comandos CLI do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="37763-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="37763-144">Abra uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="37763-144">Open a console window.</span></span>

   <span data-ttu-id="37763-145">Por exemplo, digite **prompt de comando** na caixa de pesquisa na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="37763-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="37763-146">Selecione o **prompt de comando** aplicativo da área de trabalho ou pressione **Enter** se ele já estiver selecionado nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="37763-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="37763-147">Navegue até o diretório do projeto da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="37763-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="37763-148">O diretório contém o código-fonte e um arquivo de projeto, *StringLibrary. csproj* ou *StringLibrary. vbproj*.</span><span class="sxs-lookup"><span data-stu-id="37763-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="37763-149">Execute o comando [dotnet Pack](../tools/dotnet-pack.md) para gerar um pacote com uma extensão *. nupkg* :</span><span class="sxs-lookup"><span data-stu-id="37763-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="37763-150">Se o diretório que contém *dotnet.exe* não está no seu PATH, você pode encontrar seu local digitando `where dotnet.exe` na janela do console.</span><span class="sxs-lookup"><span data-stu-id="37763-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="37763-151">Para obter mais informações sobre a criação de pacotes do NuGet, consulte [Como criar um pacote do NuGet com ferramentas de plataforma cruzada](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="37763-151">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
