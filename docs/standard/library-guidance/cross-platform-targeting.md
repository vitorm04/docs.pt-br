---
title: Direcionamento de plataforma cruzada
description: Práticas recomendadas para a criação de bibliotecas do .NET de plataforma cruzada.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374878"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="1e2ad-103">Direcionamento de plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="1e2ad-103">Cross-platform targeting</span></span>

<span data-ttu-id="1e2ad-104">.NET modernos dá suporte a vários sistemas operacionais e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="1e2ad-105">É importante para as bibliotecas de código-fonte aberto do .NET dar suporte a desenvolvedores tantos quanto possível, se eles estão criando um site ASP.NET hospedado no Azure ou um jogo de .NET no Unity.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="1e2ad-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1e2ad-106">.NET Standard</span></span>

<span data-ttu-id="1e2ad-107">.NET standard é a melhor maneira de adicionar suporte de plataforma cruzada em uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="1e2ad-108">[.NET standard](../net-standard.md) é uma especificação de APIs .NET que estão disponíveis em todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="1e2ad-109">Direcionamento para .NET Standard permite produzir bibliotecas que são restritos a usar as APIs que estão em uma determinada versão do .NET Standard, que significa que ele é usado por todas as plataformas que implementam essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="1e2ad-110">![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="1e2ad-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="1e2ad-111">Direcionamento para .NET Standard e compilar com êxito o projeto, não garantem que a biblioteca será executado com êxito em todas as plataformas:</span><span class="sxs-lookup"><span data-stu-id="1e2ad-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="1e2ad-112">APIs específicas da plataforma falhará em outras plataformas.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="1e2ad-113">Por exemplo, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> será bem-sucedida no Windows e lançar <xref:System.PlatformNotSupportedException> quando usado em qualquer outro sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="1e2ad-114">APIs podem se comportar de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-114">APIs can behave differently.</span></span> <span data-ttu-id="1e2ad-115">Por exemplo, reflexão APIs têm diferentes características de desempenho quando um aplicativo usa a compilação ahead of time em iOS ou UWP.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="1e2ad-116">A equipe do .NET [oferece um analisador Roslyn](../analyzers/api-analyzer.md) para ajudá-lo a descobrir possíveis problemas.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="1e2ad-117">**FAZER ✔️** começar com incluindo um `netstandard2.0` destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-117">**✔️ DO** start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="1e2ad-118">Mais bibliotecas de uso geral não devem precisar de APIs fora do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="1e2ad-119">.NET standard 2.0 é compatível com todas as plataformas modernas e é a maneira recomendada para dar suporte a várias plataformas com um destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="1e2ad-120">**❌ Evite** incluindo um `netstandard1.x` destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-120">**❌ AVOID** including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="1e2ad-121">.NET standard 1.x é distribuído como um conjunto granular de pacotes do NuGet, que cria um gráfico de dependência de pacote grande e resulta em download de muitos pacotes durante a criação de desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="1e2ad-122">Plataformas .NET modernas, incluindo o .NET Framework 4.6.1, UWP e Xamarin, o suporte .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="1e2ad-123">Você deve somente direcionar o .NET Standard 1.x se você precisar especificamente para ter como destino uma plataforma mais antiga.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="1e2ad-124">**FAZER ✔️** incluem uma `netstandard2.0` de destino se você precisar de um `netstandard1.x` destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-124">**✔️ DO** include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="1e2ad-125">Todas as plataformas que dão suporte a .NET Standard 2.0 usará o `netstandard2.0` de destino e se beneficiar de um grafo de pacote menor enquanto plataformas mais antigas ainda funcionarão e voltar a usar o `netstandard1.x` destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="1e2ad-126">**❌ NÃO** incluir um destino .NET Standard, se a biblioteca se baseia em um modelo de aplicativo específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-126">**❌ DO NOT** include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="1e2ad-127">Por exemplo, uma biblioteca do Kit de ferramentas de controle UWP depende de um modelo de aplicativo que está disponível apenas em UWP.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="1e2ad-128">Específico ao modelo de aplicativo APIs não estará disponíveis no .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="1e2ad-129">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="1e2ad-129">Multi-targeting</span></span>

<span data-ttu-id="1e2ad-130">Às vezes, você precisará acessar APIs específicas da estrutura de suas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="1e2ad-131">A melhor maneira de chamar APIs específicas da estrutura é usando o multi-direcionamento, que compila seu projeto para muitos [estruturas de destino do .NET](../frameworks.md) em vez de apenas um.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="1e2ad-132">Para proteger seus consumidores de ter que criar para estruturas individuais, você deve se esforçar para ter uma saída de .NET Standard além de uma ou mais saídas específicas da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="1e2ad-133">Com o multi-direcionamento, todos os assemblies são empacotados dentro de um único pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="1e2ad-134">Os consumidores podem fazer referência o mesmo pacote e NuGet escolherá a implementação apropriada.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="1e2ad-135">Sua biblioteca .NET Standard serve como a biblioteca de fallback é usado em todos os lugares, exceto para os casos em que o seu pacote do NuGet oferece uma implementação específica do framework.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="1e2ad-136">Multiplataforma permite que você usar a compilação condicional em seu código e chamar APIs específicas da estrutura.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="1e2ad-137">![Pacote NuGet com vários assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "pacote NuGet com vários assemblies")</span><span class="sxs-lookup"><span data-stu-id="1e2ad-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="1e2ad-138">**Considere a possibilidade de ✔️** direcionamento implementações do .NET, além do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-138">**✔️ CONSIDER** targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="1e2ad-139">Direcionamento de implementações do .NET permite que você chame APIs específicas da plataforma que estão fora do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="1e2ad-140">Não remova o suporte para o .NET Standard ao fazer isso.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="1e2ad-141">Em vez disso, lançar da implementação e oferecem APIs de recurso.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="1e2ad-142">Dessa forma, sua biblioteca pode ser usada em qualquer lugar e dá suporte ao tempo de execução light-up dos recursos.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

<span data-ttu-id="1e2ad-143">**❌ Evite** usando multiplataforma com o .NET Standard se seu código-fonte é o mesmo para todos os destinos.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-143">**❌ AVOID** using multi-targeting with .NET Standard if your source code is the same for all targets.</span></span>

> <span data-ttu-id="1e2ad-144">O assembly .NET padrão será usado automaticamente pelo NuGet.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="1e2ad-145">Direcionamento de implementações de .NET individuais aumenta a `*.nupkg` tamanho sem nenhum benefício.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="1e2ad-146">**Considere a possibilidade de ✔️** adicionando um destino para `net461` quando você está oferecendo uma `netstandard2.0` destino.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-146">**✔️ CONSIDER** adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span> 

> <span data-ttu-id="1e2ad-147">Usar o .NET Standard 2.0 do .NET Framework tem alguns problemas que foram resolvidos no .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="1e2ad-148">Você pode melhorar a experiência para desenvolvedores que ainda estão no .NET Framework 4.6.1 - 4.7.1, oferecendo a eles um binário que é compilado para .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="1e2ad-149">**FAZER ✔️** distribuir sua biblioteca usando um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-149">**✔️ DO** distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="1e2ad-150">NuGet selecionará o melhor destino para o desenvolvedor e protegê-las ter que ler a implementação apropriada.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="1e2ad-151">**FAZER ✔️** usar um arquivo de projeto `TargetFrameworks` propriedade quando vários destinos.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-151">**✔️ DO** use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1e2ad-152">**Considere a possibilidade de ✔️** usando [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) quando multi-targeting para UWP e Xamarin, que simplifica muito o seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-152">**✔️ CONSIDER** using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="1e2ad-153">Destinos mais antigos</span><span class="sxs-lookup"><span data-stu-id="1e2ad-153">Older targets</span></span>

<span data-ttu-id="1e2ad-154">.NET dá suporte a versões de direcionamento do .NET Framework longos sem suporte, bem como em plataformas não são mais comumente usadas.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="1e2ad-155">Embora não haja valor fazer seu trabalho de biblioteca em como muitos destinos quanto possível, necessidade de trabalhar em torno de APIs ausentes podem adicionar significativa sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="1e2ad-156">Acreditamos que determinadas estruturas não são mais que vale a pena direcionamento, considerando seu alcance e limitações.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="1e2ad-157">**❌ NÃO** incluir um destino de biblioteca de classe portátil (PCL).</span><span class="sxs-lookup"><span data-stu-id="1e2ad-157">**❌ DO NOT** include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="1e2ad-158">Por exemplo, `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="1e2ad-159">.NET standard é a maneira moderna para dar suporte a bibliotecas do .NET de plataforma cruzada e substitui PCLs.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="1e2ad-160">**❌ NÃO** incluir destinos para plataformas do .NET que não têm mais suporte.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-160">**❌ DO NOT** include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="1e2ad-161">Por exemplo, `SL4`, `WP`.</span><span class="sxs-lookup"><span data-stu-id="1e2ad-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1e2ad-162">[Anterior](./get-started.md)
[Próximo](./strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="1e2ad-162">[Previous](./get-started.md)
[Next](./strong-naming.md)</span></span>
