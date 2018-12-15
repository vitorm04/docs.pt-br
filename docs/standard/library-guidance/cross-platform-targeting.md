---
title: Direcionamento para bibliotecas do .NET multiplataforma
description: Recomendações de melhores práticas para a criação de bibliotecas do .NET multiplataforma.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6bd310f2e4b7a9bd7bb550ed9c7da9ebabdf64ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129708"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="ef6b8-103">Direcionamento multiplataforma</span><span class="sxs-lookup"><span data-stu-id="ef6b8-103">Cross-platform targeting</span></span>

<span data-ttu-id="ef6b8-104">O .NET moderno dá suporte a vários sistemas operacionais e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="ef6b8-105">É importante para as bibliotecas de software livre do .NET dar suporte a desenvolvedores tantos quanto possível, estejam eles criando um site ASP.NET hospedado no Azure ou um jogo .NET no Unity.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="ef6b8-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="ef6b8-106">.NET Standard</span></span>

<span data-ttu-id="ef6b8-107">O .NET standard é a melhor maneira de adicionar suporte multiplataforma a uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="ef6b8-108">O [.NET Standard](../net-standard.md) é uma especificação de APIs .NET disponíveis em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="ef6b8-109">O direcionamento para .NET Standard permite produzir bibliotecas restritas a usar as APIs que estão em uma determinada versão do .NET Standard, o que significa que ele é usado por todas as plataformas que implementam essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="ef6b8-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="ef6b8-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="ef6b8-111">Ter como destino o .NET Standard e compilar com êxito o projeto não assegura que a biblioteca será executada com êxito em todas as plataformas:</span><span class="sxs-lookup"><span data-stu-id="ef6b8-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="ef6b8-112">APIs específicas da plataforma falharão em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="ef6b8-113">Por exemplo, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> terá êxito no Windows e gerará <xref:System.PlatformNotSupportedException> em qualquer outro sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="ef6b8-114">APIs podem se comportar de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-114">APIs can behave differently.</span></span> <span data-ttu-id="ef6b8-115">Por exemplo, APIs de reflexão têm diferentes características de desempenho quando um aplicativo usa a compilação antecipada em iOS ou UWP.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="ef6b8-116">A equipe do .NET [oferece um analisador Roslyn](../analyzers/api-analyzer.md) para ajudá-lo a descobrir possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="ef6b8-117">**✔️ FAÇA** a inclusão de um destino `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="ef6b8-118">A maioria das bibliotecas de uso não deve precisar de APIs fora do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="ef6b8-119">O .NET standard 2.0 é compatível com todas as plataformas modernas e é a maneira recomendada de dar suporte a várias plataformas com um destino.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="ef6b8-120"> *\*EVITE** incluir um destino `netstandard1.x\`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="ef6b8-121">O .NET standard 1.x é distribuído como um conjunto granular de pacotes do NuGet, que cria um grande grafo de dependência de pacote e resulta em os desenvolvedores baixarem muitos pacotes durante o build.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="ef6b8-122">Plataformas .NET modernas, incluindo .NET Framework 4.6.1, UWP e Xamarin, dão suporte para .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="ef6b8-123">Você somente deverá direcionar o .NET Standard 1.x se precisar especificamente ter como destino uma plataforma mais antiga.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="ef6b8-124">**✔️ FAÇA** a inclusão de um destino `netstandard2.0` se você precisar de um `netstandard1.x` destino.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="ef6b8-125">Todas as plataformas que dão suporte a .NET Standard 2.0 usarão o destino `netstandard2.0` e se beneficiarão de um grafo de pacote menor, enquanto plataformas mais antigas ainda funcionarão e farão fallback usando o destino `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="ef6b8-126"> *\*NÃO** inclua um destino do .NET Standard se a biblioteca se basear em um modelo de aplicativo específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="ef6b8-127">Por exemplo, uma biblioteca do kit de ferramentas de controle UWP depende de um modelo de aplicativo disponível apenas em UWP.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="ef6b8-128">APIs específicas do modelo de aplicativo não estarão disponíveis no .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="ef6b8-129">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="ef6b8-129">Multi-targeting</span></span>

<span data-ttu-id="ef6b8-130">Às vezes, você precisará acessar APIs específicas da estrutura de suas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="ef6b8-131">A melhor maneira de chamar APIs específicas da estrutura é usando o múltiplos destinos, que compila seu projeto para muitas [estruturas de destino do .NET](../frameworks.md), em vez de apenas uma.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="ef6b8-132">Para proteger seus consumidores de precisarem criar estrutura individuais, você deve se esforçar para ter uma saída do .NET Standard além de uma ou mais saídas específicas da estrutura.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="ef6b8-133">Com o destinos múltiplos, todos os assemblies são empacotados dentro de um único pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="ef6b8-134">Os consumidores podem fazer referência o mesmo pacote e o NuGet escolherá a implementação apropriada.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="ef6b8-135">Sua biblioteca .NET Standard serve como a biblioteca de fallback usada em todos os lugares, exceto para casos em que o seu pacote do NuGet oferece uma implementação específica do framework.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="ef6b8-136">Ter destinos múltiplos permite que você use a compilação condicional em seu código e chame APIs específicas da estrutura.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="ef6b8-137">![Pacote NuGet com vários assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Pacote NuGet com vários assemblies")</span><span class="sxs-lookup"><span data-stu-id="ef6b8-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="ef6b8-138">**✔️ CONSIDERE** ter como destino implementações do .NET, além do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="ef6b8-139">Ter como destinos implementações do .NET permite que você chame APIs específicas da plataforma que estão fora do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="ef6b8-140">Não remova o suporte para o .NET Standard ao fazer isso.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="ef6b8-141">Em vez disso, geram da implementação e oferecem APIs de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="ef6b8-142">Dessa forma, sua biblioteca pode ser usada em qualquer lugar e dá suporte à iluminação em tempo de execução de recursos.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="ef6b8-143"> *\*EVITE** usar multi-targeting, bem como o direcionamento do .NET Standard se o código-fonte for o mesmo para todos os destinos.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-143">**❌ AVOID** multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="ef6b8-144">O assembly .NET padrão será usado automaticamente pelo NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="ef6b8-145">Ter como destino implementações do .NET individuais aumenta o tamanho de `*.nupkg` sem nenhum benefício.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="ef6b8-146">**✔️ CONSIDERE** adicionar um destino para `net461` quando você está oferecendo um destino `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="ef6b8-147">Usar o .NET Standard 2.0 do .NET Framework tem alguns problemas que foram resolvidos no .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="ef6b8-148">Você pode melhorar a experiência para desenvolvedores que ainda estão no .NET Framework 4.6.1 a 4.7.1 oferecendo a eles um binário compilado para .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="ef6b8-149">**✔️ FAZER** a distribuição de sua biblioteca usando um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="ef6b8-150">O NuGet seleciona o melhor destino para o desenvolvedor e os protege contra a necessidade de escolher a implementação apropriada.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="ef6b8-151">**✔️ FAÇA** uso da propriedade `TargetFrameworks` de um arquivo de projeto quando tiver vários destinos.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="ef6b8-152">**✔️ CONSIDERE** usar [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) quando ter vários destinos para UWP e Xamarin, o que simplifica muito o seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="ef6b8-153">Destinos mais antigos</span><span class="sxs-lookup"><span data-stu-id="ef6b8-153">Older targets</span></span>

<span data-ttu-id="ef6b8-154">O .NET dá suporte a ter como destino versões do .NET Framework que há muito tempo estão sem suporte, bem como plataformas que não são mais usadas comumente.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="ef6b8-155">Embora haja valor fazer sua biblioteca funcionar no máximo possível de destinos, precisar contornar APIs ausentes pode adicionar sobrecarga significativa.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="ef6b8-156">Acreditamos que não vale mais a pena ter determinadas estruturas como destino, considerando seu alcance e limitações.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="ef6b8-157"> *\*NÃO** inclua um destino de PCL (Biblioteca de Classes Portátil).</span><span class="sxs-lookup"><span data-stu-id="ef6b8-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="ef6b8-158">Por exemplo, `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="ef6b8-159">O .NET standard é a maneira moderna de dar suporte a bibliotecas do .NET multiplataforma e substitui PCLs.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="ef6b8-160"> *\*NÃO** inclua destinos para plataformas do .NET que não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="ef6b8-161">Por exemplo, `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="ef6b8-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ef6b8-162">[Anterior](get-started.md)
>[Próximo](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="ef6b8-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
