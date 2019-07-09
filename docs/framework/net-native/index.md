---
title: Compilando aplicativos com o .NET Nativo
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660899"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="f0ab0-102">Compilando aplicativos com o .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="f0ab0-102">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="f0ab0-103">.NET native é uma tecnologia de pré-compilação para compilar e implantar aplicativos do Windows que está incluída no Visual Studio 2015 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="f0ab0-104">Ele compila automaticamente a versão de lançamento de aplicativos escritos em código gerenciado (C# ou Visual Basic) e que são destinados ao .NET Framework e ao Windows 10 para código nativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="f0ab0-105">Normalmente, os aplicativos com destino para o .NET Framework são compilados para IL (linguagem intermediária).</span><span class="sxs-lookup"><span data-stu-id="f0ab0-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="f0ab0-106">No tempo de execução, uma compilação JIT (just-in-time) converte o IL em código nativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="f0ab0-107">Em contraste, o .NET Native compila aplicativos do Windows diretamente em código nativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="f0ab0-108">Para desenvolvedores, isso significa que:</span><span class="sxs-lookup"><span data-stu-id="f0ab0-108">For developers, this means:</span></span>

- <span data-ttu-id="f0ab0-109">O desempenho do código nativo de recurso de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="f0ab0-110">Normalmente, o desempenho será superior ao código que é compilado pela primeira vez para IL e, em seguida, é compilado para código nativo pelo compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="f0ab0-111">Você pode continuar a programar em C# ou em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-111">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="f0ab0-112">Você pode continuar a aproveitar os recursos fornecidos pelo .NET Framework, incluindo sua biblioteca de classes, coleta de lixo, gerenciamento automático de memória e manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="f0ab0-113">Para usuários de seus aplicativos, o .NET Native oferece estas vantagens:</span><span class="sxs-lookup"><span data-stu-id="f0ab0-113">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="f0ab0-114">Tempos de execução mais rápidos para a maioria dos aplicativos e cenários.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-114">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="f0ab0-115">Tempos de inicialização mais rápidos para a maioria dos aplicativos e cenários.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-115">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="f0ab0-116">Custos baixos de implantação e atualização.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-116">Low deployment and update costs.</span></span>

- <span data-ttu-id="f0ab0-117">Uso de memória do aplicativo otimizado.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-117">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0ab0-118">Para a maioria dos aplicativos e cenários, o .NET Native oferece tempos de inicialização significativamente mais rápidos e melhor desempenho quando comparado a um aplicativo compilado para IL ou para uma imagem NGEN.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="f0ab0-119">No entanto, os resultados podem variar.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-119">However, your results may vary.</span></span> <span data-ttu-id="f0ab0-120">Para garantir que seu aplicativo se beneficiou dos aprimoramentos de desempenho do .NET nativo, você deve comparar seu desempenho com o da versão do seu aplicativo não - .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="f0ab0-121">Para obter mais informações, consulte [visão geral da sessão de desempenho](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="f0ab0-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="f0ab0-122">Mas o .NET Native envolve mais do que uma compilação para código nativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="f0ab0-123">Ele transforma a maneira que os aplicativos .NET Framework são criados e executados.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="f0ab0-124">Em particular:</span><span class="sxs-lookup"><span data-stu-id="f0ab0-124">In particular:</span></span>

- <span data-ttu-id="f0ab0-125">Durante a pré-compilação, partes necessárias do .NET Framework são vinculadas estaticamente ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="f0ab0-126">Isso permite que o aplicativo seja executado com as bibliotecas de aplicativo local do .NET Framework e o compilador realize análises globais para proporcionar vantagens de desempenho.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="f0ab0-127">Como resultado, os aplicativos são inicializados consistentemente mais rápido mesmo depois de atualizações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="f0ab0-128">O tempo de execução .NET Native é otimizado para pré-compilação estática e na grande maioria dos casos, oferece um desempenho superior.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="f0ab0-129">Ao mesmo tempo, ele mantém os recursos de reflexão principais que os desenvolvedores acham tão produtivos.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="f0ab0-130">O .NET native usa o mesmo back-end como o C++ compilador, que é otimizado para cenários de pré-compilação estáticos.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="f0ab0-131">.NET native é capaz de trazer os benefícios de desempenho do C++ gerenciado para desenvolvedores de código porque ele usa as ferramentas iguais ou semelhantes, como C++ nos bastidores, conforme mostrado nesta tabela.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="f0ab0-132">.NET Nativo</span><span class="sxs-lookup"><span data-stu-id="f0ab0-132">.NET Native</span></span>|<span data-ttu-id="f0ab0-133">C++</span><span class="sxs-lookup"><span data-stu-id="f0ab0-133">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="f0ab0-134">Libraries</span><span class="sxs-lookup"><span data-stu-id="f0ab0-134">Libraries</span></span>|<span data-ttu-id="f0ab0-135">O .NET Framework + Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="f0ab0-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="f0ab0-136">Win32 + Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="f0ab0-136">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="f0ab0-137">Compilador</span><span class="sxs-lookup"><span data-stu-id="f0ab0-137">Compiler</span></span>|<span data-ttu-id="f0ab0-138">Compilador de otimização de UTC</span><span class="sxs-lookup"><span data-stu-id="f0ab0-138">UTC optimizing compiler</span></span>|<span data-ttu-id="f0ab0-139">Compilador de otimização de UTC</span><span class="sxs-lookup"><span data-stu-id="f0ab0-139">UTC optimizing compiler</span></span>|
|<span data-ttu-id="f0ab0-140">Implantado</span><span class="sxs-lookup"><span data-stu-id="f0ab0-140">Deployed</span></span>|<span data-ttu-id="f0ab0-141">Binários prontos para execução</span><span class="sxs-lookup"><span data-stu-id="f0ab0-141">Ready-to-run binaries</span></span>|<span data-ttu-id="f0ab0-142">Binários prontos para execução (ASM)</span><span class="sxs-lookup"><span data-stu-id="f0ab0-142">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="f0ab0-143">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f0ab0-143">Runtime</span></span>|<span data-ttu-id="f0ab0-144">MRT.dll (tempo de execução de CLR mínimo)</span><span class="sxs-lookup"><span data-stu-id="f0ab0-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="f0ab0-145">CRT.dll (tempo de execução C)</span><span class="sxs-lookup"><span data-stu-id="f0ab0-145">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="f0ab0-146">Para aplicativos do Windows para Windows 10, carregue os binários de compilação de código do .NET Native nos pacotes do aplicativo (arquivos .appx) para a Windows Store.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f0ab0-147">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f0ab0-147">In This Section</span></span>

<span data-ttu-id="f0ab0-148">Para obter mais informações sobre o desenvolvimento de aplicativos com compilação de código do .NET Nativo, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="f0ab0-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="f0ab0-149">Introdução à compilação de código nativo do .NET: Passo a passo de experiência de desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="f0ab0-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)

- <span data-ttu-id="f0ab0-150">[.NET native e compilação:](../../../docs/framework/net-native/net-native-and-compilation.md) Como o .NET Native compila seu projeto para código nativo.</span><span class="sxs-lookup"><span data-stu-id="f0ab0-150">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="f0ab0-151">Reflexão e .NET Native</span><span class="sxs-lookup"><span data-stu-id="f0ab0-151">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [<span data-ttu-id="f0ab0-152">APIs que dependem de reflexão</span><span class="sxs-lookup"><span data-stu-id="f0ab0-152">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="f0ab0-153">Referência da API de reflexão</span><span class="sxs-lookup"><span data-stu-id="f0ab0-153">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [<span data-ttu-id="f0ab0-154">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f0ab0-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="f0ab0-155">Serialização e metadados</span><span class="sxs-lookup"><span data-stu-id="f0ab0-155">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)

- [<span data-ttu-id="f0ab0-156">Migrando seu aplicativo da Windows Store para .NET Native</span><span class="sxs-lookup"><span data-stu-id="f0ab0-156">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="f0ab0-157">Solução de problemas gerais do .NET Native</span><span class="sxs-lookup"><span data-stu-id="f0ab0-157">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
