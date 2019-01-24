---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 26fb7cb25b9bf7f00f87059fbe1848763f7f175d
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415540"
---
# <a name="whats-new-in-net-core-30-preview-1"></a><span data-ttu-id="fda81-103">Novidades do .NET Core 3.0 (versão prévia 1)</span><span class="sxs-lookup"><span data-stu-id="fda81-103">What's new in .NET Core 3.0 (Preview 1)</span></span>

<span data-ttu-id="fda81-104">Este artigo descreve as novidades do .NET Core 3.0 (versão prévia 1).</span><span class="sxs-lookup"><span data-stu-id="fda81-104">This article describes what is new in .NET Core 3.0 (preview 1).</span></span> <span data-ttu-id="fda81-105">Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows).</span><span class="sxs-lookup"><span data-stu-id="fda81-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="fda81-106">Ao utilizar um componente do .NET Core 3.0 chamado Windows Desktop, você pode fazer a portabilidade dos seus aplicativos do Windows Forms e da Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="fda81-106">By utilizing a .NET Core 3.0 component called Windows Desktop, you can port your Windows Forms Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="fda81-107">Para deixar claro, o componente Windows Desktop só é compatível com Windows.</span><span class="sxs-lookup"><span data-stu-id="fda81-107">To be clear, the Windows Desktop component is only supported on Windows.</span></span> <span data-ttu-id="fda81-108">Para saber mais, confira a seção [Desktop Windows](#windows-desktop) abaixo.</span><span class="sxs-lookup"><span data-stu-id="fda81-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="fda81-109">O .NET Core 3.0 adiciona suporte para C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="fda81-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="fda81-110">[Baixe e comece a trabalhar com o .NET Core 3 Versão prévia 1](https://aka.ms/netcore3download) agora mesmo no Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="fda81-110">[Download and get started with .NET Core 3 Preview 1](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="fda81-111">Você pode ver todos os detalhes da versão nas [Notas sobre a versão do .NET Core 3 Versão prévia 1](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="fda81-111">You can see complete details of the release in the [.NET Core 3 Preview 1 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="fda81-112">Para saber mais, confira [Comunicado sobre o .NET Core 3.0 Versão prévia 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span><span class="sxs-lookup"><span data-stu-id="fda81-112">For more information, see the [.NET Core 3.0 Preview 1 announcement](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="fda81-113">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="fda81-113">.NET Standard 2.1</span></span>

<span data-ttu-id="fda81-114">O .NET Core 3.0 implementa o .NET Standard 2.1.</span><span class="sxs-lookup"><span data-stu-id="fda81-114">.NET Core 3.0 implements .NET Standard 2.1.</span></span>

## <a name="default-executables"></a><span data-ttu-id="fda81-115">Executáveis por padrão</span><span class="sxs-lookup"><span data-stu-id="fda81-115">Default executables</span></span>

<span data-ttu-id="fda81-116">Agora, o .NET Core criará [executáveis dependentes da estrutura](../deploying/index.md#framework-dependent-executables-fde), por padrão.</span><span class="sxs-lookup"><span data-stu-id="fda81-116">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="fda81-117">Isso é novidade para aplicativos que usam uma versão do .NET Core instalada globalmente.</span><span class="sxs-lookup"><span data-stu-id="fda81-117">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="fda81-118">Até agora, apenas [implantações autossuficientes](../deploying/index.md#self-contained-deployments-scd) produziam um executável.</span><span class="sxs-lookup"><span data-stu-id="fda81-118">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="fda81-119">Durante `dotnet build` ou `dotnet publish`, um arquivo executável é criado, desde que corresponda ao ambiente e à plataforma do SDK que você está usando.</span><span class="sxs-lookup"><span data-stu-id="fda81-119">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="fda81-120">Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:</span><span class="sxs-lookup"><span data-stu-id="fda81-120">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="fda81-121">Você pode clicar duas vezes no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="fda81-121">You can double-click on the executable.</span></span>
* <span data-ttu-id="fda81-122">Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="fda81-122">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="fda81-123">O build copia dependências</span><span class="sxs-lookup"><span data-stu-id="fda81-123">Build copies dependencies</span></span>

<span data-ttu-id="fda81-124">`dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache do NuGet para a pasta de saída do build.</span><span class="sxs-lookup"><span data-stu-id="fda81-124">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="fda81-125">Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="fda81-125">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="fda81-126">Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.</span><span class="sxs-lookup"><span data-stu-id="fda81-126">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="fda81-127">Ferramentas dotnet locais</span><span class="sxs-lookup"><span data-stu-id="fda81-127">Local dotnet tools</span></span>

<span data-ttu-id="fda81-128">Enquanto o .NET Core 2.1 oferecia suporte para ferramentas globais, o .NET Core 3.0 agora tem ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="fda81-128">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="fda81-129">As ferramentas locais são semelhantes às ferramentas globais, mas estão associadas a um local específico no disco.</span><span class="sxs-lookup"><span data-stu-id="fda81-129">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="fda81-130">Isso permite ferramentas por projeto e por repositório.</span><span class="sxs-lookup"><span data-stu-id="fda81-130">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="fda81-131">Qualquer ferramenta instalada localmente não está disponível globalmente.</span><span class="sxs-lookup"><span data-stu-id="fda81-131">Any tool installed locally isn't available globally.</span></span>

<span data-ttu-id="fda81-132">As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fda81-132">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="fda81-133">Esse arquivo de manifesto define as ferramentas que ficarão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fda81-133">This manifest file defines the tools to be available.</span></span> <span data-ttu-id="fda81-134">Ao criar esse arquivo de manifesto na raiz do seu repositório, garanta que qualquer pessoa que clone seu código possa restaurar e usar as ferramentas necessárias para trabalhar com êxito com seu código.</span><span class="sxs-lookup"><span data-stu-id="fda81-134">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="fda81-135">Quando o arquivo de manifesto de ferramentas locais estiver disponível, use o seguinte comando para baixar e instalar essas ferramentas localmente de modo automático:</span><span class="sxs-lookup"><span data-stu-id="fda81-135">When the local tools manifest file is available, use the following command to automatically download and install those tools locally:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="fda81-136">Execute uma ferramenta local com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fda81-136">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="fda81-137">Ao chamar uma ferramenta local, o dotnet procura um manifesto na estrutura do diretório.</span><span class="sxs-lookup"><span data-stu-id="fda81-137">When a local tool is called, dotnet searches for a manifest up the directory structure.</span></span> <span data-ttu-id="fda81-138">Ao encontrar um arquivo de manifesto de ferramenta, ele é pesquisado para a ferramenta solicitada.</span><span class="sxs-lookup"><span data-stu-id="fda81-138">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="fda81-139">Se a ferramenta for encontrada, ela incluirá as informações necessárias para encontrar a ferramenta no local de pacotes globais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="fda81-139">If the tool is found, it includes the information needed to find the tool in the NuGet global packages location.</span></span> 

<span data-ttu-id="fda81-140">Se a ferramenta for encontrada no manifesto, mas não no cache, o usuário receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="fda81-140">If the tool is found in the manifest, but not the cache, the user receives an error.</span></span> <span data-ttu-id="fda81-141">A mensagem será aprimorada após a Versão prévia 1 para solicitar que o usuário execute `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="fda81-141">The message will be improved after Preview 1 to request the user run `dotnet tool restore`.</span></span>

<span data-ttu-id="fda81-142">Para adicionar ferramentas locais a um diretório, primeiro crie o arquivo de manifesto da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="fda81-142">To add local tools to a directory, you need to first create the tool manifest file.</span></span> <span data-ttu-id="fda81-143">Após a Versão prévia 1, ofereceremos um mecanismo para criar arquivos de manifesto de ferramenta, como um novo modelo dotnet.</span><span class="sxs-lookup"><span data-stu-id="fda81-143">After Preview 1, we will offer a mechanism for creating tool manifest files, such as a dotnet new template.</span></span> <span data-ttu-id="fda81-144">Para a Versão prévia 1, crie o arquivo chamado `dotnet-tools.json` com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="fda81-144">For Preview 1 you must create the file named `dotnet-tools.json` with the following contents:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="fda81-145">Após criar o manifesto, é possível adicionar ferramentas locais a ele usando:</span><span class="sxs-lookup"><span data-stu-id="fda81-145">Once the manifest is created, you can add local tools to it using:</span></span>

```console
dotnet tool install <toolPackageId>
```

<span data-ttu-id="fda81-146">Esse comando instala a versão mais recente da ferramenta, a menos que outra versão seja especificada.</span><span class="sxs-lookup"><span data-stu-id="fda81-146">This command installs the latest version of the tool, unless another version is specified.</span></span>  <span data-ttu-id="fda81-147">Mesmo se a versão mais recente for escolhida automaticamente, a versão da ferramenta será gravada no arquivo de manifesto da ferramenta para permitir que a versão correta seja restaurada ou executada.</span><span class="sxs-lookup"><span data-stu-id="fda81-147">Even if the latest version was automatically chosen, the version of the tool is written into the tool manifest file to allow the correct version of the tool to be restored or run.</span></span>

<span data-ttu-id="fda81-148">O arquivo de manifesto da ferramenta é projetado para permitir a edição manual, o que você pode fazer para atualizar a versão necessária ao trabalhar com o repositório.</span><span class="sxs-lookup"><span data-stu-id="fda81-148">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span>

<span data-ttu-id="fda81-149">Veja aqui um exemplo de arquivo `dotnet-tools.json`:</span><span class="sxs-lookup"><span data-stu-id="fda81-149">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="fda81-150">Para remover uma ferramenta de arquivo de manifesto da ferramenta, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fda81-150">To remove a tool from the tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <toolPackageId>
```

<span data-ttu-id="fda81-151">Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fda81-151">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="fda81-152">Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="fda81-152">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="fda81-153">Para instalá-las global ou localmente, você ainda precisará instalar o [tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="fda81-153">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="fda81-154">Para saber mais, consulte a [Documentação da versão prévia antecipada de ferramentas locais](https://github.com/dotnet/cli/issues/10288).</span><span class="sxs-lookup"><span data-stu-id="fda81-154">For more information, see [Local Tools Early Preview Documentation](https://github.com/dotnet/cli/issues/10288).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="fda81-155">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="fda81-155">Windows desktop</span></span>

<span data-ttu-id="fda81-156">A partir do .NET Core 3.0 Versão prévia 1, é possível criar aplicativos de área de trabalho do Windows usando WPF e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fda81-156">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="fda81-157">Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="fda81-157">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="fda81-158">O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.</span><span class="sxs-lookup"><span data-stu-id="fda81-158">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="fda81-159">É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="fda81-159">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="fda81-160">Também é possível abrir, iniciar e depurar projetos de WPF e Windows Forms do .NET Core 3.0 no Visual Studio 2019 Versão prévia 1.</span><span class="sxs-lookup"><span data-stu-id="fda81-160">You can also open, launch, and debug .NET Core 3.0 WPF and Windows Forms projects in Visual Studio 2019 Preview 1.</span></span> <span data-ttu-id="fda81-161">Atualmente, é possível abrir esses projetos no Visual Studio 2017 15.9, no entanto, esse não é um cenário compatível (e você precisará [habilitar versões prévias](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span><span class="sxs-lookup"><span data-stu-id="fda81-161">It's currently possible to open these projects in Visual Studio 2017 15.9, however, it isn't a supported scenario (and you need to [enable previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span></span>

<span data-ttu-id="fda81-162">Os novos projetos são os mesmos que os projetos existentes do .NET Core, com algumas adições.</span><span class="sxs-lookup"><span data-stu-id="fda81-162">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="fda81-163">Veja aqui a comparação entre o projeto básico de console do .NET Core e um projeto básico do Windows Forms e WPF.</span><span class="sxs-lookup"><span data-stu-id="fda81-163">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="fda81-164">Em um projeto de console do .NET Core, o projeto usa o SDK `Microsoft.NET.Sdk` e declara uma dependência no .NET Core 3.0 por meio da estrutura de destino `netcoreapp3.0`.</span><span class="sxs-lookup"><span data-stu-id="fda81-164">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="fda81-165">Para criar um aplicativo de área de trabalho do Windows, use o SDK `Microsoft.NET.Sdk.WindowsDesktop` e escolha qual estrutura de interface do usuário usar:</span><span class="sxs-lookup"><span data-stu-id="fda81-165">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="fda81-166">Para escolher o Windows Forms ao invés da WPF, defina `UseWindowsForms` em vez de `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="fda81-166">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="fda81-167">`UseWPF` e `UseWindowsForms` podem ser definidos como `true` se o aplicativo usar ambas as estruturas; por exemplo, quando uma caixa de diálogo do Windows Forms hospeda um controle da WPF.</span><span class="sxs-lookup"><span data-stu-id="fda81-167">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="fda81-168">Compartilhe seus comentários nos repositórios [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) e [dotnet/core](https://github.com/dotnet/core/issues).</span><span class="sxs-lookup"><span data-stu-id="fda81-168">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="fda81-169">Suporte interno rápido a JSON</span><span class="sxs-lookup"><span data-stu-id="fda81-169">Fast built-in JSON support</span></span>

<span data-ttu-id="fda81-170">`System.Text.Json.Utf8JsonReader` é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="fda81-170">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="fda81-171">O `Utf8JsonReader` é um tipo fundamental de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="fda81-171">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="fda81-172">Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do [Json.NET](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="fda81-172">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from [Json.NET](https://www.newtonsoft.com/json).</span></span> <span data-ttu-id="fda81-173">Ele não faz alocação até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="fda81-173">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="fda81-174">Essa nova API incluirá os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="fda81-174">This new API will include the following components:</span></span>

* <span data-ttu-id="fda81-175">Na versão prévia 1: Leitor de JSON (acesso sequencial)</span><span class="sxs-lookup"><span data-stu-id="fda81-175">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="fda81-176">Em breve: Gravação de JSON, DOM (acesso aleatório), serializador POCO, desserializador POCO</span><span class="sxs-lookup"><span data-stu-id="fda81-176">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="fda81-177">Veja aqui o loop de leitor básico para o `Utf8JsonReader` que pode ser usado como ponto de partida:</span><span class="sxs-lookup"><span data-stu-id="fda81-177">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

<span data-ttu-id="fda81-178">O ecossistema do .NET dependia do [Json.NET](https://www.newtonsoft.com/json) e de outras bibliotecas JSON populares, que continuam a ser boas opções.</span><span class="sxs-lookup"><span data-stu-id="fda81-178">The .NET ecosystem has relied on [Json.NET](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="fda81-179">O JSON.NET usa cadeias de caracteres do .NET como seu tipo de dados base, que, na verdade, são UTF-16.</span><span class="sxs-lookup"><span data-stu-id="fda81-179">JSON.NET uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span> 

<span data-ttu-id="fda81-180">No .NET Core 2.1 e 3.0, adicionamos novas APIs que possibilitam escrever APIs JSON (como `Utf8JsonReader`) que exigem muito menos memória, com base no uso de `Span<T>` e de cadeias de caracteres UTF-8, e melhor atendem às necessidades de aplicativos de alta taxa de transferência, como Kestrel e servidores da Web do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fda81-180">In .NET Core 2.1 and 3.0, we added new APIs that makes it possible to write JSON APIs (such as `Utf8JsonReader`) that require much less memory, based on using `Span<T>` and UTF-8 strings, and better serve the needs of high-throughput applications like Kestrel, ASP.NET Core web server.</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="fda81-181">Intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="fda81-181">Ranges and indices</span></span>

<span data-ttu-id="fda81-182">O novo tipo `Index` pode ser usado para indexação.</span><span class="sxs-lookup"><span data-stu-id="fda81-182">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="fda81-183">É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:</span><span class="sxs-lookup"><span data-stu-id="fda81-183">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="fda81-184">Há também um tipo `Range`, que consiste em dois valores `Index`, um para o início e outro para o final, e pode ser escrito com uma expressão de intervalo `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="fda81-184">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="fda81-185">Você pode indexar com `Range` para produzir uma fatia:</span><span class="sxs-lookup"><span data-stu-id="fda81-185">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> <span data-ttu-id="fda81-186">Somente o [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) oferece suporte à sintaxe para `Range` e `Index`.</span><span class="sxs-lookup"><span data-stu-id="fda81-186">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports syntax for `Range` and `Index`.</span></span>

## <a name="async-streams"></a><span data-ttu-id="fda81-187">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="fda81-187">Async streams</span></span>

<span data-ttu-id="fda81-188">O tipo `IAsyncEnumerable<T>` é uma nova versão assíncrona de `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="fda81-188">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="fda81-189">A linguagem permite que você aplique `await foreach` a eles para consumir seus elementos, e aplique `yield return` a eles para produzir elementos.</span><span class="sxs-lookup"><span data-stu-id="fda81-189">The language lets you `await foreach` over these to consume their elements, and `yield return` to them to produce elements.</span></span>

<span data-ttu-id="fda81-190">O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="fda81-190">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="fda81-191">A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores.</span><span class="sxs-lookup"><span data-stu-id="fda81-191">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="fda81-192">Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="fda81-192">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> <span data-ttu-id="fda81-193">O .NET Core 3.0 Versão prévia 1 tem um bug com `await foreach` no momento.</span><span class="sxs-lookup"><span data-stu-id="fda81-193">.NET Core 3.0 Preview 1 currently has a bug with `await foreach`.</span></span> <span data-ttu-id="fda81-194">Ao invés disso, use `GetEnumerator` e `MoveNext` para processar elementos.</span><span class="sxs-lookup"><span data-stu-id="fda81-194">Instead, use `GetEnumerator` and `MoveNext` to process elements.</span></span> <span data-ttu-id="fda81-195">Para saber mais, consulte [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span><span class="sxs-lookup"><span data-stu-id="fda81-195">For more information, see [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span></span>

<span data-ttu-id="fda81-196">Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="fda81-196">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="fda81-197">Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.</span><span class="sxs-lookup"><span data-stu-id="fda81-197">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="fda81-198">Somente o [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) oferece suporte à sintaxe `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="fda81-198">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports `await foreach` syntax.</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="fda81-199">Tipo: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="fda81-199">Type: SequenceReader</span></span>

<span data-ttu-id="fda81-200">`System.Buffers.SequenceReader` foi adicionado ao .NET Core 3.0, podendo ser usado como um leitor para `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="fda81-200">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="fda81-201">Isso permite uma análise fácil, de baixa alocação e de alto desempenho dos dados `System.IO.Pipelines`, que pode cruzar vários buffers de backup.</span><span class="sxs-lookup"><span data-stu-id="fda81-201">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="fda81-202">O exemplo a seguir quebra uma `Sequence` de entrada em linhas delimitadas `CR/LF` válidas:</span><span class="sxs-lookup"><span data-stu-id="fda81-202">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="fda81-203">Tipo: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="fda81-203">Type: MetadataLoadContext</span></span>

<span data-ttu-id="fda81-204">Adicionamos o tipo `MetadataLoadContext`, permitindo a leitura de metadados de assembly sem afetar o domínio do aplicativo do chamador.</span><span class="sxs-lookup"><span data-stu-id="fda81-204">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="fda81-205">Assemblies são lidos como dados, incluindo assemblies compilados para arquiteturas e plataformas diferentes do ambiente de tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="fda81-205">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="fda81-206">`MetadataLoadContext` se sobrepõe a <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, que só está disponível no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fda81-206">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="fda81-207">`MetdataLoadContext` está disponível no [pacote System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="fda81-207">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="fda81-208">Este é um pacote do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="fda81-208">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="fda81-209">O `MetadataLoadContext` expõe APIs semelhantes ao tipo <xref:System.Runtime.Loader.AssemblyLoadContext>, mas não é baseado nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="fda81-209">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="fda81-210">Assim como <xref:System.Runtime.Loader.AssemblyLoadContext>, o `MetadataLoadContext` permite o carregamento de assemblies dentro de um universo de carregamento de assemblies isolado.</span><span class="sxs-lookup"><span data-stu-id="fda81-210">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="fda81-211">APIs `MetdataLoadContext` retornam objetos <xref:System.Reflection.Assembly>, permitindo o uso de APIs de reflexão familiares.</span><span class="sxs-lookup"><span data-stu-id="fda81-211">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="fda81-212">APIs orientadas a execução, como [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), não são permitidas e emitirão InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="fda81-212">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="fda81-213">O exemplo a seguir demonstra como localizar tipos concretos em um assembly que implementa determinada interface:</span><span class="sxs-lookup"><span data-stu-id="fda81-213">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="fda81-214">Cenários para `MetadataLoadContext` incluem recursos de tempo de design, ferramentas de tempo de build e recursos de destaque de tempo de execução, que precisam inspecionar um conjunto de assemblies como dados e ter todos os bloqueios de arquivo e memória liberados após a execução da inspeção.</span><span class="sxs-lookup"><span data-stu-id="fda81-214">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="fda81-215">Em `MetadataLoadContext`, uma classe de resolvedor é transmitida para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="fda81-215">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="fda81-216">O trabalho do resolvedor é carregar um `Assembly` considerando seu `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="fda81-216">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="fda81-217">A classe de resolvedor deriva da classe abstrata `MetadataAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="fda81-217">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="fda81-218">Uma implementação do resolvedor para cenários com base em caminho é fornecida com `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="fda81-218">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="fda81-219">Os [testes de MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstram vários casos de uso.</span><span class="sxs-lookup"><span data-stu-id="fda81-219">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="fda81-220">Os [testes de assembly](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) são uma boa forma de começar.</span><span class="sxs-lookup"><span data-stu-id="fda81-220">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="fda81-221">TLS 1.3 e OpenSSL 1.1.1 no Linux</span><span class="sxs-lookup"><span data-stu-id="fda81-221">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="fda81-222">O .NET Core agora aproveitará o [suporte do TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), quando estiver disponível em determinado ambiente.</span><span class="sxs-lookup"><span data-stu-id="fda81-222">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="fda81-223">O TLS 1.3 tem vários benefícios, de acordo com a [equipe do OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="fda81-223">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="fda81-224">Tempos de conexão aprimorados, devido a uma redução no número de viagens de ida e volta necessário entre o cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="fda81-224">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="fda81-225">Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros e à criptografia de maior quantidade do handshake de conexão.</span><span class="sxs-lookup"><span data-stu-id="fda81-225">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="fda81-226">O .NET Core 3.0 Versão prévia 1 é capaz de utilizar **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, ou **OpenSSL 1.0.2** (seja qual for a melhor versão encontrada, em um sistema Linux).</span><span class="sxs-lookup"><span data-stu-id="fda81-226">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="fda81-227">Quando o **OpenSSL 1.1.1**  estiver disponível, os tipos SslStream e HttpClient usarão **TLS 1.3** ao usar `SslProtocols.None` (protocolos padrão do sistema), considerando que o cliente e o servidor ofereçam suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="fda81-227">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="fda81-228">O exemplo a seguir demonstra o .NET Core 3.0 Versão prévia 1 em Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="fda81-228">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="fda81-229">Windows e macOS ainda não oferecem suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="fda81-229">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="fda81-230">O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="fda81-230">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="fda81-231">Criptografia</span><span class="sxs-lookup"><span data-stu-id="fda81-231">Cryptography</span></span>

<span data-ttu-id="fda81-232">Foi adicionado suporte para criptografias **AES-GCM** e **AES-CCM**, implementadas via `System.Security.Cryptography.AesGcm` e `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="fda81-232">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="fda81-233">Esses algoritmos são os [algoritmos de Criptografia Autenticada com Dados de Associação (AEAD) ](https://en.wikipedia.org/wiki/Authenticated_encryption) e os primeiros algoritmos de Criptografia Autenticada (AE) adicionados ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fda81-233">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="fda81-234">O código a seguir demonstra como usar criptografia **AesGcm** para criptografar e descriptografar dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="fda81-234">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="fda81-235">O código para **AesCcm** seria quase idêntico (somente os nomes de variáveis de classe seriam diferentes).</span><span class="sxs-lookup"><span data-stu-id="fda81-235">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="fda81-236">Importar/exportar chave de criptografia</span><span class="sxs-lookup"><span data-stu-id="fda81-236">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="fda81-237">O .NET Core 3.0 Versão prévia 1 oferece suporte à importação e exportação de chaves públicas e privadas assimétricas nos formatos padrão, sem a necessidade de usar um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="fda81-237">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="fda81-238">Todos os tipos de chave (RSA, DSA, ECDsa, ECDiffieHellman) são compatíveis com o formato **X.509 SubjectPublicKeyInfo** para chaves públicas e com os formatos **PKCS#8 PrivateKeyInfo** e **PKCS#8 EncryptedPrivateKeyInfo** para chaves privadas.</span><span class="sxs-lookup"><span data-stu-id="fda81-238">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="fda81-239">RSA também é compatível com **PKCS#1 RSAPublicKey** e **PKCS#1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="fda81-239">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="fda81-240">Todos os métodos de exportação produzem dados binários codificados por DER, e os métodos de importação esperam o mesmo.</span><span class="sxs-lookup"><span data-stu-id="fda81-240">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="fda81-241">Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.</span><span class="sxs-lookup"><span data-stu-id="fda81-241">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="fda81-242">Arquivos PKCS#8 podem ser inspecionados com a classe `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo`.</span><span class="sxs-lookup"><span data-stu-id="fda81-242">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="fda81-243">Arquivos PFX/PKCS#12 podem ser inspecionados e manipulados com `System.Security.Cryptography.Pkcs.Pkcs12Info` e `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fda81-243">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="fda81-244">SerialPort para Linux</span><span class="sxs-lookup"><span data-stu-id="fda81-244">SerialPort for Linux</span></span>

<span data-ttu-id="fda81-245">O .NET Core 3.0 agora oferece suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.</span><span class="sxs-lookup"><span data-stu-id="fda81-245">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="fda81-246">Anteriormente, o .NET Core só era compatível com o uso do tipo `SerialPort` no Windows.</span><span class="sxs-lookup"><span data-stu-id="fda81-246">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="fda81-247">Mais melhorias do BCL</span><span class="sxs-lookup"><span data-stu-id="fda81-247">More BCL Improvements</span></span>

<span data-ttu-id="fda81-248">O `Span<T>`, `Memory<T>` e tipos relacionados, que foram introduzidos no .NET Core 2.1, foram otimizados no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fda81-248">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="fda81-249">Operações comuns, como construção de intervalo, divisão, análise e formatação agora funcionam melhor.</span><span class="sxs-lookup"><span data-stu-id="fda81-249">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="fda81-250">Além disso, tipos como `String` tiveram melhorias discretas para torná-los mais eficientes quando usados como chaves com `Dictionary<TKey, TValue>` e outras coleções.</span><span class="sxs-lookup"><span data-stu-id="fda81-250">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="fda81-251">Nenhuma alteração de código é necessária para se beneficiar dessas melhorias.</span><span class="sxs-lookup"><span data-stu-id="fda81-251">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="fda81-252">As melhorias a seguir também são novas no .NET Core 3 Versão prévia 1:</span><span class="sxs-lookup"><span data-stu-id="fda81-252">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="fda81-253">Suporte a Brotli integrado a HttpClient</span><span class="sxs-lookup"><span data-stu-id="fda81-253">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="fda81-254">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="fda81-254">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="fda81-255">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="fda81-255">Unsafe.Unbox</span></span>
* <span data-ttu-id="fda81-256">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="fda81-256">CancellationToken.Unregister</span></span>
* <span data-ttu-id="fda81-257">Operadores aritméticos complexos</span><span class="sxs-lookup"><span data-stu-id="fda81-257">Complex arithmetic operators</span></span>
* <span data-ttu-id="fda81-258">APIs de soquete para TCP em atividade</span><span class="sxs-lookup"><span data-stu-id="fda81-258">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="fda81-259">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="fda81-259">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="fda81-260">Análise de IPEndPoint</span><span class="sxs-lookup"><span data-stu-id="fda81-260">IPEndPoint parsing</span></span>
* <span data-ttu-id="fda81-261">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="fda81-261">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="fda81-262">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="fda81-262">Tiered compilation</span></span>

<span data-ttu-id="fda81-263">A [compilação em camadas](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) é ativada por padrão com o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fda81-263">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="fda81-264">É um recurso que permite que o tempo de execução use de forma mais adaptável o compilador Just-In-Time (JIT) para obter um melhor desempenho, tanto na inicialização quanto para maximizar a taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="fda81-264">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="fda81-265">Esse recurso foi adicionado como um recurso opcional no [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) e, em seguida, foi habilitado por padrão no [.NET Core 2.2 Versão prévia 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="fda81-265">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="fda81-266">Subsequentemente, foi revertido novamente para opcional na versão .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="fda81-266">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="fda81-267">Suporte a ARM64 no Linux</span><span class="sxs-lookup"><span data-stu-id="fda81-267">ARM64 Linux support</span></span>

<span data-ttu-id="fda81-268">Estamos adicionando suporte a ARM64 para Linux nesta versão.</span><span class="sxs-lookup"><span data-stu-id="fda81-268">We are adding support for ARM64 for Linux this release.</span></span> <span data-ttu-id="fda81-269">Para contextualização, adicionamos suporte a ARM32 para Linux com o .NET Core 2.1 e para Windows com o .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="fda81-269">For context, we added support for ARM32 for Linux with .NET Core 2.1 and Windows with .NET Core 2.2.</span></span> <span data-ttu-id="fda81-270">O principal caso de uso para ARM64 atualmente é em cenários de IoT.</span><span class="sxs-lookup"><span data-stu-id="fda81-270">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="fda81-271">As imagens de [Docker Alpine, Debian e Ubuntu estão disponíveis para o .NET Core para ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="fda81-271">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="fda81-272">Consulte [Status do ARM64 do .NET Core](https://github.com/dotnet/announcements/issues/82) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="fda81-272">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="fda81-273">O suporte do Windows a **ARM64** ainda não está disponível.</span><span class="sxs-lookup"><span data-stu-id="fda81-273">**ARM64** Windows support isn't yet available.</span></span>
