---
title: "Compilar uma solução completa do .NET Core no Windows usando o Visual Studio 2017"
description: "Saiba como compilar uma solução completa do .NET Core no Visual Studio 2017 no Windows."
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6b164198f5fbbae5ebc6164fc281dd7de8172b70
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="a00c2-104">Compilar uma solução completa do .NET Core no Windows usando o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a00c2-104">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="a00c2-105">O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para desenvolver aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a00c2-105">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="a00c2-106">Os procedimentos deste documento descrevem as etapas necessárias para criar uma solução típica do .NET Core que inclui bibliotecas reutilizáveis, testes e o uso de bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="a00c2-106">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a00c2-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="a00c2-107">Prerequisites</span></span>

<span data-ttu-id="a00c2-108">Siga as instruções na [nossa página de pré-requisitos](../windows-prerequisites.md) para atualizar seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="a00c2-108">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="a00c2-109">Uma solução que usa apenas projetos .NET Core</span><span class="sxs-lookup"><span data-stu-id="a00c2-109">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="a00c2-110">Escrevendo a biblioteca</span><span class="sxs-lookup"><span data-stu-id="a00c2-110">Writing the library</span></span>

1. <span data-ttu-id="a00c2-111">No Visual Studio, escolha **Arquivo**, **Novo** e **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-111">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="a00c2-112">Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#**, escolha o nó **.NET Core** e escolha **Biblioteca de Classes (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-112">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Core** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="a00c2-113">Nomeie o projeto como “Biblioteca” e a solução como “Dourada”.</span><span class="sxs-lookup"><span data-stu-id="a00c2-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="a00c2-114">Deixe **Criar diretório para a solução** marcado.</span><span class="sxs-lookup"><span data-stu-id="a00c2-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="a00c2-115">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-115">Click **OK**.</span></span>

3. <span data-ttu-id="a00c2-116">No Gerenciador de Soluções, abra o menu de contexto para o nó **Dependências** e escolha **Gerenciar Pacotes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="a00c2-117">Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab.</span></span> <span data-ttu-id="a00c2-118">Procure por **Newtonsoft.json**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-118">Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="a00c2-119">Clique em **Instalar** e aceite o contrato de licença.</span><span class="sxs-lookup"><span data-stu-id="a00c2-119">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="a00c2-120">O pacote deve aparecer sob **Dependências/NuGet** e ser restaurado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a00c2-120">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="a00c2-121">Renomeie o arquivo `Class1.cs` para `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="a00c2-121">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="a00c2-122">Aceite a renomeação da classe.</span><span class="sxs-lookup"><span data-stu-id="a00c2-122">Accept the rename of the class.</span></span> <span data-ttu-id="a00c2-123">Adicionar um método: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="a00c2-123">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="a00c2-124">No menu **Compilar**, escolha **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-124">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="a00c2-125">A solução deverá ser compilada sem erros.</span><span class="sxs-lookup"><span data-stu-id="a00c2-125">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="a00c2-126">Escrevendo o projeto de teste</span><span class="sxs-lookup"><span data-stu-id="a00c2-126">Writing the test project</span></span>

1. <span data-ttu-id="a00c2-127">No Gerenciador de Soluções, abra o menu de contexto do nó **Solução** e escolha **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-127">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="a00c2-128">Na caixa de diálogo **Novo Projeto**, em **Visual C# / .NET Core**, escolha **Projeto de Teste de Unidade (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-128">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="a00c2-129">Nomeie-o como "TestLibrary" e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="a00c2-129">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="a00c2-130">No projeto **TestLibrary**, abra o menu de contexto do nó **Dependências** e escolha **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-130">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="a00c2-131">Clique em **Projetos**, verifique o projeto de Biblioteca e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="a00c2-131">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="a00c2-132">Isso adiciona uma referência à biblioteca do projeto de teste.</span><span class="sxs-lookup"><span data-stu-id="a00c2-132">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="a00c2-133">Renomeie o arquivo `UnitTest1.cs` para `LibraryTests.cs` e aceite a renomeação de classe.</span><span class="sxs-lookup"><span data-stu-id="a00c2-133">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="a00c2-134">Adicione `using Library;` à parte superior do arquivo e substitua o método `TestMethod1` com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a00c2-134">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="a00c2-135">Agora, você poderá criar a solução.</span><span class="sxs-lookup"><span data-stu-id="a00c2-135">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="a00c2-136">No menu **Teste**, escolha **Windows**, **Gerenciador de Testes** para obter a janela Gerenciador de Testes na área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a00c2-136">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="a00c2-137">Depois de alguns segundos, o teste `ThingGetsObjectValFromNumber` deve aparecer no gerenciador de testes.</span><span class="sxs-lookup"><span data-stu-id="a00c2-137">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="a00c2-138">Escolha **Executar Todos**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-138">Choose **Run All**.</span></span>
   
   <span data-ttu-id="a00c2-139">O teste deve ser aprovado.</span><span class="sxs-lookup"><span data-stu-id="a00c2-139">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="a00c2-140">Escrevendo o aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="a00c2-140">Writing the console app</span></span>

1. <span data-ttu-id="a00c2-141">No Gerenciador de Soluções, abra o menu de contexto para a solução e adicione um novo projeto de **Aplicativo de Console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-141">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="a00c2-142">Nomeie como "Aplicativo".</span><span class="sxs-lookup"><span data-stu-id="a00c2-142">Name it "App".</span></span>

2. <span data-ttu-id="a00c2-143">No projeto **Aplicativo**, abra o menu de contexto do nó **Dependências** e escolha **Adicionar**, **Referência**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-143">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="a00c2-144">Na caixa de diálogo **Gerenciador de Referências**, marque **Biblioteca** em **Projetos**, no nó **Solução** e clique em **OK**</span><span class="sxs-lookup"><span data-stu-id="a00c2-144">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="a00c2-145">Abra o menu de contexto do nó **Aplicativo** e escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="a00c2-145">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="a00c2-146">Isso garante que pressionar F5 ou CTRL+F5 iniciará o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a00c2-146">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="a00c2-147">Abra o arquivo `Program.cs`, adicione uma diretiva `using Library;` à parte superior do arquivo e adicione `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` ao método `Main`.</span><span class="sxs-lookup"><span data-stu-id="a00c2-147">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="a00c2-148">Defina um ponto de interrupção após a linha que você acabou de adicionar.</span><span class="sxs-lookup"><span data-stu-id="a00c2-148">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="a00c2-149">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a00c2-149">Press F5 to run the application..</span></span>

   <span data-ttu-id="a00c2-150">O aplicativo deve ser compilado sem erros e deve atingir o ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="a00c2-150">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="a00c2-151">Você também deve ser capaz de verificar se o aplicativo gera a saída "A resposta é 42".</span><span class="sxs-lookup"><span data-stu-id="a00c2-151">You should also be able to check that the application output "The answer is 42.".</span></span>

