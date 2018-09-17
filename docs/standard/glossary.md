---
title: Glossário .NET
description: Descubra o significado de termos selecionados usados na documentação do .NET.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 11fad691021ec897348177c67134750e72b4ff7c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45647428"
---
# <a name="net-glossary"></a><span data-ttu-id="d18c2-103">Glossário .NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-103">.NET Glossary</span></span>

<span data-ttu-id="d18c2-104">A principal meta deste glossário é esclarecer os significados de termos e acrônimos selecionados que aparecem com frequência na documentação do .NET sem definições.</span><span class="sxs-lookup"><span data-stu-id="d18c2-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="d18c2-105">AOT</span><span class="sxs-lookup"><span data-stu-id="d18c2-105">AOT</span></span>

<span data-ttu-id="d18c2-106">Compilador Ahead-of-Time.</span><span class="sxs-lookup"><span data-stu-id="d18c2-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="d18c2-107">Semelhante ao [JIT](#jit), esse compilador também converte [IL](#il) em código de máquina.</span><span class="sxs-lookup"><span data-stu-id="d18c2-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="d18c2-108">Diferentemente da compilação JIT, a compilação AOT acontece antes que o aplicativo seja executado e normalmente é executada em um computador diferente.</span><span class="sxs-lookup"><span data-stu-id="d18c2-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="d18c2-109">Como as cadeias da ferramenta da AOT não compilam em tempo de execução, elas não têm que minimizar o tempo gasto na compilação.</span><span class="sxs-lookup"><span data-stu-id="d18c2-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="d18c2-110">Isso significa que elas podem gastar mais tempo em otimização.</span><span class="sxs-lookup"><span data-stu-id="d18c2-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="d18c2-111">Como o contexto da AOT é o aplicativo inteiro, o compilador AOT também executa a vinculação de módulo cruzado e a análise de programa inteiro, o que significa que todas as referências são seguidas e um único executável é produzido.</span><span class="sxs-lookup"><span data-stu-id="d18c2-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="d18c2-112">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-112">ASP.NET</span></span> 

<span data-ttu-id="d18c2-113">A implementação do ASP.NET original que é fornecida com o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d18c2-113">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="d18c2-114">Às vezes, o ASP.NET é um termo abrangente que se refere a ambas as implementações de ASP.NET, incluindo o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-114">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="d18c2-115">O significado que o termo carrega em uma determinada instância é determinado pelo contexto.</span><span class="sxs-lookup"><span data-stu-id="d18c2-115">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="d18c2-116">Consulte ASP.NET 4.x quando quiser esclarecer que você não está usando ASP.NET para as duas implementações.</span><span class="sxs-lookup"><span data-stu-id="d18c2-116">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="d18c2-117">Confira [Documentação do ASP.NET](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="d18c2-117">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="d18c2-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-118">ASP.NET Core</span></span>

<span data-ttu-id="d18c2-119">Uma implementação multiplataforma de alto desempenho e software livre do ASP.NET com base no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="d18c2-120">Confira [Documentação do ASP.NET Core](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="d18c2-120">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="d18c2-121">assembly</span><span class="sxs-lookup"><span data-stu-id="d18c2-121">assembly</span></span>

<span data-ttu-id="d18c2-122">Um arquivo *.dll*/*.exe* que contém uma coleção de APIs que podem ser chamadas por aplicativos ou outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="d18c2-122">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="d18c2-123">Um assembly pode incluir tipos como interfaces, classes, estruturas, enumerações e delegados.</span><span class="sxs-lookup"><span data-stu-id="d18c2-123">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="d18c2-124">Às vezes, os assemblies em uma pasta *bin* de projeto são chamados de *binários*.</span><span class="sxs-lookup"><span data-stu-id="d18c2-124">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="d18c2-125">Consulte também [biblioteca](#library).</span><span class="sxs-lookup"><span data-stu-id="d18c2-125">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="d18c2-126">CLR</span><span class="sxs-lookup"><span data-stu-id="d18c2-126">CLR</span></span>

<span data-ttu-id="d18c2-127">Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="d18c2-127">Common Language Runtime.</span></span>

<span data-ttu-id="d18c2-128">O significado exato depende do contexto, mas geralmente se refere ao tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d18c2-128">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="d18c2-129">O CLR manipula a alocação e o gerenciamento de memória.</span><span class="sxs-lookup"><span data-stu-id="d18c2-129">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="d18c2-130">O CLR também é uma máquina virtual que não só executa aplicativos, mas também gera e compila código dinamicamente usando um compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="d18c2-130">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="d18c2-131">A implementação atual do CLR da Microsoft é somente para Windows.</span><span class="sxs-lookup"><span data-stu-id="d18c2-131">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="d18c2-132">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="d18c2-132">CoreCLR</span></span>

<span data-ttu-id="d18c2-133">Common Language Runtime do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-133">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="d18c2-134">Esse CLR é criado com a mesma base de código que o CLR.</span><span class="sxs-lookup"><span data-stu-id="d18c2-134">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="d18c2-135">Originalmente, o CoreCLR era o tempo de execução do Silverlight e foi projetado para ser executado em várias plataformas, especificamente o Windows e OS X. Agora o CoreCLR faz parte do .NET Core e representa uma versão simplificada do CLR.</span><span class="sxs-lookup"><span data-stu-id="d18c2-135">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="d18c2-136">Ele ainda é um tempo de execução multiplataforma, incluindo também suporte para várias distribuições do Linux.</span><span class="sxs-lookup"><span data-stu-id="d18c2-136">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="d18c2-137">O CoreCLR também é uma máquina virtual com recursos JIT e de execução de código.</span><span class="sxs-lookup"><span data-stu-id="d18c2-137">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="d18c2-138">CoreFX</span><span class="sxs-lookup"><span data-stu-id="d18c2-138">CoreFX</span></span>

<span data-ttu-id="d18c2-139">BCL (biblioteca de classes base) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-139">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="d18c2-140">Um conjunto de bibliotecas que compõem os namespaces System.\* e, até certo limite, Microsoft.\*.</span><span class="sxs-lookup"><span data-stu-id="d18c2-140">A set of libraries that comprise the System.\* (and to a limited extent  Microsoft.\*) namespaces.</span></span> <span data-ttu-id="d18c2-141">A BCL é uma estrutura de nível inferior e de uso geral, base para a criação de estruturas de aplicativo de nível mais alto, como o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-141">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="d18c2-142">O código-fonte da BCL do .NET Core está contido no [repositório CoreFX](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="d18c2-142">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="d18c2-143">No entanto, a maioria das APIs do .NET Core também estão disponíveis no .NET Framework, portanto você pode pensar no CoreFX como um fork da BCL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d18c2-143">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="d18c2-144">CoreRT</span><span class="sxs-lookup"><span data-stu-id="d18c2-144">CoreRT</span></span>

<span data-ttu-id="d18c2-145">Tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-145">.NET Core runtime.</span></span>

<span data-ttu-id="d18c2-146">Ao contrário do CLR/CoreCLR, o CoreRT não é uma máquina virtual, o que significa que ele não inclui os recursos para gerar e executar código dinamicamente, já que não inclui um [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="d18c2-146">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="d18c2-147">No entanto, ele inclui a [GC](#gc) e a capacidade de RTTI (identificação de tipo de tempo de execução) e reflexão.</span><span class="sxs-lookup"><span data-stu-id="d18c2-147">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="d18c2-148">Contudo, seu sistema de tipos é projetado para que os metadados para reflexão não sejam necessários.</span><span class="sxs-lookup"><span data-stu-id="d18c2-148">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="d18c2-149">Isso permite ter uma cadeia de ferramentas [AOT](#aot) que possa desvincular metadados supérfluos e, mais importante, identificar código que o aplicativo não usa.</span><span class="sxs-lookup"><span data-stu-id="d18c2-149">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="d18c2-150">O CoreRT está em desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d18c2-150">CoreRT is in development.</span></span>

<span data-ttu-id="d18c2-151">Consulte [Introdução ao .NET Native e ao CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="d18c2-151">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="d18c2-152">ecossistema</span><span class="sxs-lookup"><span data-stu-id="d18c2-152">ecosystem</span></span>

<span data-ttu-id="d18c2-153">Todos os softwares de tempo de execução, as ferramentas de desenvolvimento e os recursos da comunidade que são usados para compilar e executar aplicativos de uma determinada tecnologia.</span><span class="sxs-lookup"><span data-stu-id="d18c2-153">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="d18c2-154">O termo "Ecossistema do .NET" difere de termos semelhantes, como "Pilha do .NET", em relação à inclusão de bibliotecas e aplicativos de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d18c2-154">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="d18c2-155">Veja um exemplo em uma frase:</span><span class="sxs-lookup"><span data-stu-id="d18c2-155">Here's an example in a sentence:</span></span>

- <span data-ttu-id="d18c2-156">"A motivação por trás do [.NET Standard](#net-standard) é estabelecer maior uniformidade no ecossistema do .NET."</span><span class="sxs-lookup"><span data-stu-id="d18c2-156">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="d18c2-157">estrutura</span><span class="sxs-lookup"><span data-stu-id="d18c2-157">framework</span></span>

<span data-ttu-id="d18c2-158">Em geral, uma coleção abrangente de APIs que facilita o desenvolvimento e a implantação de aplicativos que são baseados em uma tecnologia específica.</span><span class="sxs-lookup"><span data-stu-id="d18c2-158">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="d18c2-159">Nesse sentido geral, o ASP.NET Core e o Windows Forms são exemplos de estruturas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d18c2-159">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="d18c2-160">Consulte também [biblioteca](#library).</span><span class="sxs-lookup"><span data-stu-id="d18c2-160">See also [library](#library).</span></span>

<span data-ttu-id="d18c2-161">A palavra "estrutura" tem um significado técnico mais específico nos seguintes termos:</span><span class="sxs-lookup"><span data-stu-id="d18c2-161">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="d18c2-162">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d18c2-162">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="d18c2-163">estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="d18c2-163">target framework</span></span>](#target-framework)
* [<span data-ttu-id="d18c2-164">TFM (Moniker de Estrutura de Destino)</span><span class="sxs-lookup"><span data-stu-id="d18c2-164">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="d18c2-165">Na documentação existente, "estrutura" às vezes se refere a uma [implementação do .NET](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="d18c2-165">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="d18c2-166">Por exemplo, um artigo pode chamar o .NET Core de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="d18c2-166">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="d18c2-167">Planejamos eliminar da documentação esse uso confuso da palavra.</span><span class="sxs-lookup"><span data-stu-id="d18c2-167">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="d18c2-168">GC</span><span class="sxs-lookup"><span data-stu-id="d18c2-168">GC</span></span>

<span data-ttu-id="d18c2-169">Coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="d18c2-169">Garbage collector.</span></span>

<span data-ttu-id="d18c2-170">O coletor de lixo é uma implementação do gerenciamento automático de memória.</span><span class="sxs-lookup"><span data-stu-id="d18c2-170">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="d18c2-171">O GC libera a memória ocupada por objetos que não estejam mais em uso.</span><span class="sxs-lookup"><span data-stu-id="d18c2-171">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="d18c2-172">Consulte [Coleta de lixo](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-172">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="d18c2-173">IL</span><span class="sxs-lookup"><span data-stu-id="d18c2-173">IL</span></span>

<span data-ttu-id="d18c2-174">Linguagem intermediária.</span><span class="sxs-lookup"><span data-stu-id="d18c2-174">Intermediate language.</span></span>

<span data-ttu-id="d18c2-175">As linguagens .NET de nível mais alto , como C#, são compiladas em um conjunto de instruções independente de hardware, que é chamado de IL (linguagem intermediária).</span><span class="sxs-lookup"><span data-stu-id="d18c2-175">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="d18c2-176">A IL às vezes é conhecida como MSIL (Microsoft Intermediate Language) ou CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d18c2-176">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="d18c2-177">JIT</span><span class="sxs-lookup"><span data-stu-id="d18c2-177">JIT</span></span>

<span data-ttu-id="d18c2-178">Compilador Just-In-Time.</span><span class="sxs-lookup"><span data-stu-id="d18c2-178">Just-in-time compiler.</span></span>

<span data-ttu-id="d18c2-179">Semelhante ao [AOT](#aot), esse compilador converte a [IL](#il) em um código de máquina que o processador entenda.</span><span class="sxs-lookup"><span data-stu-id="d18c2-179">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="d18c2-180">Ao contrário da AOT, a compilação JIT acontece sob demanda e é executada no mesmo computador em que o código precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="d18c2-180">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="d18c2-181">Como a compilação JIT ocorre durante a execução do aplicativo, o tempo de compilação faz parte do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d18c2-181">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="d18c2-182">Assim, os compiladores JIT precisam equilibrar o tempo gasto com a otimização do código em relação à economia que o código resultante pode produzir.</span><span class="sxs-lookup"><span data-stu-id="d18c2-182">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="d18c2-183">Mas um JIT reconhece o hardware e pode evitar que os desenvolvedores tenham que fornecer implementações diferentes.</span><span class="sxs-lookup"><span data-stu-id="d18c2-183">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="d18c2-184">implementação do .NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-184">implementation of .NET</span></span>

<span data-ttu-id="d18c2-185">Uma implementação do .NET inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d18c2-185">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="d18c2-186">Um ou mais tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="d18c2-186">One or more runtimes.</span></span> <span data-ttu-id="d18c2-187">Exemplos: CLR, CoreCLR e CoreRT.</span><span class="sxs-lookup"><span data-stu-id="d18c2-187">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="d18c2-188">Uma biblioteca de classes que implemente uma versão do .NET Standard, podendo incluir APIs adicionais.</span><span class="sxs-lookup"><span data-stu-id="d18c2-188">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="d18c2-189">Exemplos: biblioteca de classes base do NET Framework, biblioteca de classes base do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-189">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="d18c2-190">Opcionalmente, uma ou mais estruturas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d18c2-190">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="d18c2-191">Exemplos: ASP.NET, Windows Forms e WPF estão incluídos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d18c2-191">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="d18c2-192">Opcionalmente, ferramentas de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="d18c2-192">Optionally, development tools.</span></span> <span data-ttu-id="d18c2-193">Algumas ferramentas de desenvolvimento são compartilhadas entre várias implementações.</span><span class="sxs-lookup"><span data-stu-id="d18c2-193">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="d18c2-194">Exemplos de implementações do .NET:</span><span class="sxs-lookup"><span data-stu-id="d18c2-194">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="d18c2-195">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d18c2-195">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="d18c2-196">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-196">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="d18c2-197">UWP (Plataforma Universal do Windows)</span><span class="sxs-lookup"><span data-stu-id="d18c2-197">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="d18c2-198">biblioteca</span><span class="sxs-lookup"><span data-stu-id="d18c2-198">library</span></span>

<span data-ttu-id="d18c2-199">Uma coleção de APIs que podem ser chamadas por aplicativos ou outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="d18c2-199">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="d18c2-200">Uma biblioteca do .NET é composta de um ou mais [assemblies](#assembly).</span><span class="sxs-lookup"><span data-stu-id="d18c2-200">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="d18c2-201">A biblioteca de palavras e a [estrutura](#framework) geralmente são usadas como sinônimos.</span><span class="sxs-lookup"><span data-stu-id="d18c2-201">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="d18c2-202">metapacote</span><span class="sxs-lookup"><span data-stu-id="d18c2-202">metapackage</span></span>

<span data-ttu-id="d18c2-203">Um pacote NuGet que não tem nenhuma biblioteca própria, mas é apenas uma lista de dependências.</span><span class="sxs-lookup"><span data-stu-id="d18c2-203">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="d18c2-204">Os pacotes incluídos podem, opcionalmente, estabelecer a API para uma estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="d18c2-204">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="d18c2-205">Consulte [Pacotes, metapacotes e estruturas](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="d18c2-205">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="d18c2-206">Mono</span><span class="sxs-lookup"><span data-stu-id="d18c2-206">Mono</span></span>

<span data-ttu-id="d18c2-207">O Mono é uma implementação do .NET que é usada principalmente quando um pequeno tempo de execução é necessário.</span><span class="sxs-lookup"><span data-stu-id="d18c2-207">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="d18c2-208">É o tempo de execução que impulsiona aplicativos Xamarin no Android, Mac, iOS, tvOS e watchOS e se concentra, principalmente, em aplicativos que exigem superfície reduzida.</span><span class="sxs-lookup"><span data-stu-id="d18c2-208">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="d18c2-209">Ele dá suporte a todas as versões do .NET Standard publicadas atualmente.</span><span class="sxs-lookup"><span data-stu-id="d18c2-209">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="d18c2-210">Historicamente, o Mono implementava a maior API do .NET Framework e emulava alguns dos recursos mais populares do Unix.</span><span class="sxs-lookup"><span data-stu-id="d18c2-210">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="d18c2-211">Às vezes, ele é usado para executar aplicativos .NET que dependem desses recursos no Unix.</span><span class="sxs-lookup"><span data-stu-id="d18c2-211">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="d18c2-212">O Mono normalmente é usado com um compilador Just-In-Time, mas ele também apresenta um compilador estático completo (compilação Ahead Of Time) que é usado em plataformas como iOS.</span><span class="sxs-lookup"><span data-stu-id="d18c2-212">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="d18c2-213">Para saber mais sobre o Mono, consulte a [Documentação do Mono](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="d18c2-213">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="d18c2-214">.NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-214">.NET</span></span>

<span data-ttu-id="d18c2-215">O termo coletivo para [.NET Standard](#net-standard) e todas as [implementações de .NET](#implementation-of-net), bem como as cargas de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d18c2-215">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="d18c2-216">Sempre em maiúsculas, nunca ".Net".</span><span class="sxs-lookup"><span data-stu-id="d18c2-216">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="d18c2-217">Consulte o [guia do .NET](index.md)</span><span class="sxs-lookup"><span data-stu-id="d18c2-217">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="d18c2-218">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-218">.NET Core</span></span> 

<span data-ttu-id="d18c2-219">Uma implementação multiplataforma de alto desempenho e software livre do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-219">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="d18c2-220">Inclui o CoreCLR (Core Common Language Runtime), o CoreRT (tempo de execução Core AOT, em desenvolvimento), a biblioteca de classes base do Core e o SDK do Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-220">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="d18c2-221">Consulte [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-221">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="d18c2-222">CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-222">.NET Core CLI</span></span>

<span data-ttu-id="d18c2-223">Uma cadeia de ferramentas multiplataforma para o desenvolvimento de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-223">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="d18c2-224">Consulte [Ferramentas da CLI (interface de linha de comando) do .NET Core](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-224">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="d18c2-225">SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-225">.NET Core SDK</span></span>

<span data-ttu-id="d18c2-226">Um conjunto de bibliotecas e ferramentas que permitem aos desenvolvedores criar bibliotecas e aplicativos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-226">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="d18c2-227">Inclui a [CLI do .NET Core](#net-core-cli) para a criação de aplicativos, bibliotecas e tempo de execução do .NET Core para criar e executar aplicativos e o executável do dotnet (*dotnet.exe*) que executa comandos de CLI e executa aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d18c2-227">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="d18c2-228">Consulte a [Visão geral do SDK do .NET Core](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-228">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="d18c2-229">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d18c2-229">.NET Framework</span></span>

<span data-ttu-id="d18c2-230">Uma implementação do .NET que é executado somente no Windows.</span><span class="sxs-lookup"><span data-stu-id="d18c2-230">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="d18c2-231">Inclui o CLR (Common Language Runtime), a Biblioteca de classes base e as bibliotecas de estrutura do aplicativo, como ASP.NET, Windows Forms e WPF.</span><span class="sxs-lookup"><span data-stu-id="d18c2-231">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="d18c2-232">Consulte o [Guia do .NET Framework](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-232">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="d18c2-233">.NET Nativo</span><span class="sxs-lookup"><span data-stu-id="d18c2-233">.NET Native</span></span>

<span data-ttu-id="d18c2-234">Uma cadeia de ferramentas de compilador que gera código nativo AOT (Ahead Of Time), em vez de JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="d18c2-234">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="d18c2-235">A compilação acontece no computador do desenvolvedor, semelhante à maneira como um compilador e vinculador C++ funciona.</span><span class="sxs-lookup"><span data-stu-id="d18c2-235">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="d18c2-236">Ela remove código não utilizado e gasta mais tempo otimizando-o.</span><span class="sxs-lookup"><span data-stu-id="d18c2-236">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="d18c2-237">Ele extrai o código de bibliotecas e os mescla no executável.</span><span class="sxs-lookup"><span data-stu-id="d18c2-237">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="d18c2-238">O resultado é um módulo único que representa o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="d18c2-238">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="d18c2-239">A UWP foi a primeira estrutura de aplicativo com suporte pelo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d18c2-239">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="d18c2-240">Agora, há suporte para criação de aplicativos de console nativo para macOS, Windows e Linux.</span><span class="sxs-lookup"><span data-stu-id="d18c2-240">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="d18c2-241">Consulte [Introdução ao .NET Native e ao CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="d18c2-241">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="d18c2-242">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d18c2-242">.NET Standard</span></span>

<span data-ttu-id="d18c2-243">Uma especificação formal das APIs do .NET que estão disponíveis em cada implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-243">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="d18c2-244">Às vezes, a especificação do .NET Standard também é chamada de biblioteca na documentação.</span><span class="sxs-lookup"><span data-stu-id="d18c2-244">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="d18c2-245">Como uma biblioteca inclui implementações de API e não apenas especificações (interfaces), é um equívoco chamar .NET Standard de "biblioteca".</span><span class="sxs-lookup"><span data-stu-id="d18c2-245">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="d18c2-246">Planejamos eliminar esse uso da documentação, exceto em referência ao nome do metapacote do .NET Standard (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="d18c2-246">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="d18c2-247">Consulte [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-247">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="d18c2-248">NGEN</span><span class="sxs-lookup"><span data-stu-id="d18c2-248">NGEN</span></span>

<span data-ttu-id="d18c2-249">Geração (de imagem) nativa.</span><span class="sxs-lookup"><span data-stu-id="d18c2-249">Native (image) generation.</span></span>

<span data-ttu-id="d18c2-250">Você pode pensar nessa tecnologia como um compilador JIT persistente.</span><span class="sxs-lookup"><span data-stu-id="d18c2-250">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="d18c2-251">Ela geralmente compila o código no computador em que o código é executado, mas a compilação normalmente ocorre no momento da instalação.</span><span class="sxs-lookup"><span data-stu-id="d18c2-251">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="d18c2-252">pacote</span><span class="sxs-lookup"><span data-stu-id="d18c2-252">package</span></span>

<span data-ttu-id="d18c2-253">Um pacote NuGet &mdash; ou apenas um pacote &mdash; é um arquivo *.zip* com um ou mais assemblies de mesmo nome, junto com metadados adicionais, como o nome do autor.</span><span class="sxs-lookup"><span data-stu-id="d18c2-253">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="d18c2-254">O arquivo *.zip* tem uma extensão *.nupkg* e pode conter ativos, como arquivos *.dll* e arquivos *.xml*, para uso com várias versões e estruturas de destino.</span><span class="sxs-lookup"><span data-stu-id="d18c2-254">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="d18c2-255">Quando instalado em um aplicativo ou uma biblioteca, os ativos apropriados são selecionados com base na estrutura de destino especificada pelo aplicativo ou pela biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d18c2-255">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="d18c2-256">Os ativos que definem a interface estão na pasta *ref* e os ativos que definem a implementação estão na pasta *lib*.</span><span class="sxs-lookup"><span data-stu-id="d18c2-256">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="d18c2-257">platform</span><span class="sxs-lookup"><span data-stu-id="d18c2-257">platform</span></span>

<span data-ttu-id="d18c2-258">Um sistema operacional e o hardware em que ele é executado, como macOS, Windows, Linux, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="d18c2-258">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="d18c2-259">Veja alguns exemplos de uso nessas frases:</span><span class="sxs-lookup"><span data-stu-id="d18c2-259">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="d18c2-260">"O .NET Core é uma implementação multiplataforma do .NET."</span><span class="sxs-lookup"><span data-stu-id="d18c2-260">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="d18c2-261">"Os perfis de PCL representam plataformas da Microsoft enquanto que o .NET Standard é independente de plataforma."</span><span class="sxs-lookup"><span data-stu-id="d18c2-261">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="d18c2-262">A documentação do .NET frequentemente usa "plataforma .NET" para significar uma implementação do .NET ou a pilha do .NET, incluindo todas as implementações.</span><span class="sxs-lookup"><span data-stu-id="d18c2-262">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="d18c2-263">Os dois usos tendem a ser confundidos com o significado (SO/hardware) principal, portanto planejamos eliminar esses usos da documentação.</span><span class="sxs-lookup"><span data-stu-id="d18c2-263">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="d18c2-264">tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d18c2-264">runtime</span></span>

<span data-ttu-id="d18c2-265">O ambiente de execução de um programa gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d18c2-265">The execution environment for a managed program.</span></span>

<span data-ttu-id="d18c2-266">O SO faz parte do ambiente do tempo de execução, mas não faz parte do tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-266">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="d18c2-267">Aqui estão alguns exemplos de tempos de execução do .NET:</span><span class="sxs-lookup"><span data-stu-id="d18c2-267">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="d18c2-268">CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="d18c2-268">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="d18c2-269">Core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="d18c2-269">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="d18c2-270">.NET Native (para UWP)</span><span class="sxs-lookup"><span data-stu-id="d18c2-270">.NET Native (for UWP)</span></span>
- <span data-ttu-id="d18c2-271">tempo de execução Mono</span><span class="sxs-lookup"><span data-stu-id="d18c2-271">Mono runtime</span></span>

<span data-ttu-id="d18c2-272">Às vezes, a documentação do .NET usa "tempo de execução" para se referir a uma implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-272">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="d18c2-273">Por exemplo, nas seguintes sentenças "tempo de execução" deve ser substituído por "implementação":</span><span class="sxs-lookup"><span data-stu-id="d18c2-273">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="d18c2-274">"Os diversos tempos de execução do .NET implementam versões específicas do .NET Standard."</span><span class="sxs-lookup"><span data-stu-id="d18c2-274">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="d18c2-275">"Bibliotecas destinadas à execução em vários tempos de execução devem ter essa estrutura como destino."</span><span class="sxs-lookup"><span data-stu-id="d18c2-275">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="d18c2-276">(referindo-se ao .NET Standard)</span><span class="sxs-lookup"><span data-stu-id="d18c2-276">(referring to .NET Standard)</span></span>
- <span data-ttu-id="d18c2-277">"Os diversos tempos de execução do .NET implementam versões específicas do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d18c2-277">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="d18c2-278">…</span><span class="sxs-lookup"><span data-stu-id="d18c2-278">…</span></span> <span data-ttu-id="d18c2-279">Cada versão de tempo de execução do .NET anuncia a última versão do .NET Standard à qual ele dá suporte..."</span><span class="sxs-lookup"><span data-stu-id="d18c2-279">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="d18c2-280">Planejamos eliminar esse uso inconsistente.</span><span class="sxs-lookup"><span data-stu-id="d18c2-280">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="d18c2-281">stack</span><span class="sxs-lookup"><span data-stu-id="d18c2-281">stack</span></span>

<span data-ttu-id="d18c2-282">Um conjunto de tecnologias de programação que são usadas para compilar e executar aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d18c2-282">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="d18c2-283">"A pilha do .NET" refere-se ao .NET Standard e a todas as implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-283">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="d18c2-284">A frase "uma pilha do .NET" pode se referir a uma implementação do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-284">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="d18c2-285">estrutura de destino</span><span class="sxs-lookup"><span data-stu-id="d18c2-285">target framework</span></span>

<span data-ttu-id="d18c2-286">A coleção de APIs da qual um aplicativo ou biblioteca do .NET depende.</span><span class="sxs-lookup"><span data-stu-id="d18c2-286">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="d18c2-287">Um aplicativo ou uma biblioteca pode se destinar a uma versão do .NET Standard (por exemplo, .NET Standard 2.0), que é a especificação de um conjunto padronizado de APIs entre todas as implementações de .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-287">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="d18c2-288">Um aplicativo ou uma biblioteca também pode se destinar a uma versão de uma implementação específica do .NET, obtendo acesso a APIs específicas da implementação.</span><span class="sxs-lookup"><span data-stu-id="d18c2-288">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="d18c2-289">Por exemplo, um aplicativo que tem como destino o Xamarin.iOS obtém acesso aos wrappers da API fornecidos para Xamarin iOS.</span><span class="sxs-lookup"><span data-stu-id="d18c2-289">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="d18c2-290">Para algumas estruturas de destino (por exemplo, o .NET Framework) as APIs disponíveis são definidas pelos assemblies que uma implementação do .NET instala em um sistema, que podem incluir as APIs de estrutura do aplicativo (por exemplo, ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="d18c2-290">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="d18c2-291">Para estruturas de destino baseadas em pacote (como .NET Standard e .NET Core), a APIs de estrutura são definidas por pacotes instalados no aplicativo ou na biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d18c2-291">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="d18c2-292">Nesse caso, a estrutura de destino especifica implicitamente um metapacote que faz referência a todos os pacotes que, juntos, compõem a estrutura.</span><span class="sxs-lookup"><span data-stu-id="d18c2-292">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="d18c2-293">Consulte [Estruturas de destino](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-293">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="d18c2-294">TFM</span><span class="sxs-lookup"><span data-stu-id="d18c2-294">TFM</span></span>

<span data-ttu-id="d18c2-295">Moniker da estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="d18c2-295">Target framework moniker.</span></span>

<span data-ttu-id="d18c2-296">Um formato de token padronizado para especificar a estrutura de destino de um aplicativo ou uma biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="d18c2-296">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="d18c2-297">As estruturas de destino são geralmente referenciadas por um nome curto, como `net462`.</span><span class="sxs-lookup"><span data-stu-id="d18c2-297">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="d18c2-298">Os TFMs de formato longo (como. .NETFramework,Version=4.6.2) existem, mas não são geralmente usados para especificar uma estrutura de destino.</span><span class="sxs-lookup"><span data-stu-id="d18c2-298">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="d18c2-299">Consulte [Estruturas de destino](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d18c2-299">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="d18c2-300">UWP</span><span class="sxs-lookup"><span data-stu-id="d18c2-300">UWP</span></span>

<span data-ttu-id="d18c2-301">Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="d18c2-301">Universal Windows Platform.</span></span>

<span data-ttu-id="d18c2-302">Uma implementação do .NET que é usada para criar aplicativos do Windows modernos e sensíveis ao toque, bem como software para a IoT (Internet das Coisas).</span><span class="sxs-lookup"><span data-stu-id="d18c2-302">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="d18c2-303">Ela foi projetada para unificar os diferentes tipos de dispositivos que você talvez tenha como destinho, incluindo PCs, tablets, phablets, telefones e até mesmo ao Xbox.</span><span class="sxs-lookup"><span data-stu-id="d18c2-303">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="d18c2-304">A UWP fornece muitos serviços, como um repositório centralizado de aplicativos, um ambiente de execução (AppContainer) e um conjunto de APIs do Windows para usar em vez das APIS do Win32 (WinRT).</span><span class="sxs-lookup"><span data-stu-id="d18c2-304">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="d18c2-305">Os aplicativos podem ser escritos em C++, C#, VB.NET e JavaScript.</span><span class="sxs-lookup"><span data-stu-id="d18c2-305">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="d18c2-306">Ao usar o C# e VB.NET, as APIs do .NET são fornecidas pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d18c2-306">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="d18c2-307">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d18c2-307">See also</span></span>

- [<span data-ttu-id="d18c2-308">Guia do .NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-308">.NET Guide</span></span>](index.md)  
- [<span data-ttu-id="d18c2-309">Guia do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d18c2-309">.NET Framework Guide</span></span>](../framework/index.md)  
- [<span data-ttu-id="d18c2-310">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-310">.NET Core</span></span>](../core/index.md)  
- [<span data-ttu-id="d18c2-311">Visão geral do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d18c2-311">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
- [<span data-ttu-id="d18c2-312">Visão geral do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d18c2-312">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  
