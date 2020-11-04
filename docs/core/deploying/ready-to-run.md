---
title: Visão geral da implantação do ReadyToRun
description: Saiba o que são implantações ReadyToRun e por que você deve considerar usá-la como parte da publicação de seu aplicativo com o .NET 5 e o .NET Core 3,0 e posterior.
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: cd8eaebd05d79b11e90e255e702a52220fffda76
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342625"
---
# <a name="readytorun-compilation"></a><span data-ttu-id="9aaca-103">Compilação ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="9aaca-103">ReadyToRun Compilation</span></span>

<span data-ttu-id="9aaca-104">A latência e o tempo de inicialização do aplicativo .NET podem ser aprimorados com a compilação de seus assemblies de aplicativo como o formato ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="9aaca-104">.NET application startup time and latency can be improved by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="9aaca-105">R2R é uma forma de compilação antecipada (AOT).</span><span class="sxs-lookup"><span data-stu-id="9aaca-105">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="9aaca-106">Os binários R2R melhoram o desempenho de inicialização reduzindo a quantidade de trabalho que o compilador just-in-time (JIT) precisa fazer à medida que seu aplicativo é carregado.</span><span class="sxs-lookup"><span data-stu-id="9aaca-106">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="9aaca-107">Os binários contêm código nativo similar comparado ao que o JIT produziria.</span><span class="sxs-lookup"><span data-stu-id="9aaca-107">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="9aaca-108">Entretanto, os binários R2R são maiores porque contêm código de IL (linguagem intermediária), que ainda é necessário para alguns cenários, e a versão nativa do mesmo código.</span><span class="sxs-lookup"><span data-stu-id="9aaca-108">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="9aaca-109">O R2R só está disponível quando você publica um aplicativo destinado a ambientes de tempo de execução específicos (RID), como Linux x64 ou Windows x64.</span><span class="sxs-lookup"><span data-stu-id="9aaca-109">R2R is only available when you publish an app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="9aaca-110">Para compilar seu projeto como ReadyToRun, o aplicativo deve ser publicado com a propriedade PublishReadyToRun definida como true.</span><span class="sxs-lookup"><span data-stu-id="9aaca-110">To compile your project as ReadyToRun, the application must be published with the PublishReadyToRun property set to true.</span></span>

<span data-ttu-id="9aaca-111">Há duas maneiras de publicar seu aplicativo como ReadyToRun:</span><span class="sxs-lookup"><span data-stu-id="9aaca-111">There are two ways to publish your app as ReadyToRun:</span></span>

01. <span data-ttu-id="9aaca-112">Especifique o sinalizador PublishReadyToRun diretamente para o comando dotnet publish.</span><span class="sxs-lookup"><span data-stu-id="9aaca-112">Specify the PublishReadyToRun flag directly to the dotnet publish command.</span></span> <span data-ttu-id="9aaca-113">Consulte [dotnet Publish](../tools/dotnet-publish.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="9aaca-113">See [dotnet publish](../tools/dotnet-publish.md) for details.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. <span data-ttu-id="9aaca-114">Especifique a propriedade no projeto</span><span class="sxs-lookup"><span data-stu-id="9aaca-114">Specify the property in the project</span></span>

    - <span data-ttu-id="9aaca-115">Adicione a `<PublishReadyToRun>` configuração ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="9aaca-115">Add the `<PublishReadyToRun>` setting to your project.</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - <span data-ttu-id="9aaca-116">Publique o aplicativo sem parâmetros especiais.</span><span class="sxs-lookup"><span data-stu-id="9aaca-116">Publish the application without any special parameters.</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a><span data-ttu-id="9aaca-117">Impacto do uso do recurso ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="9aaca-117">Impact of using the ReadyToRun feature</span></span>

<span data-ttu-id="9aaca-118">A compilação antecipada tem um impacto complexo no desempenho do aplicativo, o que pode ser difícil de prever.</span><span class="sxs-lookup"><span data-stu-id="9aaca-118">Ahead-of-time compilation has complex performance impact on application performance, which may be difficult to predict.</span></span> <span data-ttu-id="9aaca-119">Em geral, o tamanho de um assembly aumentará entre dois a três vezes maior.</span><span class="sxs-lookup"><span data-stu-id="9aaca-119">In general, the size of an assembly will grow to between two to three times larger.</span></span> <span data-ttu-id="9aaca-120">Esse aumento no tamanho físico do arquivo pode reduzir o desempenho do carregamento do assembly do disco e aumentar o conjunto de trabalho do processo.</span><span class="sxs-lookup"><span data-stu-id="9aaca-120">This increase in the physical size of the file may reduce the performance of loading the assembly from disk, and increase working set of the process.</span></span> <span data-ttu-id="9aaca-121">No entanto, em retorno, o número de métodos compilados no tempo de execução normalmente é reduzido substancialmente.</span><span class="sxs-lookup"><span data-stu-id="9aaca-121">However, in return the number of methods compiled at runtime is typically reduced substantially.</span></span> <span data-ttu-id="9aaca-122">O resultado é que a maioria dos aplicativos que têm grandes quantidades de código recebem grandes benefícios de desempenho ao habilitar o ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="9aaca-122">The result is that most applications that have large amounts of code receive large performance benefits from enabling ReadyToRun.</span></span> <span data-ttu-id="9aaca-123">Os aplicativos, que têm pequenas quantidades de código, provavelmente não terão uma melhoria significativa da habilitação de ReadyToRun, já que as bibliotecas de tempo de execução do .NET ainda foram pré-compiladas com o ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="9aaca-123">Applications, which have small amounts of code will likely not experience a significant improvement from enabling ReadyToRun, as the .NET runtime libraries have already been precompiled with ReadyToRun.</span></span>

<span data-ttu-id="9aaca-124">A melhoria da inicialização discutida aqui se aplica não apenas à inicialização do aplicativo, mas também ao primeiro uso de qualquer código no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9aaca-124">The startup improvement discussed here applies not only to application startup, but also to the first use of any code in the application.</span></span> <span data-ttu-id="9aaca-125">Por exemplo, ReadyToRun pode ser usado para reduzir a latência de resposta do primeiro uso da API Web em um aplicativo ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9aaca-125">For instance, ReadyToRun can be used to reduce the response latency of the first use  of Web API in an ASP.NET application.</span></span>

### <a name="interaction-with-tiered-compilation"></a><span data-ttu-id="9aaca-126">Interação com compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="9aaca-126">Interaction with tiered compilation</span></span>

<span data-ttu-id="9aaca-127">O antes do tempo gerado não é tão otimizado quanto o código produzido pelo JIT.</span><span class="sxs-lookup"><span data-stu-id="9aaca-127">Ahead-of-time generated is not as highly optimized as code produced by the JIT.</span></span> <span data-ttu-id="9aaca-128">Para resolver esse problema, a compilação em camadas substituirá os métodos ReadyToRun usados com métodos gerados por JIT.</span><span class="sxs-lookup"><span data-stu-id="9aaca-128">To address this issue, tiered compilation will replace commonly used ReadyToRun methods with JIT-generated methods.</span></span>

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a><span data-ttu-id="9aaca-129">Como o conjunto de assemblies pré-compilados é escolhido?</span><span class="sxs-lookup"><span data-stu-id="9aaca-129">How is the set of precompiled assemblies chosen?</span></span>

<span data-ttu-id="9aaca-130">O SDK irá pré-compilar os assemblies que são distribuídos com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9aaca-130">The SDK will precompile the assemblies that are distributed with the application.</span></span> <span data-ttu-id="9aaca-131">Para aplicativos independentes, esse conjunto de assemblies incluirá a estrutura.</span><span class="sxs-lookup"><span data-stu-id="9aaca-131">For self-contained applications, this set of assemblies will include the framework.</span></span> <span data-ttu-id="9aaca-132">Os binários C++/CLI não são elegíveis para compilação ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="9aaca-132">C++/CLI binaries are not eligible for ReadyToRun compilation.</span></span>

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a><span data-ttu-id="9aaca-133">Como é escolhido o conjunto de métodos para pré-compilação?</span><span class="sxs-lookup"><span data-stu-id="9aaca-133">How is the set of methods to precompile chosen?</span></span>

<span data-ttu-id="9aaca-134">O compilador tentará pré-compilar previamente o máximo de métodos possível.</span><span class="sxs-lookup"><span data-stu-id="9aaca-134">The compiler will attempt to pre-compile as many methods as it can.</span></span> <span data-ttu-id="9aaca-135">No entanto, vários motivos pelos quais não se espera que o uso do recurso ReadyToRun resultarão em impedir a execução do JIT.</span><span class="sxs-lookup"><span data-stu-id="9aaca-135">However various reasons it is not expected that using the ReadyToRun feature will result in preventing the JIT from executing.</span></span>

<span data-ttu-id="9aaca-136">Tais motivos podem incluir, mas não estão limitados a:</span><span class="sxs-lookup"><span data-stu-id="9aaca-136">Such reasons may include, but are not limited to:</span></span>

- <span data-ttu-id="9aaca-137">Uso de tipos genéricos definidos em assemblies separados</span><span class="sxs-lookup"><span data-stu-id="9aaca-137">Use of generic types defined in separate assemblies</span></span>
- <span data-ttu-id="9aaca-138">Interoperabilidade com código nativo</span><span class="sxs-lookup"><span data-stu-id="9aaca-138">Interop with native code</span></span>
- <span data-ttu-id="9aaca-139">O uso de intrínsecos de hardware que o compilador não pode provar é seguro para uso em um computador de destino</span><span class="sxs-lookup"><span data-stu-id="9aaca-139">Use of hardware intrinsics that the compiler cannot prove are safe to use on a target machine</span></span>
- <span data-ttu-id="9aaca-140">Certos padrões de IL incomum</span><span class="sxs-lookup"><span data-stu-id="9aaca-140">Certain unusual IL patterns</span></span>
- <span data-ttu-id="9aaca-141">Criação dinâmica de métodos via reflexão ou LINQ</span><span class="sxs-lookup"><span data-stu-id="9aaca-141">Dynamic method creation via reflection, or LINQ</span></span>

## <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="9aaca-142">Restrições de plataforma cruzada/arquitetura</span><span class="sxs-lookup"><span data-stu-id="9aaca-142">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="9aaca-143">Para algumas plataformas de SDK, o compilador ReadyToRun é capaz de Compilar várias plataformas de destino.</span><span class="sxs-lookup"><span data-stu-id="9aaca-143">For some SDK platforms, the ReadyToRun compiler is capable of cross-compiling for other target platforms.</span></span> <span data-ttu-id="9aaca-144">Os destinos de compilação com suporte são descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9aaca-144">Supported compilation targets are described in the table below.</span></span>

| <span data-ttu-id="9aaca-145">Plataforma SDK</span><span class="sxs-lookup"><span data-stu-id="9aaca-145">SDK platform</span></span> | <span data-ttu-id="9aaca-146">Plataformas de destino com suporte</span><span class="sxs-lookup"><span data-stu-id="9aaca-146">Supported target platforms</span></span> |
| ------------ | --------------------------- |
| <span data-ttu-id="9aaca-147">Windows X64</span><span class="sxs-lookup"><span data-stu-id="9aaca-147">Windows X64</span></span>  | <span data-ttu-id="9aaca-148">Windows x86, Windows x64, Windows ARM32, Windows ARM64</span><span class="sxs-lookup"><span data-stu-id="9aaca-148">Windows X86, Windows X64, Windows ARM32, Windows ARM64</span></span> |
| <span data-ttu-id="9aaca-149">Windows x86</span><span class="sxs-lookup"><span data-stu-id="9aaca-149">Windows X86</span></span>  | <span data-ttu-id="9aaca-150">Windows x86, Windows ARM32</span><span class="sxs-lookup"><span data-stu-id="9aaca-150">Windows X86, Windows ARM32</span></span> |
| <span data-ttu-id="9aaca-151">Linux X64</span><span class="sxs-lookup"><span data-stu-id="9aaca-151">Linux X64</span></span>    | <span data-ttu-id="9aaca-152">Linux x86, Linux x64, Linux ARM32, Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="9aaca-152">Linux X86, Linux X64, Linux ARM32, Linux ARM64</span></span> |
| <span data-ttu-id="9aaca-153">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="9aaca-153">Linux ARM32</span></span>  | <span data-ttu-id="9aaca-154">Linux ARM32</span><span class="sxs-lookup"><span data-stu-id="9aaca-154">Linux ARM32</span></span> |
| <span data-ttu-id="9aaca-155">ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="9aaca-155">Linux ARM64</span></span>  | <span data-ttu-id="9aaca-156">ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="9aaca-156">Linux ARM64</span></span> |
| <span data-ttu-id="9aaca-157">macOS x64</span><span class="sxs-lookup"><span data-stu-id="9aaca-157">macOS X64</span></span>    | <span data-ttu-id="9aaca-158">macOS x64</span><span class="sxs-lookup"><span data-stu-id="9aaca-158">macOS X64</span></span> |
