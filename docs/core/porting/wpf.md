---
title: Compatibilizar um aplicativo WPF para o .NET Core 3.0
description: Ensina como compatibilizar um aplicativo do Windows Presentation Foundation do .NET Framework para o .NET Core 3.0 para Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 5c7e3aca0a473abb831693244d1b194985f2ef7f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342200"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="51db8-103">Como: Compatibilizar um aplicativo da área de trabalho do WPF para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="51db8-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="51db8-104">Este artigo descreve como compatibilizar seu aplicativo da área de trabalho baseado no WPF (Windows Presentation Foundation) do .NET Framework para o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db8-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="51db8-105">O SDK do .NET Core 3.0 inclui suporte para aplicativos WPF.</span><span class="sxs-lookup"><span data-stu-id="51db8-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="51db8-106">O WPF ainda é uma estrutura somente do Windows e só é executado nessa plataforma.</span><span class="sxs-lookup"><span data-stu-id="51db8-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="51db8-107">Este exemplo usa a CLI do .SDK do .NET Core para criar e gerenciar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="51db8-108">Neste artigo, vários nomes são usados a fim de identificar os tipos de arquivos usados para migração.</span><span class="sxs-lookup"><span data-stu-id="51db8-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="51db8-109">Ao migrar seu projeto, seus arquivos receberão nomes diferentes; portanto, relacione-os mentalmente aos listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="51db8-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="51db8-110">Arquivo</span><span class="sxs-lookup"><span data-stu-id="51db8-110">File</span></span> | <span data-ttu-id="51db8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="51db8-111">Description</span></span> |
| ---- | ----------- |
| **<span data-ttu-id="51db8-112">MyApps.sln</span><span class="sxs-lookup"><span data-stu-id="51db8-112">MyApps.sln</span></span>** | <span data-ttu-id="51db8-113">O nome do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="51db8-113">The name of the solution file.</span></span> |
| **<span data-ttu-id="51db8-114">MyWPF.csproj</span><span class="sxs-lookup"><span data-stu-id="51db8-114">MyWPF.csproj</span></span>** | <span data-ttu-id="51db8-115">O nome do projeto do WPF do .NET Framework a ser compatibilizado.</span><span class="sxs-lookup"><span data-stu-id="51db8-115">The name of the .NET Framework WPF project to port.</span></span> |
| **<span data-ttu-id="51db8-116">MyWPFCore.csproj</span><span class="sxs-lookup"><span data-stu-id="51db8-116">MyWPFCore.csproj</span></span>** | <span data-ttu-id="51db8-117">O nome do novo projeto do .NET Core criado.</span><span class="sxs-lookup"><span data-stu-id="51db8-117">The name of the new .NET Core project you create.</span></span> |
| **<span data-ttu-id="51db8-118">MyAppCore.exe</span><span class="sxs-lookup"><span data-stu-id="51db8-118">MyAppCore.exe</span></span>** | <span data-ttu-id="51db8-119">O executável do aplicativo WPF do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="51db8-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="51db8-120">Prerequisites</span></span>

- <span data-ttu-id="51db8-121">[Visual Studio de 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para qualquer trabalho de designer que você queira fazer.</span><span class="sxs-lookup"><span data-stu-id="51db8-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="51db8-122">Instale as seguintes cargas de trabalho do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="51db8-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="51db8-123">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="51db8-123">.NET desktop development</span></span>
  - <span data-ttu-id="51db8-124">Desenvolvimento de plataforma cruzada do .NET</span><span class="sxs-lookup"><span data-stu-id="51db8-124">.NET cross-platform development</span></span>

- <span data-ttu-id="51db8-125">Um projeto do WPF funcional em uma solução que é criada e executada sem problemas.</span><span class="sxs-lookup"><span data-stu-id="51db8-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="51db8-126">Seu projeto deve ser codificado em C#.</span><span class="sxs-lookup"><span data-stu-id="51db8-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="51db8-127">Instale a versão prévia mais recente do [.NET Core 3.0](https://aka.ms/netcore3download).</span><span class="sxs-lookup"><span data-stu-id="51db8-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="51db8-128">O **Visual Studio 2017** não oferece suporte a projetos do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db8-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="51db8-129">O **Visual Studio 2019** dá suporte a projetos do .NET Core 3.0, mas ainda não dá suporte ao designer visual para projetos do WPF do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db8-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="51db8-130">Para usar o designer visual, é necessário ter um projeto do WPF do .NET em sua solução que compartilhe os arquivos com o projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="51db8-131">Considerações</span><span class="sxs-lookup"><span data-stu-id="51db8-131">Consider</span></span>

<span data-ttu-id="51db8-132">Ao compatibilizar um aplicativo do WPF do .NET Framework, há alguns pontos a serem considerados.</span><span class="sxs-lookup"><span data-stu-id="51db8-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="51db8-133">Verifique se o seu aplicativo é um bom candidato para a migração.</span><span class="sxs-lookup"><span data-stu-id="51db8-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="51db8-134">Use o [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para determinar se o seu projeto será migrado para o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db8-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="51db8-135">Se seu projeto tiver problemas com o .NET Core 3.0, o analisador ajudará a identificar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="51db8-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="51db8-136">Você está usando uma versão diferente do WPF.</span><span class="sxs-lookup"><span data-stu-id="51db8-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="51db8-137">Quando o .NET Core 3.0 Versão Prévia 1 foi lançado, o WPF passou a ser um software livre no GitHub.</span><span class="sxs-lookup"><span data-stu-id="51db8-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="51db8-138">O código do WPF do .NET Core é um fork da base de código do WPF do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="51db8-139">É possível que haja algumas diferenças e seu aplicativo não seja portado.</span><span class="sxs-lookup"><span data-stu-id="51db8-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="51db8-140">O [Pacote de Compatibilidade do Windows][compat-pack] pode ajudar você na migração.</span><span class="sxs-lookup"><span data-stu-id="51db8-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="51db8-141">Algumas APIs disponíveis no .NET Framework não estão disponíveis no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="51db8-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="51db8-142">O [Pacote de Compatibilidade do Windows][compat-pack] adiciona muitas dessas APIs e pode ajudar seu aplicativo do WPF a se tornar compatível com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="51db8-143">Atualize os pacotes do NuGet usados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="51db8-144">É sempre uma boa prática usar as versões mais recentes dos pacotes do NuGet antes de qualquer migração.</span><span class="sxs-lookup"><span data-stu-id="51db8-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="51db8-145">Se seu aplicativo faz referência a pacotes do NuGet, atualize-os para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="51db8-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="51db8-146">Certifique-se de que seu aplicativo foi compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="51db8-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="51db8-147">Após a atualização, se houver erros de pacote, faça downgrade do pacote para a versão mais recente que não interrompa seu código.</span><span class="sxs-lookup"><span data-stu-id="51db8-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="51db8-148">O Visual Studio 2019 ainda não dá suporte ao Designer do WPF do .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="51db8-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="51db8-149">No momento, você precisa manter seu arquivo de projeto existente do WPF do .NET Framework caso queira usar o Designer do WPF no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51db8-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="51db8-150">Criar um novo projeto de SDK</span><span class="sxs-lookup"><span data-stu-id="51db8-150">Create a new SDK project</span></span>

<span data-ttu-id="51db8-151">O novo projeto do .NET Core 3.0 que você criar deverá ficar em um diretório diferente do seu projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="51db8-152">Se os dois estiverem no mesmo diretório, poderão surgir conflitos com os arquivos gerados no diretório **obj**.</span><span class="sxs-lookup"><span data-stu-id="51db8-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="51db8-153">Neste exemplo, você criará um diretório chamado **MyWPFAppCore** no diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="51db8-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="51db8-154">Em seguida, você criará o projeto **MyWPFCore.csproj** no diretório **MyWPFAppCore**.</span><span class="sxs-lookup"><span data-stu-id="51db8-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="51db8-155">Você pode criar esse arquivo manualmente usando o editor de texto de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="51db8-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="51db8-156">Cole o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="51db8-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="51db8-157">Se não quiser criar manualmente o arquivo de projeto, use o Visual Studio ou o SDK do .NET Core para gerar o projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="51db8-158">No entanto, você deverá excluir todos os outros arquivos gerados pelo modelo de projeto, exceto o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="51db8-159">Para usar o SDK, execute o seguinte comando a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="51db8-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="51db8-160">Depois que você criar o **MyWPFCore.csproj**, a estrutura de diretórios deverá ser semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="51db8-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="51db8-161">O ideal é adicionar o projeto **MyWPFCore.csproj** a **MyApps.sln** com o Visual Studio ou a CLI do .NET Core no diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="51db8-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="51db8-162">Corrigir a geração de informações do assembly</span><span class="sxs-lookup"><span data-stu-id="51db8-162">Fix assembly info generation</span></span>

<span data-ttu-id="51db8-163">Os projetos do Windows Presentation Foundation criados com o .NET Framework incluem um arquivo `AssemblyInfo.cs`, que contém atributos de assembly, como a versão do assembly a ser gerada.</span><span class="sxs-lookup"><span data-stu-id="51db8-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="51db8-164">Projetos no estilo SDK geram automaticamente essas informações com base no arquivo de projeto do SDK.</span><span class="sxs-lookup"><span data-stu-id="51db8-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="51db8-165">Ter os dois tipos de "informações do assembly" cria um conflito.</span><span class="sxs-lookup"><span data-stu-id="51db8-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="51db8-166">Para resolver esse problema, desabilite a geração automática, o que força o projeto a usar o arquivo `AssemblyInfo.cs` existente.</span><span class="sxs-lookup"><span data-stu-id="51db8-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="51db8-167">Há três configurações para adicionar ao nó `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="51db8-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- **<span data-ttu-id="51db8-168">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="51db8-168">GenerateAssemblyInfo</span></span>**\
<span data-ttu-id="51db8-169">Quando você define essa propriedade como `false`, ela não gera os atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="51db8-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="51db8-170">Isso evita conflito com o arquivo `AssemblyInfo.cs` existente do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- **<span data-ttu-id="51db8-171">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="51db8-171">AssemblyName</span></span>**\
<span data-ttu-id="51db8-172">O valor dessa propriedade é a saída binária criada na compilação.</span><span class="sxs-lookup"><span data-stu-id="51db8-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="51db8-173">O nome não precisa de uma extensão adicionada a ele.</span><span class="sxs-lookup"><span data-stu-id="51db8-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="51db8-174">Por exemplo, o uso de `MyCoreApp` produz `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="51db8-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- **<span data-ttu-id="51db8-175">RootNamespace</span><span class="sxs-lookup"><span data-stu-id="51db8-175">RootNamespace</span></span>**\
<span data-ttu-id="51db8-176">O namespace padrão usado pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-176">The default namespace used by your project.</span></span> <span data-ttu-id="51db8-177">Ele deve corresponder ao namespace padrão do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="51db8-178">Adicione estes três elementos ao nó `<PropertyGroup>` no arquivo `MyWPFCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="51db8-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="51db8-179">Adicione o código-fonte</span><span class="sxs-lookup"><span data-stu-id="51db8-179">Add source code</span></span>
<span data-ttu-id="51db8-180">No momento, o projeto **MyWPFCore.csproj** não compila qualquer código.</span><span class="sxs-lookup"><span data-stu-id="51db8-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="51db8-181">Por padrão, os projetos do .NET Core incluem automaticamente todo o código-fonte do diretório atual e de todos os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="51db8-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="51db8-182">Configure o projeto para incluir código do projeto do .NET Framework usando um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="51db8-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="51db8-183">Se o projeto do .NET Framework usar arquivos **.resx** para ícones e recursos para as janelas e os controles, você também precisará incluí-los.</span><span class="sxs-lookup"><span data-stu-id="51db8-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="51db8-184">O primeiro nó `<ItemGroup>` que você precisa adicionar ao projeto inclui o arquivo **App.xaml** que representa a configuração de inicialização e os recursos usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51db8-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="51db8-185">O arquivo **App.xaml** também tem um arquivo **App.xaml.cs** complementar, mas ele será incluído automaticamente em outro `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="51db8-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="51db8-186">Depois, adicione o nó `<ItemGroup>` a seguir ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="51db8-187">Cada instrução inclui o padrão glob de arquivo que inclui os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="51db8-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="51db8-188">Ele inclui o código-fonte do projeto, arquivos de configurações e recursos.</span><span class="sxs-lookup"><span data-stu-id="51db8-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="51db8-189">O diretório **obj** é excluído explicitamente.</span><span class="sxs-lookup"><span data-stu-id="51db8-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="51db8-190">Em seguida, inclua outro nó `<ItemGroup>` que contém uma entrada `<Page>` para cada arquivo **xaml** do projeto, exceto o arquivo **App.xaml**.</span><span class="sxs-lookup"><span data-stu-id="51db8-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="51db8-191">Eles contêm todas as janelas, as páginas e os recursos que estão no formato **xaml**.</span><span class="sxs-lookup"><span data-stu-id="51db8-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="51db8-192">Não é possível usar um padrão glob aqui e é necessário adicionar uma entrada para cada arquivo e indicar o `<Generator>` usado.</span><span class="sxs-lookup"><span data-stu-id="51db8-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="51db8-193">Adicionar pacotes do NuGet</span><span class="sxs-lookup"><span data-stu-id="51db8-193">Add NuGet packages</span></span>

<span data-ttu-id="51db8-194">Adicione cada pacote do NuGet referenciado pelo projeto do .NET Framework ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="51db8-195">Muito provavelmente, o aplicativo WPF do .NET Framework tem um arquivo **packages.config** que contém uma lista de todos os pacotes NuGet referenciados pelo projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="51db8-196">É possível examinar essa lista para determinar quais pacotes do NuGet serão adicionados ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="51db8-197">Por exemplo, se o projeto do .NET Framework referencia o pacote NuGet `MahApps.Metro`, adicione-o ao projeto com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51db8-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="51db8-198">Você também pode adicionar a referência de pacote com a CLI do .NET Core por meio do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="51db8-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="51db8-199">O comando anterior adiciona a seguinte referência do NuGet ao projeto **MyWPFCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="51db8-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="51db8-200">Problemas na compilação</span><span class="sxs-lookup"><span data-stu-id="51db8-200">Problems compiling</span></span>

<span data-ttu-id="51db8-201">Se você tiver problemas ao compilar seus projetos, talvez esteja usando algumas APIs que são somente para Windows e que estão disponíveis no .NET Framework, mas não no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="51db8-202">Experimente adicionar o pacote do NuGet do [Pacote de Compatibilidade do Windows][compat-pack] ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="51db8-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="51db8-203">Esse pacote só é executado no Windows e adiciona cerca de 20.000 APIs do Windows aos projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="51db8-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="51db8-204">O comando anterior adiciona o seguinte ao projeto **MyWPFCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="51db8-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="51db8-205">WPF Designer</span><span class="sxs-lookup"><span data-stu-id="51db8-205">WPF Designer</span></span>

<span data-ttu-id="51db8-206">Conforme detalhado neste artigo, o Visual Studio 2019 oferece suporte ao Designer do WPF apenas em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="51db8-207">Ao criar um projeto do .NET Core lado a lado, você pode testar seu projeto com o .NET Core enquanto usa o projeto do .NET Framework para criar formulários.</span><span class="sxs-lookup"><span data-stu-id="51db8-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="51db8-208">Seu arquivo de solução inclui projetos do .NET Framework e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="51db8-209">Adicione e crie seus formulários e controles no projeto do .NET Framework e, com base nos padrões glob de arquivos que adicionamos aos projetos do .NET Core, todos os arquivos novos ou alterados serão incluídos automaticamente nos projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="51db8-210">Depois que o Visual Studio 2019 der suporte ao Designer do WPF, você poderá copiar/colar o conteúdo do arquivo de projeto do .NET Core no arquivo de projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51db8-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="51db8-211">Depois, poderá excluir os padrões glob de arquivo adicionados com os itens `<Source>` e `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="51db8-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="51db8-212">Corrija os caminhos de qualquer referência de projeto usada pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51db8-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="51db8-213">Isso atualiza efetivamente o projeto do .NET Framework para um projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="51db8-214">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="51db8-214">Next steps</span></span>

* <span data-ttu-id="51db8-215">Leia mais sobre o [Pacote de Compatibilidade do Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="51db8-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="51db8-216">Assista a um [vídeo sobre como compatibilizar](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) seu projeto do WPF do .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51db8-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
