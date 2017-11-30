---
title: "Glossário .NET"
description: "Descubra o significado de termos selecionados usados na documentação do .NET."
keywords: "glossário do .NET, dicionário do .NET, terminologia do .NET, plataforma .NET, .NET framework, tempo de execução do .NET"
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: a6546818eaeac3c32a6a9ddd7e64b1b0e0ea170f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="net-glossary"></a><span data-ttu-id="9ecd7-104">Glossário .NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-104">.NET Glossary</span></span>

<span data-ttu-id="9ecd7-105">A principal meta deste glossário é esclarecer os significados de termos e acrônimos selecionados que aparecem com frequência na documentação do .NET sem definições.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-105">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="9ecd7-106">AOT</span><span class="sxs-lookup"><span data-stu-id="9ecd7-106">AOT</span></span>

<span data-ttu-id="9ecd7-107">Compilador Ahead-of-Time.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-107">Ahead-of-time compiler.</span></span>

<span data-ttu-id="9ecd7-108">Semelhante ao [JIT](#jit), esse compilador também converte [IL](#il) em código de máquina.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-108">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="9ecd7-109">Diferentemente da compilação JIT, a compilação AOT acontece antes que o aplicativo seja executado e normalmente é executada em um computador diferente.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-109">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="9ecd7-110">Como as cadeias da ferramenta da AOT não compilam em tempo de execução, elas não têm que minimizar o tempo gasto na compilação.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-110">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="9ecd7-111">Isso significa que elas podem gastar mais tempo em otimização.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-111">That means they can spend more time optimizing.</span></span> <span data-ttu-id="9ecd7-112">Como o contexto da AOT é o aplicativo inteiro, o compilador AOT também executa a vinculação de módulo cruzado e a análise de programa inteiro, o que significa que todas as referências são seguidas e um único executável é produzido.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-112">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="9ecd7-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-113">ASP.NET</span></span> 

<span data-ttu-id="9ecd7-114">A implementação do ASP.NET original que é fornecida com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="9ecd7-115">Às vezes, o ASP.NET é um termo abrangente que se refere a ambas as implementações de ASP.NET, incluindo o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="9ecd7-116">O significado que o termo carrega em uma determinada instância é determinado pelo contexto.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="9ecd7-117">Consulte para ASP.NET 4. x para tornar claro que você não estiver usando ASP.NET significa ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="9ecd7-118">Consulte [ASP.NET documentação](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="9ecd7-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-119">ASP.NET Core</span></span>

<span data-ttu-id="9ecd7-120">Uma implementação multiplataforma de alto desempenho e software livre do ASP.NET com base no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="9ecd7-121">Consulte [documentação do ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="9ecd7-122">assembly</span><span class="sxs-lookup"><span data-stu-id="9ecd7-122">assembly</span></span>

<span data-ttu-id="9ecd7-123">Um arquivo *.dll* que contém uma coleção de APIs que podem ser chamadas por aplicativos ou outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-123">A *.dll* file that contains a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="9ecd7-124">Um assembly .NET é uma coleção de tipos.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-124">A .NET assembly is a collection of types.</span></span> <span data-ttu-id="9ecd7-125">Um assembly inclui interfaces, classes, estruturas, enumerações e delegados.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-125">An assembly includes interfaces, classes, structures, enumerations, and delegates.</span></span>  <span data-ttu-id="9ecd7-126">Às vezes, os assemblies em uma pasta *bin* de projeto são chamados de *binários*.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-126">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="9ecd7-127">Consulte também [biblioteca](#library).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-127">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="9ecd7-128">CLR</span><span class="sxs-lookup"><span data-stu-id="9ecd7-128">CLR</span></span>

<span data-ttu-id="9ecd7-129">Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-129">Common Language Runtime.</span></span>

<span data-ttu-id="9ecd7-130">O significado exato depende do contexto, mas geralmente se refere ao tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-130">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="9ecd7-131">O CLR manipula a alocação e o gerenciamento de memória.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-131">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="9ecd7-132">O CLR também é uma máquina virtual que não só executa aplicativos, mas também gera e compila código dinamicamente usando um compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-132">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="9ecd7-133">A implementação atual do CLR da Microsoft é somente para Windows.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-133">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="9ecd7-134">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="9ecd7-134">CoreCLR</span></span>

<span data-ttu-id="9ecd7-135">Common Language Runtime do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-135">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="9ecd7-136">Esse CLR é criado com a mesma base de código que o CLR.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-136">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="9ecd7-137">Originalmente, o CoreCLR era o tempo de execução do Silverlight e foi projetado para ser executado em várias plataformas, especificamente o Windows e OS X. Agora o CoreCLR faz parte do .NET Core e representa uma versão simplificada do CLR.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-137">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="9ecd7-138">Ele ainda é um tempo de execução multiplataforma, incluindo também suporte para várias distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-138">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="9ecd7-139">O CoreCLR também é uma máquina virtual com recursos JIT e de execução de código.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-139">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="9ecd7-140">CoreFX</span><span class="sxs-lookup"><span data-stu-id="9ecd7-140">CoreFX</span></span>

<span data-ttu-id="9ecd7-141">BCL (biblioteca de classes base) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-141">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="9ecd7-142">Um conjunto de bibliotecas que compõem os namespaces System.* e, até certo limite, Microsoft.*.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-142">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="9ecd7-143">A BCL é uma estrutura de nível inferior e de uso geral, base para a criação de estruturas de aplicativo de nível mais alto, como o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-143">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="9ecd7-144">O código-fonte da BCL do .NET Core está contido no [repositório CoreFX](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-144">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="9ecd7-145">No entanto, a maioria das APIs do .NET Core também estão disponíveis no .NET Framework, portanto você pode pensar no CoreFX como um fork da BCL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-145">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="9ecd7-146">CoreRT</span><span class="sxs-lookup"><span data-stu-id="9ecd7-146">CoreRT</span></span>

<span data-ttu-id="9ecd7-147">Tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-147">.NET Core runtime.</span></span>

<span data-ttu-id="9ecd7-148">Ao contrário do CLR/CoreCLR, o CoreRT não é uma máquina virtual, o que significa que ele não inclui os recursos para gerar e executar código dinamicamente, já que não inclui um [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-148">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="9ecd7-149">No entanto, ele inclui a [GC](#gc) e a capacidade de RTTI (identificação de tipo de tempo de execução) e reflexão.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-149">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="9ecd7-150">Contudo, seu sistema de tipos é projetado para que os metadados para reflexão não sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="9ecd7-151">Isso permite ter uma cadeia de ferramentas [AOT](#aot) que possa desvincular metadados supérfluos e, mais importante, identificar código que o aplicativo não usa.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-151">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="9ecd7-152">O CoreRT está em desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-152">CoreRT is in development.</span></span>

<span data-ttu-id="9ecd7-153">Consulte [Introdução ao .NET Native e ao CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="9ecd7-154">ecossistema</span><span class="sxs-lookup"><span data-stu-id="9ecd7-154">ecosystem</span></span>

<span data-ttu-id="9ecd7-155">Todos os softwares de tempo de execução, as ferramentas de desenvolvimento e os recursos da comunidade que são usados para compilar e executar aplicativos de uma determinada tecnologia.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-155">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="9ecd7-156">O termo "Ecossistema do .NET" difere de termos semelhantes, como "Pilha do .NET", em relação à inclusão de bibliotecas e aplicativos de terceiros.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-156">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="9ecd7-157">Veja um exemplo em uma frase:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-157">Here's an example in a sentence:</span></span>

- <span data-ttu-id="9ecd7-158">"A motivação por trás do [.NET Standard](#net-standard) é estabelecer maior uniformidade no ecossistema do .NET."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-158">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="9ecd7-159">estrutura</span><span class="sxs-lookup"><span data-stu-id="9ecd7-159">framework</span></span>

<span data-ttu-id="9ecd7-160">Em geral, uma coleção abrangente de APIs que facilita o desenvolvimento e a implantação de aplicativos que são baseados em uma tecnologia específica.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-160">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="9ecd7-161">Nesse sentido geral, o ASP.NET Core e o Windows Forms são exemplos de estruturas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-161">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="9ecd7-162">Consulte também [biblioteca](#library).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-162">See also [library](#library).</span></span>

<span data-ttu-id="9ecd7-163">A palavra "estrutura" tem um significado técnico mais específico nos seguintes termos:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-163">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="9ecd7-164">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ecd7-164">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="9ecd7-165">estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="9ecd7-165">target framework</span></span>](#target-framework)
* [<span data-ttu-id="9ecd7-166">TFM (Moniker de Estrutura de Destino)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-166">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="9ecd7-167">Na documentação existente, "estrutura" às vezes se refere a uma [implementação do .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-167">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="9ecd7-168">Por exemplo, um artigo pode chamar o .NET Core de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-168">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="9ecd7-169">Planejamos eliminar da documentação esse uso confuso da palavra.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-169">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="9ecd7-170">GC</span><span class="sxs-lookup"><span data-stu-id="9ecd7-170">GC</span></span>

<span data-ttu-id="9ecd7-171">Coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-171">Garbage collector.</span></span>

<span data-ttu-id="9ecd7-172">O coletor de lixo é uma implementação do gerenciamento automático de memória.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-172">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="9ecd7-173">O GC libera a memória ocupada por objetos que não estejam mais em uso.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-173">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="9ecd7-174">Consulte [Coleta de lixo](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-174">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="9ecd7-175">IL</span><span class="sxs-lookup"><span data-stu-id="9ecd7-175">IL</span></span>

<span data-ttu-id="9ecd7-176">Linguagem intermediária.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-176">Intermediate language.</span></span>

<span data-ttu-id="9ecd7-177">As linguagens .NET de nível mais alto , como C#, são compiladas em um conjunto de instruções independente de hardware, que é chamado de IL (linguagem intermediária).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-177">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="9ecd7-178">A IL às vezes é conhecida como MSIL (Microsoft Intermediate Language) ou CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-178">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="9ecd7-179">JIT</span><span class="sxs-lookup"><span data-stu-id="9ecd7-179">JIT</span></span>

<span data-ttu-id="9ecd7-180">Compilador Just-In-Time.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-180">Just-in-time compiler.</span></span>

<span data-ttu-id="9ecd7-181">Semelhante ao [AOT](#aot), esse compilador converte a [IL](#il) em um código de máquina que o processador entenda.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-181">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="9ecd7-182">Ao contrário da AOT, a compilação JIT acontece sob demanda e é executada no mesmo computador em que o código precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-182">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="9ecd7-183">Como a compilação JIT ocorre durante a execução do aplicativo, o tempo de compilação faz parte do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-183">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="9ecd7-184">Assim, os compiladores JIT precisam equilibrar o tempo gasto com a otimização do código em relação à economia que o código resultante pode produzir.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-184">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="9ecd7-185">Mas um JIT reconhece o hardware e pode evitar que os desenvolvedores tenham que fornecer implementações diferentes.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-185">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="9ecd7-186">implementação do .NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-186">implementation of .NET</span></span>

<span data-ttu-id="9ecd7-187">Uma implementação do .NET inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-187">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="9ecd7-188">Um ou mais tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-188">One or more runtimes.</span></span> <span data-ttu-id="9ecd7-189">Exemplos: CLR, CoreCLR e CoreRT.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-189">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="9ecd7-190">Uma biblioteca de classes que implemente uma versão do .NET Standard, podendo incluir APIs adicionais.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-190">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="9ecd7-191">Exemplos: biblioteca de classes base do NET Framework, biblioteca de classes base do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-191">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="9ecd7-192">Opcionalmente, uma ou mais estruturas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-192">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="9ecd7-193">Exemplos: ASP.NET, Windows Forms e WPF estão incluídos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-193">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="9ecd7-194">Opcionalmente, ferramentas de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-194">Optionally, development tools.</span></span> <span data-ttu-id="9ecd7-195">Algumas ferramentas de desenvolvimento são compartilhadas entre várias implementações.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-195">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="9ecd7-196">Exemplos de implementações do .NET:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-196">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="9ecd7-197">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ecd7-197">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="9ecd7-198">.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-198">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="9ecd7-199">UWP (Plataforma Universal do Windows)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-199">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="9ecd7-200">biblioteca</span><span class="sxs-lookup"><span data-stu-id="9ecd7-200">library</span></span>

<span data-ttu-id="9ecd7-201">Uma coleção de APIs que podem ser chamadas por aplicativos ou outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-201">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="9ecd7-202">Uma biblioteca do .NET é composta de um ou mais [assemblies](#assembly).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-202">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="9ecd7-203">A biblioteca de palavras e a [estrutura](#framework) geralmente são usadas como sinônimos.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-203">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="9ecd7-204">metapacote</span><span class="sxs-lookup"><span data-stu-id="9ecd7-204">metapackage</span></span>

<span data-ttu-id="9ecd7-205">Um pacote NuGet que não tem nenhuma biblioteca própria, mas é apenas uma lista de dependências.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-205">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="9ecd7-206">Os pacotes incluídos podem, opcionalmente, estabelecer a API para uma estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-206">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="9ecd7-207">Consulte [Pacotes, metapacotes e estruturas](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-207">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="9ecd7-208">Mono</span><span class="sxs-lookup"><span data-stu-id="9ecd7-208">Mono</span></span>

<span data-ttu-id="9ecd7-209">O Mono é uma implementação do .NET que é usada principalmente quando um pequeno tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-209">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="9ecd7-210">É o tempo de execução que impulsiona aplicativos Xamarin no Android, Mac, iOS, tvOS e watchOS e se concentra, principalmente, em aplicativos que exigem superfície reduzida.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="9ecd7-211">Ele dá suporte a todas as versões do .NET Standard publicadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="9ecd7-212">Historicamente, o Mono implementava a maior API do .NET Framework e emulava alguns dos recursos mais populares do Unix.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="9ecd7-213">Às vezes, ele é usado para executar aplicativos .NET que dependem desses recursos no Unix.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="9ecd7-214">O Mono normalmente é usado com um compilador Just-In-Time, mas ele também apresenta um compilador estático completo (compilação Ahead Of Time) que é usado em plataformas como iOS.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-214">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="9ecd7-215">Para saber mais sobre o Mono, consulte a [Documentação do Mono](http://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-215">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="9ecd7-216">.NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-216">.NET</span></span>

<span data-ttu-id="9ecd7-217">O termo coletivo para [.NET Standard](#net-standard) e todas as [implementações de .NET](#implementation-of-net), bem como as cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="9ecd7-218">Sempre em maiúsculas, nunca ".Net".</span><span class="sxs-lookup"><span data-stu-id="9ecd7-218">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="9ecd7-219">Consulte o [guia do .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-219">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="9ecd7-220">.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-220">.NET Core</span></span> 

<span data-ttu-id="9ecd7-221">Uma implementação multiplataforma de alto desempenho e software livre do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-221">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="9ecd7-222">Inclui o CoreCLR (Core Common Language Runtime), o CoreRT (tempo de execução Core AOT, em desenvolvimento), a biblioteca de classes base do Core e o SDK do Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-222">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="9ecd7-223">Consulte [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-223">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="9ecd7-224">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-224">.NET Core CLI</span></span>

<span data-ttu-id="9ecd7-225">Uma cadeia de ferramentas multiplataforma para o desenvolvimento de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-225">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="9ecd7-226">Consulte [Ferramentas da CLI (interface de linha de comando) do .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-226">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="9ecd7-227">SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-227">.NET Core SDK</span></span>

<span data-ttu-id="9ecd7-228">Um conjunto de bibliotecas e ferramentas que permitem aos desenvolvedores criar bibliotecas e aplicativos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-228">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="9ecd7-229">Inclui a [CLI do .NET Core](#net-core-cli) para a criação de aplicativos, bibliotecas e tempo de execução do .NET Core para criar e executar aplicativos e o executável do dotnet (*dotnet.exe*) que executa comandos de CLI e executa aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-229">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="9ecd7-230">Consulte a [Visão geral do SDK do .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-230">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="9ecd7-231">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ecd7-231">.NET Framework</span></span>

<span data-ttu-id="9ecd7-232">Uma implementação do .NET que é executado somente no Windows.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-232">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="9ecd7-233">Inclui o CLR (Common Language Runtime), a Biblioteca de classes base e as bibliotecas de estrutura do aplicativo, como ASP.NET, Windows Forms e WPF.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-233">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="9ecd7-234">Consulte o [Guia do .NET Framework](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-234">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="9ecd7-235">.NET Nativo</span><span class="sxs-lookup"><span data-stu-id="9ecd7-235">.NET Native</span></span>

<span data-ttu-id="9ecd7-236">Uma cadeia de ferramentas de compilador que gera código nativo AOT (Ahead Of Time), em vez de JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-236">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="9ecd7-237">A compilação acontece no computador do desenvolvedor, semelhante à maneira como um compilador e vinculador C++ funciona.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-237">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="9ecd7-238">Ela remove código não utilizado e gasta mais tempo otimizando-o.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-238">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="9ecd7-239">Ele extrai o código de bibliotecas e os mescla no executável.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-239">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="9ecd7-240">O resultado é um módulo único que representa o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-240">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="9ecd7-241">A UWP foi a primeira estrutura de aplicativo com suporte pelo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-241">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="9ecd7-242">Agora, há suporte para criação de aplicativos de console nativo para macOS, Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-242">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="9ecd7-243">Consulte [Introdução ao .NET Native e ao CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-243">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="9ecd7-244">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9ecd7-244">.NET Standard</span></span>

<span data-ttu-id="9ecd7-245">Uma especificação formal das APIs do .NET que estão disponíveis em cada implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-245">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="9ecd7-246">Às vezes, a especificação do .NET Standard também é chamada de biblioteca na documentação.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-246">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="9ecd7-247">Como uma biblioteca inclui implementações de API e não apenas especificações (interfaces), é um equívoco chamar .NET Standard de "biblioteca".</span><span class="sxs-lookup"><span data-stu-id="9ecd7-247">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="9ecd7-248">Planejamos eliminar esse uso da documentação, exceto em referência ao nome do metapacote do .NET Standard (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-248">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="9ecd7-249">Consulte [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-249">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="9ecd7-250">NGEN</span><span class="sxs-lookup"><span data-stu-id="9ecd7-250">NGEN</span></span>

<span data-ttu-id="9ecd7-251">Geração (de imagem) nativa.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-251">Native (image) generation.</span></span>

<span data-ttu-id="9ecd7-252">Você pode pensar nessa tecnologia como um compilador JIT persistente.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-252">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="9ecd7-253">Ela geralmente compila o código no computador em que o código é executado, mas a compilação normalmente ocorre no momento da instalação.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-253">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="9ecd7-254">pacote</span><span class="sxs-lookup"><span data-stu-id="9ecd7-254">package</span></span>

<span data-ttu-id="9ecd7-255">Um pacote NuGet &mdash; ou apenas um pacote &mdash; é um arquivo *.zip* com um ou mais assemblies de mesmo nome, junto com metadados adicionais, como o nome do autor.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-255">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="9ecd7-256">O arquivo *.zip* tem uma extensão *.nupkg* e pode conter ativos, como arquivos *.dll* e arquivos *.xml*, para uso com várias versões e estruturas.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-256">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple frameworks and versions.</span></span> <span data-ttu-id="9ecd7-257">Quando instalado em um aplicativo ou uma biblioteca, os ativos apropriados são selecionados com base na estrutura de destino especificada pelo aplicativo ou pela biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-257">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="9ecd7-258">Os ativos que definem a interface estão na pasta *ref* e os ativos que definem a implementação estão na pasta *lib*.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-258">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="9ecd7-259">platform</span><span class="sxs-lookup"><span data-stu-id="9ecd7-259">platform</span></span>

<span data-ttu-id="9ecd7-260">Um sistema operacional e o hardware em que ele é executado, como macOS, Windows, Linux, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-260">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="9ecd7-261">Veja alguns exemplos de uso nessas frases:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-261">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="9ecd7-262">"O .NET Core é uma implementação multiplataforma do .NET."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-262">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="9ecd7-263">"Os perfis de PCL representam plataformas da Microsoft enquanto que o .NET Standard é independente de plataforma."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-263">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="9ecd7-264">A documentação do .NET frequentemente usa "plataforma .NET" para significar uma implementação do .NET ou a pilha do .NET, incluindo todas as implementações.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-264">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="9ecd7-265">Os dois usos tendem a ser confundidos com o significado (SO/hardware) principal, portanto planejamos eliminar esses usos da documentação.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-265">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="9ecd7-266">tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9ecd7-266">runtime</span></span>

<span data-ttu-id="9ecd7-267">O ambiente de execução de um programa gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-267">The execution environment for a managed program.</span></span>

<span data-ttu-id="9ecd7-268">O SO faz parte do ambiente do tempo de execução, mas não faz parte do tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-268">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="9ecd7-269">Aqui estão alguns exemplos de tempos de execução do .NET:</span><span class="sxs-lookup"><span data-stu-id="9ecd7-269">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="9ecd7-270">CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-270">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="9ecd7-271">Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-271">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="9ecd7-272">.NET Native (para UWP)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-272">.NET Native (for UWP)</span></span>
- <span data-ttu-id="9ecd7-273">tempo de execução Mono</span><span class="sxs-lookup"><span data-stu-id="9ecd7-273">Mono runtime</span></span>

<span data-ttu-id="9ecd7-274">Às vezes, a documentação do .NET usa "tempo de execução" para se referir a uma implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-274">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="9ecd7-275">Por exemplo, nas seguintes sentenças "tempo de execução" deve ser substituído por "implementação":</span><span class="sxs-lookup"><span data-stu-id="9ecd7-275">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="9ecd7-276">"Os diversos tempos de execução do .NET implementam versões específicas do .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-276">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="9ecd7-277">"Bibliotecas destinadas à execução em vários tempos de execução devem ter essa estrutura como destino."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-277">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="9ecd7-278">(referindo-se ao .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="9ecd7-278">(referring to .NET Standard)</span></span>
- <span data-ttu-id="9ecd7-279">"Os diversos tempos de execução do .NET implementam versões específicas do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-279">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="9ecd7-280">…</span><span class="sxs-lookup"><span data-stu-id="9ecd7-280">…</span></span> <span data-ttu-id="9ecd7-281">Cada versão de tempo de execução do .NET anuncia a última versão do .NET Standard à qual ele dá suporte..."</span><span class="sxs-lookup"><span data-stu-id="9ecd7-281">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="9ecd7-282">Planejamos eliminar esse uso inconsistente.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-282">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="9ecd7-283">stack</span><span class="sxs-lookup"><span data-stu-id="9ecd7-283">stack</span></span>

<span data-ttu-id="9ecd7-284">Um conjunto de tecnologias de programação que são usadas para compilar e executar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-284">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="9ecd7-285">"A pilha do .NET" refere-se ao .NET Standard e a todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-285">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="9ecd7-286">A frase "uma pilha do .NET" pode se referir a uma implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-286">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="9ecd7-287">estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="9ecd7-287">target framework</span></span>

<span data-ttu-id="9ecd7-288">A coleção de APIs da qual um aplicativo ou biblioteca do .NET depende.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-288">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="9ecd7-289">Um aplicativo ou uma biblioteca pode se destinar a uma versão do .NET Standard (por exemplo, .NET Standard 2.0), que é a especificação de um conjunto padronizado de APIs entre todas as implementações de .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-289">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="9ecd7-290">Um aplicativo ou uma biblioteca também pode se destinar a uma versão de uma implementação específica do .NET, obtendo acesso a APIs específicas da implementação.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-290">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="9ecd7-291">Por exemplo, um aplicativo que tem como destino o Xamarin.iOS obtém acesso aos wrappers da API fornecidos para Xamarin iOS.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-291">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="9ecd7-292">Para algumas estruturas de destino (por exemplo, o .NET Framework) as APIs disponíveis são definidas pelos assemblies que uma implementação do .NET instala em um sistema, que podem incluir as APIs de estrutura do aplicativo (por exemplo, ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-292">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="9ecd7-293">Para estruturas de destino baseadas em pacote (como .NET Standard e .NET Core), a APIs de estrutura são definidas por pacotes instalados no aplicativo ou na biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-293">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="9ecd7-294">Nesse caso, a estrutura de destino especifica implicitamente um metapacote que faz referência a todos os pacotes que, juntos, compõem a estrutura.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-294">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="9ecd7-295">Consulte [Estruturas de destino](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-295">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="9ecd7-296">TFM</span><span class="sxs-lookup"><span data-stu-id="9ecd7-296">TFM</span></span>

<span data-ttu-id="9ecd7-297">Moniker da estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-297">Target framework moniker.</span></span>

<span data-ttu-id="9ecd7-298">Um formato de token padronizado para especificar a estrutura de destino de um aplicativo ou uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-298">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="9ecd7-299">As estruturas de destino são geralmente referenciadas por um nome curto, como `net462`.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-299">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="9ecd7-300">Os TFMs de formato longo (como. .NETFramework,Version=4.6.2) existem, mas não são geralmente usados para especificar uma estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-300">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="9ecd7-301">Consulte [Estruturas de destino](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-301">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="9ecd7-302">UWP</span><span class="sxs-lookup"><span data-stu-id="9ecd7-302">UWP</span></span>

<span data-ttu-id="9ecd7-303">Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-303">Universal Windows Platform.</span></span>

<span data-ttu-id="9ecd7-304">Uma implementação do .NET que é usada para criar aplicativos do Windows modernos e sensíveis ao toque, bem como software para a IoT (Internet das Coisas).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-304">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="9ecd7-305">Ela foi projetada para unificar os diferentes tipos de dispositivos que você talvez tenha como destinho, incluindo PCs, tablets, phablets, telefones e até mesmo ao Xbox.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-305">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="9ecd7-306">A UWP fornece muitos serviços, como um repositório centralizado de aplicativos, um ambiente de execução (AppContainer) e um conjunto de APIs do Windows para usar em vez das APIS do Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="9ecd7-306">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="9ecd7-307">Os aplicativos podem ser escritos em C++, C#, VB.NET e JavaScript.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-307">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="9ecd7-308">Ao usar o C# e VB.NET, as APIs do .NET são fornecidas pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9ecd7-308">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ecd7-309">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ecd7-309">See also</span></span>

[<span data-ttu-id="9ecd7-310">Guia do .NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-310">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="9ecd7-311">Guia do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9ecd7-311">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="9ecd7-312">.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-312">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="9ecd7-313">Visão geral do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9ecd7-313">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="9ecd7-314">Visão geral do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9ecd7-314">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

