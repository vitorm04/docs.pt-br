---
title: Compilando aplicativos com o .NET Nativo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 76645ae43ce6754ffdf505729ec1198785a71561
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="70ab2-102">Compilando aplicativos com o .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="70ab2-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="70ab2-103"> é uma tecnologia de pré-compilação para compilação e implantação de aplicativos do Windows que está incluída com [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ab2-103"> is a precompilation technology for building and deploying Windows apps that is included with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)].</span></span> <span data-ttu-id="70ab2-104">Ele compila automaticamente a versão de lançamento de aplicativos escritos em código gerenciado (C# ou Visual Basic) e que são destinados ao .NET Framework e ao Windows 10 para código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="70ab2-105">Normalmente, os aplicativos com destino para o .NET Framework são compilados para IL (linguagem intermediária).</span><span class="sxs-lookup"><span data-stu-id="70ab2-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="70ab2-106">No tempo de execução, uma compilação JIT (just-in-time) converte o IL em código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="70ab2-107">Em contraste, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] compila aplicativos do Windows diretamente em código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="70ab2-108">Para desenvolvedores, isso significa que:</span><span class="sxs-lookup"><span data-stu-id="70ab2-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="70ab2-109">Seus aplicativos fornecerão o melhor desempenho do código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-109">Your apps will provide the superior performance of native code.</span></span>  
  
-   <span data-ttu-id="70ab2-110">Você pode continuar a programar em C# ou em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70ab2-110">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="70ab2-111">Você pode continuar a aproveitar os recursos fornecidos pelo .NET Framework, incluindo sua biblioteca de classes, coleta de lixo, gerenciamento automático de memória e manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="70ab2-111">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="70ab2-112">Para os usuários dos seus aplicativos, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] oferece estas vantagens:</span><span class="sxs-lookup"><span data-stu-id="70ab2-112">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="70ab2-113">Tempos de execução rápidos</span><span class="sxs-lookup"><span data-stu-id="70ab2-113">Fast execution times</span></span>  
  
-   <span data-ttu-id="70ab2-114">Tempos de inicialização rápida consistentemente</span><span class="sxs-lookup"><span data-stu-id="70ab2-114">Consistently speedy startup times</span></span>  
  
-   <span data-ttu-id="70ab2-115">Custos baixos de implantação e atualização</span><span class="sxs-lookup"><span data-stu-id="70ab2-115">Low deployment and update costs</span></span>  
  
-   <span data-ttu-id="70ab2-116">Uso da memória otimizada do aplicativo</span><span class="sxs-lookup"><span data-stu-id="70ab2-116">Optimized app memory usage</span></span>  
  
 <span data-ttu-id="70ab2-117">Porém, o [!INCLUDE[net_native](../../../includes/net-native-md.md)] representa mais do que uma compilação para código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-117">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="70ab2-118">Ele transforma a maneira que os aplicativos .NET Framework são criados e executados.</span><span class="sxs-lookup"><span data-stu-id="70ab2-118">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="70ab2-119">Em particular:</span><span class="sxs-lookup"><span data-stu-id="70ab2-119">In particular:</span></span>  
  
-   <span data-ttu-id="70ab2-120">Durante a pré-compilação, partes necessárias do .NET Framework são vinculadas estaticamente ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-120">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="70ab2-121">Isso permite que o aplicativo seja executado com as bibliotecas de aplicativo local do .NET Framework e o compilador realize análises globais para proporcionar vantagens de desempenho.</span><span class="sxs-lookup"><span data-stu-id="70ab2-121">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="70ab2-122">Como resultado, os aplicativos são inicializados consistentemente mais rápido mesmo depois de atualizações do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70ab2-122">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="70ab2-123">O tempo de execução do [!INCLUDE[net_native](../../../includes/net-native-md.md)] é otimizado para pré-compilação estática, podendo oferecer melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="70ab2-123">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and thus is able to offer superior performance.</span></span> <span data-ttu-id="70ab2-124">Ao mesmo tempo, ele mantém os recursos de reflexão principais que os desenvolvedores acham tão produtivos.</span><span class="sxs-lookup"><span data-stu-id="70ab2-124">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   <span data-ttu-id="70ab2-125">O [!INCLUDE[net_native](../../../includes/net-native-md.md)] usa o mesmo back-end que o compilador do C++, que é otimizado para cenários de pré-compilação estáticos.</span><span class="sxs-lookup"><span data-stu-id="70ab2-125">[!INCLUDE[net_native](../../../includes/net-native-md.md)] uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 <span data-ttu-id="70ab2-126">O [!INCLUDE[net_native](../../../includes/net-native-md.md)] também oferece benefícios de desempenho do C++ para desenvolvedores de código gerenciado porque ele usa as ferramentas iguais ou semelhantes às do C++ nos bastidores, conforme mostrado nesta tabela.</span><span class="sxs-lookup"><span data-stu-id="70ab2-126">[!INCLUDE[net_native](../../../includes/net-native-md.md)] is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="70ab2-127">C++</span><span class="sxs-lookup"><span data-stu-id="70ab2-127">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="70ab2-128">Libraries</span><span class="sxs-lookup"><span data-stu-id="70ab2-128">Libraries</span></span>|<span data-ttu-id="70ab2-129">O .NET Framework + Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="70ab2-129">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="70ab2-130">Win32 + Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="70ab2-130">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="70ab2-131">Compilador</span><span class="sxs-lookup"><span data-stu-id="70ab2-131">Compiler</span></span>|<span data-ttu-id="70ab2-132">Compilador de otimização de UTC</span><span class="sxs-lookup"><span data-stu-id="70ab2-132">UTC optimizing compiler</span></span>|<span data-ttu-id="70ab2-133">Compilador de otimização de UTC</span><span class="sxs-lookup"><span data-stu-id="70ab2-133">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="70ab2-134">Implantado</span><span class="sxs-lookup"><span data-stu-id="70ab2-134">Deployed</span></span>|<span data-ttu-id="70ab2-135">Binários prontos para execução</span><span class="sxs-lookup"><span data-stu-id="70ab2-135">Ready-to-run binaries</span></span>|<span data-ttu-id="70ab2-136">Binários prontos para execução (ASM)</span><span class="sxs-lookup"><span data-stu-id="70ab2-136">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="70ab2-137">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="70ab2-137">Runtime</span></span>|<span data-ttu-id="70ab2-138">MRT.dll (tempo de execução de CLR mínimo)</span><span class="sxs-lookup"><span data-stu-id="70ab2-138">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="70ab2-139">CRT.dll (tempo de execução C)</span><span class="sxs-lookup"><span data-stu-id="70ab2-139">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="70ab2-140">Para aplicativos do Windows para Windows 10, carregue os binários de compilação de código do .NET Native nos pacotes do aplicativo (arquivos .appx) para a Windows Store.</span><span class="sxs-lookup"><span data-stu-id="70ab2-140">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70ab2-141">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="70ab2-141">In This Section</span></span>  
 <span data-ttu-id="70ab2-142">Para obter mais informações sobre o desenvolvimento de aplicativos com compilação de código do .NET Nativo, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="70ab2-142">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="70ab2-143">Guia de Introdução à compilação de código do .NET Native: passo a passo da experiência de desenvolvedor</span><span class="sxs-lookup"><span data-stu-id="70ab2-143">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="70ab2-144">[Compilação e .NET Native:](../../../docs/framework/net-native/net-native-and-compilation.md) como o .NET Native compila seu projeto para código nativo.</span><span class="sxs-lookup"><span data-stu-id="70ab2-144">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="70ab2-145">Reflexão e .NET Native</span><span class="sxs-lookup"><span data-stu-id="70ab2-145">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="70ab2-146">APIs que dependem de reflexão</span><span class="sxs-lookup"><span data-stu-id="70ab2-146">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="70ab2-147">Referência da API de reflexão</span><span class="sxs-lookup"><span data-stu-id="70ab2-147">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="70ab2-148">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="70ab2-148">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="70ab2-149">Serialização e metadados</span><span class="sxs-lookup"><span data-stu-id="70ab2-149">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="70ab2-150">Migrando seu aplicativo da Windows Store para .NET Native</span><span class="sxs-lookup"><span data-stu-id="70ab2-150">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="70ab2-151">Solução de problemas gerais do .NET Native</span><span class="sxs-lookup"><span data-stu-id="70ab2-151">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a><span data-ttu-id="70ab2-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70ab2-152">See Also</span></span>  
 [<span data-ttu-id="70ab2-153">Perguntas frequentes do .NET Native</span><span class="sxs-lookup"><span data-stu-id="70ab2-153">.NET Native FAQ</span></span>](http://msdn.microsoft.com/vstudio/dn642499.aspx)

