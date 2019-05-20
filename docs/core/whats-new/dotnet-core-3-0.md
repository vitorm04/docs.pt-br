---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 8d6ff6bc55384281119600f2323212441c1815e9
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452474"
---
# <a name="whats-new-in-net-core-30-preview-5"></a><span data-ttu-id="9ad8a-103">Novidades do .NET Core 3.0 (Versão Prévia 5)</span><span class="sxs-lookup"><span data-stu-id="9ad8a-103">What's new in .NET Core 3.0 (Preview 5)</span></span>

<span data-ttu-id="9ad8a-104">Este artigo descreve as novidades do .NET Core 3.0 (por meio da versão prévia 5).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-104">This article describes what is new in .NET Core 3.0 (through preview 5).</span></span> <span data-ttu-id="9ad8a-105">Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="9ad8a-106">Usando a Área de Trabalho do Windows do componente de SDK do .NET Core 3.0, você pode portar seus aplicativos Windows Forms e WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="9ad8a-107">Para deixar claro, o componente Windows Desktop só é compatível com o Windows e só é incluído nele.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="9ad8a-108">Para obter mais informações, consulte a seção [Área de Trabalho do Windows](#windows-desktop) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="9ad8a-109">O .NET Core 3.0 adiciona suporte para C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="9ad8a-110">É altamente recomendável que você use a versão mais recente do Visual Studio 2019 Atualização 1 Versão Prévia ou o VSCode com a extensão OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-110">It's highly recommended that you use the latest release of Visual Studio 2019 Update 1 Preview or VSCode with the OmniSharp extension.</span></span>

<span data-ttu-id="9ad8a-111">[Baixe e comece a trabalhar com o .NET Core 3.0 Versão Prévia 5](https://aka.ms/netcore3download) agora no Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-111">[Download and get started with .NET Core 3.0 Preview 5](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="9ad8a-112">Para obter mais informações sobre cada versão prévia, veja os seguintes avisos:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="9ad8a-113">Comunicado do .NET Core 3.0 Versão Prévia 5</span><span class="sxs-lookup"><span data-stu-id="9ad8a-113">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="9ad8a-114">Comunicado do .NET Core 3.0 Versão Prévia 4</span><span class="sxs-lookup"><span data-stu-id="9ad8a-114">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="9ad8a-115">Comunicado do .NET Core 3.0 Versão Prévia 3</span><span class="sxs-lookup"><span data-stu-id="9ad8a-115">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="9ad8a-116">Comunicado do .NET Core 3.0 Versão Prévia 2</span><span class="sxs-lookup"><span data-stu-id="9ad8a-116">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="9ad8a-117">Comunicado do .NET Core 3.0 Versão Prévia 1</span><span class="sxs-lookup"><span data-stu-id="9ad8a-117">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="9ad8a-118">Windows Installer do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ad8a-118">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="9ad8a-119">O instalador MSI para Windows foi alterado do .NET Core 3.0 em diante.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-119">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="9ad8a-120">Os instaladores de SDK agora atualizarão versões de faixa de recurso do SDK no local.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-120">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="9ad8a-121">Faixas de recurso são definidas nos grupos de *centenas* na seção *patch* do número de versão.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-121">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="9ad8a-122">Por exemplo, **3.0.\*101**\* e **3.0.\*201** são versões em duas faixas de recurso diferentes, enquanto **3.0.\*101**\* e **3.0.\*199**\* estão na mesma faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-122">For example, **3.0.\*101**\* and **3.0.\*201**\* are versions in two different feature bands while **3.0.\*101**\* and **3.0.\*199**\* are in the same feature band.</span></span> <span data-ttu-id="9ad8a-123">Além disso, quando o SDK do .NET Core **3.0.\*101**\* for instalado, o SDK do .NET Core **3.0.\*100**\* será removido do computador se ele existir.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-123">And, when .NET Core SDK **3.0.\*101**\* is installed, .NET Core SDK **3.0.\*100**\* will be removed from the machine if it exists.</span></span> <span data-ttu-id="9ad8a-124">Quando o SDK do .NET Core **3.0.\*200**\* é instalado no mesmo computador, o SDK do .NET Core **3.0.\*101**\* não é removido.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-124">When .NET Core SDK **3.0.\*200**\* is installed on the same machine, .NET Core SDK **3.0.\*101**\* won't be removed.</span></span>

<span data-ttu-id="9ad8a-125">Para obter mais informações sobre controle de versão, consulte [Visão geral de como é o controle de versão no .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-125">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="9ad8a-126">C# 8.0 versão prévia</span><span class="sxs-lookup"><span data-stu-id="9ad8a-126">C# 8.0 preview</span></span>

<span data-ttu-id="9ad8a-127">O .NET Core 3.0 dá suporte ao C# 8 versão prévia.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-127">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="9ad8a-128">Para obter mais informações sobre recursos do C# 8.0, consulte [Novidades do C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-128">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="9ad8a-129">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="9ad8a-129">.NET Standard 2.1</span></span>

<span data-ttu-id="9ad8a-130">Embora o .NET Core 3.0 dê suporte ao **.NET Standard 2.1**, o modelo `dotnet new classlib` padrão gera um projeto direcionado ao **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-130">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="9ad8a-131">Para direcionar ao **.NET Standard 2.1**, edite seu arquivo de projeto e altere a propriedade `TargetFramework` para `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-131">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="9ad8a-132">Se você estiver usando o Visual Studio, precisará do Visual Studio 2019, já que o Visual Studio 2017 não dá suporte ao **.NET Standard 2.1** nem ao **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-132">If you're using Visual Studio, you need Visual Studio 2019, as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span> <span data-ttu-id="9ad8a-133">É altamente recomendável que você use o [Visual Studio 2019 Atualização 1 Versão Prévia](https://visualstudio.microsoft.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-133">We highly recommend that you use [Visual Studio 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/).</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="9ad8a-134">APIs de versão aprimoradas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ad8a-134">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="9ad8a-135">Começando com o .NET Core 3.0, as APIs de versão fornecidas com o .NET Core agora retornam as informações que você espera.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-135">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="9ad8a-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-136">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="9ad8a-137">Alteração da falha.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-137">Breaking change.</span></span> <span data-ttu-id="9ad8a-138">Isso é tecnicamente uma alteração da falha, porque o esquema de controle de versão foi alterado.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-138">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="9ad8a-139">Intrínsecos dependentes da plataforma .NET</span><span class="sxs-lookup"><span data-stu-id="9ad8a-139">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="9ad8a-140">Foram adicionadas APIs que permitem acesso a determinadas instruções da CPU orientadas a desempenho, como o **SIMD** ou conjuntos de **instruções de manipulação de bits**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-140">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="9ad8a-141">Essas instruções podem ajudar a obter melhorias significativas de desempenho em determinados cenários, tais como processamento de dados eficiente em paralelo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-141">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="9ad8a-142">Quando apropriado, as bibliotecas .NET começaram usando estas instruções para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-142">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="9ad8a-143">Para obter mais informações, consulte [Intrínsecos dependentes da plataforma .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-143">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="9ad8a-144">Executáveis por padrão</span><span class="sxs-lookup"><span data-stu-id="9ad8a-144">Default executables</span></span>

<span data-ttu-id="9ad8a-145">O .NET Core agora compila [executáveis dependentes de estrutura](../deploying/index.md#framework-dependent-executables-fde) por padrão.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-145">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="9ad8a-146">Esse comportamento é novo para aplicativos que usam uma versão do .NET Core instalada globalmente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-146">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="9ad8a-147">Anteriormente, apenas [implantações autocontidas](../deploying/index.md#self-contained-deployments-scd) produziam um executável.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-147">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="9ad8a-148">Durante `dotnet build` ou `dotnet publish`, é criado um executável que corresponde ao ambiente e à plataforma do SDK que você está usando.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-148">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="9ad8a-149">Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-149">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="9ad8a-150">Você pode clicar duas vezes no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-150">You can double-click on the executable.</span></span>
* <span data-ttu-id="9ad8a-151">Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-151">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="9ad8a-152">Executáveis de arquivo único</span><span class="sxs-lookup"><span data-stu-id="9ad8a-152">Single-file executables</span></span>

<span data-ttu-id="9ad8a-153">O comando `dotnet publish` dá suporte ao empacotamento de seu aplicativo em um executável de arquivo único específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-153">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="9ad8a-154">O executável é autoextraível e contém todas as dependências (incluindo nativas) necessárias para a execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-154">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="9ad8a-155">Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-155">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="9ad8a-156">A inicialização é mais rápida quando o aplicativo é executado novamente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-156">Startup is faster when the application is run again.</span></span> <span data-ttu-id="9ad8a-157">O aplicativo não precisará autoextrair uma segunda vez, a menos que uma versão nova tenha sido usada.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-157">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="9ad8a-158">Para publicar um único arquivo executável, defina o `PublishSingleFile` em seu projeto ou na linha de comando com o comando `dotnet publish`:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-158">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="9ad8a-159">Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-159">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="9ad8a-160">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="9ad8a-160">Tiered compilation</span></span>

<span data-ttu-id="9ad8a-161">A TC ([compilação em camadas](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/)) está ativa por padrão com o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-161">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="9ad8a-162">Esse recurso permite que o tempo de execução use de modo mais adaptável o compilador JIT (just-in-time) para obter um melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-162">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="9ad8a-163">O principal benefício de TC é habilitar métodos de (re)jitting com um perfil para produzir o código, que pode ser de qualidade inferior mas mais rápido ou de qualidade superior mas mais lento.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-163">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="9ad8a-164">Isso ajuda a aumentar o desempenho de um aplicativo quando ele passa por vários estágios da execução, desde a inicialização até o estado estável.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-164">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="9ad8a-165">Isso contrasta com a abordagem de não TC, em que cada método é compilado de uma única maneira (o mesmo que a camada de alta qualidade) que é mais voltada para o estado estável em detrimento do desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-165">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="9ad8a-166">Para habilitar o JIT rápido (código com compilação JIT de camada 0), use esta configuração em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-166">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="9ad8a-167">Para desabilitar completamente a TC, use esta configuração em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-167">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="build-copies-dependencies"></a><span data-ttu-id="9ad8a-168">O build copia dependências</span><span class="sxs-lookup"><span data-stu-id="9ad8a-168">Build copies dependencies</span></span>

<span data-ttu-id="9ad8a-169">O comando `dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache NuGet para a pasta de saída de build.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-169">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="9ad8a-170">Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-170">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="9ad8a-171">Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-171">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="9ad8a-172">Ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="9ad8a-172">Local tools</span></span>

<span data-ttu-id="9ad8a-173">O .NET Core 3.0 apresenta ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-173">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="9ad8a-174">Ferramentas locais são semelhantes às [ferramentas globais](../tools/global-tools.md), mas estão associadas a um local específico no disco.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-174">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="9ad8a-175">Ferramentas locais não estão disponíveis globalmente e são distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-175">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="9ad8a-176">Se você tiver tentado ferramentas locais no .NET Core 3.0 Versão Prévia 1, tais como executar `dotnet tool restore` ou `dotnet tool install`, exclua a pasta de cache local de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-176">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="9ad8a-177">Caso contrário, as ferramentas locais não funcionarão em nenhuma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-177">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="9ad8a-178">Essa pasta está localizada em:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-178">This folder is located at:</span></span>
>
> <span data-ttu-id="9ad8a-179">No macOS ou Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-179">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="9ad8a-180">No Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-180">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="9ad8a-181">As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-181">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="9ad8a-182">Esse arquivo de manifesto define as ferramentas que estarão disponíveis nessa pasta e abaixo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-182">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="9ad8a-183">Você pode distribuir o arquivo de manifesto com o seu código para garantir que qualquer pessoa que trabalha com o seu código possa restaurar e usar as mesmas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-183">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="9ad8a-184">Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-184">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="9ad8a-185">Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-185">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="9ad8a-186">Para instalar essas ferramentas, de forma global ou local, você ainda precisará instalar o [Tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-186">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="9ad8a-187">Roll forward de versão principal</span><span class="sxs-lookup"><span data-stu-id="9ad8a-187">Major-version Roll Forward</span></span>

<span data-ttu-id="9ad8a-188">O .NET Core 3.0 introduz um recurso opcional que permite que seu aplicativo efetue roll forward para a versão principal mais recente do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-188">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="9ad8a-189">Adicionalmente, foi adicionada uma nova configuração para controlar como o roll forward é aplicado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-189">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="9ad8a-190">Isso pode ser configurado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-190">This can be configured in the following ways:</span></span>

- <span data-ttu-id="9ad8a-191">Propriedade do arquivo de projeto: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-191">Project file property: `RollForward`</span></span>
- <span data-ttu-id="9ad8a-192">Propriedade do arquivo de configuração de tempo de execução: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-192">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="9ad8a-193">Variável de ambiente: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-193">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="9ad8a-194">Argumento de linha de comando: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="9ad8a-194">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="9ad8a-195">Um dos valores a seguir precisa ser especificado.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-195">One of the following values must be specified.</span></span> <span data-ttu-id="9ad8a-196">Se a configuração for omitida, **Secundária** será o padrão.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-196">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="9ad8a-197">**LatestPatch**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-197">**LatestPatch**\\</span></span>
<span data-ttu-id="9ad8a-198">Efetuar roll forward para a versão de patch mais recente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-198">Roll forward to the highest patch version.</span></span> <span data-ttu-id="9ad8a-199">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-199">This disables minor version roll forward.</span></span>
- <span data-ttu-id="9ad8a-200">**Secundária**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-200">**Minor**\\</span></span>
<span data-ttu-id="9ad8a-201">Se a versão secundária solicitada estiver ausente, efetue roll forward para a menor versão secundária mais alta.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-201">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="9ad8a-202">Se a versão secundária solicitada estiver presente, a política **LatestPatch** será usada.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-202">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="9ad8a-203">**Principal**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-203">**Major**\\</span></span>
<span data-ttu-id="9ad8a-204">Se a versão principal solicitada estiver ausente, efetuar roll forward para a versão principal mais alta e a versão secundária mais baixa.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-204">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="9ad8a-205">Se a versão principal solicitada está presente, a política **Secundária** é usada.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-205">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="9ad8a-206">**LatestMinor**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-206">**LatestMinor**\\</span></span>
<span data-ttu-id="9ad8a-207">Efetuar roll forward para a versão secundária mais recente, mesmo se a versão secundária solicitada estiver presente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-207">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="9ad8a-208">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-208">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="9ad8a-209">**LatestMajor**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-209">**LatestMajor**\\</span></span>
<span data-ttu-id="9ad8a-210">Efetuar roll forward para a versão principal e a secundária mais altas, mesmo se a principal solicitada estiver presente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-210">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="9ad8a-211">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-211">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="9ad8a-212">**Desabilitar**\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-212">**Disable**\\</span></span>
<span data-ttu-id="9ad8a-213">Não efetuar roll forward.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-213">Don't roll forward.</span></span> <span data-ttu-id="9ad8a-214">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-214">Only bind to specified version.</span></span> <span data-ttu-id="9ad8a-215">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-215">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="9ad8a-216">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-216">This value is only recommended for testing.</span></span>

<span data-ttu-id="9ad8a-217">Com a exceção da configuração **Desabilitar**, todas as configurações usarão a versão de patch mais recente disponível.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-217">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="9ad8a-218">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="9ad8a-218">Windows desktop</span></span>

<span data-ttu-id="9ad8a-219">O .NET Core 3.0 dá suporte a aplicativos da Área de Trabalho do Windows usando o Windows Forms e o WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-219">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="9ad8a-220">Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-220">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="9ad8a-221">O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-221">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="9ad8a-222">É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-222">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="9ad8a-223">O Visual Studio 2019 adiciona modelos de **Novo Projeto** ao Windows Forms e WPF no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-223">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="9ad8a-224">Para obter mais informações sobre como portar um aplicativo existente do .NET Framework, consulte [Portar projetos do WPF](../porting/wpf.md) e [Portar projetos do Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-224">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="9ad8a-225">Componentes que podem ser chamados por COM – Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="9ad8a-225">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="9ad8a-226">No Windows, agora você pode criar componentes gerenciados que podem ser chamados por COM.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-226">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="9ad8a-227">Essa funcionalidade é fundamental para usar o .NET Core com modelos de suplemento do COM e também para fornecer paridade com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-227">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="9ad8a-228">Ao contrário do .NET Framework em que o *mscoree. dll* foi usado como o servidor COM, o .NET Core adicionará uma dll de inicializador nativa ao diretório *bin* quando você compilar o componente COM.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-228">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="9ad8a-229">Para obter um exemplo de como criar um componente COM e consumi-lo, veja a [demonstração de COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-229">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="9ad8a-230">Implantação de MSIX – Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="9ad8a-230">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="9ad8a-231">[MSIX](https://docs.microsoft.com/windows/msix/) é um novo formato de pacote de aplicativos do Windows.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-231">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="9ad8a-232">Ele pode ser usado para implantar aplicativos da área de trabalho do .NET Core 3.0 no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-232">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="9ad8a-233">O [Projeto de Empacotamento de Aplicativos do Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponível no Visual Studio 2019, permite criar pacotes MSIX com aplicativos .NET Core [autossuficientes](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-233">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="9ad8a-234">O arquivo de projeto do .NET Core precisa especificar os tempos de execução compatíveis na propriedade `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-234">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="9ad8a-235">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="9ad8a-235">WinForms HighDPI</span></span>

<span data-ttu-id="9ad8a-236">Aplicativos do Windows Forms do .NET Core podem definir o modo de DPI Alto com <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-236">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9ad8a-237">O método `SetHighDpiMode` define o modo de DPI Alto correspondente, a menos que a configuração tenha sido definida por outros meios, tais como `App.Manifest` ou P/Invoke antes de `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-237">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="9ad8a-238">Os valores `highDpiMode` possíveis, conforme expressos pelo enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, são:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-238">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="9ad8a-239">Para obter mais informações sobre os modos de DPI Alto, consulte [Desenvolvimento de aplicativos de área de trabalho de DPI Alto no Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-239">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="9ad8a-240">Intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="9ad8a-240">Ranges and indices</span></span>

<span data-ttu-id="9ad8a-241">O novo tipo <xref:System.Index?displayProperty=nameWithType> pode ser usado para indexação.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-241">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="9ad8a-242">É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-242">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="9ad8a-243">Há também o tipo <xref:System.Range?displayProperty=nameWithType>, que consiste em dois valores `Index` (um para o início e outro para o final) e pode ser escrito com uma expressão de intervalo `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-243">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="9ad8a-244">Em seguida, você pode indexar com um `Range`, o que produz uma fatia:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-244">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="9ad8a-245">Para obter mais informações, consulte o [tutorial de intervalos e índices](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-245">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="9ad8a-246">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="9ad8a-246">Async streams</span></span>

<span data-ttu-id="9ad8a-247">O tipo <xref:System.Collections.Generic.IAsyncEnumerable%601> é uma nova versão assíncrona de <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-247">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="9ad8a-248">A linguagem permite o uso de `await foreach` em `IAsyncEnumerable<T>` para consumir seus elementos e o uso de `yield return` neles para produzir elementos.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-248">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="9ad8a-249">O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-249">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="9ad8a-250">A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-250">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="9ad8a-251">Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-251">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="9ad8a-252">Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-252">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="9ad8a-253">Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-253">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="9ad8a-254">Para obter mais informações, consulte o [tutorial de fluxos assíncronos](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-254">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="9ad8a-255">Melhorias de ponto flutuante IEEE</span><span class="sxs-lookup"><span data-stu-id="9ad8a-255">IEEE Floating-point improvements</span></span>

<span data-ttu-id="9ad8a-256">APIs de ponto flutuante estão sendo atualizadas para entrar em conformidade com a [revisão IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-256">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="9ad8a-257">A meta dessas alterações é expor todas as operações **necessárias** e verificar se elas estão comportamentalmente em conformidade com a especificação IEEE. Para obter mais informações sobre as melhorias de ponto flutuante, consulte a postagem no blog [Aprimoramentos de formatação e análise de ponto flutuante no .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-257">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="9ad8a-258">As correções de análise e formatação incluem:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-258">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="9ad8a-259">Analisar e arredondar corretamente entradas de qualquer tamanho.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-259">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="9ad8a-260">Analisar e formatar corretamente o zero negativo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-260">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="9ad8a-261">Analisar corretamente `Infinity` e `NaN`, fazendo uma verificação sem diferenciação de maiúsculas e minúsculas e permitindo um `+` precedente opcional onde aplicável.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-261">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="9ad8a-262">Novas APIs <xref:System.Math?displayProperty=nameWithType> incluem:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-262">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="9ad8a-263"><xref:System.Math.BitIncrement(System.Double)> e <xref:System.Math.BitDecrement(System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-263"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)>\\</span></span>
<span data-ttu-id="9ad8a-264">Correspondem às operações `nextUp` e `nextDown` do IEEE.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-264">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="9ad8a-265">Retornam o menor número de ponto flutuante que compara o valor maior ou menor que a entrada (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-265">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="9ad8a-266">Por exemplo, `Math.BitIncrement(0.0)` retorna `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-266">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="9ad8a-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> e <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span><span class="sxs-lookup"><span data-stu-id="9ad8a-267"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)>\\</span></span>
<span data-ttu-id="9ad8a-268">Correspondem às operações `maxNumMag` e `minNumMag` do IEEE; retornam o valor maior ou menor em magnitude das duas entradas (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-268">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="9ad8a-269">Por exemplo, `Math.MaxMagnitude(2.0, -3.0)` retorna `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-269">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="9ad8a-270">Corresponde à operação `logB` IEEE que retorna um valor integral, ele retorna o log de base 2 integral do parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-270">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="9ad8a-271">Esse método é praticamente o mesmo que `floor(log2(x))`, mas feito com o mínimo de erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-271">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="9ad8a-272">Corresponde à operação IEEE `scaleB` que usa um valor integral, ele retorna efetivamente `x * pow(2, n)`, mas é feito com o mínimo de erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-272">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="9ad8a-273">Corresponde à operação `log2` do IEEE; retorna o logaritmo de base 2.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-273">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="9ad8a-274">Minimiza o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-274">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="9ad8a-275">Corresponde à operação `fma` do IEEE; executa uma adição e multiplicação fundida.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-275">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="9ad8a-276">Em outras palavras, realiza `(x * y) + z` como uma única operação, minimizando o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-276">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="9ad8a-277">Um exemplo é `FusedMultiplyAdd(1e308, 2.0, -1e308)`, que retorna `1e308`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-277">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="9ad8a-278">O `(1e308 * 2.0) - 1e308` regular retorna `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-278">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="9ad8a-279">Corresponde à operação `copySign` do IEEE; retorna o valor de `x`, mas com o sinal de `y`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-279">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="9ad8a-280">Suporte interno rápido a JSON</span><span class="sxs-lookup"><span data-stu-id="9ad8a-280">Fast built-in JSON support</span></span>

<span data-ttu-id="9ad8a-281">Usuários do .NET têm dependido basicamente de [**Json.NET**](https://www.newtonsoft.com/json) e outras bibliotecas JSON populares, que continuam a ser boas opções.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-281">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="9ad8a-282">O **Json.NET** usa cadeias de caracteres do .NET como seu tipo de dados base, o qual subjacentemente é UTF-16.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-282">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="9ad8a-283">O novo suporte interno ao JSON é de alto desempenho, baixa alocação e baseado em `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-283">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="9ad8a-284">Três novos tipos principais relacionados ao JSON tiveram o namespace <xref:System.Text.Json?displayProperty=nameWithType> adicionados ao .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-284">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9ad8a-285">Esses tipos *ainda* não dão suporte à serialização e desserialização de POCO (objeto CLR básico).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-285">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="9ad8a-286">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="9ad8a-286">Utf8JsonReader</span></span>

<span data-ttu-id="9ad8a-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-287"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="9ad8a-288">O `Utf8JsonReader` é um tipo fundamental, de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-288">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="9ad8a-289">Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-289">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="9ad8a-290">Ele não alocar até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-290">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="9ad8a-291">Aqui está um exemplo de leitura por meio do arquivo [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) criado pelo Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-291">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="9ad8a-292">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="9ad8a-292">Utf8JsonWriter</span></span>

<span data-ttu-id="9ad8a-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> fornece um modo de alto desempenho, não armazenado em cache, somente avanço para escrita de texto JSON codificado em UTF-8 com base em tipos .NET comuns como `String`, `Int32` e `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-293"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="9ad8a-294">Assim como o leitor, o gravador é um tipo fundamental, de baixo nível, que pode ser usado para criar os serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-294">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="9ad8a-295">Gravar uma carga JSON usando o novo `Utf8JsonWriter` é de 30 a 80% mais rápido do que usando o gravador de **Json.NET** e não aloca.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-295">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="9ad8a-296">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="9ad8a-296">JsonDocument</span></span>

<span data-ttu-id="9ad8a-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> é criado com base no `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-297"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="9ad8a-298">O `JsonDocument` fornece a capacidade de analisar dados JSON e criar um DOM (Modelo de Objeto do Documento) somente leitura que pode ser consultado para dar suporte a enumeração e acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-298">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="9ad8a-299">Os elementos JSON que compõem os dados podem ser acessados por meio do tipo <xref:System.Text.Json.JsonElement>, que é exposto pelo `JsonDocument` como uma propriedade chamada `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-299">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="9ad8a-300">O `JsonElement` contém os enumeradores de objeto e de matriz JSON junto com as APIs para converter o texto JSON em tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-300">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="9ad8a-301">Analisar uma carga típica do JSON e acessar todos os seus membros usando o `JsonDocument` é 2 a 3 vezes mais rápido do que o **Json.NET** com poucas alocações para os dados que são dimensionados de forma razoável (ou seja, < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-301">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="9ad8a-302">Este é um uso de exemplo de `JsonDocument` e `JsonElement` que pode ser usado como ponto de partida:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-302">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="9ad8a-303">Aqui está um exemplo em C# 8.0 de leitura por meio do arquivo [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) criado pelo Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-303">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="9ad8a-304">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="9ad8a-304">JsonSerializer</span></span>

<span data-ttu-id="9ad8a-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> baseia-se em <xref:System.Text.Json.Utf8JsonReader> e <xref:System.Text.Json.Utf8JsonWriter> para fornecer uma opção de serialização rápida e de pouca memória ao trabalhar com fragmentos e documentos JSON.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-305"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="9ad8a-306">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md para obter um exemplo para portar para este artigo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-306">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="9ad8a-307">Aqui está um exemplo de como serializar um objeto para JSON:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-307">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="9ad8a-308">Aqui está um exemplo de como desserializar uma cadeia de caracteres JSON para um objeto.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-308">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="9ad8a-309">Você pode usar a cadeia de caracteres JSON produzida pelo exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-309">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="9ad8a-310">Aprimoramentos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9ad8a-310">Interop improvements</span></span>

<span data-ttu-id="9ad8a-311">O .NET Core 3.0 melhora a interoperabilidade de API nativa.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-311">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="9ad8a-312">Tipo: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="9ad8a-312">Type: NativeLibrary</span></span>

<span data-ttu-id="9ad8a-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> fornece um encapsulamento para carregar uma biblioteca nativa (usando a mesma lógica de carga que o .NET Core P/Invoke) e fornecer as funções auxiliares relevantes, tais como `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-313"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="9ad8a-314">Para obter um exemplo de código, consulte a [demonstração de DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-314">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="9ad8a-315">Interoperabilidade nativa do Windows</span><span class="sxs-lookup"><span data-stu-id="9ad8a-315">Windows Native Interop</span></span>

<span data-ttu-id="9ad8a-316">O Windows oferece uma API nativa rica na forma de APIs C simples, COM e WinRT.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-316">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="9ad8a-317">Embora o .NET Core dê suporte a **P/Invoke**, o .NET Core 3.0 adiciona a capacidade de **criar conjuntamente APIs COM** e **ativar APIs WinRT**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-317">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="9ad8a-318">Para obter um exemplo de código, consulte a [demonstração do Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-318">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="9ad8a-319">Compatibilidade com HTTP/2</span><span class="sxs-lookup"><span data-stu-id="9ad8a-319">HTTP/2 support</span></span>

<span data-ttu-id="9ad8a-320">O tipo <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dá suporte ao protocolo HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-320">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="9ad8a-321">O suporte está desabilitado no momento, mas pode ser ativado chamando `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` antes de usar <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-321">Support is currently disabled but can be turned on by calling `AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2Support", true);` before you use <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="9ad8a-322">Você também pode habilitar o suporte a HTTP/2, configurando a variável de ambiente `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` para `true` antes de executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-322">You can also enable HTTP/2 support by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` environment variable to `true` before you run your app.</span></span>

<span data-ttu-id="9ad8a-323">Se o HTTP/2 estiver habilitado, a versão do protocolo HTTP será negociada via TLS/ALPN e HTTP/2 será usado apenas se o servidor selecionar o seu uso.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-323">If HTTP/2 is enabled, the HTTP protocol version will be negotiated via TLS/ALPN, and HTTP/2 will only be used if the server selects to use it.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="9ad8a-324">TLS 1.3 e OpenSSL 1.1.1 no Linux</span><span class="sxs-lookup"><span data-stu-id="9ad8a-324">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="9ad8a-325">O .NET Core agora faz proveito do [suporte a protocolo TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/) quando esse protocolo está disponível em um determinado ambiente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-325">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="9ad8a-326">Com o TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-326">With TLS 1.3:</span></span>

* <span data-ttu-id="9ad8a-327">Tempos de conexão são aprimorados com um menor número de viagens de ida e volta necessárias entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-327">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="9ad8a-328">Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-328">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="9ad8a-329">Quando disponíveis, o .NET Core 3.0 usa **OpenSSL 1.1.1**, **1.1.0** ou **1.0.2** em um sistema Linux.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-329">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="9ad8a-330">Quando o **OpenSSL 1.1.1** está disponível, ambos os tipos <xref:System.Net.Security.SslStream?displayProperty=nameWithType> e <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> usarão o **protocolo TLS 1.3** (supondo que o cliente e o servidor deem suporte ao **protocolo TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-330">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="9ad8a-331">Windows e macOS ainda não oferecem suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-331">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="9ad8a-332">O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-332">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="9ad8a-333">O exemplo de C# 8.0 a seguir demonstra o .NET Core 3.0 no Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-333">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="9ad8a-334">Cifras de criptografia</span><span class="sxs-lookup"><span data-stu-id="9ad8a-334">Cryptography ciphers</span></span>

<span data-ttu-id="9ad8a-335">O .NET 3.0 adiciona o suporte para as criptografias **AES-GCM** e **AES-CCM**, implementadas com <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> e <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-335">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="9ad8a-336">Esses algoritmos são ambos do tipo [AEAD (criptografia autenticada com os dados de associação)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-336">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="9ad8a-337">O código a seguir demonstra como usar criptografia `AesGcm` para criptografar e descriptografar dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-337">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="9ad8a-338">Importar/exportar chave de criptografia</span><span class="sxs-lookup"><span data-stu-id="9ad8a-338">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="9ad8a-339">O .NET Core 3.0 dá suporte à importação e exportação de chaves públicas e privadas assimétricas de formatos padrão.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-339">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="9ad8a-340">Você não precisa usar um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-340">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="9ad8a-341">Todos os tipos principais, tais como *RSA*, *DSA*, *ECDsa* e *ECDiffieHellman*, dão suporte aos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-341">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="9ad8a-342">**Chave pública**</span><span class="sxs-lookup"><span data-stu-id="9ad8a-342">**Public Key**</span></span>
  * <span data-ttu-id="9ad8a-343">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-343">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="9ad8a-344">**Chave privada**</span><span class="sxs-lookup"><span data-stu-id="9ad8a-344">**Private key**</span></span>
  * <span data-ttu-id="9ad8a-345">PKCS nº 8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-345">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="9ad8a-346">PKCS nº 8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-346">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="9ad8a-347">Chaves RSA também dão suporte a:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-347">RSA keys also support:</span></span>

* <span data-ttu-id="9ad8a-348">**Chave pública**</span><span class="sxs-lookup"><span data-stu-id="9ad8a-348">**Public Key**</span></span>
  * <span data-ttu-id="9ad8a-349">PKCS nº 1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="9ad8a-349">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="9ad8a-350">**Chave privada**</span><span class="sxs-lookup"><span data-stu-id="9ad8a-350">**Private key**</span></span>
  * <span data-ttu-id="9ad8a-351">PKCS nº 1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="9ad8a-351">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="9ad8a-352">Os métodos de exportação produzem dados binários codificados em DER e os métodos de importação esperam o mesmo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-352">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="9ad8a-353">Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-353">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="9ad8a-354">Arquivos **PKCS nº 8** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> e **arquivos PFX/PKCS nº 12** podem ser inspecionados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-354">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9ad8a-355">Arquivos **PFX/PKCS nº 12** podem ser manipulados com <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-355">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="9ad8a-356">SerialPort para Linux</span><span class="sxs-lookup"><span data-stu-id="9ad8a-356">SerialPort for Linux</span></span>

<span data-ttu-id="9ad8a-357">O .NET Core 3.0 dá suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-357">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="9ad8a-358">Anteriormente, o .NET Core só dava suporte ao uso de `SerialPort` no Windows.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-358">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="9ad8a-359">Limites de memória do Docker e cgroup</span><span class="sxs-lookup"><span data-stu-id="9ad8a-359">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="9ad8a-360">Da Versão Prévia 3 em diante, a execução do .NET Core 3.0 no Linux com o Docker funciona melhor com limites de memória cgroup.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-360">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="9ad8a-361">Executar um contêiner do Docker com limites de memória, tais como `docker run -m`, altera o comportamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-361">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="9ad8a-362">Tamanho de heap do GC (coletor de lixo) padrão: máximo de 20 MB ou 75% do limite de memória no contêiner.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-362">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="9ad8a-363">O tamanho explícito pode ser definido como um número absoluto ou um percentual do limite de cgroup.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-363">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="9ad8a-364">O tamanho mínimo do segmento reservado por heap de GC é de 16 MB.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-364">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="9ad8a-365">Esse tamanho reduz o número de heaps que são criados em computadores.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-365">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="9ad8a-366">Tamanhos menores de heap de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-366">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="9ad8a-367">O tamanho do heap do coletor de lixo padrão foi reduzido, resultando em menor uso de memória pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-367">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="9ad8a-368">Essa alteração se alinha melhor com o orçamento de alocação de geração 0 com os tamanhos de cache de processadores modernos.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-368">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="9ad8a-369">Suporte de página grande de coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9ad8a-369">Garbage Collection Large Page support</span></span>

<span data-ttu-id="9ad8a-370">Páginas grandes (também conhecidas como páginas enormes no Linux) é um recurso em que o sistema operacional é capaz de estabelecer regiões de memória maiores do que o tamanho da página nativo (geralmente 4K) para melhorar o desempenho do aplicativo que está solicitando essas páginas grandes.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-370">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="9ad8a-371">O coletor de lixo agora pode ser configurado com a configuração **GCLargePages** como um recurso opcional a ser escolhido para alocar páginas grandes no Windows.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-371">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="9ad8a-372">Suporte de GPIO para o Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="9ad8a-372">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="9ad8a-373">Foram lançados dois pacotes para o NuGet que você pode usar para programação de GPIO:</span><span class="sxs-lookup"><span data-stu-id="9ad8a-373">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="9ad8a-374">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="9ad8a-374">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="9ad8a-375">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="9ad8a-375">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="9ad8a-376">Os pacotes GPIO incluem as APIs para dispositivos *GPIO*, *SPI*, *I2C* e *PWM*.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-376">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="9ad8a-377">O pacote de associações de IoT inclui associações de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-377">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="9ad8a-378">Para obter mais informações, veja o [repositório GitHub de dispositivos](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-378">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="9ad8a-379">Suporte a ARM64 no Linux</span><span class="sxs-lookup"><span data-stu-id="9ad8a-379">ARM64 Linux support</span></span>

<span data-ttu-id="9ad8a-380">O .NET Core 3.0 adiciona suporte para ARM64 para Linux.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-380">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="9ad8a-381">O principal caso de uso para ARM64 atualmente é em cenários de IoT.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-381">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="9ad8a-382">Para obter mais informações, consulte [Status do .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="9ad8a-382">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="9ad8a-383">[Imagens do Docker para o .NET Core ARM64](https://hub.docker.com/r/microsoft/dotnet/) estão disponíveis para Alpine, Debian e Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-383">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="9ad8a-384">O suporte do Windows a **ARM64** ainda não está disponível.</span><span class="sxs-lookup"><span data-stu-id="9ad8a-384">**ARM64** Windows support isn't yet available.</span></span>
