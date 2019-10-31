---
title: Catálogo do RID (Identificador de Runtime) do .NET Core
description: Saiba mais sobre o RID (Identificador de runtime) e como os RIDs são usados no .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: e6bc3f75858d4b67cc8598e49ff4ad75521f16d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100914"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="698b7-103">Catálogo de RIDs do .NET Core</span><span class="sxs-lookup"><span data-stu-id="698b7-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="698b7-104">RID é a abreviação de *Identificador de Tempo de Execução*.</span><span class="sxs-lookup"><span data-stu-id="698b7-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="698b7-105">Os valores do RID são usados para identificar plataformas de destino onde o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="698b7-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="698b7-106">Eles são usados por pacotes .NET para representar ativos específicos de plataforma em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="698b7-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="698b7-107">Os seguintes valores são exemplos de RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="698b7-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="698b7-108">Para os pacotes com dependências nativas, o RID designará as plataformas em que o pacote pode ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="698b7-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="698b7-109">Um único RID pode ser definido no elemento `<RuntimeIdentifier>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="698b7-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="698b7-110">Vários RIDs podem ser definidos como uma lista separada por ponto-e-vírgula no elemento `<RuntimeIdentifiers>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="698b7-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="698b7-111">Eles também são usados por meio da opção `--runtime` com os seguintes [comandos da CLI do .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="698b7-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="698b7-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="698b7-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="698b7-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="698b7-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="698b7-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="698b7-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="698b7-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="698b7-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="698b7-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="698b7-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="698b7-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="698b7-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="698b7-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="698b7-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="698b7-119">RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[architecture]-[additional qualifiers]` em que:</span><span class="sxs-lookup"><span data-stu-id="698b7-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="698b7-120">`[os]` é o moniker do sistema operacional/plataforma.</span><span class="sxs-lookup"><span data-stu-id="698b7-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="698b7-121">Por exemplo, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="698b7-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="698b7-122">`[version]` é a versão do sistema operacional na forma de um separado de versão separado por ponto (`.`).</span><span class="sxs-lookup"><span data-stu-id="698b7-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="698b7-123">Por exemplo, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="698b7-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="698b7-124">A versão **não deve** ser uma versão de marketing, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.</span><span class="sxs-lookup"><span data-stu-id="698b7-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="698b7-125">`[architecture]` é a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="698b7-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="698b7-126">Por exemplo: `x86`, `x64`, `arm` ou `arm64`.</span><span class="sxs-lookup"><span data-stu-id="698b7-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="698b7-127">`[additional qualifiers]` distingue diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="698b7-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="698b7-128">Por exemplo: `aot`.</span><span class="sxs-lookup"><span data-stu-id="698b7-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="698b7-129">Gráfico RID</span><span class="sxs-lookup"><span data-stu-id="698b7-129">RID graph</span></span>

<span data-ttu-id="698b7-130">O gráfico RID ou gráfico de fallback de runtime é uma lista de RIDs que são compatíveis entre si.</span><span class="sxs-lookup"><span data-stu-id="698b7-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="698b7-131">Os RIDs são definidos no pacote [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="698b7-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="698b7-132">Você pode ver a lista de RIDs suportados e o gráfico RID no arquivo [*runtime.json*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json), que está localizado no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="698b7-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="698b7-133">Nesse arquivo, você pode ver todos os RIDs, exceto para a base um, que contém uma instrução `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="698b7-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="698b7-134">Essas instruções indicam RIDs compatíveis.</span><span class="sxs-lookup"><span data-stu-id="698b7-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="698b7-135">Quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para o runtime especificado.</span><span class="sxs-lookup"><span data-stu-id="698b7-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="698b7-136">Se uma correspondência exata não for encontrada, o NuGet voltará ao gráfico até encontrar o sistema compatível mais próximo de acordo com o gráfico RID.</span><span class="sxs-lookup"><span data-stu-id="698b7-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="698b7-137">O exemplo a seguir é a entrada real para o RID `osx.10.12-x64`:</span><span class="sxs-lookup"><span data-stu-id="698b7-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="698b7-138">O RID acima especifica que `osx.10.12-x64` importa `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="698b7-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="698b7-139">Desse modo, quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para `osx.10.12-x64` no pacote.</span><span class="sxs-lookup"><span data-stu-id="698b7-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="698b7-140">Se o NuGet não puder encontrar o tempo de execução específico, ele poderá restaurar pacotes que especificam tempos de execução `osx.10.11-x64`, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="698b7-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="698b7-141">O seguinte exemplo mostra um gráfico RID ligeiramente maior, também definido no arquivo *runtime.json*:</span><span class="sxs-lookup"><span data-stu-id="698b7-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="698b7-142">Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.</span><span class="sxs-lookup"><span data-stu-id="698b7-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="698b7-143">Há algumas considerações sobre RIDs das quais você precisa se lembrar ao trabalhar com eles:</span><span class="sxs-lookup"><span data-stu-id="698b7-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="698b7-144">Os RIDs são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas.</span><span class="sxs-lookup"><span data-stu-id="698b7-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="698b7-145">Não crie RIDs de modo programático.</span><span class="sxs-lookup"><span data-stu-id="698b7-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="698b7-146">Use RIDs que já estão definidos para a plataforma.</span><span class="sxs-lookup"><span data-stu-id="698b7-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="698b7-147">Os RIDs precisam ser específicos, portanto, não presuma nada usando o valor RID real.</span><span class="sxs-lookup"><span data-stu-id="698b7-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="698b7-148">Usando RIDs</span><span class="sxs-lookup"><span data-stu-id="698b7-148">Using RIDs</span></span>

<span data-ttu-id="698b7-149">Para poder usar RIDs, você precisa saber quais RIDs existem.</span><span class="sxs-lookup"><span data-stu-id="698b7-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="698b7-150">Novos RIDs são adicionados regularmente à plataforma.</span><span class="sxs-lookup"><span data-stu-id="698b7-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="698b7-151">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="698b7-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="698b7-152">O SDK do .NET Core 2.0 apresenta o conceito de RIDs portáteis.</span><span class="sxs-lookup"><span data-stu-id="698b7-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="698b7-153">Eles são novos valores adicionados ao gráfico RID que não estão associados a uma versão específica ou distribuição de SO e são a opção preferida ao usar o .NET Core 2.0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="698b7-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="698b7-154">Eles são particularmente úteis ao lidar com várias distribuições Linux, já que a maioria dos RIDs de distribuição são mapeados para os RIDs portáteis.</span><span class="sxs-lookup"><span data-stu-id="698b7-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="698b7-155">A lista a seguir mostra um pequeno subconjunto dos RIDs mais comuns usados para cada SO.</span><span class="sxs-lookup"><span data-stu-id="698b7-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="698b7-156">RIDs do Windows</span><span class="sxs-lookup"><span data-stu-id="698b7-156">Windows RIDs</span></span>

<span data-ttu-id="698b7-157">Apenas os valores comuns são listados.</span><span class="sxs-lookup"><span data-stu-id="698b7-157">Only common values are listed.</span></span> <span data-ttu-id="698b7-158">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="698b7-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="698b7-159">Portátil (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="698b7-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="698b7-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="698b7-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="698b7-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="698b7-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="698b7-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="698b7-163">Consulte [Pré-requisitos para o .NET Core no Windows](windows-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="698b7-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="698b7-164">RIDs do Linux</span><span class="sxs-lookup"><span data-stu-id="698b7-164">Linux RIDs</span></span>

<span data-ttu-id="698b7-165">Apenas os valores comuns são listados.</span><span class="sxs-lookup"><span data-stu-id="698b7-165">Only common values are listed.</span></span> <span data-ttu-id="698b7-166">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="698b7-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="698b7-167">Os dispositivos que executam uma distribuição não listada abaixo podem funcionar com um dos RIDs Portáteis.</span><span class="sxs-lookup"><span data-stu-id="698b7-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="698b7-168">Por exemplo, os dispositivos Raspberry Pi executando uma distribuição Linux não listada podem ser direcionados com `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="698b7-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="698b7-169">Portátil (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="698b7-170">`linux-x64` (A maioria das distribuições de área de trabalho como CentOS, Debian, Fedora, Ubuntu e derivados)</span><span class="sxs-lookup"><span data-stu-id="698b7-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="698b7-171">`linux-musl-x64` (Distribuições leves usando [musl](https://wiki.musl-libc.org/projects-using-musl.html), como o Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="698b7-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="698b7-172">`linux-arm` (Distribuições Linux em execução em ARM, como Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="698b7-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="698b7-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="698b7-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="698b7-174">`rhel-x64` (Substituído por `linux-x64` para RHEL acima da versão 6)</span><span class="sxs-lookup"><span data-stu-id="698b7-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="698b7-175">`rhel.6-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="698b7-176">Tizen (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="698b7-177">Consulte [Pré-requisitos para o .NET Core no Linux](linux-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="698b7-177">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="698b7-178">RIDs do macOS</span><span class="sxs-lookup"><span data-stu-id="698b7-178">macOS RIDs</span></span>

<span data-ttu-id="698b7-179">Os RIDs do macOS usam a identidade visual “OSX” mais antiga.</span><span class="sxs-lookup"><span data-stu-id="698b7-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="698b7-180">Apenas os valores comuns são listados.</span><span class="sxs-lookup"><span data-stu-id="698b7-180">Only common values are listed.</span></span> <span data-ttu-id="698b7-181">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="698b7-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="698b7-182">Portátil (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="698b7-183">`osx-x64` (A versão mínima do sistema operacional é macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="698b7-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="698b7-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="698b7-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="698b7-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="698b7-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="698b7-186">macOS 10.12 Sierra (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="698b7-187">macOS 10.13 High Sierra (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="698b7-188">macOS 10.14 Mojave (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="698b7-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="698b7-189">Consulte [Pré-requisitos para o .NET Core no macOS](macos-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="698b7-189">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="698b7-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="698b7-190">See also</span></span>

- [<span data-ttu-id="698b7-191">IDs de Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="698b7-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/readme.md)
