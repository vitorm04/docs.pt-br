---
title: Catálogo do RID (Identificador de Tempo de Execução) do .NET Core
description: Saiba mais sobre o RID (Identificador de tempo de execução) e como os RIDs são usados no .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.openlocfilehash: ff0449f7c6f878131f0ec4b16d685d2c02d26719
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517373"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="56c7b-103">Catálogo de RIDs do .NET Core</span><span class="sxs-lookup"><span data-stu-id="56c7b-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="56c7b-104">RID é a abreviação de *Identificador de Tempo de Execução*.</span><span class="sxs-lookup"><span data-stu-id="56c7b-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="56c7b-105">Os valores do RID são usados para identificar plataformas de destino onde o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="56c7b-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="56c7b-106">Eles são usados por pacotes .NET para representar ativos específicos de plataforma em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="56c7b-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="56c7b-107">Os seguintes valores são exemplos de RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64` ou `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="56c7b-108">Para os pacotes com dependências nativas, o RID designará as plataformas em que o pacote pode ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="56c7b-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="56c7b-109">Um único RID pode ser definido no elemento `<RuntimeIdentifier>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="56c7b-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="56c7b-110">Vários RIDs podem ser definidos como uma lista separada por ponto-e-vírgula no elemento `<RuntimeIdentifiers>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="56c7b-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="56c7b-111">Eles também são usados por meio da opção `--runtime` com os seguintes [comandos da CLI do .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="56c7b-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="56c7b-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="56c7b-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="56c7b-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="56c7b-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="56c7b-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="56c7b-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="56c7b-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="56c7b-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="56c7b-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="56c7b-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="56c7b-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="56c7b-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="56c7b-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="56c7b-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="56c7b-119">RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[architecture]-[additional qualifiers]` em que:</span><span class="sxs-lookup"><span data-stu-id="56c7b-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="56c7b-120">`[os]` é o moniker do sistema operacional/plataforma.</span><span class="sxs-lookup"><span data-stu-id="56c7b-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="56c7b-121">Por exemplo, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="56c7b-122">`[version]` é a versão do sistema operacional na forma de um separado de versão separado por ponto (`.`).</span><span class="sxs-lookup"><span data-stu-id="56c7b-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="56c7b-123">Por exemplo, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="56c7b-124">A versão **não deve** ser uma versão de marketing, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.</span><span class="sxs-lookup"><span data-stu-id="56c7b-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="56c7b-125">`[architecture]` é a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="56c7b-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="56c7b-126">Por exemplo: `x86`, `x64`, `arm` ou `arm64`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="56c7b-127">`[additional qualifiers]` distingue diferentes plataformas.</span><span class="sxs-lookup"><span data-stu-id="56c7b-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="56c7b-128">Por exemplo `aot` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="56c7b-129">Gráfico RID</span><span class="sxs-lookup"><span data-stu-id="56c7b-129">RID graph</span></span>

<span data-ttu-id="56c7b-130">O gráfico RID ou gráfico de fallback de tempo de execução é uma lista de RIDs que são compatíveis entre si.</span><span class="sxs-lookup"><span data-stu-id="56c7b-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="56c7b-131">Os RIDs são definidos no pacote [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/).</span><span class="sxs-lookup"><span data-stu-id="56c7b-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="56c7b-132">Você pode ver a lista de RIDs suportados e o gráfico RID no arquivo [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json), que está localizado no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="56c7b-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="56c7b-133">Nesse arquivo, você pode ver todos os RIDs, exceto para a base um, que contém uma instrução `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="56c7b-134">Essas instruções indicam RIDs compatíveis.</span><span class="sxs-lookup"><span data-stu-id="56c7b-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="56c7b-135">Quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para o tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="56c7b-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="56c7b-136">Se uma correspondência exata não for encontrada, o NuGet voltará ao gráfico até encontrar o sistema compatível mais próximo de acordo com o gráfico RID.</span><span class="sxs-lookup"><span data-stu-id="56c7b-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="56c7b-137">O exemplo a seguir é a entrada real para o RID `osx.10.12-x64`:</span><span class="sxs-lookup"><span data-stu-id="56c7b-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="56c7b-138">O RID acima especifica que `osx.10.12-x64` importa `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="56c7b-139">Desse modo, quando o NuGet restaura pacotes, ele tenta encontrar uma correspondência exata para `osx.10.12-x64` no pacote.</span><span class="sxs-lookup"><span data-stu-id="56c7b-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="56c7b-140">Se o NuGet não puder encontrar o tempo de execução específico, ele poderá restaurar pacotes que especificam tempos de execução `osx.10.11-x64`, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="56c7b-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="56c7b-141">O seguinte exemplo mostra um gráfico RID ligeiramente maior, também definido no arquivo *runtime.json*:</span><span class="sxs-lookup"><span data-stu-id="56c7b-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="56c7b-142">Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.</span><span class="sxs-lookup"><span data-stu-id="56c7b-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="56c7b-143">Há algumas considerações sobre RIDs das quais você precisa se lembrar ao trabalhar com eles:</span><span class="sxs-lookup"><span data-stu-id="56c7b-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="56c7b-144">Os RIDs são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas.</span><span class="sxs-lookup"><span data-stu-id="56c7b-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="56c7b-145">Não crie RIDs de modo programático.</span><span class="sxs-lookup"><span data-stu-id="56c7b-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="56c7b-146">Use RIDs que já estão definidos para a plataforma.</span><span class="sxs-lookup"><span data-stu-id="56c7b-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="56c7b-147">Os RIDs precisam ser específicos, portanto, não presuma nada usando o valor RID real.</span><span class="sxs-lookup"><span data-stu-id="56c7b-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="56c7b-148">Usando RIDs</span><span class="sxs-lookup"><span data-stu-id="56c7b-148">Using RIDs</span></span>

<span data-ttu-id="56c7b-149">Para poder usar RIDs, você precisa saber quais RIDs existem.</span><span class="sxs-lookup"><span data-stu-id="56c7b-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="56c7b-150">Novos RIDs são adicionados regularmente à plataforma.</span><span class="sxs-lookup"><span data-stu-id="56c7b-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="56c7b-151">Para obter a versão completa e mais recente, confira o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="56c7b-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="56c7b-152">O SDK do .NET Core 2.0 apresenta o conceito de RIDs portáteis.</span><span class="sxs-lookup"><span data-stu-id="56c7b-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="56c7b-153">Eles são novos valores adicionados ao gráfico RID que não estão associados a uma versão específica ou distribuição de SO.</span><span class="sxs-lookup"><span data-stu-id="56c7b-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="56c7b-154">Eles são particularmente úteis ao lidar com várias distribuições Linux.</span><span class="sxs-lookup"><span data-stu-id="56c7b-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="56c7b-155">A lista a seguir mostra os RIDs mais comuns usados para cada SO.</span><span class="sxs-lookup"><span data-stu-id="56c7b-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="56c7b-156">Ela não cobre os valores `arm` ou `corert`.</span><span class="sxs-lookup"><span data-stu-id="56c7b-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="56c7b-157">RIDs do Windows</span><span class="sxs-lookup"><span data-stu-id="56c7b-157">Windows RIDs</span></span>

- <span data-ttu-id="56c7b-158">Portáteis</span><span class="sxs-lookup"><span data-stu-id="56c7b-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="56c7b-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="56c7b-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="56c7b-160">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="56c7b-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="56c7b-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="56c7b-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="56c7b-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="56c7b-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="56c7b-163">Consulte [Pré-requisitos para o .NET Core no Windows](windows-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="56c7b-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="56c7b-164">RIDs do Linux</span><span class="sxs-lookup"><span data-stu-id="56c7b-164">Linux RIDs</span></span>

- <span data-ttu-id="56c7b-165">Portáteis</span><span class="sxs-lookup"><span data-stu-id="56c7b-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="56c7b-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="56c7b-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="56c7b-167">Debian</span><span class="sxs-lookup"><span data-stu-id="56c7b-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
  - <span data-ttu-id="56c7b-168">`debian.9-x64` (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-168">`debian.9-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="56c7b-169">Fedora</span><span class="sxs-lookup"><span data-stu-id="56c7b-169">Fedora</span></span>
  - `fedora-x64`
  - `fedora.27-x64`
  - <span data-ttu-id="56c7b-170">`fedora.28-x64` (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-170">`fedora.28-x64` (.NET Core 1.1 or later versions)</span></span>
- <span data-ttu-id="56c7b-171">Gentoo (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="56c7b-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="56c7b-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- <span data-ttu-id="56c7b-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="56c7b-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- <span data-ttu-id="56c7b-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="56c7b-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="56c7b-175">`rhel.6-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="56c7b-176">`rhel.7.3-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="56c7b-177">`rhel.7.4-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="56c7b-178">Tizen (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- <span data-ttu-id="56c7b-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56c7b-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- <span data-ttu-id="56c7b-180">Derivados do Ubuntu</span><span class="sxs-lookup"><span data-stu-id="56c7b-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - <span data-ttu-id="56c7b-181">`linuxmint.18-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-181">`linuxmint.18-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="56c7b-182">`linuxmint.18.1-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-182">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="56c7b-183">`linuxmint.18.2-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-183">`linuxmint.18.2-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="56c7b-184">`linuxmint.18.3-x64` (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-184">`linuxmint.18.3-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="56c7b-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-185">SUSE Enterprise Linux (SLES) (.NET Core 2.0 or later versions)</span></span>
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- <span data-ttu-id="56c7b-186">Alpine Linux (.NET Core 2.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-186">Alpine Linux (.NET Core 2.1 or later versions)</span></span>
  - `alpine-x64`
  - `alpine.3.7-x64`

<span data-ttu-id="56c7b-187">Consulte [Pré-requisitos para o .NET Core no Linux](linux-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="56c7b-187">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="56c7b-188">RIDs do macOS</span><span class="sxs-lookup"><span data-stu-id="56c7b-188">macOS RIDs</span></span>

<span data-ttu-id="56c7b-189">Os RIDs do macOS usam a identidade visual “OSX” mais antiga.</span><span class="sxs-lookup"><span data-stu-id="56c7b-189">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="56c7b-190">`osx-x64` (.NET Core 2.0 ou versões posteriores; a versão mínima é `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="56c7b-190">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="56c7b-191">`osx.10.12-x64` (.NET Core 1.1 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-191">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="56c7b-192">Consulte [Pré-requisitos para o .NET Core no macOS](macos-prerequisites.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="56c7b-192">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="56c7b-193">RIDs Android (.NET Core 2.0 ou versões posteriores)</span><span class="sxs-lookup"><span data-stu-id="56c7b-193">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="56c7b-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56c7b-194">See also</span></span>

* [<span data-ttu-id="56c7b-195">IDs de Tempo de Execução</span><span class="sxs-lookup"><span data-stu-id="56c7b-195">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
