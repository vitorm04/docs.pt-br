---
title: A evolução do .NET Core para o .NET 5
description: Saiba mais sobre o .NET 5, uma plataforma de desenvolvimento de plataforma cruzada e de software livre que é a próxima evolução do .NET Core.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 9318b1afbe22c97f056bd38732306c6a6b60ad00
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598121"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="e1eed-103">A evolução do .NET Core para o .NET 5</span><span class="sxs-lookup"><span data-stu-id="e1eed-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="e1eed-104">Este artigo fornece detalhes sobre o que está incluído no .NET 5, que é a próxima versão do .NET Core a seguir 3,1.</span><span class="sxs-lookup"><span data-stu-id="e1eed-104">This article details what's included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="e1eed-105">O número de versão é 5,0 para evitar confusão com .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="e1eed-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="e1eed-106">E "Core" é descartado do nome porque é a principal implementação do .NET em frente.</span><span class="sxs-lookup"><span data-stu-id="e1eed-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="e1eed-107">ASP.NET Core retém o nome "Core" para evitar confusão com o ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="e1eed-107">ASP.NET Core retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="e1eed-108">Além disso, Entity Framework Core retém o nome "Core" para evitar confusão com Entity Framework 5 e 6.</span><span class="sxs-lookup"><span data-stu-id="e1eed-108">Additionally, Entity Framework Core retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span> <span data-ttu-id="e1eed-109">O .NET 5 dá suporte a mais tipos de aplicativos e mais plataformas do que o .NET Core ou o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1eed-109">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="e1eed-110">O advento do .NET Core evoluiu o ecossistema do .NET de maneiras atraentes.</span><span class="sxs-lookup"><span data-stu-id="e1eed-110">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="e1eed-111">Ele amadureceu como um projeto de software livre no GitHub, comemorando contribuições da Comunidade e humildemente melhorando com o tempo.</span><span class="sxs-lookup"><span data-stu-id="e1eed-111">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="e1eed-112">O .NET Core tem várias características principais:</span><span class="sxs-lookup"><span data-stu-id="e1eed-112">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e1eed-113">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="e1eed-113">Cross-platform</span></span>
> - <span data-ttu-id="e1eed-114">Software livre</span><span class="sxs-lookup"><span data-stu-id="e1eed-114">Open-source</span></span>
> - <span data-ttu-id="e1eed-115">Instalação lado a lado</span><span class="sxs-lookup"><span data-stu-id="e1eed-115">Side-by-side installation</span></span>
> - <span data-ttu-id="e1eed-116">Arquivos de projeto pequenos (estilo de SDK)</span><span class="sxs-lookup"><span data-stu-id="e1eed-116">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="e1eed-117">Implantação flexível</span><span class="sxs-lookup"><span data-stu-id="e1eed-117">Flexible deployment</span></span>

<span data-ttu-id="e1eed-118">O .NET 5 estende essas características, fazendo melhorias incrementais:</span><span class="sxs-lookup"><span data-stu-id="e1eed-118">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="e1eed-119">Aplicativos de arquivo único</span><span class="sxs-lookup"><span data-stu-id="e1eed-119">Single file apps</span></span>
- <span data-ttu-id="e1eed-120">Intrínsecos do Windows ARM64 e ARM64</span><span class="sxs-lookup"><span data-stu-id="e1eed-120">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="e1eed-121">Aprimoramentos de desempenho de limpeza para:</span><span class="sxs-lookup"><span data-stu-id="e1eed-121">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="e1eed-122">Coleta de lixo (GC)</span><span class="sxs-lookup"><span data-stu-id="e1eed-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="e1eed-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e1eed-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="e1eed-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e1eed-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="e1eed-125">Pooling ValueTask assíncrona</span><span class="sxs-lookup"><span data-stu-id="e1eed-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="e1eed-126">Muito mais áreas</span><span class="sxs-lookup"><span data-stu-id="e1eed-126">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="e1eed-127">Otimizações de tamanho de contêiner</span><span class="sxs-lookup"><span data-stu-id="e1eed-127">Container size optimizations</span></span>
- [<span data-ttu-id="e1eed-128">Corte de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e1eed-128">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="e1eed-129">Aprimoramentos do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e1eed-129">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="e1eed-130">Suporte de ferramentas para depuração de despejo</span><span class="sxs-lookup"><span data-stu-id="e1eed-130">Tooling support for dump debugging</span></span>
- <span data-ttu-id="e1eed-131">A plataforma é 80% anotada para [tipos de referência anuláveis](../csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="e1eed-131">Platform is 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="e1eed-132">O que o .NET 5 não é</span><span class="sxs-lookup"><span data-stu-id="e1eed-132">What .NET 5 is not</span></span>

<span data-ttu-id="e1eed-133">O .NET 5 não é uma substituição para .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1eed-133">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="e1eed-134">Não há planos de portar as seguintes tecnologias de .NET Framework para o .NET 5, mas há alternativas com suporte incluídas no .NET 5:</span><span class="sxs-lookup"><span data-stu-id="e1eed-134">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="e1eed-135">Tecnologia</span><span class="sxs-lookup"><span data-stu-id="e1eed-135">Technology</span></span>                             | <span data-ttu-id="e1eed-136">Recomendação</span><span class="sxs-lookup"><span data-stu-id="e1eed-136">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="e1eed-137">Web Forms</span><span class="sxs-lookup"><span data-stu-id="e1eed-137">Web Forms</span></span>                              | [<span data-ttu-id="e1eed-138">ASP.NET Core mais</span><span class="sxs-lookup"><span data-stu-id="e1eed-138">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="e1eed-139">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="e1eed-139">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="e1eed-140">gRPC</span><span class="sxs-lookup"><span data-stu-id="e1eed-140">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="e1eed-141">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="e1eed-141">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="e1eed-142">CoreWF de código-fonte aberto</span><span class="sxs-lookup"><span data-stu-id="e1eed-142">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="e1eed-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e1eed-143">.NET Standard</span></span>

<span data-ttu-id="e1eed-144">O novo desenvolvimento de aplicativos pode especificar o `net5.0` moniker do Framework de destino (TFM) para todos os tipos de projeto, incluindo bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="e1eed-144">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="e1eed-145">O compartilhamento de código entre as cargas de trabalho do .NET 5 é simplificado, pois tudo o que você precisa é o `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="e1eed-145">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="e1eed-146">O `net5.0` TFM combina e substitui os `netcoreapp` `netstandard` nomes e.</span><span class="sxs-lookup"><span data-stu-id="e1eed-146">The `net5.0` TFM combines and replaces the `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="e1eed-147">Esse TFM geralmente incluirá apenas tecnologias que funcionam entre plataformas, como foi feito com .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e1eed-147">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="e1eed-148">No entanto, se você planeja compartilhar o código entre as cargas de trabalho .NET Framework, .NET Core e .NET 5, poderá fazer isso especificando `netstandard2.0` como seu TFM.</span><span class="sxs-lookup"><span data-stu-id="e1eed-148">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="e1eed-149">Para obter mais informações, consulte [como especificar estruturas de destino](../standard/frameworks.md#how-to-specify-a-target-framework).</span><span class="sxs-lookup"><span data-stu-id="e1eed-149">For more information, see [How to specify target frameworks](../standard/frameworks.md#how-to-specify-a-target-framework).</span></span>

## <a name="language-updates"></a><span data-ttu-id="e1eed-150">Atualizações de linguagem</span><span class="sxs-lookup"><span data-stu-id="e1eed-150">Language updates</span></span>

<span data-ttu-id="e1eed-151">Com o .NET 5, as linguagens de programação do .NET continuam a melhorar.</span><span class="sxs-lookup"><span data-stu-id="e1eed-151">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="e1eed-152">Atualizações em C#</span><span class="sxs-lookup"><span data-stu-id="e1eed-152">C# updates</span></span>

<span data-ttu-id="e1eed-153">Os desenvolvedores que escrevem aplicativos .NET 5 terão acesso à versão e aos recursos mais recentes do C#.</span><span class="sxs-lookup"><span data-stu-id="e1eed-153">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="e1eed-154">O .NET 5 é emparelhado com o C# 9, que traz muitos recursos novos para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="e1eed-154">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="e1eed-155">Aqui estão alguns destaques:</span><span class="sxs-lookup"><span data-stu-id="e1eed-155">Here are a few highlights:</span></span>

- <span data-ttu-id="e1eed-156">Registros: tipos de referência imutáveis que se comportam como tipos de valor e apresentam a nova `with` palavra-chave à linguagem.</span><span class="sxs-lookup"><span data-stu-id="e1eed-156">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="e1eed-157">Correspondência de padrão relacional: estende os recursos de correspondência de padrões para operadores relacionais para avaliações e expressões comparativa, incluindo padrões lógicos – novas palavras-chave `and` , `or` e `not` .</span><span class="sxs-lookup"><span data-stu-id="e1eed-157">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="e1eed-158">Instruções de nível superior: como um meio para acelerar a adoção e o aprendizado do C#, o `Main` método pode ser omitido e o aplicativo tão simples quanto o seguinte é válido:</span><span class="sxs-lookup"><span data-stu-id="e1eed-158">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="e1eed-159">Ponteiros de função: constructos de linguagem que expõem os seguintes opcodes de linguagem intermediária (IL): `ldftn` e `calli` .</span><span class="sxs-lookup"><span data-stu-id="e1eed-159">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="e1eed-160">Para obter mais informações sobre os recursos disponíveis do C# 9, consulte [o que há de novo no c# 9](../csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="e1eed-160">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="e1eed-161">Geradores de origem</span><span class="sxs-lookup"><span data-stu-id="e1eed-161">Source generators</span></span>

<span data-ttu-id="e1eed-162">Além de alguns dos novos recursos do C# destacados, os geradores de origem estão fazendo seu caminho em projetos de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e1eed-162">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="e1eed-163">Os geradores de origem permitem o código que é executado durante a compilação para inspecionar seu programa e produzir arquivos adicionais que são compilados junto com o restante do seu código.</span><span class="sxs-lookup"><span data-stu-id="e1eed-163">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="e1eed-164">Para obter mais informações sobre geradores de origem, consulte [introdução aos geradores de código](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) -fonte c# e [exemplos do gerador de código-fonte c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="e1eed-164">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="e1eed-165">Atualizações de F #</span><span class="sxs-lookup"><span data-stu-id="e1eed-165">F# updates</span></span>

<span data-ttu-id="e1eed-166">O f # é a linguagem de programação funcional do .NET e, com o .NET 5, os desenvolvedores têm acesso ao F # 5.</span><span class="sxs-lookup"><span data-stu-id="e1eed-166">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="e1eed-167">Aqui estão vários recursos novos do F # 5:</span><span class="sxs-lookup"><span data-stu-id="e1eed-167">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="e1eed-168">Cadeias de caracteres interpoladas</span><span class="sxs-lookup"><span data-stu-id="e1eed-168">Interpolated strings</span></span>

<span data-ttu-id="e1eed-169">Semelhante à cadeia de caracteres interpolada em C# e até mesmo JavaScript, F # dá suporte à interpolação de cadeia de caracteres básica.</span><span class="sxs-lookup"><span data-stu-id="e1eed-169">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="e1eed-170">Além da interpolação de cadeia de caracteres básica, há interpolação de tipo.</span><span class="sxs-lookup"><span data-stu-id="e1eed-170">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="e1eed-171">Com a interpolação digitada, um determinado tipo deve corresponder ao especificador de formato.</span><span class="sxs-lookup"><span data-stu-id="e1eed-171">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="e1eed-172">Isso é semelhante à [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) função que formata uma cadeia de caracteres com base em entradas de tipo seguro.</span><span class="sxs-lookup"><span data-stu-id="e1eed-172">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a><span data-ttu-id="e1eed-173">Atualizações de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1eed-173">Visual Basic updates</span></span>

<span data-ttu-id="e1eed-174">Não há novos recursos de linguagem para Visual Basic no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e1eed-174">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="e1eed-175">No entanto, com o .NET 5, Visual Basic suporte é estendido para:</span><span class="sxs-lookup"><span data-stu-id="e1eed-175">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="e1eed-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1eed-176">Description</span></span>                            | <span data-ttu-id="e1eed-177">Parâmetro `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="e1eed-177">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="e1eed-178">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="e1eed-178">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="e1eed-179">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="e1eed-179">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="e1eed-180">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="e1eed-180">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="e1eed-181">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="e1eed-181">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="e1eed-182">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="e1eed-182">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="e1eed-183">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="e1eed-183">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="e1eed-184">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e1eed-184">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="e1eed-185">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e1eed-185">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="e1eed-186">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="e1eed-186">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="e1eed-187">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e1eed-187">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="e1eed-188">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e1eed-188">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="e1eed-189">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="e1eed-189">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="e1eed-190">Para obter mais informações sobre modelos de projeto da CLI do .NET, consulte [`dotnet new`](tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="e1eed-190">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="e1eed-191">.NET MAUI</span><span class="sxs-lookup"><span data-stu-id="e1eed-191">.NET MAUI</span></span>

<span data-ttu-id="e1eed-192">O .NET MAUI é uma evolução do mais popular Xamarin. Forms Toolkit e é de software livre no GitHub em [dotnet/Maui](https://github.com/dotnet/maui).</span><span class="sxs-lookup"><span data-stu-id="e1eed-192">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="e1eed-193">Com o .NET MAUI, a escolha para desenvolvedores .NET é simplificada, fornecendo uma única pilha que dá suporte a todas as cargas de trabalho modernas: Android, iOS, macOS e Windows.</span><span class="sxs-lookup"><span data-stu-id="e1eed-193">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="e1eed-194">Com o .NET MAUI, você obtém uma experiência de desenvolvedor de projeto único que tem como alvo várias plataformas e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e1eed-194">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1eed-195">O .NET MAUI está na visualização inicial.</span><span class="sxs-lookup"><span data-stu-id="e1eed-195">.NET MAUI is in early preview.</span></span> <span data-ttu-id="e1eed-196">O código-fonte de exemplo pode ser encontrado em [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).</span><span class="sxs-lookup"><span data-stu-id="e1eed-196">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="e1eed-197">Modelo-exibição-padrão de atualização</span><span class="sxs-lookup"><span data-stu-id="e1eed-197">Model-View-Update pattern</span></span>

<span data-ttu-id="e1eed-198">Os desenvolvedores adoram padrões de desenvolvimento modernos.</span><span class="sxs-lookup"><span data-stu-id="e1eed-198">Developers love modern development patterns.</span></span> <span data-ttu-id="e1eed-199">Uma abordagem fluente do desenvolvimento da interface do usuário, inspirado pela "arquitetura Elm", é o padrão [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU.</span><span class="sxs-lookup"><span data-stu-id="e1eed-199">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="e1eed-200">O MVU promove um fluxo unidirecional de gerenciamento de dados e estado, bem como uma experiência de desenvolvimento de primeiro código que atualiza rapidamente a interface do usuário aplicando apenas as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="e1eed-200">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="e1eed-201">Como exemplo, considere o seguinte contador escrito em .NET MAUI usando o padrão MVU:</span><span class="sxs-lookup"><span data-stu-id="e1eed-201">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

<span data-ttu-id="e1eed-202">Para obter mais informações, consulte o [roteiro do .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)e apresentando o artigo do [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="e1eed-202">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1eed-203">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1eed-203">See also</span></span>

- [<span data-ttu-id="e1eed-204">A jornada para um .NET</span><span class="sxs-lookup"><span data-stu-id="e1eed-204">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="e1eed-205">Melhorias de desempenho no .NET 5</span><span class="sxs-lookup"><span data-stu-id="e1eed-205">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
