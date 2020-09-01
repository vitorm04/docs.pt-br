---
title: Instalar o .NET Core no macOS
description: Saiba mais sobre quais versões do macOS você pode instalar o .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 19d5ca77b0308533c8f228be70c61daf1b7f82d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132749"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="4c601-103">Instalar o .NET Core no macOS</span><span class="sxs-lookup"><span data-stu-id="4c601-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Instalar no Windows](windows.md)
> - [Instalar no macOS](macos.md)
> - [Instalar no Linux](linux.md)

<span data-ttu-id="4c601-107">Neste artigo, você aprenderá a instalar o .NET Core no macOS.</span><span class="sxs-lookup"><span data-stu-id="4c601-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="4c601-108">O .NET Core é composto do tempo de execução e do SDK.</span><span class="sxs-lookup"><span data-stu-id="4c601-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="4c601-109">O tempo de execução é usado para executar um aplicativo .NET Core e pode ou não ser incluído com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c601-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="4c601-110">O SDK é usado para criar bibliotecas e aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="4c601-111">O tempo de execução do .NET Core é sempre instalado com o SDK.</span><span class="sxs-lookup"><span data-stu-id="4c601-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="4c601-112">A versão mais recente do .NET Core é a 3,1.</span><span class="sxs-lookup"><span data-stu-id="4c601-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4c601-113">Baixe o .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c601-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="4c601-114">Versões com suporte</span><span class="sxs-lookup"><span data-stu-id="4c601-114">Supported releases</span></span>

<span data-ttu-id="4c601-115">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do macOS nas quais elas têm suporte.</span><span class="sxs-lookup"><span data-stu-id="4c601-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="4c601-116">Essas versões permanecem com suporte, ou seja, a versão do [.NET Core atinge o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4c601-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="4c601-117">Um ✔️ indica que a versão do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="4c601-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="4c601-118">Um ❌ indica que a versão do .NET Core não tem suporte.</span><span class="sxs-lookup"><span data-stu-id="4c601-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="4c601-119">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="4c601-119">Operating System</span></span>          | <span data-ttu-id="4c601-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4c601-120">.NET Core 2.1</span></span> | <span data-ttu-id="4c601-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4c601-121">.NET Core 3.1</span></span> | <span data-ttu-id="4c601-122">Versão prévia do .NET 5</span><span class="sxs-lookup"><span data-stu-id="4c601-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4c601-123">macOS 10,15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="4c601-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="4c601-124">✔️ 2,1 ([notas de versão][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c601-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c601-125">✔️ 3,1 ([notas de versão][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c601-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c601-126">✔️ 5,0 Preview ([notas de versão][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c601-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c601-127">macOS 10,14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="4c601-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="4c601-128">✔️ 2,1 ([notas de versão][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c601-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c601-129">✔️ 3,1 ([notas de versão][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c601-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c601-130">✔️ 5,0 Preview ([notas de versão][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c601-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c601-131">macOS 10,13 "alta serra"</span><span class="sxs-lookup"><span data-stu-id="4c601-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="4c601-132">✔️ 2,1 ([notas de versão][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c601-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c601-133">✔️ 3,1 ([notas de versão][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c601-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c601-134">✔️ 5,0 Preview ([notas de versão][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c601-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4c601-135">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="4c601-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="4c601-136">✔️ 2,1 ([notas de versão][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4c601-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4c601-137">❌ 3,1 ([notas de versão][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4c601-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4c601-138">❌ 5,0 visualização ([notas de versão][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4c601-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="4c601-139">Versões sem suporte</span><span class="sxs-lookup"><span data-stu-id="4c601-139">Unsupported releases</span></span>

<span data-ttu-id="4c601-140">Não há mais suporte para as seguintes versões do .NET Core ❌ .</span><span class="sxs-lookup"><span data-stu-id="4c601-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="4c601-141">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="4c601-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4c601-142">3,0 ([notas de versão][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="4c601-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="4c601-143">2,2 ([notas de versão][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="4c601-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="4c601-144">2,0 ([notas de versão][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="4c601-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="4c601-145">Informações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4c601-145">Runtime information</span></span>

<span data-ttu-id="4c601-146">O tempo de execução é usado para executar aplicativos criados com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="4c601-147">Quando um autor de aplicativo publica um aplicativo, ele pode incluir o tempo de execução com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c601-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="4c601-148">Se eles não incluírem o tempo de execução, cabe ao usuário instalar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c601-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="4c601-149">Há três tempos de execução diferentes que você pode instalar no macOS:</span><span class="sxs-lookup"><span data-stu-id="4c601-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="4c601-150">*Tempo de execução ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="4c601-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="4c601-151">Executa ASP.NET Core aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4c601-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="4c601-152">Inclui o tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="4c601-153">*Tempo de execução do .NET Core*</span><span class="sxs-lookup"><span data-stu-id="4c601-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="4c601-154">Esse tempo de execução é o tempo de execução mais simples e não inclui nenhum outro tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c601-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="4c601-155">É altamente recomendável que você instale o *ASP.NET Core Runtime* para obter a melhor compatibilidade com os aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4c601-156">Baixar o tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c601-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="4c601-157">Informações do SDK</span><span class="sxs-lookup"><span data-stu-id="4c601-157">SDK information</span></span>

<span data-ttu-id="4c601-158">O SDK é usado para compilar e publicar aplicativos e bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="4c601-159">A instalação do SDK inclui ambos os [tempos de execução](#runtime-information): ASP.NET Core e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4c601-160">Baixar o SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c601-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="4c601-161">Dependências</span><span class="sxs-lookup"><span data-stu-id="4c601-161">Dependencies</span></span>

<span data-ttu-id="4c601-162">O .NET Core tem suporte nas seguintes versões do macOS:</span><span class="sxs-lookup"><span data-stu-id="4c601-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="4c601-163">Um `+` símbolo representa a versão mínima.</span><span class="sxs-lookup"><span data-stu-id="4c601-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4c601-164">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c601-164">.NET Core Version</span></span> | <span data-ttu-id="4c601-165">macOS</span><span class="sxs-lookup"><span data-stu-id="4c601-165">macOS</span></span>                 | <span data-ttu-id="4c601-166">Arquiteturas</span><span class="sxs-lookup"><span data-stu-id="4c601-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="4c601-167">3.1</span><span class="sxs-lookup"><span data-stu-id="4c601-167">3.1</span></span>               | <span data-ttu-id="4c601-168">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="4c601-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4c601-169">x64</span><span class="sxs-lookup"><span data-stu-id="4c601-169">x64</span></span> | [<span data-ttu-id="4c601-170">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4c601-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="4c601-171">3.0</span><span class="sxs-lookup"><span data-stu-id="4c601-171">3.0</span></span>               | <span data-ttu-id="4c601-172">Alta serra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="4c601-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4c601-173">x64</span><span class="sxs-lookup"><span data-stu-id="4c601-173">x64</span></span> | [<span data-ttu-id="4c601-174">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4c601-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="4c601-175">2,2</span><span class="sxs-lookup"><span data-stu-id="4c601-175">2.2</span></span>               | <span data-ttu-id="4c601-176">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="4c601-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="4c601-177">x64</span><span class="sxs-lookup"><span data-stu-id="4c601-177">x64</span></span> | [<span data-ttu-id="4c601-178">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4c601-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="4c601-179">2.1</span><span class="sxs-lookup"><span data-stu-id="4c601-179">2.1</span></span>               | <span data-ttu-id="4c601-180">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="4c601-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="4c601-181">x64</span><span class="sxs-lookup"><span data-stu-id="4c601-181">x64</span></span> | [<span data-ttu-id="4c601-182">Mais informações</span><span class="sxs-lookup"><span data-stu-id="4c601-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="4c601-183">A partir do macOS Catalina (versão 10,15), todo software criado após 1º de junho de 2019 que é distribuído com a ID do desenvolvedor deve ser notarized.</span><span class="sxs-lookup"><span data-stu-id="4c601-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="4c601-184">Esse requisito se aplica ao tempo de execução do .NET Core, SDK do .NET Core e software criado com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="4c601-185">Os instaladores do .NET Core (Runtime e SDK) versões 3,1, 3,0 e 2,1, foram notarizeddos desde 18 de fevereiro de 2020.</span><span class="sxs-lookup"><span data-stu-id="4c601-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="4c601-186">Versões anteriores liberadas não são notarized.</span><span class="sxs-lookup"><span data-stu-id="4c601-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="4c601-187">Se você executar um aplicativo não notarized, verá um erro semelhante à imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="4c601-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerta de notarization Catalina do macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="4c601-189">Para obter mais informações sobre como o imforced-notarization afeta o .NET Core (e seus aplicativos .NET Core), consulte [trabalhando com o MacOS Catalina notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="4c601-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="4c601-190">libgdiplus</span></span>

<span data-ttu-id="4c601-191">Os aplicativos .NET Core que usam o assembly *System. sorteio. Common* exigem que o libgdiplus seja instalado.</span><span class="sxs-lookup"><span data-stu-id="4c601-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="4c601-192">Uma maneira fácil de obter o libgdiplus é usando o Gerenciador de pacotes [homebrew ("Brew")](https://brew.sh/) para MacOS.</span><span class="sxs-lookup"><span data-stu-id="4c601-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="4c601-193">Depois de instalar o *Brew*, instale o libgdiplus executando os seguintes comandos em um prompt de terminal (comando):</span><span class="sxs-lookup"><span data-stu-id="4c601-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="4c601-194">Instalar com um instalador</span><span class="sxs-lookup"><span data-stu-id="4c601-194">Install with an installer</span></span>

<span data-ttu-id="4c601-195">o macOS tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="4c601-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="4c601-196">CPUs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="4c601-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="4c601-197">Baixar e instalar manualmente</span><span class="sxs-lookup"><span data-stu-id="4c601-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="4c601-198">Como alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o SDK e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c601-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="4c601-199">A instalação manual geralmente é executada como parte do teste de integração contínua.</span><span class="sxs-lookup"><span data-stu-id="4c601-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="4c601-200">Para um desenvolvedor ou usuário, geralmente é melhor usar um [instalador](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4c601-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="4c601-201">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="4c601-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="4c601-202">Primeiro, Baixe uma versão **binária** para o SDK ou o tempo de execução de um dos seguintes sites:</span><span class="sxs-lookup"><span data-stu-id="4c601-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="4c601-203">✔️ [downloads da versão prévia do .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="4c601-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="4c601-204">downloads do ✔️ [.NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="4c601-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="4c601-205">downloads do ✔️ [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="4c601-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="4c601-206">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c601-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="4c601-207">Em seguida, extraia o arquivo baixado e use o `export` comando para definir as variáveis usadas pelo .NET Core e, em seguida, verifique se o .NET Core está no caminho.</span><span class="sxs-lookup"><span data-stu-id="4c601-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="4c601-208">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro Baixe uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="4c601-209">Em seguida, abra um terminal e execute os seguintes comandos no diretório em que o arquivo foi salvo.</span><span class="sxs-lookup"><span data-stu-id="4c601-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="4c601-210">O nome do arquivo morto pode ser diferente dependendo do que você baixou.</span><span class="sxs-lookup"><span data-stu-id="4c601-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="4c601-211">**Use o seguinte comando para extrair o tempo de execução**:</span><span class="sxs-lookup"><span data-stu-id="4c601-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="4c601-212">**Use o seguinte comando para extrair o SDK**:</span><span class="sxs-lookup"><span data-stu-id="4c601-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="4c601-213">Os `export` comandos anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="4c601-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="4c601-214">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="4c601-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="4c601-215">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="4c601-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="4c601-216">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4c601-216">For example:</span></span>
>
> - <span data-ttu-id="4c601-217">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="4c601-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="4c601-218">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="4c601-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="4c601-219">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="4c601-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="4c601-220">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da `PATH` instrução existente.</span><span class="sxs-lookup"><span data-stu-id="4c601-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="4c601-221">Se nenhuma `PATH` instrução for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="4c601-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="4c601-222">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4c601-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="4c601-223">Essa abordagem permite que você instale versões diferentes em locais separados e escolha explicitamente qual deles usar por qual aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c601-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="4c601-224">Instalar com o Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="4c601-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="4c601-225">Visual Studio para Mac instala o SDK do .NET Core quando a carga de trabalho do **.NET Core** é selecionada.</span><span class="sxs-lookup"><span data-stu-id="4c601-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="4c601-226">Para começar a usar o desenvolvimento do .NET Core no macOS, consulte [instalar o Visual Studio 2019 para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="4c601-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="4c601-227">Para a versão mais recente, o .NET Core 3,1, você deve usar o Visual Studio para Mac 8,4.</span><span class="sxs-lookup"><span data-stu-id="4c601-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="4c601-228">[![recurso macOS Visual Studio 2019 para Mac com carga de trabalho do .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="4c601-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="4c601-229">Instalar junto com Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4c601-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="4c601-230">Visual Studio Code é um editor de código-fonte leve e avançado que é executado em sua área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4c601-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="4c601-231">Visual Studio Code está disponível para Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="4c601-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="4c601-232">Embora Visual Studio Code não venha com um instalador .NET Core automatizado como o Visual Studio, adicionar o suporte ao .NET Core é simples.</span><span class="sxs-lookup"><span data-stu-id="4c601-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="4c601-233">[Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="4c601-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="4c601-234">[Baixe e instale o SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4c601-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="4c601-235">[Instale a extensão C# do Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="4c601-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="4c601-236">Instalar com a automação do bash</span><span class="sxs-lookup"><span data-stu-id="4c601-236">Install with bash automation</span></span>

<span data-ttu-id="4c601-237">Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c601-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="4c601-238">Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="4c601-239">O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4c601-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="4c601-240">Você pode escolher uma versão específica especificando a `current` opção.</span><span class="sxs-lookup"><span data-stu-id="4c601-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="4c601-241">Inclua a `runtime` opção para instalar um tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c601-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="4c601-242">Caso contrário, o script instalará o [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-242">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="4c601-243">O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima.</span><span class="sxs-lookup"><span data-stu-id="4c601-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="4c601-244">O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4c601-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="4c601-245">Docker</span><span class="sxs-lookup"><span data-stu-id="4c601-245">Docker</span></span>

<span data-ttu-id="4c601-246">Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host.</span><span class="sxs-lookup"><span data-stu-id="4c601-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="4c601-247">Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c601-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="4c601-248">O .NET Core pode ser executado em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="4c601-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="4c601-249">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="4c601-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="4c601-250">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="4c601-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="4c601-251">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="4c601-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="4c601-252">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="4c601-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="4c601-253">Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c601-254">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4c601-254">Next steps</span></span>

- <span data-ttu-id="4c601-255">[Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="4c601-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="4c601-256">[Trabalhando com o notarization Catalina do MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="4c601-257">[Tutorial: introdução ao MacOS](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-257">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="4c601-258">[Tutorial: criar um novo aplicativo com Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="4c601-259">[Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="4c601-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
