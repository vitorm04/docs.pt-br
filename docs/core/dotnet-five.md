---
title: Novidades do .NET 5
description: Saiba mais sobre o .NET 5, uma plataforma de desenvolvimento de plataforma cruzada e de software livre que é a próxima evolução do .NET Core.
ms.date: 11/06/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 43d7a2baa75f3d71de8bbbf1d0bff7d1beb3d7cd
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440530"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="e46ba-103">Novidades do .NET 5</span><span class="sxs-lookup"><span data-stu-id="e46ba-103">What's new in .NET 5</span></span>

<span data-ttu-id="e46ba-104">O .NET 5,0 é a próxima versão principal do .NET Core a seguir 3,1.</span><span class="sxs-lookup"><span data-stu-id="e46ba-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="e46ba-105">Nomeamos essa nova versão do .NET 5,0 em vez do .NET Core 4,0 por dois motivos:</span><span class="sxs-lookup"><span data-stu-id="e46ba-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="e46ba-106">Ignoramos os números de versão 4. x para evitar confusão com .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="e46ba-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="e46ba-107">Descartamos "Core" do nome para enfatizar que esta é a principal implementação do .NET em diante.</span><span class="sxs-lookup"><span data-stu-id="e46ba-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="e46ba-108">O .NET 5,0 dá suporte a mais tipos de aplicativos e mais plataformas do que o .NET Core ou o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e46ba-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="e46ba-109">ASP.NET Core 5,0 é baseado no .NET 5,0, mas mantém o nome "Core" para evitar confusão com o ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="e46ba-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="e46ba-110">Da mesma forma, Entity Framework Core 5,0 mantém o nome "Core" para evitar confusão com Entity Framework 5 e 6.</span><span class="sxs-lookup"><span data-stu-id="e46ba-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="e46ba-111">O .NET 5,0 inclui os seguintes aprimoramentos e novos recursos em comparação com o .NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="e46ba-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="e46ba-112">Atualizações em C#</span><span class="sxs-lookup"><span data-stu-id="e46ba-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="e46ba-113">Atualizações de F #</span><span class="sxs-lookup"><span data-stu-id="e46ba-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="e46ba-114">Atualizações de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e46ba-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="e46ba-115">System.Text.Jssobre novos recursos</span><span class="sxs-lookup"><span data-stu-id="e46ba-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="e46ba-116">Aplicativos de arquivo único</span><span class="sxs-lookup"><span data-stu-id="e46ba-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="e46ba-117">Corte de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e46ba-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="e46ba-118">Intrínsecos do Windows ARM64 e ARM64</span><span class="sxs-lookup"><span data-stu-id="e46ba-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="e46ba-119">Suporte de ferramentas para depuração de despejo</span><span class="sxs-lookup"><span data-stu-id="e46ba-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="e46ba-120">As bibliotecas de tempo de execução são 80% anotadas para [tipos de referência anuláveis](../csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="e46ba-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="e46ba-121">Aprimoramentos de desempenho:</span><span class="sxs-lookup"><span data-stu-id="e46ba-121">Performance improvements:</span></span>
  - [<span data-ttu-id="e46ba-122">Coleta de lixo (GC)</span><span class="sxs-lookup"><span data-stu-id="e46ba-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="e46ba-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e46ba-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="e46ba-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="e46ba-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="e46ba-125">Pooling ValueTask assíncrona</span><span class="sxs-lookup"><span data-stu-id="e46ba-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="e46ba-126">Otimizações de tamanho de contêiner</span><span class="sxs-lookup"><span data-stu-id="e46ba-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="e46ba-127">Muito mais áreas</span><span class="sxs-lookup"><span data-stu-id="e46ba-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="e46ba-128">O .NET 5,0 não substitui .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e46ba-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="e46ba-129">O .NET 5,0 é a principal implementação do .NET no futuro e .NET Framework 4. x ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="e46ba-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="e46ba-130">Não há planos de portar as tecnologias a seguir de .NET Framework para o .NET 5,0, mas há alternativas no .NET 5,0:</span><span class="sxs-lookup"><span data-stu-id="e46ba-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="e46ba-131">Tecnologia</span><span class="sxs-lookup"><span data-stu-id="e46ba-131">Technology</span></span>                             | <span data-ttu-id="e46ba-132">Alternativa recomendada</span><span class="sxs-lookup"><span data-stu-id="e46ba-132">Recommended alternative</span></span>                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e46ba-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="e46ba-133">Web Forms</span></span>                              | <span data-ttu-id="e46ba-134">ASP.NET Core [mais](/aspnet/core/blazor) ou [Razor Pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="e46ba-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="e46ba-135">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="e46ba-135">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="e46ba-136">gRPC</span><span class="sxs-lookup"><span data-stu-id="e46ba-136">gRPC</span></span>](/aspnet/core/grpc)                                                                       |
| <span data-ttu-id="e46ba-137">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="e46ba-137">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="e46ba-138">CoreWF de código-fonte aberto</span><span class="sxs-lookup"><span data-stu-id="e46ba-138">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="e46ba-139">O .NET 5,0 não substitui .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e46ba-139">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="e46ba-140">O novo desenvolvimento de aplicativos pode especificar o `net5.0` moniker do Framework de destino (TFM) para todos os tipos de projeto, incluindo bibliotecas de classes.</span><span class="sxs-lookup"><span data-stu-id="e46ba-140">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="e46ba-141">O compartilhamento de código entre as cargas de trabalho do .NET 5 é simplificado, pois tudo o que você precisa é o `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="e46ba-141">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="e46ba-142">Para aplicativos e bibliotecas do .NET 5,0, o `net5.0` moniker da estrutura de destino (TFM) combina e substitui o `netcoreapp` e o `netstandard` TFMs.</span><span class="sxs-lookup"><span data-stu-id="e46ba-142">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="e46ba-143">No entanto, se você planeja compartilhar o código entre as cargas de trabalho .NET Framework, .NET Core e .NET 5, poderá fazer isso especificando `netstandard2.0` como seu TFM.</span><span class="sxs-lookup"><span data-stu-id="e46ba-143">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="e46ba-144">Para obter mais informações, confira [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="e46ba-144">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="e46ba-145">Atualizações em C#</span><span class="sxs-lookup"><span data-stu-id="e46ba-145">C# updates</span></span>

<span data-ttu-id="e46ba-146">Os desenvolvedores que escrevem aplicativos .NET 5 terão acesso à versão e aos recursos mais recentes do C#.</span><span class="sxs-lookup"><span data-stu-id="e46ba-146">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="e46ba-147">O .NET 5 é emparelhado com o C# 9, que traz muitos recursos novos para a linguagem.</span><span class="sxs-lookup"><span data-stu-id="e46ba-147">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="e46ba-148">Aqui estão alguns destaques:</span><span class="sxs-lookup"><span data-stu-id="e46ba-148">Here are a few highlights:</span></span>

- <span data-ttu-id="e46ba-149">Registros: tipos de referência imutáveis que se comportam como tipos de valor e apresentam a nova `with` palavra-chave à linguagem.</span><span class="sxs-lookup"><span data-stu-id="e46ba-149">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="e46ba-150">Correspondência de padrão relacional: estende os recursos de correspondência de padrões para operadores relacionais para avaliações e expressões comparativa, incluindo padrões lógicos – novas palavras-chave `and` , `or` e `not` .</span><span class="sxs-lookup"><span data-stu-id="e46ba-150">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="e46ba-151">Instruções de nível superior: como um meio para acelerar a adoção e o aprendizado do C#, o `Main` método pode ser omitido e o aplicativo tão simples quanto o seguinte é válido:</span><span class="sxs-lookup"><span data-stu-id="e46ba-151">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="e46ba-152">Ponteiros de função: constructos de linguagem que expõem os seguintes opcodes de linguagem intermediária (IL): `ldftn` e `calli` .</span><span class="sxs-lookup"><span data-stu-id="e46ba-152">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="e46ba-153">Para obter mais informações sobre os recursos disponíveis do C# 9, consulte [o que há de novo no c# 9](../csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="e46ba-153">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="e46ba-154">Geradores de origem</span><span class="sxs-lookup"><span data-stu-id="e46ba-154">Source generators</span></span>

<span data-ttu-id="e46ba-155">Além de alguns dos novos recursos do C# destacados, os geradores de origem estão fazendo seu caminho em projetos de desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="e46ba-155">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="e46ba-156">Os geradores de origem permitem o código que é executado durante a compilação para inspecionar seu programa e produzir arquivos adicionais que são compilados junto com o restante do seu código.</span><span class="sxs-lookup"><span data-stu-id="e46ba-156">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="e46ba-157">Para obter mais informações sobre geradores de origem, consulte [introdução aos geradores de código](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) -fonte c# e [exemplos do gerador de código-fonte c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="e46ba-157">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="e46ba-158">Atualizações de F #</span><span class="sxs-lookup"><span data-stu-id="e46ba-158">F# updates</span></span>

<span data-ttu-id="e46ba-159">O f # é a linguagem de programação funcional do .NET e, com o .NET 5, os desenvolvedores têm acesso ao F # 5.</span><span class="sxs-lookup"><span data-stu-id="e46ba-159">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="e46ba-160">Aqui estão vários recursos novos do F # 5:</span><span class="sxs-lookup"><span data-stu-id="e46ba-160">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="e46ba-161">Cadeias de caracteres interpoladas</span><span class="sxs-lookup"><span data-stu-id="e46ba-161">Interpolated strings</span></span>

<span data-ttu-id="e46ba-162">Semelhante à cadeia de caracteres interpolada em C# e até mesmo JavaScript, F # dá suporte à interpolação de cadeia de caracteres básica.</span><span class="sxs-lookup"><span data-stu-id="e46ba-162">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="e46ba-163">Além da interpolação de cadeia de caracteres básica, há interpolação de tipo.</span><span class="sxs-lookup"><span data-stu-id="e46ba-163">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="e46ba-164">Com a interpolação digitada, um determinado tipo deve corresponder ao especificador de formato.</span><span class="sxs-lookup"><span data-stu-id="e46ba-164">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="e46ba-165">Isso é semelhante à [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) função que formata uma cadeia de caracteres com base em entradas de tipo seguro.</span><span class="sxs-lookup"><span data-stu-id="e46ba-165">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="e46ba-166">Atualizações de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e46ba-166">Visual Basic updates</span></span>

<span data-ttu-id="e46ba-167">Não há novos recursos de linguagem para Visual Basic no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e46ba-167">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="e46ba-168">No entanto, com o .NET 5, Visual Basic suporte é estendido para:</span><span class="sxs-lookup"><span data-stu-id="e46ba-168">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="e46ba-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="e46ba-169">Description</span></span>                            | <span data-ttu-id="e46ba-170">Parâmetro `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="e46ba-170">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="e46ba-171">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="e46ba-171">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="e46ba-172">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="e46ba-172">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="e46ba-173">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="e46ba-173">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="e46ba-174">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="e46ba-174">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="e46ba-175">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="e46ba-175">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="e46ba-176">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="e46ba-176">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="e46ba-177">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e46ba-177">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="e46ba-178">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="e46ba-178">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="e46ba-179">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="e46ba-179">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="e46ba-180">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e46ba-180">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="e46ba-181">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="e46ba-181">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="e46ba-182">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="e46ba-182">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="e46ba-183">Para obter mais informações sobre modelos de projeto da CLI do .NET, consulte [`dotnet new`](tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="e46ba-183">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="e46ba-184">System.Text.Jssobre novos recursos</span><span class="sxs-lookup"><span data-stu-id="e46ba-184">System.Text.Json new features</span></span>

<span data-ttu-id="e46ba-185">Há novos recursos no e para o [System.Text.Jsem](../standard/serialization/system-text-json-overview.md):</span><span class="sxs-lookup"><span data-stu-id="e46ba-185">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="e46ba-186">Preservar referências e manipular referências circulares</span><span class="sxs-lookup"><span data-stu-id="e46ba-186">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="e46ba-187">Métodos de extensão HttpClient e HttpContent</span><span class="sxs-lookup"><span data-stu-id="e46ba-187">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="e46ba-188">Permitir ou gravar números entre aspas</span><span class="sxs-lookup"><span data-stu-id="e46ba-188">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="e46ba-189">Suporte a tipos imutáveis e registros C# 9</span><span class="sxs-lookup"><span data-stu-id="e46ba-189">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="e46ba-190">Suporte a acessadores de propriedade não públicos</span><span class="sxs-lookup"><span data-stu-id="e46ba-190">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="e46ba-191">campos de suporte</span><span class="sxs-lookup"><span data-stu-id="e46ba-191">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="e46ba-192">Ignorar as propriedades condicionalmente</span><span class="sxs-lookup"><span data-stu-id="e46ba-192">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="e46ba-193">Suporte a dicionários de chave não cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e46ba-193">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="e46ba-194">Suporte a acessadores de propriedade não públicos</span><span class="sxs-lookup"><span data-stu-id="e46ba-194">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="e46ba-195">Permitir que conversores personalizados manipulem NULL</span><span class="sxs-lookup"><span data-stu-id="e46ba-195">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="e46ba-196">Copiar JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="e46ba-196">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="e46ba-197">Criar JsonSerializerOptions com padrões da Web</span><span class="sxs-lookup"><span data-stu-id="e46ba-197">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="net-maui"></a><span data-ttu-id="e46ba-198">.NET MAUI</span><span class="sxs-lookup"><span data-stu-id="e46ba-198">.NET MAUI</span></span>

<span data-ttu-id="e46ba-199">O .NET MAUI é uma evolução do mais popular Xamarin. Forms Toolkit e é de software livre no GitHub em [dotnet/Maui](https://github.com/dotnet/maui).</span><span class="sxs-lookup"><span data-stu-id="e46ba-199">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="e46ba-200">Com o .NET MAUI, a escolha para desenvolvedores .NET é simplificada, fornecendo uma única pilha que dá suporte a todas as cargas de trabalho modernas: Android, iOS, macOS e Windows.</span><span class="sxs-lookup"><span data-stu-id="e46ba-200">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="e46ba-201">Com o .NET MAUI, você obtém uma experiência de desenvolvedor de projeto único que tem como alvo várias plataformas e dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e46ba-201">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e46ba-202">O .NET MAUI está na visualização inicial.</span><span class="sxs-lookup"><span data-stu-id="e46ba-202">.NET MAUI is in early preview.</span></span> <span data-ttu-id="e46ba-203">O código-fonte de exemplo pode ser encontrado em [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).</span><span class="sxs-lookup"><span data-stu-id="e46ba-203">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="e46ba-204">Modelo-exibição-padrão de atualização</span><span class="sxs-lookup"><span data-stu-id="e46ba-204">Model-View-Update pattern</span></span>

<span data-ttu-id="e46ba-205">Os desenvolvedores adoram padrões de desenvolvimento modernos.</span><span class="sxs-lookup"><span data-stu-id="e46ba-205">Developers love modern development patterns.</span></span> <span data-ttu-id="e46ba-206">Uma abordagem fluente do desenvolvimento da interface do usuário, inspirado pela "arquitetura Elm", é o padrão [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU.</span><span class="sxs-lookup"><span data-stu-id="e46ba-206">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="e46ba-207">O MVU promove um fluxo unidirecional de gerenciamento de dados e estado, bem como uma experiência de desenvolvimento de primeiro código que atualiza rapidamente a interface do usuário aplicando apenas as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="e46ba-207">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="e46ba-208">Como exemplo, considere o seguinte contador escrito em .NET MAUI usando o padrão MVU:</span><span class="sxs-lookup"><span data-stu-id="e46ba-208">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="e46ba-209">Para obter mais informações, consulte o [roteiro do .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)e apresentando o artigo do [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="e46ba-209">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="e46ba-210">Confira também</span><span class="sxs-lookup"><span data-stu-id="e46ba-210">See also</span></span>

- [<span data-ttu-id="e46ba-211">A jornada para um .NET</span><span class="sxs-lookup"><span data-stu-id="e46ba-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="e46ba-212">Melhorias de desempenho no .NET 5</span><span class="sxs-lookup"><span data-stu-id="e46ba-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
