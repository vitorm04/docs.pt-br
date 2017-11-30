---
title: "Catálogo do RID (Identificador de Tempo de Execução) do .NET Core"
description: "Saiba mais sobre o RID (Identificador de tempo de execução) e como os RIDs são usados no .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="15d2c-103">Catálogo de RIDs do .NET Core</span><span class="sxs-lookup"><span data-stu-id="15d2c-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="15d2c-104">RID é a abreviação de *Identificador de Tempo de Execução*.</span><span class="sxs-lookup"><span data-stu-id="15d2c-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="15d2c-105">Os valores do RID são usados para identificar plataformas de destino onde o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="15d2c-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="15d2c-106">Eles são usados por pacotes .NET para representar ativos específicos de plataforma em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="15d2c-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="15d2c-107">Os seguintes valores são exemplos de RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="15d2c-108">Para os pacotes com dependências nativas, o RID designará as plataformas em que o pacote pode ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="15d2c-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="15d2c-109">Os RIDs podem ser definidos no elemento `<RuntimeIdentifier>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="15d2c-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="15d2c-110">Eles também são usados por meio da opção `--runtime` com os seguintes [comandos da CLI do .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="15d2c-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="15d2c-111">dotnet build</span><span class="sxs-lookup"><span data-stu-id="15d2c-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="15d2c-112">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="15d2c-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="15d2c-113">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="15d2c-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="15d2c-114">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="15d2c-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="15d2c-115">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="15d2c-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="15d2c-116">dotnet run</span><span class="sxs-lookup"><span data-stu-id="15d2c-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="15d2c-117">dotnet store</span><span class="sxs-lookup"><span data-stu-id="15d2c-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="15d2c-118">RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[architecture]-[additional qualifiers]` em que:</span><span class="sxs-lookup"><span data-stu-id="15d2c-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="15d2c-119">`[os]` é o moniker do sistema operacional/plataforma.</span><span class="sxs-lookup"><span data-stu-id="15d2c-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="15d2c-120">Por exemplo, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="15d2c-121">`[version]` é a versão do sistema operacional na forma de um separado de versão separado por ponto (`.`).</span><span class="sxs-lookup"><span data-stu-id="15d2c-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="15d2c-122">Por exemplo, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="15d2c-123">A versão **não deve** ser uma versão de marketing, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.</span><span class="sxs-lookup"><span data-stu-id="15d2c-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="15d2c-124">`[architecture]` é a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="15d2c-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="15d2c-125">Por exemplo: `x86`, `x64`, `arm` ou `arm64`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="15d2c-126">`[additional qualifiers]` distingue diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="15d2c-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="15d2c-127">Por exemplo `aot` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="15d2c-128">Gráfico RID</span><span class="sxs-lookup"><span data-stu-id="15d2c-128">RID graph</span></span>

<span data-ttu-id="15d2c-129">O gráfico RID ou gráfico de fallback de tempo de execução é uma lista de RIDs que são compatíveis entre si.</span><span class="sxs-lookup"><span data-stu-id="15d2c-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="15d2c-130">Os RIDs são definidos no pacote [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="15d2c-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="15d2c-131">Você pode ver a lista de RIDs suportados e o gráfico RID no arquivo [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json), que está localizado no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="15d2c-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="15d2c-132">Nesse arquivo, você pode ver todos os RIDs, exceto para a base um, que contém uma instrução `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="15d2c-133">Essas instruções indicam RIDs compatíveis.</span><span class="sxs-lookup"><span data-stu-id="15d2c-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="15d2c-134">Quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para o tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="15d2c-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="15d2c-135">Se uma correspondência exata não for encontrada, o NuGet voltará ao gráfico até encontrar o sistema compatível mais próximo de acordo com o gráfico RID.</span><span class="sxs-lookup"><span data-stu-id="15d2c-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="15d2c-136">O exemplo a seguir é a entrada real para o RID `osx.10.12-x64`:</span><span class="sxs-lookup"><span data-stu-id="15d2c-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="15d2c-137">O RID acima especifica que `osx.10.12-x64` importa `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="15d2c-138">Desse modo, quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para `osx.10.12-x64` no pacote.</span><span class="sxs-lookup"><span data-stu-id="15d2c-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="15d2c-139">Se o NuGet não puder encontrar o tempo de execução específico, ele poderá restaurar pacotes que especificam tempos de execução `osx.10.11-x64`, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="15d2c-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="15d2c-140">O seguinte exemplo mostra um gráfico RID ligeiramente maior, também definido no arquivo *runtime.json*:</span><span class="sxs-lookup"><span data-stu-id="15d2c-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="15d2c-141">Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.</span><span class="sxs-lookup"><span data-stu-id="15d2c-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="15d2c-142">Há algumas considerações sobre RIDs das quais você precisa se lembrar ao trabalhar com eles:</span><span class="sxs-lookup"><span data-stu-id="15d2c-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="15d2c-143">Os RIDs são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas.</span><span class="sxs-lookup"><span data-stu-id="15d2c-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="15d2c-144">Não crie RIDs de modo programático.</span><span class="sxs-lookup"><span data-stu-id="15d2c-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="15d2c-145">Use RIDs que já estão definidos para a plataforma.</span><span class="sxs-lookup"><span data-stu-id="15d2c-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="15d2c-146">Os RIDs precisam ser específicos, portanto, não presuma nada usando o valor RID real.</span><span class="sxs-lookup"><span data-stu-id="15d2c-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="15d2c-147">Usando RIDs</span><span class="sxs-lookup"><span data-stu-id="15d2c-147">Using RIDs</span></span>

<span data-ttu-id="15d2c-148">Para poder usar RIDs, você precisa saber quais RIDs existem.</span><span class="sxs-lookup"><span data-stu-id="15d2c-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="15d2c-149">Novos RIDs são adicionados regularmente à plataforma.</span><span class="sxs-lookup"><span data-stu-id="15d2c-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="15d2c-150">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="15d2c-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="15d2c-151">O SDK do .NET Core 2.0 apresenta o conceito de RIDs portáteis.</span><span class="sxs-lookup"><span data-stu-id="15d2c-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="15d2c-152">Eles são novos valores adicionados ao gráfico RID que não estão associados a uma versão específica ou distribuição de SO.</span><span class="sxs-lookup"><span data-stu-id="15d2c-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="15d2c-153">Eles são particularmente úteis ao lidar com várias distribuições de Linux.</span><span class="sxs-lookup"><span data-stu-id="15d2c-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="15d2c-154">A lista a seguir mostra os RIDs mais comuns usados para cada SO.</span><span class="sxs-lookup"><span data-stu-id="15d2c-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="15d2c-155">Ela não cobre os valores `arm` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="15d2c-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="15d2c-156">RIDs do Windows</span><span class="sxs-lookup"><span data-stu-id="15d2c-156">Windows RIDs</span></span>

- <span data-ttu-id="15d2c-157">Portáteis</span><span class="sxs-lookup"><span data-stu-id="15d2c-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="15d2c-158">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="15d2c-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="15d2c-159">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="15d2c-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="15d2c-160">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="15d2c-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="15d2c-161">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="15d2c-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="15d2c-162">Consulte [pré-requisitos para o .NET Core no Windows](windows-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="15d2c-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="15d2c-163">RIDs do Linux</span><span class="sxs-lookup"><span data-stu-id="15d2c-163">Linux RIDs</span></span>

- <span data-ttu-id="15d2c-164">Portáteis</span><span class="sxs-lookup"><span data-stu-id="15d2c-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="15d2c-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="15d2c-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="15d2c-166">Debian</span><span class="sxs-lookup"><span data-stu-id="15d2c-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="15d2c-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="15d2c-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="15d2c-168">`fedora.25-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="15d2c-169">`fedora.26-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="15d2c-170">Gentoo (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="15d2c-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="15d2c-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="15d2c-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="15d2c-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="15d2c-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="15d2c-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="15d2c-174">`rhel.6-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="15d2c-175">`rhel.7.3-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="15d2c-176">`rhel.7.4-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="15d2c-177">Tizen (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="15d2c-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="15d2c-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="15d2c-179">Derivados do Ubuntu</span><span class="sxs-lookup"><span data-stu-id="15d2c-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="15d2c-180">`linuxmint.18.1-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="15d2c-181">Consulte [pré-requisitos para o .NET Core no Linux](linux-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="15d2c-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="15d2c-182">macOS RIDs</span><span class="sxs-lookup"><span data-stu-id="15d2c-182">macOS RIDs</span></span>

<span data-ttu-id="15d2c-183">macOS RIDs usam a marca de "OSX" mais antigos.</span><span class="sxs-lookup"><span data-stu-id="15d2c-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="15d2c-184">`osx-x64`(.NET core 2.0 ou versões posteriores, a versão mínima é `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="15d2c-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="15d2c-185">`osx.10.12-x64` (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="15d2c-186">Consulte [pré-requisitos para o .NET Core em macOS](macos-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="15d2c-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="15d2c-187">RIDs Android (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="15d2c-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="15d2c-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15d2c-188">See also</span></span>

[<span data-ttu-id="15d2c-189">IDs de Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="15d2c-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
