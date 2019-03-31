---
title: Portar um aplicativo do Windows Forms para o .NET Core 3.0
description: Ensina como portar um aplicativo do Windows Forms do .NET Framework para .NET Core 3.0 para Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 3a50b5f085aee4afc2f388aeac8a4f68823b92c7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675855"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="223f2-103">Como: Portar um aplicativo da área de trabalho do Windows Forms para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="223f2-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="223f2-104">Este artigo descreve como portar seu aplicativo da área de trabalho baseado no Windows Forms do .NET Framework para o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="223f2-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="223f2-105">O SDK do .NET Core 3.0 inclui suporte para aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="223f2-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="223f2-106">O Windows Forms ainda é uma estrutura somente do Windows e só é executado nessa plataforma.</span><span class="sxs-lookup"><span data-stu-id="223f2-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="223f2-107">Este exemplo usa a CLI do .SDK do .NET Core para criar e gerenciar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="223f2-108">Neste artigo, vários nomes são usados a fim de identificar os tipos de arquivos usados para migração.</span><span class="sxs-lookup"><span data-stu-id="223f2-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="223f2-109">Ao migrar seu projeto, seus arquivos receberão nomes diferentes; portanto, relacione-os mentalmente aos listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="223f2-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="223f2-110">Arquivo</span><span class="sxs-lookup"><span data-stu-id="223f2-110">File</span></span> | <span data-ttu-id="223f2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="223f2-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="223f2-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="223f2-112">**MyApps.sln**</span></span> | <span data-ttu-id="223f2-113">O nome do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="223f2-113">The name of the solution file.</span></span> |
| <span data-ttu-id="223f2-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="223f2-114">**MyForms.csproj**</span></span> | <span data-ttu-id="223f2-115">O nome do projeto do Windows Forms do .NET Framework a ser portado.</span><span class="sxs-lookup"><span data-stu-id="223f2-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="223f2-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="223f2-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="223f2-117">O nome do novo projeto do .NET Core criado.</span><span class="sxs-lookup"><span data-stu-id="223f2-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="223f2-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="223f2-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="223f2-119">O arquivo executável do aplicativo do Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="223f2-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="223f2-120">Prerequisites</span></span>

- <span data-ttu-id="223f2-121">[Visual Studio de 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) para qualquer trabalho de designer que você queira fazer.</span><span class="sxs-lookup"><span data-stu-id="223f2-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="223f2-122">Instale as seguintes cargas de trabalho do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="223f2-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="223f2-123">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="223f2-123">.NET desktop development</span></span>
  - <span data-ttu-id="223f2-124">Desenvolvimento de plataforma cruzada do .NET</span><span class="sxs-lookup"><span data-stu-id="223f2-124">.NET cross-platform development</span></span>

- <span data-ttu-id="223f2-125">Um projeto do Windows Forms em funcionamento em uma solução compilada e executada sem problemas.</span><span class="sxs-lookup"><span data-stu-id="223f2-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="223f2-126">Seu projeto deve ser codificado em C#.</span><span class="sxs-lookup"><span data-stu-id="223f2-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="223f2-127">Instale a versão prévia mais recente do [.NET Core 3.0](https://aka.ms/netcore3download).</span><span class="sxs-lookup"><span data-stu-id="223f2-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>


>[!NOTE]
><span data-ttu-id="223f2-128">O **Visual Studio 2017** não oferece suporte a projetos do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="223f2-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="223f2-129">A **versão prévia/RC do Visual Studio 2019** oferece suporte a projetos do .NET Core 3.0, mas ainda não dá suporte ao designer visual para projetos do Windows Forms do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="223f2-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="223f2-130">Para usar o designer visual, você deve ter um projeto do Windows Forms do .NET em sua solução que compartilhe os arquivos de formulários com o projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="223f2-131">Considerações</span><span class="sxs-lookup"><span data-stu-id="223f2-131">Consider</span></span>

<span data-ttu-id="223f2-132">Ao portar um aplicativo do Windows Forms do .NET Framework, há alguns pontos a ser considerados.</span><span class="sxs-lookup"><span data-stu-id="223f2-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="223f2-133">Verifique se o seu aplicativo é um bom candidato para a migração.</span><span class="sxs-lookup"><span data-stu-id="223f2-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="223f2-134">Use o [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para determinar se o seu projeto será migrado para o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="223f2-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="223f2-135">Se seu projeto tiver problemas com o .NET Core 3.0, o analisador ajudará a identificar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="223f2-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="223f2-136">Você está usando uma versão diferente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="223f2-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="223f2-137">Quando a versão prévia 1 do .NET Core 3.0 foi lançada, o Windows Forms passou a ser um software livre no GitHub.</span><span class="sxs-lookup"><span data-stu-id="223f2-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="223f2-138">O código para o Windows Forms do .NET Core é uma bifurcação do código base do Windows Forms do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="223f2-139">É possível que haja algumas diferenças e seu aplicativo não seja portado.</span><span class="sxs-lookup"><span data-stu-id="223f2-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="223f2-140">O [Pacote de Compatibilidade do Windows][compat-pack] pode ajudar você na migração.</span><span class="sxs-lookup"><span data-stu-id="223f2-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="223f2-141">Algumas APIs disponíveis no .NET Framework não estão disponíveis no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="223f2-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="223f2-142">O [Pacote de Compatibilidade do Windows][compat-pack] adiciona muitas dessas APIs e podem ajudar seu aplicativo do Windows Forms a se tornar compatível com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="223f2-143">Atualize os pacotes do NuGet usados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="223f2-144">É sempre uma boa prática usar as versões mais recentes dos pacotes do NuGet antes de qualquer migração.</span><span class="sxs-lookup"><span data-stu-id="223f2-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="223f2-145">Se seu aplicativo faz referência a pacotes do NuGet, atualize-os para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="223f2-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="223f2-146">Certifique-se de que seu aplicativo foi compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="223f2-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="223f2-147">Após a atualização, se houver erros de pacote, faça downgrade do pacote para a versão mais recente que não interrompa seu código.</span><span class="sxs-lookup"><span data-stu-id="223f2-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="223f2-148">A versão prévia/RC do Visual Studio 2019 ainda não oferece suporte ao Designer de Formulários do .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="223f2-148">Visual Studio 2019 Preview/RC doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="223f2-149">No momento, você precisa manter seu arquivo de projeto existente do Windows Forms do .NET Framework caso queira usar o Designer de Formulários do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="223f2-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="223f2-150">Criar um novo projeto de SDK</span><span class="sxs-lookup"><span data-stu-id="223f2-150">Create a new SDK project</span></span>

<span data-ttu-id="223f2-151">O novo projeto do .NET Core 3.0 que você criar deverá ficar em um diretório diferente do seu projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="223f2-152">Se os dois estiverem no mesmo diretório, poderão surgir conflitos com os arquivos gerados no diretório **obj**.</span><span class="sxs-lookup"><span data-stu-id="223f2-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="223f2-153">Neste exemplo, vamos criar um diretório chamado **MyFormsAppCore** no diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="223f2-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="223f2-154">Em seguida, crie o projeto **MyFormsCore.csproj** no diretório **MyFormsAppCore**.</span><span class="sxs-lookup"><span data-stu-id="223f2-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="223f2-155">Você pode criar esse arquivo manualmente usando o editor de texto de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="223f2-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="223f2-156">Cole o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="223f2-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="223f2-157">Se não quiser criar manualmente o arquivo de projeto, use o Visual Studio ou o SDK do .NET Core para gerar o projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="223f2-158">No entanto, você deverá excluir todos os outros arquivos gerados pelo modelo de projeto, exceto o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="223f2-159">Para usar o SDK, execute o seguinte comando a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="223f2-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="223f2-160">Depois que criar o **MyFormsCore.csproj**, sua estrutura de diretórios deverá ser semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="223f2-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="223f2-161">É recomendável adicionar o projeto **MyFormsCore.csproj** a **MyApps.sln** com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="223f2-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="223f2-162">Corrigir a geração de informações do assembly</span><span class="sxs-lookup"><span data-stu-id="223f2-162">Fix assembly info generation</span></span>

<span data-ttu-id="223f2-163">Projetos do Windows Forms criados com o .NET Framework incluem um arquivo `AssemblyInfo.cs`, que contém os atributos de assembly, como a versão do assembly a ser gerado.</span><span class="sxs-lookup"><span data-stu-id="223f2-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="223f2-164">Projetos no estilo SDK geram automaticamente essas informações com base no arquivo de projeto do SDK.</span><span class="sxs-lookup"><span data-stu-id="223f2-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="223f2-165">Ter os dois tipos de "informações do assembly" cria um conflito.</span><span class="sxs-lookup"><span data-stu-id="223f2-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="223f2-166">Para resolver esse problema, desabilite a geração automática, o que força o projeto a usar o arquivo `AssemblyInfo.cs` existente.</span><span class="sxs-lookup"><span data-stu-id="223f2-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="223f2-167">Há três configurações para adicionar ao nó `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="223f2-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="223f2-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="223f2-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="223f2-169">Quando você define essa propriedade como `false`, ela não gera os atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="223f2-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="223f2-170">Isso evita conflito com o arquivo `AssemblyInfo.cs` existente do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="223f2-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="223f2-171">**AssemblyName**\\</span></span>
<span data-ttu-id="223f2-172">O valor dessa propriedade é a saída binária criada na compilação.</span><span class="sxs-lookup"><span data-stu-id="223f2-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="223f2-173">O nome não precisa de uma extensão adicionada a ele.</span><span class="sxs-lookup"><span data-stu-id="223f2-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="223f2-174">Por exemplo, o uso de `MyCoreApp` produz `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="223f2-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="223f2-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="223f2-175">**RootNamespace**\\</span></span>
<span data-ttu-id="223f2-176">O namespace padrão usado pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-176">The default namespace used by your project.</span></span> <span data-ttu-id="223f2-177">Ele deve corresponder ao namespace padrão do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="223f2-178">Adicione estes três elementos ao nó `<PropertyGroup>` no arquivo `MyFormsCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="223f2-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="223f2-179">Adicione o código-fonte</span><span class="sxs-lookup"><span data-stu-id="223f2-179">Add source code</span></span>

<span data-ttu-id="223f2-180">No momento, o projeto **MyFormsCore.csproj** não compila qualquer código.</span><span class="sxs-lookup"><span data-stu-id="223f2-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="223f2-181">Por padrão, os projetos do .NET Core incluem automaticamente todo o código-fonte do diretório atual e de todos os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="223f2-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="223f2-182">Configure o projeto para incluir código do projeto do .NET Framework usando um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="223f2-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="223f2-183">Se o seu projeto do .NET Framework tiver usado arquivos **.resx** para ícones e recursos dos formulários, você precisará incluí-los também.</span><span class="sxs-lookup"><span data-stu-id="223f2-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="223f2-184">Adicione o seguinte nó `<ItemGroup>` ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="223f2-185">Cada instrução inclui o padrão glob de arquivo que inclui os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="223f2-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="223f2-186">Como alternativa, você pode criar uma entrada `<Compile>` ou `<EmbeddedResource>` para cada arquivo em seu projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="223f2-187">Adicionar pacotes do NuGet</span><span class="sxs-lookup"><span data-stu-id="223f2-187">Add NuGet packages</span></span>

<span data-ttu-id="223f2-188">Adicione cada pacote do NuGet referenciado pelo projeto do .NET Framework ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="223f2-189">Muito provavelmente, seu aplicativo do Windows Forms do .NET Framework tem um arquivo **packages.config** que contém uma lista de todos os pacotes do NuGet referenciados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="223f2-190">É possível examinar essa lista para determinar quais pacotes do NuGet serão adicionados ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="223f2-191">Por exemplo, se o projeto do .NET Framework tiver referenciado os pacotes do NuGet `MetroFramework`, `MetroFramework.Design` e `MetroFramework.Fonts`, adicione cada um deles ao projeto com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="223f2-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="223f2-192">Os comandos anteriores adicionariam as seguintes referências do NuGet ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="223f2-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="223f2-193">Portar bibliotecas de controles</span><span class="sxs-lookup"><span data-stu-id="223f2-193">Port control libraries</span></span>

<span data-ttu-id="223f2-194">Se você tem um projeto de biblioteca de controles do Windows Forms para portar, as instruções são iguais às da portabilidade de um projeto de aplicativo do Windows Forms do .NET Framework, com exceção de algumas configurações.</span><span class="sxs-lookup"><span data-stu-id="223f2-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="223f2-195">E, em vez de compilar em um arquivo executável, você compila em uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="223f2-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="223f2-196">A diferença entre o projeto executável e o projeto de biblioteca, além dos caminhos para os globs de arquivo que incluem seu código-fonte, é mínima.</span><span class="sxs-lookup"><span data-stu-id="223f2-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="223f2-197">Usando o exemplo da etapa anterior, vamos expandir os projetos e arquivos com que estamos trabalhando.</span><span class="sxs-lookup"><span data-stu-id="223f2-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="223f2-198">Arquivo</span><span class="sxs-lookup"><span data-stu-id="223f2-198">File</span></span> | <span data-ttu-id="223f2-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="223f2-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="223f2-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="223f2-200">**MyApps.sln**</span></span> | <span data-ttu-id="223f2-201">O nome do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="223f2-201">The name of the solution file.</span></span> |
| <span data-ttu-id="223f2-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="223f2-202">**MyControls.csproj**</span></span> | <span data-ttu-id="223f2-203">O nome do projeto de controles do Windows Forms do .NET Framework a ser portado.</span><span class="sxs-lookup"><span data-stu-id="223f2-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="223f2-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="223f2-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="223f2-205">O nome do novo projeto de biblioteca do .NET Core criado.</span><span class="sxs-lookup"><span data-stu-id="223f2-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="223f2-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="223f2-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="223f2-207">A biblioteca de controles do Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-207">The .NET Core Windows Forms Controls library.</span></span> |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

<span data-ttu-id="223f2-208">Considere as diferenças entre o projeto `MyControlsCore.csproj` e o projeto `MyFormsCore.csproj` criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="223f2-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

<span data-ttu-id="223f2-209">Veja um exemplo de como o arquivo de projeto de biblioteca de controles do Windows Forms do .NET Core ficaria:</span><span class="sxs-lookup"><span data-stu-id="223f2-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

<span data-ttu-id="223f2-210">Como você pode ver, o nó `<OutputType>` foi removido, o que padroniza o compilador para produzir uma biblioteca em vez de um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="223f2-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="223f2-211">O `<AssemblyName>` e `<RootNamespace>` foram alterados.</span><span class="sxs-lookup"><span data-stu-id="223f2-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="223f2-212">Especificamente, o `<RootNamespace>` deve corresponder ao namespace da biblioteca de controles do Windows Forms que está passando pela portabilidade.</span><span class="sxs-lookup"><span data-stu-id="223f2-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="223f2-213">Por fim, os nós `<Compile>` e `<EmbeddedResource>` foram ajustados para apontar para a pasta da biblioteca de controles de Windows Forms que você está portando.</span><span class="sxs-lookup"><span data-stu-id="223f2-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="223f2-214">Em seguida, no projeto principal do .NET Core **MyFormsCore.csproj**, inclua referência à nova biblioteca de controles do Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="223f2-215">Adicione uma referência com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="223f2-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="223f2-216">O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="223f2-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="223f2-217">Problemas na compilação</span><span class="sxs-lookup"><span data-stu-id="223f2-217">Problems compiling</span></span>

<span data-ttu-id="223f2-218">Se você tiver problemas ao compilar seus projetos, talvez esteja usando algumas APIs que são somente para Windows e que estão disponíveis no .NET Framework, mas não no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="223f2-219">Experimente adicionar o pacote do NuGet do [Pacote de Compatibilidade do Windows][compat-pack] ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="223f2-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="223f2-220">Esse pacote só é executado no Windows e adiciona cerca de 20.000 APIs do Windows aos projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="223f2-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="223f2-221">O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="223f2-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="223f2-222">Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="223f2-222">Windows Forms Designer</span></span>

<span data-ttu-id="223f2-223">Conforme detalhado neste artigo, a versão prévia/RC do Visual Studio 2019 oferece suporte ao Designer de Formulários apenas em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-223">As detailed in this article, Visual Studio 2019 Preview/RC only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="223f2-224">Ao criar um projeto do .NET Core lado a lado, você pode testar seu projeto com o .NET Core enquanto usa o projeto do .NET Framework para criar formulários.</span><span class="sxs-lookup"><span data-stu-id="223f2-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="223f2-225">Seu arquivo de solução inclui projetos do .NET Framework e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="223f2-226">Adicione e crie seus formulários e controles no projeto do .NET Framework e, com base nos padrões glob de arquivos que adicionamos aos projetos do .NET Core, todos os arquivos novos ou alterados serão incluídos automaticamente nos projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="223f2-227">Depois que o Visual Studio 2019 oferecer suporte ao Designer de Formulários do Windows, você poderá copiar/colar o conteúdo do arquivo de projeto do .NET Core no arquivo de projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="223f2-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="223f2-228">Depois, poderá excluir os padrões glob de arquivo adicionados com os itens `<Source>` e `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="223f2-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="223f2-229">Corrija os caminhos de qualquer referência de projeto usada pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="223f2-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="223f2-230">Isso atualiza efetivamente o projeto do .NET Framework para um projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="223f2-231">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="223f2-231">Next steps</span></span>

* <span data-ttu-id="223f2-232">Leia mais sobre o [Pacote de Compatibilidade do Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="223f2-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="223f2-233">Assista a um [vídeo sobre como portar](https://www.youtube.com/watch?v=upVQEUc_KwU) seu projeto do Windows Forms do .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="223f2-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
