---
title: O que há de novo no C# 8,0 – Guia C#
description: Obtenha uma visão geral dos novos recursos disponíveis no C# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: 27c2d7e2d6f0e665e7abe4fdcfb94c140224cc89
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895430"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="c351d-103">Novidades no C# 8.0</span><span class="sxs-lookup"><span data-stu-id="c351d-103">What's new in C# 8.0</span></span>

<span data-ttu-id="c351d-104">O c# 8,0 adiciona os seguintes recursos e aprimoramentos à linguagem C#:</span><span class="sxs-lookup"><span data-stu-id="c351d-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="c351d-105">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="c351d-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="c351d-106">Métodos de interface padrão</span><span class="sxs-lookup"><span data-stu-id="c351d-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="c351d-107">[Aprimoramentos de correspondência de padrões](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="c351d-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="c351d-108">Expressões Switch</span><span class="sxs-lookup"><span data-stu-id="c351d-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="c351d-109">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="c351d-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="c351d-110">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="c351d-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="c351d-111">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="c351d-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="c351d-112">Declarações using</span><span class="sxs-lookup"><span data-stu-id="c351d-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="c351d-113">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="c351d-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="c351d-114">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="c351d-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="c351d-115">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="c351d-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="c351d-116">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="c351d-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="c351d-117">Descartável assíncrono</span><span class="sxs-lookup"><span data-stu-id="c351d-117">Asynchronous disposable</span></span>](#asynchronous-disposable)
- [<span data-ttu-id="c351d-118">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="c351d-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="c351d-119">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="c351d-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="c351d-120">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="c351d-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="c351d-121">Stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="c351d-121">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="c351d-122">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="c351d-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="c351d-123">O C# 8,0 tem suporte no **.NET Core 3. x** e **.net Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="c351d-123">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="c351d-124">Para obter mais informações, consulte [controle de versão da linguagem C#](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-124">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="c351d-125">O restante deste artigo descreve rapidamente esses recursos.</span><span class="sxs-lookup"><span data-stu-id="c351d-125">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="c351d-126">Quando houver artigos detalhados disponíveis, forneceremos links para esses tutoriais e visões gerais.</span><span class="sxs-lookup"><span data-stu-id="c351d-126">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="c351d-127">Você pode explorar esses recursos em seu ambiente usando a ferramenta global `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="c351d-127">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="c351d-128">Instale a ferramenta global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="c351d-128">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="c351d-129">Clone o repositório [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="c351d-129">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="c351d-130">Defina o diretório atual do subdiretório *csharp8* para o repositório *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="c351d-130">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="c351d-131">Execute `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="c351d-131">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="c351d-132">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="c351d-132">Readonly members</span></span>

<span data-ttu-id="c351d-133">Você pode aplicar o `readonly` modificador a membros de um struct.</span><span class="sxs-lookup"><span data-stu-id="c351d-133">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="c351d-134">Indica que o membro não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="c351d-134">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="c351d-135">É mais granular do que aplicar o modificador `readonly` a uma declaração `struct`.</span><span class="sxs-lookup"><span data-stu-id="c351d-135">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="c351d-136">Considere o seguinte struct mutável:</span><span class="sxs-lookup"><span data-stu-id="c351d-136">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="c351d-137">Como a maioria das structs `ToString()` , o método não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="c351d-137">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="c351d-138">É possível indicar isso adicionando o modificador `readonly` à declaração de `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="c351d-138">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="c351d-139">A alteração anterior gera um aviso do compilador, `ToString` pois acessa a `Distance` Propriedade, que não está `readonly`marcada:</span><span class="sxs-lookup"><span data-stu-id="c351d-139">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="c351d-140">O compilador avisa quando há a necessidade de criar uma cópia de defesa.</span><span class="sxs-lookup"><span data-stu-id="c351d-140">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="c351d-141">A `Distance` propriedade não muda de estado, portanto você pode corrigir esse aviso adicionando o `readonly` modificador à declaração:</span><span class="sxs-lookup"><span data-stu-id="c351d-141">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="c351d-142">Observe que o `readonly` modificador é necessário em uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c351d-142">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="c351d-143">O compilador não pressupõe `get` que os acessadores não modifiquem o estado; Você deve declarar `readonly` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="c351d-143">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="c351d-144">As propriedades implementadas automaticamente são uma exceção; o compilador tratará todos os getters autoimplementados `readonly`como, portanto, aqui não há necessidade de adicionar `readonly` o modificador `X` às `Y` Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="c351d-144">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as `readonly`, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="c351d-145">O compilador impõe a regra que `readonly` os membros não modificam o estado.</span><span class="sxs-lookup"><span data-stu-id="c351d-145">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="c351d-146">O método a seguir não será compilado, a `readonly` menos que você remova o modificador:</span><span class="sxs-lookup"><span data-stu-id="c351d-146">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="c351d-147">Esse recurso permite que você especifique sua intenção de design para que o compilador possa impô-la e faça otimizações com base nessa intenção.</span><span class="sxs-lookup"><span data-stu-id="c351d-147">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

<span data-ttu-id="c351d-148">Para obter mais informações, consulte [ `readonly` ](../language-reference/builtin-types/struct.md#readonly-instance-members) a seção Membros da instância do artigo [tipos de estrutura](../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="c351d-148">For more information, see the [`readonly` instance members](../language-reference/builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../language-reference/builtin-types/struct.md) article.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="c351d-149">Métodos de interface padrão</span><span class="sxs-lookup"><span data-stu-id="c351d-149">Default interface methods</span></span>

<span data-ttu-id="c351d-150">Agora é possível adicionar membros a interfaces e fornecer uma implementação para esses membros.</span><span class="sxs-lookup"><span data-stu-id="c351d-150">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="c351d-151">Esse recurso de linguagem permite que os autores de API adicionem métodos a uma interface em versões posteriores sem interromper a fonte ou a compatibilidade binária com implementações existentes dessa interface.</span><span class="sxs-lookup"><span data-stu-id="c351d-151">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="c351d-152">As implementações existentes *herdam* a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="c351d-152">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="c351d-153">Esse recurso também permite que o C# interopere com APIs que direcionam o Android ou o Swift, que dão suporte a recursos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="c351d-153">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="c351d-154">Os métodos de interface padrão também habilitam cenários semelhantes a um recurso de linguagem de "características".</span><span class="sxs-lookup"><span data-stu-id="c351d-154">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="c351d-155">Os métodos de interface padrão afetam muitos cenários e elementos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="c351d-155">Default interface methods affect many scenarios and language elements.</span></span> <span data-ttu-id="c351d-156">Nosso primeiro tutorial aborda [como atualizar uma interface com implementações padrão](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-156">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="c351d-157">Outros tutoriais e atualizações de referência chegarão a tempo para a versão geral.</span><span class="sxs-lookup"><span data-stu-id="c351d-157">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="c351d-158">Mais padrões em mais partes</span><span class="sxs-lookup"><span data-stu-id="c351d-158">More patterns in more places</span></span>

<span data-ttu-id="c351d-159">Com a **correspondência de padrões**, você recebe ferramentas para fornecer funcionalidades dependentes da forma em tipos de dados relacionados, mas diferentes.</span><span class="sxs-lookup"><span data-stu-id="c351d-159">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="c351d-160">O C# 7,0 introduziu a sintaxe para padrões de tipo e padrões [`is`](../language-reference/keywords/is.md) constantes usando a [`switch`](../language-reference/keywords/switch.md) expressão e a instrução.</span><span class="sxs-lookup"><span data-stu-id="c351d-160">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="c351d-161">Esses recursos representaram os primeiros passos em direção ao suporte a paradigmas de programação, em que os dados e a funcionalidade vivem separados.</span><span class="sxs-lookup"><span data-stu-id="c351d-161">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="c351d-162">À medida que o setor se aproxima mais de microsserviços e de outras arquiteturas baseadas em nuvem, outras ferramentas de linguagem de tornam necessárias.</span><span class="sxs-lookup"><span data-stu-id="c351d-162">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="c351d-163">O C# 8.0 expande esse vocabulário, para que você possa usar mais expressões de padrão em mais partes do seu código.</span><span class="sxs-lookup"><span data-stu-id="c351d-163">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="c351d-164">Considere esses recursos quando seus dados e funcionalidades estiverem separados.</span><span class="sxs-lookup"><span data-stu-id="c351d-164">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="c351d-165">Considere a correspondência de padrões quando seus algoritmos dependerem de um fato diferente do tipo de runtime de um objeto.</span><span class="sxs-lookup"><span data-stu-id="c351d-165">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="c351d-166">Essas técnicas fornecem outra maneira de expressar designs.</span><span class="sxs-lookup"><span data-stu-id="c351d-166">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="c351d-167">Além dos novos padrões em novas partes, o C# 8.0 adiciona **padrões recursivos**.</span><span class="sxs-lookup"><span data-stu-id="c351d-167">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="c351d-168">O resultado de qualquer expressão padrão é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c351d-168">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="c351d-169">Um padrão recursivo é simplesmente uma expressão padrão aplicada à saída de outra expressão padrão.</span><span class="sxs-lookup"><span data-stu-id="c351d-169">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="c351d-170">Expressões switch</span><span class="sxs-lookup"><span data-stu-id="c351d-170">Switch expressions</span></span>

<span data-ttu-id="c351d-171">Geralmente, uma [`switch`](../language-reference/keywords/switch.md) instrução produz um valor em cada um de `case` seus blocos.</span><span class="sxs-lookup"><span data-stu-id="c351d-171">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="c351d-172">As **expressões switch** permitem que você use a sintaxe de expressão mais concisa.</span><span class="sxs-lookup"><span data-stu-id="c351d-172">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="c351d-173">Há menos palavras-chave `case` e `break` repetidas, e menos chaves.</span><span class="sxs-lookup"><span data-stu-id="c351d-173">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="c351d-174">Por exemplo, considere a enumeração a seguir que lista as cores do arco-íris:</span><span class="sxs-lookup"><span data-stu-id="c351d-174">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="c351d-175">Se seu aplicativo definiu um tipo `RGBColor` que é construído a partir dos componentes `R`, `G` e `B`, você poderia converter um valor `Rainbow` em seus valores RGB usando o método a seguir que contém uma expressão de opção:</span><span class="sxs-lookup"><span data-stu-id="c351d-175">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="c351d-176">Há vários aprimoramentos de sintaxe aqui:</span><span class="sxs-lookup"><span data-stu-id="c351d-176">There are several syntax improvements here:</span></span>

- <span data-ttu-id="c351d-177">A variável vem antes da palavra-chave `switch`.</span><span class="sxs-lookup"><span data-stu-id="c351d-177">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="c351d-178">A ordem diferente facilita distinguir visualmente a expressão switch da instrução switch.</span><span class="sxs-lookup"><span data-stu-id="c351d-178">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="c351d-179">Os elementos `case` e `:` são substituídos por `=>`.</span><span class="sxs-lookup"><span data-stu-id="c351d-179">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="c351d-180">É mais conciso e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="c351d-180">It's more concise and intuitive.</span></span>
- <span data-ttu-id="c351d-181">O caso `default` é substituído por um descarte `_`.</span><span class="sxs-lookup"><span data-stu-id="c351d-181">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="c351d-182">Os corpos são expressões, não instruções.</span><span class="sxs-lookup"><span data-stu-id="c351d-182">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="c351d-183">Compare isso com o código equivalente usando a instrução clássica `switch`:</span><span class="sxs-lookup"><span data-stu-id="c351d-183">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="c351d-184">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="c351d-184">Property patterns</span></span>

<span data-ttu-id="c351d-185">O **padrão da propriedade** permite que você compare as propriedades do objeto examinado.</span><span class="sxs-lookup"><span data-stu-id="c351d-185">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="c351d-186">Considere um site de comércio eletrônico que deve calcular o imposto da venda com base no endereço do comprador.</span><span class="sxs-lookup"><span data-stu-id="c351d-186">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="c351d-187">Essa computação não é uma responsabilidade principal de `Address` uma classe.</span><span class="sxs-lookup"><span data-stu-id="c351d-187">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="c351d-188">Ele mudará ao longo do tempo, provavelmente com mais frequência do que as alterações de formato de endereço.</span><span class="sxs-lookup"><span data-stu-id="c351d-188">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="c351d-189">O valor do imposto depende da propriedade `State` do endereço.</span><span class="sxs-lookup"><span data-stu-id="c351d-189">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="c351d-190">O método a seguir usa o padrão de propriedade para calcular o imposto da venda de acordo com o endereço e o preço:</span><span class="sxs-lookup"><span data-stu-id="c351d-190">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="c351d-191">A correspondência de padrão cria uma sintaxe concisa para expressar esse algoritmo.</span><span class="sxs-lookup"><span data-stu-id="c351d-191">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="c351d-192">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="c351d-192">Tuple patterns</span></span>

<span data-ttu-id="c351d-193">Alguns algoritmos dependem de várias entradas.</span><span class="sxs-lookup"><span data-stu-id="c351d-193">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="c351d-194">**Padrões de tupla** permitem que você alterne com base em vários valores, expressadas como uma [tupla](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-194">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="c351d-195">O código a seguir mostra uma expressão de comutador para o jogo *pedra, papel, tesoura*:</span><span class="sxs-lookup"><span data-stu-id="c351d-195">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="c351d-196">As mensagens indicam o vencedor.</span><span class="sxs-lookup"><span data-stu-id="c351d-196">The messages indicate the winner.</span></span> <span data-ttu-id="c351d-197">O caso de descarte representa três combinações para empates ou outras entradas de texto.</span><span class="sxs-lookup"><span data-stu-id="c351d-197">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="c351d-198">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="c351d-198">Positional patterns</span></span>

<span data-ttu-id="c351d-199">Alguns tipos incluem um método `Deconstruct` que desconstrói suas propriedades em variáveis discretas.</span><span class="sxs-lookup"><span data-stu-id="c351d-199">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="c351d-200">Quando um método `Deconstruct` é acessível, você pode usar **padrões posicionais** para inspecionar as propriedades do objeto e usar essas propriedades para um padrão.</span><span class="sxs-lookup"><span data-stu-id="c351d-200">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="c351d-201">Considere a seguinte classe `Point`, que inclui um método `Deconstruct` para criar variáveis discretas para `X` e `Y`:</span><span class="sxs-lookup"><span data-stu-id="c351d-201">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="c351d-202">Além disso, considere a seguinte enumeração que representa várias posições de um quadrante:</span><span class="sxs-lookup"><span data-stu-id="c351d-202">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="c351d-203">O método a seguir usa o **padrão posicional** para extrair os valores de `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="c351d-203">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="c351d-204">Em seguida, ele usa uma cláusula `when` para determinar o `Quadrant` do ponto:</span><span class="sxs-lookup"><span data-stu-id="c351d-204">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="c351d-205">O padrão de discard na opção anterior encontra a correspondência quando `x` ou `y` é 0, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="c351d-205">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="c351d-206">Uma expressão switch deve produzir um valor ou lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c351d-206">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="c351d-207">Se não houver correspondência em nenhum dos casos, a expressão switch gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c351d-207">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="c351d-208">O compilador gerará um aviso para você se você não cobrir todos os casos possíveis em sua expressão de comutador.</span><span class="sxs-lookup"><span data-stu-id="c351d-208">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="c351d-209">Explore técnicas de correspondência de padrões neste [tutorial avançado sobre correspondência de padrões](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-209">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="c351d-210">Declarações using</span><span class="sxs-lookup"><span data-stu-id="c351d-210">Using declarations</span></span>

<span data-ttu-id="c351d-211">Uma **declaração using** é uma declaração de variável precedida pela palavra-chave `using`.</span><span class="sxs-lookup"><span data-stu-id="c351d-211">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="c351d-212">Ele informa ao compilador que a variável que está sendo declarada deve ser descartada ao final do escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="c351d-212">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="c351d-213">Por exemplo, considere o seguinte código que grava um arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="c351d-213">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="c351d-214">No exemplo anterior, o arquivo é descartado quando a chave de fechamento do método é atingida.</span><span class="sxs-lookup"><span data-stu-id="c351d-214">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="c351d-215">Esse é o final do escopo no qual `file` é declarado.</span><span class="sxs-lookup"><span data-stu-id="c351d-215">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="c351d-216">O código anterior equivale ao código a seguir que usa as [instruções using](../language-reference/keywords/using-statement.md) clássicas:</span><span class="sxs-lookup"><span data-stu-id="c351d-216">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

<span data-ttu-id="c351d-217">No exemplo anterior, o arquivo é descartado quando a chave de fechamento associada à instrução `using` é atingida.</span><span class="sxs-lookup"><span data-stu-id="c351d-217">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="c351d-218">Em ambos os casos, o compilador gera a chamada para `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="c351d-218">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="c351d-219">O compilador gerará um erro se a expressão na `using` instrução não for descartável.</span><span class="sxs-lookup"><span data-stu-id="c351d-219">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="c351d-220">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="c351d-220">Static local functions</span></span>

<span data-ttu-id="c351d-221">Agora você pode adicionar o modificador `static` para funções locais a fim de garantir que essa função local não capture (faça referência) às variáveis no escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="c351d-221">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="c351d-222">Essa ação gera `CS8421`, "Uma função local estática não pode conter uma referência à \<variable>".</span><span class="sxs-lookup"><span data-stu-id="c351d-222">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="c351d-223">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c351d-223">Consider the following code.</span></span> <span data-ttu-id="c351d-224">A função local `LocalFunction` acessa a variável `y`, declarada no escopo delimitador (o método `M`).</span><span class="sxs-lookup"><span data-stu-id="c351d-224">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="c351d-225">Portanto, `LocalFunction` não pode ser declarada com o modificador `static`:</span><span class="sxs-lookup"><span data-stu-id="c351d-225">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="c351d-226">O código a seguir contém uma função local estática.</span><span class="sxs-lookup"><span data-stu-id="c351d-226">The following code contains a static local function.</span></span> <span data-ttu-id="c351d-227">Ela pode ser estática porque não acesse as variáveis no escopo delimitador:</span><span class="sxs-lookup"><span data-stu-id="c351d-227">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="c351d-228">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="c351d-228">Disposable ref structs</span></span>

<span data-ttu-id="c351d-229">Um `struct` declarado com o `ref` modificador não pode implementar nenhuma interface e, portanto <xref:System.IDisposable>, não pode implementar.</span><span class="sxs-lookup"><span data-stu-id="c351d-229">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="c351d-230">Portanto, para permitir que uma `ref struct` seja descartada, ela deve ter um método `void Dispose()` acessível.</span><span class="sxs-lookup"><span data-stu-id="c351d-230">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="c351d-231">Esse recurso também se aplica `readonly ref struct` a declarações.</span><span class="sxs-lookup"><span data-stu-id="c351d-231">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="c351d-232">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="c351d-232">Nullable reference types</span></span>

<span data-ttu-id="c351d-233">Dentro de um contexto de anotação anulável, qualquer variável de um tipo de referência é considerado um **tipo de referência não anulável**.</span><span class="sxs-lookup"><span data-stu-id="c351d-233">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="c351d-234">Se você quiser indicar que uma variável pode ser nula, acrescente o nome do tipo com o `?` para declarar a variável como um **tipo de referência anulável**.</span><span class="sxs-lookup"><span data-stu-id="c351d-234">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="c351d-235">Para tipos de referência não anuláveis, o compilador usa a análise de fluxo para garantir que as variáveis locais sejam inicializadas como um valor não nulo quando declaradas.</span><span class="sxs-lookup"><span data-stu-id="c351d-235">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="c351d-236">Os campos devem ser inicializados durante a construção.</span><span class="sxs-lookup"><span data-stu-id="c351d-236">Fields must be initialized during construction.</span></span> <span data-ttu-id="c351d-237">O compilador gerará um aviso se a variável não for definida por uma chamada para qualquer um dos construtores disponíveis ou por um inicializador.</span><span class="sxs-lookup"><span data-stu-id="c351d-237">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="c351d-238">Além disso, os tipos de referência não anuláveis não podem receber um valor que possa ser nulo.</span><span class="sxs-lookup"><span data-stu-id="c351d-238">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="c351d-239">Os tipos de referência anuláveis não são verificados para garantir que não tenham sido atribuídos ou inicializados como nulos.</span><span class="sxs-lookup"><span data-stu-id="c351d-239">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="c351d-240">No entanto, o compilador usa a análise de fluxo para garantir que qualquer variável de um tipo de referência anulável passe por verificação com relação a um nulo antes de ser acessada ou atribuída a um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="c351d-240">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="c351d-241">Saiba mais sobre o recurso na visão geral sobre [Tipos de referência anuláveis](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-241">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="c351d-242">Experimente-o em um novo aplicativo neste [tutorial de tipos de referência anuláveis](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-242">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="c351d-243">Saiba mais sobre as etapas para migrar uma base de códigos existente para usar tipos de referência anuláveis no [tutorial sobre como migrar um aplicativo para usar tipos de referência anuláveis](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-243">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="c351d-244">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="c351d-244">Asynchronous streams</span></span>

<span data-ttu-id="c351d-245">A partir do C# 8.0, você pode criar e consumir fluxos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="c351d-245">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="c351d-246">Um método que retorna um fluxo assíncrono tem três propriedades:</span><span class="sxs-lookup"><span data-stu-id="c351d-246">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="c351d-247">Ele é declarado com o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="c351d-247">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="c351d-248">Ela retorna um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c351d-248">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="c351d-249">O método contém instruções `yield return` para retornar elementos sucessivos no fluxo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="c351d-249">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="c351d-250">O consumo de um fluxo assíncrono exige que você adicione a palavra-chave `await` antes da palavra-chave `foreach` quando você enumera os elementos do fluxo.</span><span class="sxs-lookup"><span data-stu-id="c351d-250">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="c351d-251">A adição da palavra-chave `await` exige o método que enumera o fluxo assíncrono seja declarado com o modificador `async` e retorne um tipo permitido para um método `async`.</span><span class="sxs-lookup"><span data-stu-id="c351d-251">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="c351d-252">Normalmente, isso significa retornar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c351d-252">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c351d-253">Também pode ser <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="c351d-253">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="c351d-254">Um método pode consumir e produzir um fluxo assíncrono, o que significa que retornaria um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c351d-254">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="c351d-255">O código a seguir gera uma sequência de 0 a 19, esperando 100 ms entre a geração de cada número:</span><span class="sxs-lookup"><span data-stu-id="c351d-255">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="c351d-256">Você enumeraria a sequência usando a instrução `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="c351d-256">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="c351d-257">Experimente você mesmo os fluxos assíncronos em nosso tutorial sobre como [criar e consumir fluxos assíncronos](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-257">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="c351d-258">Por padrão, os elementos de fluxo são processados no contexto capturado.</span><span class="sxs-lookup"><span data-stu-id="c351d-258">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="c351d-259">Se você quiser desabilitar a captura do contexto, use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> método de extensão.</span><span class="sxs-lookup"><span data-stu-id="c351d-259">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="c351d-260">Para obter mais informações sobre contextos de sincronização e como capturar o contexto atual, consulte o artigo sobre como [consumir o padrão assíncrono baseado em tarefa](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-260">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="asynchronous-disposable"></a><span data-ttu-id="c351d-261">Descartável assíncrono</span><span class="sxs-lookup"><span data-stu-id="c351d-261">Asynchronous disposable</span></span>

<span data-ttu-id="c351d-262">A partir do C# 8,0, a linguagem dá suporte a tipos descartáveis <xref:System.IAsyncDisposable?displayProperty=nameWithType> assíncronos que implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="c351d-262">Starting with C# 8.0, the language supports asynchronous disposable types that implement the <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c351d-263">O operando de uma `using` expressão pode implementar um <xref:System.IDisposable> ou <xref:System.IAsyncDisposable>.</span><span class="sxs-lookup"><span data-stu-id="c351d-263">The operand of a `using` expression can implement either <xref:System.IDisposable> or <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="c351d-264">No caso `IAsyncDisposable`do, o compilador gera código `await` para o <xref:System.Threading.Tasks.Task> retornado de. <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c351d-264">In the case of `IAsyncDisposable`, the compiler generates code to `await` the <xref:System.Threading.Tasks.Task> returned from <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c351d-265">Para obter mais informações, consulte a [ `using` instrução](../language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-265">For more information, see the [`using` statement](../language-reference/keywords/using-statement.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="c351d-266">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="c351d-266">Indices and ranges</span></span>

<span data-ttu-id="c351d-267">Índices e intervalos fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="c351d-267">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="c351d-268">Esse suporte a idioma depende de dois novos tipos e de dois novos operadores:</span><span class="sxs-lookup"><span data-stu-id="c351d-268">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="c351d-269"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="c351d-269"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="c351d-270">O índice do operador `^`end, que especifica que um índice é relativo ao final da sequência.</span><span class="sxs-lookup"><span data-stu-id="c351d-270">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="c351d-271"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="c351d-271"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="c351d-272">O operador `..`Range, que especifica o início e o término de um intervalo como seus operandos.</span><span class="sxs-lookup"><span data-stu-id="c351d-272">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="c351d-273">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="c351d-273">Let's start with the rules for indexes.</span></span> <span data-ttu-id="c351d-274">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="c351d-274">Consider an array `sequence`.</span></span> <span data-ttu-id="c351d-275">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="c351d-275">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="c351d-276">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="c351d-276">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="c351d-277">Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz.</span><span class="sxs-lookup"><span data-stu-id="c351d-277">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="c351d-278">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="c351d-278">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="c351d-279">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="c351d-279">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="c351d-280">O início do intervalo é inclusivo, mas o final do intervalo é exclusivo, o que significa que o *início* é incluído no intervalo, mas o *final* não é incluído no intervalo.</span><span class="sxs-lookup"><span data-stu-id="c351d-280">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="c351d-281">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="c351d-281">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="c351d-282">Vamos analisar alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="c351d-282">Let's look at a few examples.</span></span> <span data-ttu-id="c351d-283">Considere a matriz a seguir, anotada com seu índice do início e do final:</span><span class="sxs-lookup"><span data-stu-id="c351d-283">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="c351d-284">Recupere a última palavra com o índice `^1`:</span><span class="sxs-lookup"><span data-stu-id="c351d-284">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="c351d-285">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="c351d-285">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="c351d-286">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="c351d-286">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="c351d-287">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="c351d-287">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="c351d-288">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="c351d-288">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="c351d-289">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="c351d-289">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="c351d-290">O índice `words[^0]` final não está incluído:</span><span class="sxs-lookup"><span data-stu-id="c351d-290">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="c351d-291">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="c351d-291">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="c351d-292">Você também pode declarar intervalos como variáveis:</span><span class="sxs-lookup"><span data-stu-id="c351d-292">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="c351d-293">Em seguida, o intervalo pode ser usado dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="c351d-293">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="c351d-294">Não apenas as matrizes dão suporte a índices e intervalos.</span><span class="sxs-lookup"><span data-stu-id="c351d-294">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="c351d-295">Você também pode usar índices e intervalos com [cadeia](../language-reference/builtin-types/reference-types.md#the-string-type)de <xref:System.Span%601>caracteres, <xref:System.ReadOnlySpan%601>ou.</span><span class="sxs-lookup"><span data-stu-id="c351d-295">You can also use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="c351d-296">Para obter mais informações, consulte [suporte de tipo para índices e intervalos](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="c351d-296">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="c351d-297">Você pode explorar mais sobre índices e intervalos do tutorial sobre [índices e intervalos](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-297">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="c351d-298">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="c351d-298">Null-coalescing assignment</span></span>

<span data-ttu-id="c351d-299">O C# 8,0 apresenta o operador `??=`de atribuição de União nula.</span><span class="sxs-lookup"><span data-stu-id="c351d-299">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="c351d-300">Você pode usar o `??=` operador para atribuir o valor do seu operando à direita para seu operando à esquerda somente se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="c351d-300">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="c351d-301">Para obter mais informações, consulte [?? e?? =](../language-reference/operators/null-coalescing-operator.md) artigo de operadores.</span><span class="sxs-lookup"><span data-stu-id="c351d-301">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="c351d-302">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="c351d-302">Unmanaged constructed types</span></span>

<span data-ttu-id="c351d-303">No C# 7,3 e anterior, um tipo construído (um tipo que inclui pelo menos um argumento de tipo) não pode ser um [tipo não gerenciado](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-303">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="c351d-304">A partir do C# 8,0, um tipo de valor construído não será gerenciado se ele contiver campos apenas de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c351d-304">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="c351d-305">Por exemplo, dada a seguinte definição do tipo genérico `Coords<T>` :</span><span class="sxs-lookup"><span data-stu-id="c351d-305">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="c351d-306">o `Coords<int>` tipo é um tipo não gerenciado em C# 8,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="c351d-306">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="c351d-307">Como para qualquer tipo não gerenciado, você pode criar um ponteiro para uma variável desse tipo ou [alocar um bloco de memória na pilha](../language-reference/operators/stackalloc.md) para instâncias desse tipo:</span><span class="sxs-lookup"><span data-stu-id="c351d-307">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="c351d-308">Para obter mais informações, consulte [tipos não gerenciados](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="c351d-308">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="c351d-309">Stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="c351d-309">Stackalloc in nested expressions</span></span>

<span data-ttu-id="c351d-310">A partir do C# 8,0, se o resultado de uma expressão [stackalloc](../language-reference/operators/stackalloc.md) for do <xref:System.Span%601?displayProperty=nameWithType> tipo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> ou, você poderá usar a `stackalloc` expressão em outras expressões:</span><span class="sxs-lookup"><span data-stu-id="c351d-310">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="c351d-311">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="c351d-311">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="c351d-312">`$` A ordem dos tokens `@` e nas cadeias de caracteres idênticas [interpoladas](../language-reference/tokens/interpolated.md) pode ser any: `$@"..."` e `@$"..."` são cadeias de caracteres idênticas interpoladas válidas.</span><span class="sxs-lookup"><span data-stu-id="c351d-312">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="c351d-313">Em versões anteriores do C#, `$` o token deve aparecer antes `@` do token.</span><span class="sxs-lookup"><span data-stu-id="c351d-313">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
