---
title: Novidades do .NET Core 3.0
description: Conheça os novos recursos encontrados no .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/31/2018
ms.openlocfilehash: 086be4649f4e7e27ff98df6f26d08856683865c8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611777"
---
# <a name="whats-new-in-net-core-30-preview-2"></a><span data-ttu-id="2a29a-103">Novidades do .NET Core 3.0 (Versão Prévia 2)</span><span class="sxs-lookup"><span data-stu-id="2a29a-103">What's new in .NET Core 3.0 (Preview 2)</span></span>

<span data-ttu-id="2a29a-104">Este artigo descreve as novidades do .NET Core 3.0 (Versão Prévia 2).</span><span class="sxs-lookup"><span data-stu-id="2a29a-104">This article describes what is new in .NET Core 3.0 (preview 2).</span></span> <span data-ttu-id="2a29a-105">Um dos maiores avanços é o suporte para aplicativos Windows de área de trabalho (somente Windows).</span><span class="sxs-lookup"><span data-stu-id="2a29a-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="2a29a-106">Utilizando um componente do SDK do .NET Core 3.0 chamado Windows Desktop, você pode portar seus aplicativos do Windows Forms e WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="2a29a-106">By utilizing a .NET Core 3.0 SDK component called Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="2a29a-107">Para deixar claro, o componente Windows Desktop só é compatível com o Windows e só é incluído nele.</span><span class="sxs-lookup"><span data-stu-id="2a29a-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="2a29a-108">Para saber mais, confira a seção [Desktop Windows](#windows-desktop) abaixo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="2a29a-109">O .NET Core 3.0 adiciona suporte para C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="2a29a-110">[Baixe e comece a trabalhar com o .NET Core 3.0 Versão Prévia 2](https://aka.ms/netcore3download) agora no Windows, no Mac e no Linux.</span><span class="sxs-lookup"><span data-stu-id="2a29a-110">[Download and get started with .NET Core 3.0 Preview 2](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="2a29a-111">Veja detalhes completos sobre a versão nas [notas sobre a versão do .NET Core 3.0 Versão Prévia 2](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="2a29a-111">You can see complete details of the release in the [.NET Core 3.0 Preview 2 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="2a29a-112">Para obter mais informações sobre o que foi lançado com cada versão, confira os seguintes avisos:</span><span class="sxs-lookup"><span data-stu-id="2a29a-112">For more information about what was released with each version, see the following announcements:</span></span>

- [<span data-ttu-id="2a29a-113">Comunicado do .NET Core 3.0 Versão Prévia 1</span><span class="sxs-lookup"><span data-stu-id="2a29a-113">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)
- [<span data-ttu-id="2a29a-114">Comunicado do .NET Core 3.0 Versão Prévia 2</span><span class="sxs-lookup"><span data-stu-id="2a29a-114">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)

## <a name="c-8"></a><span data-ttu-id="2a29a-115">C# 8</span><span class="sxs-lookup"><span data-stu-id="2a29a-115">C# 8</span></span>

<span data-ttu-id="2a29a-116">O .NET Core 3.0 dá suporte ao C# 8 e, no .NET Core 3.0 Versão Prévia 2 em diante, ele dá suporte a essas novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="2a29a-116">.NET Core 3.0 supports C# 8, and as of .NET Core 3.0 Preview 2, supports these new features.</span></span> <span data-ttu-id="2a29a-117">Para obter mais informações sobre as funcionalidades do C# 8.0, confira as seguintes postagens no blog:</span><span class="sxs-lookup"><span data-stu-id="2a29a-117">For more information about C# 8.0 features, see the following blog posts:</span></span>

- <span data-ttu-id="2a29a-118">[Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/) (Faça mais com padrões no C# 8.0)</span><span class="sxs-lookup"><span data-stu-id="2a29a-118">[Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/)</span></span>
- <span data-ttu-id="2a29a-119">[Take C# 8.0 for a spin](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/) (Leve o C# 8.0 para dar uma volta)</span><span class="sxs-lookup"><span data-stu-id="2a29a-119">[Take C# 8.0 for a spin](https://devblogs.microsoft.com/dotnet/take-c-8-0-for-a-spin/)</span></span>
- <span data-ttu-id="2a29a-120">[Building C# 8.0](https://devblogs.microsoft.com/dotnet/building-c-8-0/) (Compilando o C# 8.0)</span><span class="sxs-lookup"><span data-stu-id="2a29a-120">[Building C# 8.0](https://devblogs.microsoft.com/dotnet/building-c-8-0/)</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="2a29a-121">Intervalos e índices</span><span class="sxs-lookup"><span data-stu-id="2a29a-121">Ranges and indices</span></span>

<span data-ttu-id="2a29a-122">O novo tipo `Index` pode ser usado para indexação.</span><span class="sxs-lookup"><span data-stu-id="2a29a-122">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="2a29a-123">É possível criar um a partir de um `int` que conta desde o início, ou com um operador `^` de prefixo (C#) que conta do final:</span><span class="sxs-lookup"><span data-stu-id="2a29a-123">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="2a29a-124">Há também um tipo `Range`, que consiste em dois valores `Index`, um para o início e outro para o final, e pode ser escrito com uma expressão de intervalo `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="2a29a-124">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="2a29a-125">Você pode indexar com `Range` para produzir uma fatia:</span><span class="sxs-lookup"><span data-stu-id="2a29a-125">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

### <a name="async-streams"></a><span data-ttu-id="2a29a-126">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="2a29a-126">Async streams</span></span>

<span data-ttu-id="2a29a-127">O tipo `IAsyncEnumerable<T>` é uma nova versão assíncrona de `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-127">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="2a29a-128">A linguagem permite o uso de `await foreach` em `IAsyncEnumerable<T>` para consumir seus elementos e o uso de `yield return` neles para produzir elementos.</span><span class="sxs-lookup"><span data-stu-id="2a29a-128">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="2a29a-129">O exemplo a seguir demonstra a produção e o consumo de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="2a29a-129">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="2a29a-130">A instrução `foreach` é assíncrona e usa `yield return` para produzir um fluxo assíncrono para chamadores.</span><span class="sxs-lookup"><span data-stu-id="2a29a-130">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="2a29a-131">Esse padrão (usar `yield return`) é o modelo recomendado para a produção de fluxos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="2a29a-131">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="2a29a-132">Além de poder `await foreach`, você também pode criar iteradores assíncronos, por exemplo, um iterador que retorne um `IAsyncEnumerable/IAsyncEnumerator` em que é possível aplicar `await` e `yield`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-132">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="2a29a-133">Para objetos que precisam ser descartados, você pode usar `IAsyncDisposable`, que vários tipos BCL implementam, como `Stream` e `Timer`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-133">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="2a29a-134">Você precisará que o .NET Core 3.0 Versão Prévia 2 use fluxos assíncronos caso deseje fazer o desenvolvimento com o Visual Studio 2019 ou a última versão prévia da [extensão do C# para Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span><span class="sxs-lookup"><span data-stu-id="2a29a-134">You need .NET Core 3.0 Preview 2 to use async streams if you want to develop with either Visual Studio 2019 or the latest preview of the [C# extension for Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/releases/tag/v1.18.0-beta5).</span></span> <span data-ttu-id="2a29a-135">Se você estiver usando o .NET Core 3.0 Versão Prévia 2 na linha de comando, tudo funcionará conforme esperado.</span><span class="sxs-lookup"><span data-stu-id="2a29a-135">If you are using .NET Core 3.0 Preview 2 at the command line, then everything will work as expected.</span></span>

### <a name="using-declarations"></a><span data-ttu-id="2a29a-136">Declarações using</span><span class="sxs-lookup"><span data-stu-id="2a29a-136">Using Declarations</span></span>

<span data-ttu-id="2a29a-137">As *declarações using* são uma nova maneira de garantir que o objeto seja descartado corretamente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-137">*Using declarations* are a new way to ensure your object is properly disposed.</span></span> <span data-ttu-id="2a29a-138">Uma *declaração using* mantém o objeto ativo enquanto ele ainda está no escopo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-138">A *using declaration* keeps the object alive while it is still in scope.</span></span> <span data-ttu-id="2a29a-139">Depois que o objeto fica fora do escopo, ele é automaticamente descartado.</span><span class="sxs-lookup"><span data-stu-id="2a29a-139">Once the object becomes out of scope, it is automatically disposed.</span></span> <span data-ttu-id="2a29a-140">Isso reduzirá as *instruções using* aninhadas e tornará o código mais limpo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-140">This will reduce nested *using statements* and make your code cleaner.</span></span>

```csharp
static void Main(string[] args)
{
    using var options = Parse(args);
    if (options["verbose"]) { WriteLine("Logging..."); }

} // options disposed here
```

### <a name="switch-expressions"></a><span data-ttu-id="2a29a-141">Expressões switch</span><span class="sxs-lookup"><span data-stu-id="2a29a-141">Switch Expressions</span></span>

<span data-ttu-id="2a29a-142">As *expressões switch* são uma forma mais limpa de criar uma *instrução switch* mas, como são uma expressão, elas retornam um valor.</span><span class="sxs-lookup"><span data-stu-id="2a29a-142">*Switch expressions* are a cleaner way of doing a *switch statement* but, since it's an expression, returns a value.</span></span> <span data-ttu-id="2a29a-143">As *expressões switch* também são totalmente integradas à correspondência de padrões e usam o padrão de descarte, `_`, para representar o valor `default`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-143">*Switch expressions* are also fully integrated with pattern matching, and use the discard pattern, `_`, to represent the `default` value.</span></span>

<span data-ttu-id="2a29a-144">Veja a sintaxe para as *expressões switch* no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="2a29a-144">You can see the syntax for *switch expressions* in the following example:</span></span>

```csharp
static string Display(object o) => o switch
{
    Point { X: 0, Y: 0 }         => "origin",
    Point { X: var x, Y: var y } => $"({x}, {y})",
    _                            => "unknown"
};
```

<span data-ttu-id="2a29a-145">Há dois padrões envolvidos nesse exemplo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-145">There are two patterns at play in this example.</span></span> <span data-ttu-id="2a29a-146">`o` corresponde primeiro ao *padrão de tipo* `Point` e, em seguida, ao *padrão de propriedade* dentro das *{chaves}*.</span><span class="sxs-lookup"><span data-stu-id="2a29a-146">`o` first matches with the `Point` *type pattern* and then with the *property pattern* inside the *{curly braces}*.</span></span> <span data-ttu-id="2a29a-147">O `_` descreve o `discard pattern`, que é igual a `default` em *instruções switch*.</span><span class="sxs-lookup"><span data-stu-id="2a29a-147">The `_` describes the `discard pattern`, which is the same as `default` for *switch statements*.</span></span>

<span data-ttu-id="2a29a-148">Os padrões permitem que você escreva um código declarativo que captura sua intenção, em vez de um código de procedimento que implementa testes para ela.</span><span class="sxs-lookup"><span data-stu-id="2a29a-148">Patterns enable you to write declarative code that captures your intent instead of procedural code that implements tests for it.</span></span> <span data-ttu-id="2a29a-149">O compilador fica responsável por implementar esse código de procedimento entediante e oferece a garantia de sempre fazer isso corretamente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-149">The compiler becomes responsible for implementing that boring procedural code and is guaranteed to always do it correctly.</span></span>

<span data-ttu-id="2a29a-150">Ainda haverá casos em que as *instruções switch* serão uma escolha melhor que as *expressões switch* e os padrões poderão ser usados com ambos os estilos de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2a29a-150">There will still be cases where *switch statements* will be a better choice than *switch expressions* and patterns can be used with both syntax styles.</span></span>

<span data-ttu-id="2a29a-151">Para obter mais informações, confira [Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/) (Faça mais com padrões no C# 8.0).</span><span class="sxs-lookup"><span data-stu-id="2a29a-151">For more information, see [Do more with patterns in C# 8.0](https://devblogs.microsoft.com/dotnet/do-more-with-patterns-in-c-8-0/).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="2a29a-152">Melhorias de ponto flutuante IEEE</span><span class="sxs-lookup"><span data-stu-id="2a29a-152">IEEE Floating-point improvements</span></span>

<span data-ttu-id="2a29a-153">As APIs de ponto flutuante estão no processo de serem atualizadas para conformidade com a [revisão do IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="2a29a-153">Floating point APIs are in the process of being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="2a29a-154">O objetivo dessas alterações é expor todas as operações "obrigatórias" e garantir que seu comportamento esteja em conformidade com a especificação IEEE.</span><span class="sxs-lookup"><span data-stu-id="2a29a-154">The goal of these changes is to expose all "required" operations and ensure that they are behaviorally compliant with the IEEE spec.</span></span>

<span data-ttu-id="2a29a-155">Correções de análise e formatação:</span><span class="sxs-lookup"><span data-stu-id="2a29a-155">Parsing and formatting fixes:</span></span>

* <span data-ttu-id="2a29a-156">Analisar e arredondar corretamente entradas de qualquer tamanho.</span><span class="sxs-lookup"><span data-stu-id="2a29a-156">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="2a29a-157">Analisar e formatar corretamente o zero negativo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-157">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="2a29a-158">Analisar corretamente o Infinito e o NaN executando uma verificação que não diferencia maiúsculas de minúsculas e permitindo um `+` anterior opcional quando aplicável.</span><span class="sxs-lookup"><span data-stu-id="2a29a-158">Correctly parse Infinity and NaN by performing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="2a29a-159">As novas APIs de Matemática têm:</span><span class="sxs-lookup"><span data-stu-id="2a29a-159">New Math APIs have:</span></span>

* `BitIncrement/BitDecrement`\
<span data-ttu-id="2a29a-160">Correspondem às operações `nextUp` e `nextDown` do IEEE.</span><span class="sxs-lookup"><span data-stu-id="2a29a-160">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="2a29a-161">Retornam o menor número de ponto flutuante que compara o valor maior ou menor que a entrada (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="2a29a-161">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="2a29a-162">Por exemplo, `Math.BitIncrement(0.0)` retorna `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-162">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* `MaxMagnitude/MinMagnitude`\
<span data-ttu-id="2a29a-163">Correspondem às operações `maxNumMag` e `minNumMag` do IEEE; retornam o valor maior ou menor em magnitude das duas entradas (respectivamente).</span><span class="sxs-lookup"><span data-stu-id="2a29a-163">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="2a29a-164">Por exemplo, `Math.MaxMagnitude(2.0, -3.0)` retorna `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-164">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* `ILogB`\
<span data-ttu-id="2a29a-165">Corresponde à operação `logB` do IEEE que retorna um valor integral; retorna o log de base 2 integral do parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="2a29a-165">Corresponds to the `logB` IEEE operation which returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="2a29a-166">Isso é praticamente o mesmo que `floor(log2(x))`, mas feito com erro de arredondamento mínimo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-166">This is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* `ScaleB`\
<span data-ttu-id="2a29a-167">Corresponde à operação `scaleB` do IEEE que usa um valor integral; retorna efetivamente `x * pow(2, n)`, mas é feito com erro de arredondamento mínimo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-167">Corresponds to the `scaleB` IEEE operation which takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* `Log2`\
<span data-ttu-id="2a29a-168">Corresponde à operação `log2` do IEEE; retorna o logaritmo de base 2.</span><span class="sxs-lookup"><span data-stu-id="2a29a-168">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="2a29a-169">Minimiza o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="2a29a-169">It minimizes rounding error.</span></span>

* `FusedMultiplyAdd`\
<span data-ttu-id="2a29a-170">Corresponde à operação `fma` do IEEE; executa uma adição e multiplicação fundida.</span><span class="sxs-lookup"><span data-stu-id="2a29a-170">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="2a29a-171">Em outras palavras, realiza `(x * y) + z` como uma única operação, minimizando o erro de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="2a29a-171">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="2a29a-172">Um exemplo é `FusedMultiplyAdd(1e308, 2.0, -1e308)`, que retorna `1e308`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-172">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="2a29a-173">O `(1e308 * 2.0) - 1e308` regular retorna `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-173">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* `CopySign`\
<span data-ttu-id="2a29a-174">Corresponde à operação `copySign` do IEEE; retorna o valor de `x`, mas com o sinal de `y`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-174">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="2a29a-175">Intrínsecos dependentes da plataforma .NET</span><span class="sxs-lookup"><span data-stu-id="2a29a-175">.NET Platform Dependent Intrinsics</span></span>

<span data-ttu-id="2a29a-176">Foram adicionadas APIs que permitem acesso a determinadas instruções da CPU orientadas a desempenho, como o **SIMD** ou conjuntos de **instruções de manipulação de bits**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-176">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="2a29a-177">Essas instruções podem ajudar a obter melhorias significativas de desempenho em determinados cenários, como processamento de dados com eficiência em paralelo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-177">These instructions can help achieve big performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> <span data-ttu-id="2a29a-178">Além de expor as APIs para uso dos programas, as bibliotecas .NET começaram a usar essas instruções para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2a29a-178">In addition to exposing the APIs for your programs to use, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="2a29a-179">Os seguintes PRs do CoreCLR demonstram alguns intrínsecos, por meio de implementação ou uso:</span><span class="sxs-lookup"><span data-stu-id="2a29a-179">The following CoreCLR PRs demonstrate a few of the intrinsics, either via implementation or use:</span></span>

* [<span data-ttu-id="2a29a-180">Implementar intrínsecos de hardware SSE2 simples</span><span class="sxs-lookup"><span data-stu-id="2a29a-180">Implement simple SSE2 hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15585)
* [<span data-ttu-id="2a29a-181">Implementar intrínsecos de hardware SSE</span><span class="sxs-lookup"><span data-stu-id="2a29a-181">Implement the SSE hardware intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/15538)
* [<span data-ttu-id="2a29a-182">Intrínsecos de HW base Arm64</span><span class="sxs-lookup"><span data-stu-id="2a29a-182">Arm64 Base HW Intrinsics</span></span>](https://github.com/dotnet/coreclr/pull/16822)
* [<span data-ttu-id="2a29a-183">Usar TZCNT e LZCNT para Locate{First|Last}Found{Byte|Char}</span><span class="sxs-lookup"><span data-stu-id="2a29a-183">Use TZCNT and LZCNT for Locate{First|Last}Found{Byte|Char}</span></span>](https://github.com/dotnet/coreclr/pull/21073)

<span data-ttu-id="2a29a-184">Para obter mais informações, confira [Intrínsecos dependentes da plataforma .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), que define uma abordagem para definição dessa infraestrutura de hardware, permitindo que a Microsoft, fornecedores de chips ou qualquer outra empresa ou indivíduo defina APIs de chip/hardware que devem ser expostas ao código .NET.</span><span class="sxs-lookup"><span data-stu-id="2a29a-184">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md), which defines an approach for defining this hardware infrastructure, allowing Microsoft, chip vendors, or any other company or individual to define hardware/chip APIs that should be exposed to .NET code.</span></span>

## <a name="default-executables"></a><span data-ttu-id="2a29a-185">Executáveis por padrão</span><span class="sxs-lookup"><span data-stu-id="2a29a-185">Default executables</span></span>

<span data-ttu-id="2a29a-186">Agora, o .NET Core criará [executáveis dependentes da estrutura](../deploying/index.md#framework-dependent-executables-fde), por padrão.</span><span class="sxs-lookup"><span data-stu-id="2a29a-186">.NET Core will now build [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="2a29a-187">Isso é novidade para aplicativos que usam uma versão do .NET Core instalada globalmente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-187">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="2a29a-188">Até agora, apenas [implantações autossuficientes](../deploying/index.md#self-contained-deployments-scd) produziam um executável.</span><span class="sxs-lookup"><span data-stu-id="2a29a-188">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="2a29a-189">Durante `dotnet build` ou `dotnet publish`, um arquivo executável é criado, desde que corresponda ao ambiente e à plataforma do SDK que você está usando.</span><span class="sxs-lookup"><span data-stu-id="2a29a-189">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="2a29a-190">Você pode esperar desses executáveis o mesmo que de outros executáveis nativos, como:</span><span class="sxs-lookup"><span data-stu-id="2a29a-190">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="2a29a-191">Você pode clicar duas vezes no arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="2a29a-191">You can double-click on the executable.</span></span>
* <span data-ttu-id="2a29a-192">Você pode iniciar o aplicativo diretamente de um prompt de comando, como `myapp.exe` no Windows e `./myapp` no Linux e macOS.</span><span class="sxs-lookup"><span data-stu-id="2a29a-192">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="2a29a-193">O build copia dependências</span><span class="sxs-lookup"><span data-stu-id="2a29a-193">Build copies dependencies</span></span>

<span data-ttu-id="2a29a-194">`dotnet build` agora copia as dependências do NuGet para seu aplicativo do cache do NuGet para a pasta de saída do build.</span><span class="sxs-lookup"><span data-stu-id="2a29a-194">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="2a29a-195">Anteriormente, as dependências eram copiadas apenas como parte de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-195">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="2a29a-196">Há algumas operações, como vinculação e publicação de página do razor, que ainda exigem publicação.</span><span class="sxs-lookup"><span data-stu-id="2a29a-196">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-dotnet-tools"></a><span data-ttu-id="2a29a-197">Ferramentas dotnet locais</span><span class="sxs-lookup"><span data-stu-id="2a29a-197">Local dotnet tools</span></span>

> [!WARNING]
> <span data-ttu-id="2a29a-198">Houve uma alteração nas Ferramentas Locais do .NET Core entre o .NET Core 3.0 Versão Prévia 1 e o .NET Core 3.0 Versão Prévia 2.</span><span class="sxs-lookup"><span data-stu-id="2a29a-198">There was a change in .NET Core Local Tools between .NET Core 3.0 Preview 1 and .NET Core 3.0 Preview 2.</span></span>  <span data-ttu-id="2a29a-199">Se você tentou usar as ferramentas locais na Versão Prévia 1 executando um comando semelhante a `dotnet tool restore` ou `dotnet tool install`, você precisa excluir a pasta de cache das ferramentas locais antes que as ferramentas locais funcionem corretamente na Versão Prévia 2.</span><span class="sxs-lookup"><span data-stu-id="2a29a-199">If you tried out local tools in Preview 1 by running a command like `dotnet tool restore` or `dotnet tool install`, you need to delete your local tools cache folder before local tools will work correctly in Preview 2.</span></span> <span data-ttu-id="2a29a-200">Essa pasta está localizada em:</span><span class="sxs-lookup"><span data-stu-id="2a29a-200">This folder is located at:</span></span>
>
> <span data-ttu-id="2a29a-201">No Mac/Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="2a29a-201">On mac, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="2a29a-202">No Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="2a29a-202">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>
>
> <span data-ttu-id="2a29a-203">Se você não excluir essa pasta, receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="2a29a-203">If you do not delete this folder, you will receive an error.</span></span>

<span data-ttu-id="2a29a-204">Enquanto o .NET Core 2.1 oferecia suporte para ferramentas globais, o .NET Core 3.0 agora tem ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="2a29a-204">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="2a29a-205">As ferramentas locais são semelhantes às ferramentas globais, mas estão associadas a um local específico no disco.</span><span class="sxs-lookup"><span data-stu-id="2a29a-205">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="2a29a-206">Isso permite ferramentas por projeto e por repositório.</span><span class="sxs-lookup"><span data-stu-id="2a29a-206">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="2a29a-207">Qualquer ferramenta instalada localmente não está disponível globalmente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-207">Any tool installed locally isn't available globally.</span></span> <span data-ttu-id="2a29a-208">As ferramentas são distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="2a29a-208">Tools are distributed as NuGet packages.</span></span>

<span data-ttu-id="2a29a-209">As ferramentas locais dependem de um nome de arquivo de manifesto `dotnet-tools.json` no seu diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2a29a-209">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="2a29a-210">Esse arquivo de manifesto define as ferramentas que estarão disponíveis nessa pasta e abaixo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-210">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="2a29a-211">Ao criar esse arquivo de manifesto na raiz do seu repositório, garanta que qualquer pessoa que clone seu código possa restaurar e usar as ferramentas necessárias para trabalhar com êxito com seu código.</span><span class="sxs-lookup"><span data-stu-id="2a29a-211">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="2a29a-212">Para criar um arquivo de manifesto `dotnet-tools.json`, use:</span><span class="sxs-lookup"><span data-stu-id="2a29a-212">To create a `dotnet-tools.json` manifest file, use:</span></span>

```console
dotnet new tool-manifest
```

<span data-ttu-id="2a29a-213">Adicione uma nova ferramenta ao manifesto local com:</span><span class="sxs-lookup"><span data-stu-id="2a29a-213">Add a new tool to the local manifest with:</span></span>

```console
dotnet tool install <packageId>
```

<span data-ttu-id="2a29a-214">Liste também as ferramentas no manifesto local com:</span><span class="sxs-lookup"><span data-stu-id="2a29a-214">You can also list the tools in the local manifest with:</span></span>

```console
dotnet tool list
```

<span data-ttu-id="2a29a-215">Para ver quais ferramentas são instaladas globalmente, use:</span><span class="sxs-lookup"><span data-stu-id="2a29a-215">To see what tools are installed globally, use:</span></span>

```console
dotnet tool list -g
```

<span data-ttu-id="2a29a-216">Quando o arquivo de manifesto das ferramentas locais estiver disponível, mas as ferramentas definidas no manifesto não tiverem sido instaladas, use o seguinte comando para baixar e instalar essas ferramentas automaticamente:</span><span class="sxs-lookup"><span data-stu-id="2a29a-216">When the local tools manifest file is available, but the tools defined in the manifest have not been installed, use the following command to automatically download and install those tools:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="2a29a-217">Execute uma ferramenta local com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2a29a-217">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="2a29a-218">Quando uma ferramenta local é executada, o dotnet pesquisa um manifesto na estrutura do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2a29a-218">When a local tool is run, dotnet searches for a manifest up the current directory structure.</span></span> <span data-ttu-id="2a29a-219">Ao encontrar um arquivo de manifesto de ferramenta, ele é pesquisado para a ferramenta solicitada.</span><span class="sxs-lookup"><span data-stu-id="2a29a-219">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="2a29a-220">Se a ferramenta for encontrada no manifesto, mas não no cache, o usuário receberá um erro e precisará executar `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-220">If the tool is found in the manifest, but not the cache, the user receives an error and needs to run `dotnet tool restore`.</span></span>

<span data-ttu-id="2a29a-221">Para remover uma ferramenta do arquivo de manifesto da ferramenta local, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2a29a-221">To remove a tool from the local tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <packageId>
```

<span data-ttu-id="2a29a-222">O arquivo de manifesto da ferramenta é projetado para permitir a edição manual, o que você pode fazer para atualizar a versão necessária ao trabalhar com o repositório.</span><span class="sxs-lookup"><span data-stu-id="2a29a-222">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span> <span data-ttu-id="2a29a-223">Veja aqui um exemplo de arquivo `dotnet-tools.json`:</span><span class="sxs-lookup"><span data-stu-id="2a29a-223">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="2a29a-224">Para ferramentas globais e locais, é necessária uma versão compatível do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2a29a-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="2a29a-225">Muitas ferramentas que estão atualmente em NuGet.org direcionam para o tempo de execução do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="2a29a-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="2a29a-226">Para instalá-las global ou localmente, você ainda precisará instalar o [tempo de execução do NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="2a29a-226">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="2a29a-227">Área de Trabalho do Windows</span><span class="sxs-lookup"><span data-stu-id="2a29a-227">Windows desktop</span></span>

<span data-ttu-id="2a29a-228">A partir do .NET Core 3.0 Versão prévia 1, é possível criar aplicativos de área de trabalho do Windows usando WPF e Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2a29a-228">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="2a29a-229">Essas estruturas também oferecem suporte ao uso de controles modernos e no estilo Fluent da biblioteca XAML da interface do usuário do Windows (WinUI) por meio de [Ilhas XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="2a29a-229">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="2a29a-230">O componente Windows Desktop faz parte do SDK do .NET Core 3.0 do Windows.</span><span class="sxs-lookup"><span data-stu-id="2a29a-230">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="2a29a-231">É possível criar um novo aplicativo de WPF ou Windows Forms com os seguintes comandos `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="2a29a-231">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="2a29a-232">O Visual Studio 2019 adiciona modelos de **Novo Projeto** ao Windows Forms e WPF no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-232">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span> <span data-ttu-id="2a29a-233">Ainda não há suporte para designers.</span><span class="sxs-lookup"><span data-stu-id="2a29a-233">Designers are still not yet supported.</span></span> <span data-ttu-id="2a29a-234">Além disso, é possível abrir, iniciar e depurar esses projetos no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2a29a-234">And you can open, launch, and debug these projects in Visual Studio 2019.</span></span>

<span data-ttu-id="2a29a-235">O Visual Studio 2017 15.9 adiciona a capacidade de [habilitar versões prévias do .NET Core](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), mas você precisa ativar essa funcionalidade e esse não é um cenário compatível.</span><span class="sxs-lookup"><span data-stu-id="2a29a-235">Visual Studio 2017 15.9 adds the ability to [enable .NET Core previews](https://devblogs.microsoft.com/dotnet/net-core-tooling-update-for-visual-studio-2017-version-15-9/), but you need to turn that feature on, and it's not a supported scenario.</span></span>

<span data-ttu-id="2a29a-236">Os novos projetos são os mesmos que os projetos existentes do .NET Core, com algumas adições.</span><span class="sxs-lookup"><span data-stu-id="2a29a-236">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="2a29a-237">Veja aqui a comparação entre o projeto básico de console do .NET Core e um projeto básico do Windows Forms e WPF.</span><span class="sxs-lookup"><span data-stu-id="2a29a-237">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="2a29a-238">Em um projeto de console do .NET Core, o projeto usa o SDK `Microsoft.NET.Sdk` e declara uma dependência no .NET Core 3.0 por meio da estrutura de destino `netcoreapp3.0`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-238">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="2a29a-239">Para criar um aplicativo de área de trabalho do Windows, use o SDK `Microsoft.NET.Sdk.WindowsDesktop` e escolha qual estrutura de interface do usuário usar:</span><span class="sxs-lookup"><span data-stu-id="2a29a-239">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2a29a-240">Para escolher o Windows Forms ao invés da WPF, defina `UseWindowsForms` em vez de `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="2a29a-240">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="2a29a-241">`UseWPF` e `UseWindowsForms` podem ser definidos como `true` se o aplicativo usar ambas as estruturas; por exemplo, quando uma caixa de diálogo do Windows Forms hospeda um controle da WPF.</span><span class="sxs-lookup"><span data-stu-id="2a29a-241">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="2a29a-242">Compartilhe seus comentários nos repositórios [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) e [dotnet/core](https://github.com/dotnet/core/issues).</span><span class="sxs-lookup"><span data-stu-id="2a29a-242">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="msix-deployment-for-windows-desktop"></a><span data-ttu-id="2a29a-243">Implantação do MSIX para Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="2a29a-243">MSIX Deployment for Windows Desktop</span></span>

<span data-ttu-id="2a29a-244">O [MSIX](https://docs.microsoft.com/windows/msix/) é um novo formato de pacote do aplicativo do Windows.</span><span class="sxs-lookup"><span data-stu-id="2a29a-244">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows app package format.</span></span> <span data-ttu-id="2a29a-245">Ele pode ser usado para implantar aplicativos da área de trabalho do .NET Core 3.0 no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2a29a-245">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="2a29a-246">O [Projeto de Empacotamento de Aplicativos do Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponível no Visual Studio 2019, permite criar pacotes MSIX com aplicativos .NET Core [autossuficientes](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="2a29a-246">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2a29a-247">O arquivo de projeto do .NET Core precisa especificar os tempos de execução compatíveis na propriedade `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="2a29a-247">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>
>
> ```xml
> <RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
> ```

## <a name="fast-built-in-json-support"></a><span data-ttu-id="2a29a-248">Suporte interno rápido a JSON</span><span class="sxs-lookup"><span data-stu-id="2a29a-248">Fast built-in JSON support</span></span>

<span data-ttu-id="2a29a-249">O ecossistema do .NET dependia do [**Json.NET**](https://www.newtonsoft.com/json) e de outras bibliotecas JSON populares, que continuam sendo boas opções.</span><span class="sxs-lookup"><span data-stu-id="2a29a-249">The .NET ecosystem has relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="2a29a-250">O **Json.NET** usa cadeias de caracteres do .NET como seu tipo de dados base, que, na verdade, são UTF-16.</span><span class="sxs-lookup"><span data-stu-id="2a29a-250">**Json.NET** uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span>

<span data-ttu-id="2a29a-251">O novo suporte interno ao JSON é de alto desempenho, baixa alocação e baseado em `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-251">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="2a29a-252">Três novos tipos principais relacionados ao JSON tiveram o namespace `System.Text.Json` adicionados ao .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-252">Three new main JSON-related types have been added to .NET Core 3.0 the `System.Text.Json` namespace.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="2a29a-253">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="2a29a-253">Utf8JsonReader</span></span>

<span data-ttu-id="2a29a-254">`System.Text.Json.Utf8JsonReader` é um leitor de alto desempenho, baixa alocação e somente para encaminhamento para texto JSON codificado em UTF-8, lido de um `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-254">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="2a29a-255">O `Utf8JsonReader` é um tipo fundamental de baixo nível, que pode ser usado para criar analisadores e desserializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="2a29a-255">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="2a29a-256">Ler por meio de uma payload JSON usando o novo `Utf8JsonReader` é duas vezes mais rápido do que usar o leitor do **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-256">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="2a29a-257">Ele não faz alocação até que você precise atualizar tokens JSON como cadeias de caracteres (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="2a29a-257">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="2a29a-258">Essa nova API incluirá os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="2a29a-258">This new API will include the following components:</span></span>

* <span data-ttu-id="2a29a-259">Na versão prévia 1: Leitor de JSON (acesso sequencial)</span><span class="sxs-lookup"><span data-stu-id="2a29a-259">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="2a29a-260">Em breve: Gravação de JSON, DOM (acesso aleatório), serializador POCO, desserializador POCO</span><span class="sxs-lookup"><span data-stu-id="2a29a-260">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="2a29a-261">Veja aqui o loop de leitor básico para o `Utf8JsonReader` que pode ser usado como ponto de partida:</span><span class="sxs-lookup"><span data-stu-id="2a29a-261">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

### <a name="utf8jsonwriter"></a><span data-ttu-id="2a29a-262">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="2a29a-262">Utf8JsonWriter</span></span>

<span data-ttu-id="2a29a-263">`System.Text.Json.Utf8JsonWriter` fornece um modo de alto desempenho, não armazenado em cache, somente avanço para escrita de texto JSON codificado em UTF-8 com base em tipos .NET comuns como `String`, `Int32` e `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-263">`System.Text.Json.Utf8JsonWriter` provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="2a29a-264">Assim como o leitor, o gravador é um tipo fundamental de baixo nível que pode ser utilizado para criar serializadores personalizados.</span><span class="sxs-lookup"><span data-stu-id="2a29a-264">Like the reader, the writer is a foundational, low-level type, that can be leveraged to build custom serializers.</span></span> <span data-ttu-id="2a29a-265">A escrita de um conteúdo em JSON usando o novo `Utf8JsonWriter` é 30-80% mais rápido do que o uso do gravador no **Json.NET** e não faz alocações.</span><span class="sxs-lookup"><span data-stu-id="2a29a-265">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and does not allocate.</span></span>

<span data-ttu-id="2a29a-266">Este é um uso de exemplo do `Utf8JsonWriter` que pode ser usado como ponto de partida:</span><span class="sxs-lookup"><span data-stu-id="2a29a-266">Here is a sample usage of the `Utf8JsonWriter` that can be used as a starting point:</span></span>

```csharp
static int WriteJson(IBufferWriter<byte> output, long[] extraData)
{
    var json = new Utf8JsonWriter(output, state: default);

    json.WriteStartObject();

    json.WriteNumber("age", 15, escape: false);
    json.WriteString("date", DateTime.Now);
    json.WriteString("first", "John");
    json.WriteString("last", "Smith");

    json.WriteStartArray("phoneNumbers", escape: false);
    json.WriteStringValue("425-000-1212", escape: false);
    json.WriteStringValue("425-000-1213");
    json.WriteEndArray();

    json.WriteStartObject("address");
    json.WriteString("street", "1 Microsoft Way");
    json.WriteString("city", "Redmond");
    json.WriteNumber("zip", 98052);
    json.WriteEndObject();

    json.WriteStartArray("ExtraArray");
    for (var i = 0; i < extraData.Length; i++)
    {
        json.WriteNumberValue(extraData[i]);
    }
    json.WriteEndArray();

    json.WriteEndObject();

    json.Flush(isFinalBlock: true);

    return (int)json.BytesWritten;
}
```

<span data-ttu-id="2a29a-267">O `Utf8JsonWriter` aceita `IBufferWriter<byte>` como a localização de saída na qual gravar os dados JSON de forma síncrona e você, como o chamador, precisa fornecer uma implementação concreta.</span><span class="sxs-lookup"><span data-stu-id="2a29a-267">The `Utf8JsonWriter` accepts `IBufferWriter<byte>` as the output location to synchronously write the json data into, and you as the caller need to provide a concrete implementation.</span></span> <span data-ttu-id="2a29a-268">Atualmente, a plataforma não inclui uma implementação dessa interface.</span><span class="sxs-lookup"><span data-stu-id="2a29a-268">The platform does not currently include an implementation of this interface.</span></span> <span data-ttu-id="2a29a-269">Para obter um exemplo de `IBufferWriter<byte>`, confira <https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35>.</span><span class="sxs-lookup"><span data-stu-id="2a29a-269">For an example of `IBufferWriter<byte>`, see <https://gist.github.com/ahsonkhan/c76a1cc4dc7107537c3fdc0079a68b35>.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="2a29a-270">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="2a29a-270">JsonDocument</span></span>

<span data-ttu-id="2a29a-271">`System.Text.Json.JsonDocument` é criado com base no `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-271">`System.Text.Json.JsonDocument` is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="2a29a-272">O `JsonDocument` fornece a capacidade de analisar dados JSON e criar um DOM (Modelo de Objeto do Documento) somente leitura que pode ser consultado para dar suporte a enumeração e acesso aleatório.</span><span class="sxs-lookup"><span data-stu-id="2a29a-272">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="2a29a-273">Os elementos JSON que compõem os dados podem ser acessados por meio do tipo `JsonElement` que é exposto pelo `JsonDocument` como uma propriedade chamada `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-273">The JSON elements that compose the data can be accessed via the `JsonElement` type which is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="2a29a-274">O `JsonElement` contém os enumeradores de objeto e de matriz JSON junto com as APIs para converter o texto JSON em tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="2a29a-274">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="2a29a-275">A análise de um conteúdo JSON típico e o acesso a todos os seus membros usando o `JsonDocument` é de 2 a 3 vezes mais rápido do que o **Json.NET**, com muito poucas alocações para dados que são razoavelmente dimensionados (ou seja, < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="2a29a-275">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with very little allocations for data that is reasonably sized (i.e. < 1 MB).</span></span>

<span data-ttu-id="2a29a-276">Este é um uso de exemplo de `JsonDocument` e `JsonElement` que pode ser usado como ponto de partida:</span><span class="sxs-lookup"><span data-stu-id="2a29a-276">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

```csharp
static double ParseJson()
{
    const string json = " [ { \"name\": \"John\" }, [ \"425-000-1212\", 15 ], { \"grades\": [ 90, 80, 100, 75 ] } ]";

    double average = -1;

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        JsonElement root = doc.RootElement;
        JsonElement info = root[1];

        string phoneNumber = info[0].GetString();
        int age = info[1].GetInt32();

        JsonElement grades = root[2].GetProperty("grades");

        double sum = 0;
        foreach (JsonElement grade in grades.EnumerateArray())
        {
            sum += grade.GetInt32();
        }

        int numberOfCourses = grades.GetArrayLength();
        average = sum / numberOfCourses;
    }

    return average;
}
```

## <a name="assembly-unloadability"></a><span data-ttu-id="2a29a-277">Capacidade de descarregamento de assembly</span><span class="sxs-lookup"><span data-stu-id="2a29a-277">Assembly Unloadability</span></span>

<span data-ttu-id="2a29a-278">A capacidade de descarregamento de assembly é uma nova funcionalidade do `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-278">Assembly unloadability is a new capability of `AssemblyLoadContext`.</span></span> <span data-ttu-id="2a29a-279">Essa nova funcionalidade é amplamente transparente de uma perspectiva da API, exposta com apenas algumas novas APIs.</span><span class="sxs-lookup"><span data-stu-id="2a29a-279">This new feature is largely transparent from an API perspective, exposed with just a few new APIs.</span></span> <span data-ttu-id="2a29a-280">Ela permite que um contexto do carregador seja descarregado, liberando toda a memória para tipos instanciados, campos estáticos e para o próprio assembly.</span><span class="sxs-lookup"><span data-stu-id="2a29a-280">It enables a loader context to be unloaded, releasing all memory for instantiated types, static fields and for the assembly itself.</span></span> <span data-ttu-id="2a29a-281">Um aplicativo deve conseguir carregar e descarregar assemblies por meio desse mecanismo para sempre, sem experimentar perda de memória.</span><span class="sxs-lookup"><span data-stu-id="2a29a-281">An application should be able to load and unload assemblies via this mechanism forever without experiencing a memory leak.</span></span>

<span data-ttu-id="2a29a-282">Essa nova funcionalidade pode ser usada para cenários semelhantes a:</span><span class="sxs-lookup"><span data-stu-id="2a29a-282">This new capability can be used for scenarios similar to:</span></span>

* <span data-ttu-id="2a29a-283">Cenários de plug-in em que o carregamento e o descarregamento dinâmicos de plug-in são necessários.</span><span class="sxs-lookup"><span data-stu-id="2a29a-283">Plugin scenarios where dynamic plugin loading and unloading is required.</span></span>
* <span data-ttu-id="2a29a-284">Compilação, execução e, em seguida, liberação dinâmicas do código.</span><span class="sxs-lookup"><span data-stu-id="2a29a-284">Dynamically compiling, running and then flushing code.</span></span> <span data-ttu-id="2a29a-285">Útil para sites, mecanismos de script etc.</span><span class="sxs-lookup"><span data-stu-id="2a29a-285">Useful for web sites, scripting engines, etc.</span></span>
* <span data-ttu-id="2a29a-286">Carregamento de assemblies para introspecção (como ReflectionOnlyLoad), embora [MetadataLoadContext](#type-metadataloadcontext) (lançado na Versão Prévia 1) seja uma opção melhor em muitos casos.</span><span class="sxs-lookup"><span data-stu-id="2a29a-286">Loading assemblies for introspection (like ReflectionOnlyLoad), although [MetadataLoadContext](#type-metadataloadcontext) (released in Preview 1) will be a better choice in many cases.</span></span>

<span data-ttu-id="2a29a-287">Para obter mais informações, confira o documento [Usando a capacidade de descarregamento](https://github.com/dotnet/coreclr/pull/22221).</span><span class="sxs-lookup"><span data-stu-id="2a29a-287">For more information, see the [Using Unloadability](https://github.com/dotnet/coreclr/pull/22221) document.</span></span>

<span data-ttu-id="2a29a-288">O descarregamento de assembly exige cuidado significativo para garantir que todas as referências a objetos gerenciados externas a um contexto do carregador sejam compreendidas e gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="2a29a-288">Assembly unloading requires significant care to ensure that all references to managed objects from outside a loader context are understood and managed.</span></span> <span data-ttu-id="2a29a-289">Quando o contexto do carregador é solicitado a ser descarregado, as referências externas precisam ter sido removidas, de modo que o contexto do carregador seja autoconsistente somente consigo mesmo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-289">When the loader context is requested to be unloaded, any outside references need to have been unreferenced so that the loader context is self-consistent only to itself.</span></span>

<span data-ttu-id="2a29a-290">A capacidade de descarregamento de assembly era fornecida no .NET Framework por Domínios do Aplicativo (AppDomains), que não são compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a29a-290">Assembly unloadability was provided in the .NET Framework by Application Domains (AppDomains), which are not supported with .NET Core.</span></span> <span data-ttu-id="2a29a-291">Os AppDomains apresentavam benefícios e limitações em comparação com esse novo modelo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-291">AppDomains had both benefits and limitations compared to this new model.</span></span> <span data-ttu-id="2a29a-292">Considere que esse novo modelo de carregador seja mais flexível e tenha um desempenho mais alto quando comparado aos AppDomains.</span><span class="sxs-lookup"><span data-stu-id="2a29a-292">Consider this new loader model to be more flexible and higher performant when compared to AppDomains.</span></span>

## <a name="windows-native-interop"></a><span data-ttu-id="2a29a-293">Interoperabilidade nativa do Windows</span><span class="sxs-lookup"><span data-stu-id="2a29a-293">Windows Native Interop</span></span>

<span data-ttu-id="2a29a-294">O Windows oferece uma API nativa sofisticada, na forma de APIs C simples, COM e WinRT.</span><span class="sxs-lookup"><span data-stu-id="2a29a-294">Windows offers a rich native API, in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="2a29a-295">No .NET Core 1.0 em diante, há suporte para **PInvoke**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-295">Since .NET Core 1.0, **P/Invoke** has been supported.</span></span> <span data-ttu-id="2a29a-296">Agora com o .NET Core 3.0, foi adicionado o suporte para a capacidade de **Cocriar APIs COM** e **Ativar APIs WinRT**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-296">Now with .NET Core 3.0, support for the ability to **CoCreate COM APIs** and **Activate WinRT APIs** has been added.</span></span>

<span data-ttu-id="2a29a-297">Veja um exemplo de como usar o COM com o [código-fonte de Demonstração do Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="2a29a-297">You can see an example of using COM with the [Excel Demo source code](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="2a29a-298">Tipo: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="2a29a-298">Type: SequenceReader</span></span>

<span data-ttu-id="2a29a-299">`System.Buffers.SequenceReader` foi adicionado ao .NET Core 3.0, podendo ser usado como um leitor para `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-299">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="2a29a-300">Isso permite uma análise fácil, de baixa alocação e de alto desempenho dos dados `System.IO.Pipelines`, que pode cruzar vários buffers de backup.</span><span class="sxs-lookup"><span data-stu-id="2a29a-300">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span>

<span data-ttu-id="2a29a-301">O exemplo a seguir quebra uma `Sequence` de entrada em linhas delimitadas `CR/LF` válidas:</span><span class="sxs-lookup"><span data-stu-id="2a29a-301">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="2a29a-302">Tipo: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="2a29a-302">Type: MetadataLoadContext</span></span>

<span data-ttu-id="2a29a-303">Adicionamos o tipo `MetadataLoadContext`, permitindo a leitura de metadados de assembly sem afetar o domínio do aplicativo do chamador.</span><span class="sxs-lookup"><span data-stu-id="2a29a-303">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="2a29a-304">Assemblies são lidos como dados, incluindo assemblies compilados para arquiteturas e plataformas diferentes do ambiente de tempo de execução atual.</span><span class="sxs-lookup"><span data-stu-id="2a29a-304">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="2a29a-305">`MetadataLoadContext` se sobrepõe a <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, que só está disponível no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a29a-305">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="2a29a-306">`MetdataLoadContext` está disponível no [pacote System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="2a29a-306">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="2a29a-307">Este é um pacote do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-307">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="2a29a-308">O `MetadataLoadContext` expõe APIs semelhantes ao tipo <xref:System.Runtime.Loader.AssemblyLoadContext>, mas não é baseado nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-308">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="2a29a-309">Assim como <xref:System.Runtime.Loader.AssemblyLoadContext>, o `MetadataLoadContext` permite o carregamento de assemblies dentro de um universo de carregamento de assemblies isolado.</span><span class="sxs-lookup"><span data-stu-id="2a29a-309">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="2a29a-310">APIs `MetdataLoadContext` retornam objetos <xref:System.Reflection.Assembly>, permitindo o uso de APIs de reflexão familiares.</span><span class="sxs-lookup"><span data-stu-id="2a29a-310">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="2a29a-311">APIs orientadas a execução, como [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), não são permitidas e emitirão InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="2a29a-311">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="2a29a-312">O exemplo a seguir demonstra como localizar tipos concretos em um assembly que implementa determinada interface:</span><span class="sxs-lookup"><span data-stu-id="2a29a-312">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="2a29a-313">Cenários para `MetadataLoadContext` incluem recursos de tempo de design, ferramentas de tempo de build e recursos de destaque de tempo de execução, que precisam inspecionar um conjunto de assemblies como dados e ter todos os bloqueios de arquivo e memória liberados após a execução da inspeção.</span><span class="sxs-lookup"><span data-stu-id="2a29a-313">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="2a29a-314">Em `MetadataLoadContext`, uma classe de resolvedor é transmitida para seu construtor.</span><span class="sxs-lookup"><span data-stu-id="2a29a-314">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="2a29a-315">O trabalho do resolvedor é carregar um `Assembly` considerando seu `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-315">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="2a29a-316">A classe de resolvedor deriva da classe abstrata `MetadataAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-316">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="2a29a-317">Uma implementação do resolvedor para cenários com base em caminho é fornecida com `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-317">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="2a29a-318">Os [testes de MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstram vários casos de uso.</span><span class="sxs-lookup"><span data-stu-id="2a29a-318">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="2a29a-319">Os [testes de assembly](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) são uma boa forma de começar.</span><span class="sxs-lookup"><span data-stu-id="2a29a-319">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="2a29a-320">TLS 1.3 e OpenSSL 1.1.1 no Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-320">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="2a29a-321">O .NET Core agora aproveitará o [suporte do TLS 1.3 no OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), quando estiver disponível em determinado ambiente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-321">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="2a29a-322">O TLS 1.3 tem vários benefícios, de acordo com a [equipe do OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="2a29a-322">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="2a29a-323">Tempos de conexão aprimorados, devido a uma redução no número de viagens de ida e volta necessário entre o cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="2a29a-323">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="2a29a-324">Segurança aprimorada devido à remoção de vários algoritmos criptográficos obsoletos e não seguros e à criptografia de maior quantidade do handshake de conexão.</span><span class="sxs-lookup"><span data-stu-id="2a29a-324">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="2a29a-325">O .NET Core 3.0 Versão prévia 1 é capaz de utilizar **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, ou **OpenSSL 1.0.2** (seja qual for a melhor versão encontrada, em um sistema Linux).</span><span class="sxs-lookup"><span data-stu-id="2a29a-325">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="2a29a-326">Quando o **OpenSSL 1.1.1**  estiver disponível, os tipos SslStream e HttpClient usarão **TLS 1.3** ao usar `SslProtocols.None` (protocolos padrão do sistema), considerando que o cliente e o servidor ofereçam suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-326">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="2a29a-327">O exemplo a seguir demonstra o .NET Core 3.0 Versão prévia 1 em Ubuntu 18.10 conectando-se a <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="2a29a-327">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="2a29a-328">Windows e macOS ainda não oferecem suporte a **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-328">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="2a29a-329">O .NET Core 3.0 será compatível com **TLS 1.3** nesses sistemas operacionais quando o suporte for disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="2a29a-329">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="2a29a-330">Criptografia</span><span class="sxs-lookup"><span data-stu-id="2a29a-330">Cryptography</span></span>

<span data-ttu-id="2a29a-331">Foi adicionado suporte para criptografias **AES-GCM** e **AES-CCM**, implementadas via `System.Security.Cryptography.AesGcm` e `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-331">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="2a29a-332">Esses algoritmos são os [algoritmos de Criptografia Autenticada com Dados de Associação (AEAD) ](https://en.wikipedia.org/wiki/Authenticated_encryption) e os primeiros algoritmos de Criptografia Autenticada (AE) adicionados ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a29a-332">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="2a29a-333">O código a seguir demonstra como usar criptografia **AesGcm** para criptografar e descriptografar dados aleatórios.</span><span class="sxs-lookup"><span data-stu-id="2a29a-333">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="2a29a-334">O código para **AesCcm** seria quase idêntico (somente os nomes de variáveis de classe seriam diferentes).</span><span class="sxs-lookup"><span data-stu-id="2a29a-334">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="2a29a-335">Importar/exportar chave de criptografia</span><span class="sxs-lookup"><span data-stu-id="2a29a-335">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="2a29a-336">O .NET Core 3.0 Versão prévia 1 oferece suporte à importação e exportação de chaves públicas e privadas assimétricas nos formatos padrão, sem a necessidade de usar um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="2a29a-336">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="2a29a-337">Todos os tipos de chave (RSA, DSA, ECDsa, ECDiffieHellman) são compatíveis com o formato **X.509 SubjectPublicKeyInfo** para chaves públicas e com os formatos **PKCS#8 PrivateKeyInfo** e **PKCS#8 EncryptedPrivateKeyInfo** para chaves privadas.</span><span class="sxs-lookup"><span data-stu-id="2a29a-337">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="2a29a-338">RSA também é compatível com **PKCS#1 RSAPublicKey** e **PKCS#1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="2a29a-338">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="2a29a-339">Todos os métodos de exportação produzem dados binários codificados por DER, e os métodos de importação esperam o mesmo.</span><span class="sxs-lookup"><span data-stu-id="2a29a-339">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="2a29a-340">Se uma chave for armazenada no formato PEM compatível com texto, o chamador precisará decodificar o conteúdo em Base64 antes de chamar um método de importação.</span><span class="sxs-lookup"><span data-stu-id="2a29a-340">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);

                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="2a29a-341">Arquivos PKCS#8 podem ser inspecionados com a classe `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-341">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="2a29a-342">Arquivos PFX/PKCS#12 podem ser inspecionados e manipulados com `System.Security.Cryptography.Pkcs.Pkcs12Info` e `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-342">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="2a29a-343">SerialPort para Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-343">SerialPort for Linux</span></span>

<span data-ttu-id="2a29a-344">O .NET Core 3.0 agora oferece suporte a <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> no Linux.</span><span class="sxs-lookup"><span data-stu-id="2a29a-344">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="2a29a-345">Anteriormente, o .NET Core só era compatível com o uso do tipo `SerialPort` no Windows.</span><span class="sxs-lookup"><span data-stu-id="2a29a-345">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="2a29a-346">Mais melhorias do BCL</span><span class="sxs-lookup"><span data-stu-id="2a29a-346">More BCL Improvements</span></span>

<span data-ttu-id="2a29a-347">O `Span<T>`, `Memory<T>` e tipos relacionados, que foram introduzidos no .NET Core 2.1, foram otimizados no .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-347">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="2a29a-348">Operações comuns, como construção de intervalo, divisão, análise e formatação agora funcionam melhor.</span><span class="sxs-lookup"><span data-stu-id="2a29a-348">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span>

<span data-ttu-id="2a29a-349">Além disso, tipos como `String` tiveram melhorias discretas para torná-los mais eficientes quando usados como chaves com `Dictionary<TKey, TValue>` e outras coleções.</span><span class="sxs-lookup"><span data-stu-id="2a29a-349">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="2a29a-350">Nenhuma alteração de código é necessária para se beneficiar dessas melhorias.</span><span class="sxs-lookup"><span data-stu-id="2a29a-350">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="2a29a-351">As melhorias a seguir também são novas no .NET Core 3 Versão prévia 1:</span><span class="sxs-lookup"><span data-stu-id="2a29a-351">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="2a29a-352">Suporte a Brotli integrado a HttpClient</span><span class="sxs-lookup"><span data-stu-id="2a29a-352">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="2a29a-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="2a29a-353">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="2a29a-354">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="2a29a-354">Unsafe.Unbox</span></span>
* <span data-ttu-id="2a29a-355">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="2a29a-355">CancellationToken.Unregister</span></span>
* <span data-ttu-id="2a29a-356">Operadores aritméticos complexos</span><span class="sxs-lookup"><span data-stu-id="2a29a-356">Complex arithmetic operators</span></span>
* <span data-ttu-id="2a29a-357">APIs de soquete para TCP em atividade</span><span class="sxs-lookup"><span data-stu-id="2a29a-357">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="2a29a-358">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="2a29a-358">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="2a29a-359">Análise de IPEndPoint</span><span class="sxs-lookup"><span data-stu-id="2a29a-359">IPEndPoint parsing</span></span>
* <span data-ttu-id="2a29a-360">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="2a29a-360">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="2a29a-361">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="2a29a-361">Tiered compilation</span></span>

<span data-ttu-id="2a29a-362">A [compilação em camadas](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) é ativada por padrão com o .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2a29a-362">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="2a29a-363">É um recurso que permite que o tempo de execução use de forma mais adaptável o compilador Just-In-Time (JIT) para obter um melhor desempenho, tanto na inicialização quanto para maximizar a taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="2a29a-363">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="2a29a-364">Esse recurso foi adicionado como um recurso opcional no [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) e, em seguida, foi habilitado por padrão no [.NET Core 2.2 Versão prévia 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="2a29a-364">This feature was added as an opt-in feature in [.NET Core 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="2a29a-365">Subsequentemente, foi revertido novamente para opcional na versão .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="2a29a-365">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="2a29a-366">Suporte a ARM64 no Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-366">ARM64 Linux support</span></span>

<span data-ttu-id="2a29a-367">Foi adicionado suporte para o ARM64 no Linux.</span><span class="sxs-lookup"><span data-stu-id="2a29a-367">Support has been added for ARM64 for Linux.</span></span> <span data-ttu-id="2a29a-368">O principal caso de uso para ARM64 atualmente é em cenários de IoT.</span><span class="sxs-lookup"><span data-stu-id="2a29a-368">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="2a29a-369">As imagens de [Docker Alpine, Debian e Ubuntu estão disponíveis para o .NET Core para ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="2a29a-369">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="2a29a-370">Consulte [Status do ARM64 do .NET Core](https://github.com/dotnet/announcements/issues/82) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="2a29a-370">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="2a29a-371">O suporte do Windows a **ARM64** ainda não está disponível.</span><span class="sxs-lookup"><span data-stu-id="2a29a-371">**ARM64** Windows support isn't yet available.</span></span>

## <a name="install-net-core-30-previews-on-linux-with-snap"></a><span data-ttu-id="2a29a-372">Instalar as Versões Prévias do .NET Core 3.0 no Linux com o Snap</span><span class="sxs-lookup"><span data-stu-id="2a29a-372">Install .NET Core 3.0 Previews on Linux with Snap</span></span>

<span data-ttu-id="2a29a-373">O Snap é a maneira preferencial para instalar e testar versões prévias do .NET Core em [distribuições Linux que dão suporte ao Snap](https://docs.snapcraft.io/installing-snapd/6735).</span><span class="sxs-lookup"><span data-stu-id="2a29a-373">Snap is the preferred way to install and try .NET Core previews on [Linux distributions that support Snap](https://docs.snapcraft.io/installing-snapd/6735).</span></span>

<span data-ttu-id="2a29a-374">Depois de configurar o Snap no sistema, execute o comando a seguir para instalar o [SDK da Versão Prévia do SDK do .NET Core 3.0](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="2a29a-374">After configuring Snap on your system, run the following command to install the [.NET Core SDK 3.0 Preview SDK](https://snapcraft.io/dotnet-sdk).</span></span>

```console
sudo snap install dotnet-sdk --beta --classic
```

<span data-ttu-id="2a29a-375">Quando o .NET Core é instalado usando o pacote do Snap, o comando padrão do .NET Core é `dotnet-sdk.dotnet`, em vez de apenas `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2a29a-375">When .NET Core in installed using the Snap package, the default .NET Core command is `dotnet-sdk.dotnet`, as opposed to just `dotnet`.</span></span> <span data-ttu-id="2a29a-376">O benefício do comando com namespace é que ele não entrará em conflito com uma possível versão do .NET Core instalada globalmente existente.</span><span class="sxs-lookup"><span data-stu-id="2a29a-376">The benefit of the namespaced command is that it will not conflict with a globally installed .NET Core version you may have.</span></span> <span data-ttu-id="2a29a-377">Esse comando pode ter um alias com o `dotnet` com:</span><span class="sxs-lookup"><span data-stu-id="2a29a-377">This command can be aliased to `dotnet` with:</span></span>

```console
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="2a29a-378">Algumas distribuições exigem uma etapa adicional para habilitar o acesso ao certificado SSL.</span><span class="sxs-lookup"><span data-stu-id="2a29a-378">Some distros require an additional step to enable access to the SSL certificate.</span></span> <span data-ttu-id="2a29a-379">Confira nossa [Configuração do Linux](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="2a29a-379">See our [Linux Setup](https://github.com/dotnet/core/blob/master/Documentation/linux-setup.md) for details.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="2a29a-380">Suporte de GPIO para o Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="2a29a-380">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="2a29a-381">Dois novos pacotes foram lançados para o NuGet, que podem ser usados para a programação de GPIO.</span><span class="sxs-lookup"><span data-stu-id="2a29a-381">Two new packages have been released to NuGet that you can use for GPIO programming.</span></span>

* [<span data-ttu-id="2a29a-382">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="2a29a-382">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio/0.1.0-prerelease.19078.2)
* [<span data-ttu-id="2a29a-383">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="2a29a-383">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings/0.1.0-prerelease.19078.2)

<span data-ttu-id="2a29a-384">Os Pacotes de GPIO incluem APIs para dispositivos GPIO, SPI, I2C e PWM.</span><span class="sxs-lookup"><span data-stu-id="2a29a-384">The GPIO Packages includes APIs for GPIO, SPI, I2C and PWM devices.</span></span> <span data-ttu-id="2a29a-385">O pacote de associações de IoT inclui [associações de dispositivo](https://github.com/dotnet/iot/blob/master/src/devices/README.md) para vários chips e sensores, as mesmas disponíveis em [dotnet/iot – src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span><span class="sxs-lookup"><span data-stu-id="2a29a-385">The IoT bindings package includes [device bindings](https://github.com/dotnet/iot/blob/master/src/devices/README.md) for various chips and sensors, the same ones available at [dotnet/iot - src/devices](https://github.com/dotnet/iot/tree/master/src/devices).</span></span>

<span data-ttu-id="2a29a-386">As APIs de porta serial atualizadas que foram anunciadas como parte do .NET Core 3.0 Versão Prévia 1 não fazem parte desses pacotes, mas estão disponíveis como parte da plataforma .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a29a-386">The updated serial port APIs that were announced as part of .NET Core 3.0 Preview 1 are not part of these packages but are available as part of the .NET Core platform.</span></span>

## <a name="platform-support"></a><span data-ttu-id="2a29a-387">Suporte de plataforma</span><span class="sxs-lookup"><span data-stu-id="2a29a-387">Platform Support</span></span>

<span data-ttu-id="2a29a-388">O .NET Core 3 terá suporte nos seguintes sistemas operacionais:</span><span class="sxs-lookup"><span data-stu-id="2a29a-388">.NET Core 3 will be supported on the following operating systems:</span></span>

* <span data-ttu-id="2a29a-389">Cliente Windows: 7, 8.1, 10 (1607 e posterior)</span><span class="sxs-lookup"><span data-stu-id="2a29a-389">Windows Client: 7, 8.1, 10 (1607+)</span></span>
* <span data-ttu-id="2a29a-390">Windows Server: 2012 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="2a29a-390">Windows Server: 2012 R2 SP1+</span></span>
* <span data-ttu-id="2a29a-391">macOS: 10.12 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-391">macOS: 10.12+</span></span>
* <span data-ttu-id="2a29a-392">RHEL: 6 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-392">RHEL: 6+</span></span>
* <span data-ttu-id="2a29a-393">Fedora: 26 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-393">Fedora: 26+</span></span>
* <span data-ttu-id="2a29a-394">Ubuntu: 16.04 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-394">Ubuntu: 16.04+</span></span>
* <span data-ttu-id="2a29a-395">Debian: 9 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-395">Debian: 9+</span></span>
* <span data-ttu-id="2a29a-396">SLES: 12 e posterior</span><span class="sxs-lookup"><span data-stu-id="2a29a-396">SLES: 12+</span></span>
* <span data-ttu-id="2a29a-397">openSUSE: 42.3+</span><span class="sxs-lookup"><span data-stu-id="2a29a-397">openSUSE: 42.3+</span></span>
* <span data-ttu-id="2a29a-398">Alpine: 3.8+</span><span class="sxs-lookup"><span data-stu-id="2a29a-398">Alpine: 3.8+</span></span>

<span data-ttu-id="2a29a-399">O suporte de chip é descrito a seguir:</span><span class="sxs-lookup"><span data-stu-id="2a29a-399">Chip support follows:</span></span>

* <span data-ttu-id="2a29a-400">x64 no Windows, no macOS e no Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-400">x64 on Windows, macOS, and Linux</span></span>
* <span data-ttu-id="2a29a-401">x86 no Windows</span><span class="sxs-lookup"><span data-stu-id="2a29a-401">x86 on Windows</span></span>
* <span data-ttu-id="2a29a-402">ARM32 no Windows e no Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-402">ARM32 on Windows and Linux</span></span>
* <span data-ttu-id="2a29a-403">ARM64 no Linux</span><span class="sxs-lookup"><span data-stu-id="2a29a-403">ARM64 on Linux</span></span>

<span data-ttu-id="2a29a-404">Para o Linux, há suporte para o ARM32 no Debian 9 ou posterior e no Ubuntu 16.04 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="2a29a-404">For Linux, ARM32 is supported on Debian 9+ and Ubuntu 16.04+.</span></span> <span data-ttu-id="2a29a-405">Para o ARM64, isso é o mesmo que o ARM32 com a adição do Alpine 3.8.</span><span class="sxs-lookup"><span data-stu-id="2a29a-405">For ARM64, it is the same as ARM32 with the addition of Alpine 3.8.</span></span> <span data-ttu-id="2a29a-406">Essas são as mesmas versões dessas distribuições que têm suporte para o X64.</span><span class="sxs-lookup"><span data-stu-id="2a29a-406">These are the same versions of those distros as is supported for X64.</span></span>

<span data-ttu-id="2a29a-407">As imagens do Docker para o .NET Core 3.0 estão disponíveis em [microsoft/dotnet no Hub do Docker](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="2a29a-407">Docker images for .NET Core 3.0 are available at [microsoft/dotnet on Docker Hub](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="2a29a-408">Atualmente, a Microsoft está no processo de adoção do [MCR (Registro de Contêiner da Microsoft)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) e é esperado que as imagens finais do .NET Core 3.0 sejam publicadas somente no MCR.</span><span class="sxs-lookup"><span data-stu-id="2a29a-408">Microsoft is currently in the process of adopting [Microsoft Container Registry (MCR)](https://cloudblogs.microsoft.com/opensource/2019/01/17/improved-discovery-experience-microsoft-containers-docker-hub/) and it is expected that the final .NET Core 3.0 images will only be published to MCR.</span></span>
