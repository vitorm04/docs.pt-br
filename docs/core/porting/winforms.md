---
title: Porta um aplicativo Do Windows Forms para .NET Core
description: Ensina como portar um aplicativo .NET Framework Windows Forms para .NET Core for Windows.
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: 80b4bb225d6a6748743d91a4c70e8b09c10cc94b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635511"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="b8625-103">Como portar um aplicativo de desktop do Windows Forms para .NET Core</span><span class="sxs-lookup"><span data-stu-id="b8625-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="b8625-104">Este artigo descreve como portar seu aplicativo de desktop baseado no Windows Forms do .NET Framework para .NET Core 3.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="b8625-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="b8625-105">O SDK do .NET Core 3.0 inclui suporte para aplicativos do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8625-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="b8625-106">O Windows Forms ainda é uma estrutura somente do Windows e só é executado nessa plataforma.</span><span class="sxs-lookup"><span data-stu-id="b8625-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="b8625-107">Este exemplo usa a CLI do .SDK do .NET Core para criar e gerenciar seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="b8625-108">Neste artigo, vários nomes são usados a fim de identificar os tipos de arquivos usados para migração.</span><span class="sxs-lookup"><span data-stu-id="b8625-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="b8625-109">Ao migrar seu projeto, seus arquivos receberão nomes diferentes; portanto, relacione-os mentalmente aos listados abaixo:</span><span class="sxs-lookup"><span data-stu-id="b8625-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="b8625-110">Arquivo</span><span class="sxs-lookup"><span data-stu-id="b8625-110">File</span></span> | <span data-ttu-id="b8625-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8625-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="b8625-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="b8625-112">**MyApps.sln**</span></span> | <span data-ttu-id="b8625-113">O nome do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="b8625-113">The name of the solution file.</span></span> |
| <span data-ttu-id="b8625-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="b8625-114">**MyForms.csproj**</span></span> | <span data-ttu-id="b8625-115">O nome do projeto do Windows Forms do .NET Framework a ser portado.</span><span class="sxs-lookup"><span data-stu-id="b8625-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="b8625-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="b8625-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="b8625-117">O nome do novo projeto do .NET Core criado.</span><span class="sxs-lookup"><span data-stu-id="b8625-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="b8625-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="b8625-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="b8625-119">O arquivo executável do aplicativo do Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="b8625-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b8625-120">Prerequisites</span></span>

- <span data-ttu-id="b8625-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) ou mais tarde para qualquer trabalho de designer que você queira fazer.</span><span class="sxs-lookup"><span data-stu-id="b8625-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) or later for any designer work you want to do.</span></span> <span data-ttu-id="b8625-122">Recomendamos atualizar para a versão mais recente [do Visual Studio](https://visualstudio.microsoft.com/vs/preview/)</span><span class="sxs-lookup"><span data-stu-id="b8625-122">We recommend to update to the latest [Preview version of Visual Studio](https://visualstudio.microsoft.com/vs/preview/)</span></span>

  <span data-ttu-id="b8625-123">Instale as seguintes cargas de trabalho do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="b8625-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="b8625-124">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="b8625-124">.NET desktop development</span></span>
  - <span data-ttu-id="b8625-125">Desenvolvimento multiplataforma com o .NET Core</span><span class="sxs-lookup"><span data-stu-id="b8625-125">.NET Core cross-platform development</span></span>

- <span data-ttu-id="b8625-126">Um projeto do Windows Forms em funcionamento em uma solução compilada e executada sem problemas.</span><span class="sxs-lookup"><span data-stu-id="b8625-126">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="b8625-127">Um projeto codificado em C#.</span><span class="sxs-lookup"><span data-stu-id="b8625-127">A project coded in C#.</span></span>

> [!NOTE]
> <span data-ttu-id="b8625-128">Os projetos .NET Core 3.0 só são suportados no **Visual Studio 2019** ou em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="b8625-128">.NET Core 3.0 projects are only supported in **Visual Studio 2019** or a later version.</span></span> <span data-ttu-id="b8625-129">Começando com **o Visual Studio 2019 versão 16.5 Preview 1**, o designer .NET Core Windows Forms também é suportado.</span><span class="sxs-lookup"><span data-stu-id="b8625-129">Starting with **Visual Studio 2019 version 16.5 Preview 1**, the .NET Core Windows Forms designer is also supported.</span></span>
>
> <span data-ttu-id="b8625-130">Para habilitar o designer, vá para Recursos**de visualização** **do ambiente** > **de opções** > de **ferramentas** > e selecione **usar a opção Usar o designer de formulários do Windows para a opção de aplicativos .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="b8625-130">To enable the designer, go to **Tools** > **Options** > **Environment** > **Preview Features** and select the **Use the preview Windows Forms designer for .NET Core apps** option.</span></span>

### <a name="consider"></a><span data-ttu-id="b8625-131">Considerações</span><span class="sxs-lookup"><span data-stu-id="b8625-131">Consider</span></span>

<span data-ttu-id="b8625-132">Ao portar um aplicativo do Windows Forms do .NET Framework, há alguns pontos a ser considerados.</span><span class="sxs-lookup"><span data-stu-id="b8625-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="b8625-133">Verifique se o seu aplicativo é um bom candidato para a migração.</span><span class="sxs-lookup"><span data-stu-id="b8625-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="b8625-134">Use o [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) para determinar se o seu projeto será migrado para o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b8625-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="b8625-135">Se seu projeto tiver problemas com o .NET Core 3.0, o analisador ajudará a identificar esses problemas.</span><span class="sxs-lookup"><span data-stu-id="b8625-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="b8625-136">Você está usando uma versão diferente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8625-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="b8625-137">Quando o .NET Core 3.0 Preview 1 foi lançado, o Windows Forms foi de código aberto no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b8625-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="b8625-138">O código para .NET Core Windows Forms é um garfo da base de código .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8625-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="b8625-139">É possível que haja algumas diferenças e seu aplicativo não seja portado.</span><span class="sxs-lookup"><span data-stu-id="b8625-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="b8625-140">O [Pacote de Compatibilidade do Windows][compat-pack] pode ajudar você na migração.</span><span class="sxs-lookup"><span data-stu-id="b8625-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="b8625-141">Algumas APIs disponíveis no .NET Framework não estão disponíveis no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="b8625-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="b8625-142">O [Pacote de Compatibilidade do Windows][compat-pack] adiciona muitas dessas APIs e podem ajudar seu aplicativo do Windows Forms a se tornar compatível com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="b8625-143">Atualize os pacotes do NuGet usados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="b8625-144">É sempre uma boa prática usar as versões mais recentes dos pacotes do NuGet antes de qualquer migração.</span><span class="sxs-lookup"><span data-stu-id="b8625-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="b8625-145">Se seu aplicativo faz referência a pacotes do NuGet, atualize-os para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="b8625-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="b8625-146">Certifique-se de que seu aplicativo foi compilado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b8625-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="b8625-147">Após a atualização, se houver erros de pacote, faça downgrade do pacote para a versão mais recente que não interrompa seu código.</span><span class="sxs-lookup"><span data-stu-id="b8625-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="b8625-148">Criar um novo projeto de SDK</span><span class="sxs-lookup"><span data-stu-id="b8625-148">Create a new SDK project</span></span>

<span data-ttu-id="b8625-149">O novo projeto do .NET Core 3.0 que você criar deverá ficar em um diretório diferente do seu projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-149">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="b8625-150">Se os dois estiverem no mesmo diretório, poderão surgir conflitos com os arquivos gerados no diretório **obj**.</span><span class="sxs-lookup"><span data-stu-id="b8625-150">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="b8625-151">Neste exemplo, vamos criar um diretório chamado **MyFormsAppCore** no diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="b8625-151">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="b8625-152">Em seguida, crie o projeto **MyFormsCore.csproj** no diretório **MyFormsAppCore**.</span><span class="sxs-lookup"><span data-stu-id="b8625-152">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="b8625-153">Você pode criar esse arquivo manualmente usando o editor de texto de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="b8625-153">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="b8625-154">Cole o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="b8625-154">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="b8625-155">Se não quiser criar manualmente o arquivo de projeto, use o Visual Studio ou o SDK do .NET Core para gerar o projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-155">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="b8625-156">No entanto, você deverá excluir todos os outros arquivos gerados pelo modelo de projeto, exceto o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-156">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="b8625-157">Para usar o SDK, execute o seguinte comando a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="b8625-157">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="b8625-158">Depois que criar o **MyFormsCore.csproj**, sua estrutura de diretórios deverá ser semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="b8625-158">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="b8625-159">Adicione o projeto **MyFormsCore.csproj** ao **MyApps.sln** com o Visual Studio ou o .NET Core CLI do diretório **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="b8625-159">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="b8625-160">Corrigir a geração de informações do assembly</span><span class="sxs-lookup"><span data-stu-id="b8625-160">Fix assembly info generation</span></span>

<span data-ttu-id="b8625-161">Projetos do Windows Forms criados com o .NET Framework incluem um arquivo `AssemblyInfo.cs`, que contém os atributos de assembly, como a versão do assembly a ser gerado.</span><span class="sxs-lookup"><span data-stu-id="b8625-161">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="b8625-162">Projetos no estilo SDK geram automaticamente essas informações com base no arquivo de projeto do SDK.</span><span class="sxs-lookup"><span data-stu-id="b8625-162">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="b8625-163">Ter os dois tipos de "informações do assembly" cria um conflito.</span><span class="sxs-lookup"><span data-stu-id="b8625-163">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="b8625-164">Para resolver esse problema, desabilite a geração automática, o que força o projeto a usar o arquivo `AssemblyInfo.cs` existente.</span><span class="sxs-lookup"><span data-stu-id="b8625-164">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="b8625-165">Há três configurações para adicionar ao nó `<PropertyGroup>` principal.</span><span class="sxs-lookup"><span data-stu-id="b8625-165">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="b8625-166">**GerarAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="b8625-166">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="b8625-167">Quando você define essa propriedade como `false`, ela não gera os atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8625-167">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="b8625-168">Isso evita conflito com o arquivo `AssemblyInfo.cs` existente do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-168">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="b8625-169">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="b8625-169">**AssemblyName**</span></span>\
<span data-ttu-id="b8625-170">O valor dessa propriedade é a saída binária criada na compilação.</span><span class="sxs-lookup"><span data-stu-id="b8625-170">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="b8625-171">O nome não precisa de uma extensão adicionada a ele.</span><span class="sxs-lookup"><span data-stu-id="b8625-171">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="b8625-172">Por exemplo, o uso de `MyCoreApp` produz `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="b8625-172">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="b8625-173">**Rootnamespace**</span><span class="sxs-lookup"><span data-stu-id="b8625-173">**RootNamespace**</span></span>\
<span data-ttu-id="b8625-174">O namespace padrão usado pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-174">The default namespace used by your project.</span></span> <span data-ttu-id="b8625-175">Ele deve corresponder ao namespace padrão do projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-175">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="b8625-176">Adicione estes três elementos ao nó `<PropertyGroup>` no arquivo `MyFormsCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="b8625-176">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="b8625-177">Adicionar código-fonte</span><span class="sxs-lookup"><span data-stu-id="b8625-177">Add source code</span></span>

<span data-ttu-id="b8625-178">No momento, o projeto **MyFormsCore.csproj** não compila qualquer código.</span><span class="sxs-lookup"><span data-stu-id="b8625-178">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="b8625-179">Por padrão, os projetos do .NET Core incluem automaticamente todo o código-fonte do diretório atual e de todos os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="b8625-179">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="b8625-180">Configure o projeto para incluir código do projeto do .NET Framework usando um caminho relativo.</span><span class="sxs-lookup"><span data-stu-id="b8625-180">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="b8625-181">Se o seu projeto do .NET Framework tiver usado arquivos **.resx** para ícones e recursos dos formulários, você precisará incluí-los também.</span><span class="sxs-lookup"><span data-stu-id="b8625-181">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="b8625-182">Adicione o seguinte nó `<ItemGroup>` ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-182">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="b8625-183">Cada instrução inclui o padrão glob de arquivo que inclui os diretórios filho.</span><span class="sxs-lookup"><span data-stu-id="b8625-183">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="b8625-184">Como alternativa, você pode criar uma entrada `<Compile>` ou `<EmbeddedResource>` para cada arquivo em seu projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-184">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="b8625-185">Adicionar pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="b8625-185">Add NuGet packages</span></span>

<span data-ttu-id="b8625-186">Adicione cada pacote do NuGet referenciado pelo projeto do .NET Framework ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-186">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="b8625-187">Muito provavelmente, seu aplicativo do Windows Forms do .NET Framework tem um arquivo **packages.config** que contém uma lista de todos os pacotes do NuGet referenciados pelo seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-187">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="b8625-188">É possível examinar essa lista para determinar quais pacotes do NuGet serão adicionados ao projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-188">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="b8625-189">Por exemplo, se o projeto do .NET Framework tiver referenciado os pacotes do NuGet `MetroFramework`, `MetroFramework.Design` e `MetroFramework.Fonts`, adicione cada um deles ao projeto com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="b8625-189">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="b8625-190">Os comandos anteriores adicionariam as seguintes referências do NuGet ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="b8625-190">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="b8625-191">Portar bibliotecas de controles</span><span class="sxs-lookup"><span data-stu-id="b8625-191">Port control libraries</span></span>

<span data-ttu-id="b8625-192">Se você tem um projeto de biblioteca de controles do Windows Forms para portar, as instruções são iguais às da portabilidade de um projeto de aplicativo do Windows Forms do .NET Framework, com exceção de algumas configurações.</span><span class="sxs-lookup"><span data-stu-id="b8625-192">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="b8625-193">E, em vez de compilar em um arquivo executável, você compila em uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="b8625-193">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="b8625-194">A diferença entre o projeto executável e o projeto de biblioteca, além dos caminhos para os globs de arquivo que incluem seu código-fonte, é mínima.</span><span class="sxs-lookup"><span data-stu-id="b8625-194">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="b8625-195">Usando o exemplo da etapa anterior, vamos expandir os projetos e arquivos com que estamos trabalhando.</span><span class="sxs-lookup"><span data-stu-id="b8625-195">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="b8625-196">Arquivo</span><span class="sxs-lookup"><span data-stu-id="b8625-196">File</span></span> | <span data-ttu-id="b8625-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8625-197">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="b8625-198">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="b8625-198">**MyApps.sln**</span></span> | <span data-ttu-id="b8625-199">O nome do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="b8625-199">The name of the solution file.</span></span> |
| <span data-ttu-id="b8625-200">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="b8625-200">**MyControls.csproj**</span></span> | <span data-ttu-id="b8625-201">O nome do projeto de controles do Windows Forms do .NET Framework a ser portado.</span><span class="sxs-lookup"><span data-stu-id="b8625-201">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="b8625-202">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="b8625-202">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="b8625-203">O nome do novo projeto de biblioteca do .NET Core criado.</span><span class="sxs-lookup"><span data-stu-id="b8625-203">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="b8625-204">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="b8625-204">**MyCoreControls.dll**</span></span> | <span data-ttu-id="b8625-205">A biblioteca de controles do Windows Forms do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-205">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="b8625-206">Considere as diferenças entre o projeto `MyControlsCore.csproj` e o projeto `MyFormsCore.csproj` criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b8625-206">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="b8625-207">Veja um exemplo de como o arquivo de projeto de biblioteca de controles do Windows Forms do .NET Core ficaria:</span><span class="sxs-lookup"><span data-stu-id="b8625-207">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="b8625-208">Como você pode ver, o nó `<OutputType>` foi removido, o que padroniza o compilador para produzir uma biblioteca em vez de um arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="b8625-208">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="b8625-209">O `<AssemblyName>` e `<RootNamespace>` foram alterados.</span><span class="sxs-lookup"><span data-stu-id="b8625-209">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="b8625-210">Especificamente, o `<RootNamespace>` deve corresponder ao namespace da biblioteca de controles do Windows Forms que está passando pela portabilidade.</span><span class="sxs-lookup"><span data-stu-id="b8625-210">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="b8625-211">Por fim, os nós `<Compile>` e `<EmbeddedResource>` foram ajustados para apontar para a pasta da biblioteca de controles de Windows Forms que você está portando.</span><span class="sxs-lookup"><span data-stu-id="b8625-211">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="b8625-212">Em seguida, no projeto principal .NET Core **MyFormsCore.csproj,** adicione uma referência à nova biblioteca de controle de formulários do .NET Core Windows.</span><span class="sxs-lookup"><span data-stu-id="b8625-212">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="b8625-213">Adicione uma referência com o Visual Studio ou a CLI do .NET Core a partir do diretório **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="b8625-213">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="b8625-214">O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="b8625-214">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="b8625-215">Problemas de compilação</span><span class="sxs-lookup"><span data-stu-id="b8625-215">Compilation problems</span></span>

<span data-ttu-id="b8625-216">Se você tiver problemas ao compilar seus projetos, talvez esteja usando algumas APIs que são somente para Windows e que estão disponíveis no .NET Framework, mas não no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-216">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="b8625-217">Experimente adicionar o pacote do NuGet do [Pacote de Compatibilidade do Windows][compat-pack] ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b8625-217">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="b8625-218">Esse pacote só é executado no Windows e adiciona cerca de 20.000 APIs do Windows aos projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b8625-218">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="b8625-219">O comando anterior adiciona o seguinte ao projeto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="b8625-219">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="b8625-220">Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="b8625-220">Windows Forms Designer</span></span>

<span data-ttu-id="b8625-221">Conforme detalhado neste artigo, o Visual Studio 2019 oferece suporte ao Designer de Formulários apenas em projetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-221">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="b8625-222">Ao criar um projeto do .NET Core lado a lado, você pode testar seu projeto com o .NET Core enquanto usa o projeto do .NET Framework para criar formulários.</span><span class="sxs-lookup"><span data-stu-id="b8625-222">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="b8625-223">Seu arquivo de solução inclui projetos do .NET Framework e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-223">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="b8625-224">Adicione e crie seus formulários e controles no projeto do .NET Framework e, com base nos padrões glob de arquivos que adicionamos aos projetos do .NET Core, todos os arquivos novos ou alterados serão incluídos automaticamente nos projetos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-224">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="b8625-225">Depois que o Visual Studio 2019 oferecer suporte ao Designer de Formulários do Windows, você poderá copiar/colar o conteúdo do arquivo de projeto do .NET Core no arquivo de projeto do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8625-225">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="b8625-226">Depois, poderá excluir os padrões glob de arquivo adicionados com os itens `<Source>` e `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="b8625-226">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="b8625-227">Corrija os caminhos de qualquer referência de projeto usada pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8625-227">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="b8625-228">Isso atualiza efetivamente o projeto do .NET Framework para um projeto do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-228">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b8625-229">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b8625-229">Next steps</span></span>

- <span data-ttu-id="b8625-230">Saiba como [mudar de .NET Framework para .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="b8625-230">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="b8625-231">Leia mais sobre o [Pacote de Compatibilidade do Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="b8625-231">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="b8625-232">Assista a um [vídeo sobre como portar](https://www.youtube.com/watch?v=upVQEUc_KwU) seu projeto do Windows Forms do .NET Framework para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8625-232">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
