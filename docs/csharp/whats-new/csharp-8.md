---
title: O que há de C# novo no C# guia de 8,0
description: Obtenha uma visão geral dos novos recursos disponíveis no C# 8.0.
ms.date: 09/20/2019
ms.openlocfilehash: 335ae37b20f752f4181a4d1828cb2a1f02c0fa9e
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798925"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="dc0e4-103">Novidades no C# 8.0</span><span class="sxs-lookup"><span data-stu-id="dc0e4-103">What's new in C# 8.0</span></span>

<span data-ttu-id="dc0e4-104">C#8,0 adiciona os seguintes recursos e aprimoramentos ao C# Idioma:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="dc0e4-105">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="dc0e4-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="dc0e4-106">Métodos de interface padrão</span><span class="sxs-lookup"><span data-stu-id="dc0e4-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="dc0e4-107">[Aprimoramentos de correspondência de padrões](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="dc0e4-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="dc0e4-108">Expressões Switch</span><span class="sxs-lookup"><span data-stu-id="dc0e4-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="dc0e4-109">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="dc0e4-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="dc0e4-110">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="dc0e4-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="dc0e4-111">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="dc0e4-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="dc0e4-112">Declarações using</span><span class="sxs-lookup"><span data-stu-id="dc0e4-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="dc0e4-113">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="dc0e4-114">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="dc0e4-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="dc0e4-115">Tipos de referência nula</span><span class="sxs-lookup"><span data-stu-id="dc0e4-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="dc0e4-116">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="dc0e4-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="dc0e4-117">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="dc0e4-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="dc0e4-118">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="dc0e4-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="dc0e4-119">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="dc0e4-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="dc0e4-120">Stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="dc0e4-121">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="dc0e4-122">O restante deste artigo descreve rapidamente esses recursos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-122">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="dc0e4-123">Quando houver artigos detalhados disponíveis, forneceremos links para esses tutoriais e visões gerais.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-123">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="dc0e4-124">Você pode explorar esses recursos em seu ambiente usando a ferramenta global `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="dc0e4-125">Instale a ferramenta global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="dc0e4-126">Clone o repositório [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="dc0e4-127">Defina o diretório atual do subdiretório *csharp8* para o repositório *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-127">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="dc0e4-128">Execute `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-128">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="dc0e4-129">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="dc0e4-129">Readonly members</span></span>

<span data-ttu-id="dc0e4-130">É possível aplicar o modificador `readonly` a qualquer membro de um struct.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-130">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="dc0e4-131">Ele indica que o membro não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-131">It indicates that the member does not modify state.</span></span> <span data-ttu-id="dc0e4-132">É mais granular do que aplicar o modificador `readonly` a uma declaração `struct`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-132">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="dc0e4-133">Considere o seguinte struct mutável:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-133">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="dc0e4-134">Como a maioria dos structs, o método `ToString()` não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-134">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="dc0e4-135">É possível indicar isso adicionando o modificador `readonly` à declaração de `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-135">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="dc0e4-136">A alteração anterior gera um aviso do compilador, porque o `ToString` acessa a propriedade `Distance`, que não está marcada como `readonly`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-136">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="dc0e4-137">O compilador avisa quando há a necessidade de criar uma cópia de defesa.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-137">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="dc0e4-138">A propriedade `Distance` não altera o estado, portanto, é possível corrigir esse aviso adicionando o modificador `readonly` à declaração:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-138">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="dc0e4-139">Observe que o modificador `readonly` é necessário em uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-139">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="dc0e4-140">O compilador não pressupõe que os acessadores `get` não modificam o estado; é necessário declarar `readonly` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-140">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="dc0e4-141">As propriedades implementadas automaticamente são uma exceção; o compilador tratará todos os getters autoimplementados como ReadOnly, portanto, aqui não há necessidade de adicionar o modificador `readonly` às propriedades `X` e `Y`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-141">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there is no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="dc0e4-142">O compilador impõe como regra que membros `readonly` não modificam o estado.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-142">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="dc0e4-143">O método a seguir não será compilado, a menos que você remova o modificador `readonly`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-143">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="dc0e4-144">Esse recurso permite que você especifique sua intenção de design para que o compilador possa impô-la e faça otimizações com base nessa intenção.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-144">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="dc0e4-145">Métodos de interface padrão</span><span class="sxs-lookup"><span data-stu-id="dc0e4-145">Default interface methods</span></span>

<span data-ttu-id="dc0e4-146">Agora é possível adicionar membros a interfaces e fornecer uma implementação para esses membros.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-146">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="dc0e4-147">Esse recurso de linguagem permite que os autores de API adicionem métodos a uma interface em versões posteriores sem interromper a fonte ou a compatibilidade binária com implementações existentes dessa interface.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-147">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="dc0e4-148">As implementações existentes *herdam* a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-148">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="dc0e4-149">Esse recurso também permite que o C# interopere com APIs que direcionam o Android ou o Swift, que dão suporte a recursos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-149">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="dc0e4-150">Os métodos de interface padrão também habilitam cenários semelhantes a um recurso de linguagem de "características".</span><span class="sxs-lookup"><span data-stu-id="dc0e4-150">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="dc0e4-151">Os métodos de interface padrão afetam muitos cenários e elementos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-151">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="dc0e4-152">Nosso primeiro tutorial aborda [como atualizar uma interface com implementações padrão](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-152">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="dc0e4-153">Outros tutoriais e atualizações de referência chegarão a tempo para a versão geral.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-153">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="dc0e4-154">Mais padrões em mais partes</span><span class="sxs-lookup"><span data-stu-id="dc0e4-154">More patterns in more places</span></span>

<span data-ttu-id="dc0e4-155">Com a **correspondência de padrões**, você recebe ferramentas para fornecer funcionalidades dependentes da forma em tipos de dados relacionados, mas diferentes.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-155">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="dc0e4-156">O C# 7.0 introduziu uma sintaxe para padrões de tipo e padrões de constante usando a expressão [`is`](../language-reference/keywords/is.md) e a instrução [`switch`](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-156">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="dc0e4-157">Esses recursos representaram os primeiros passos em direção ao suporte a paradigmas de programação, em que os dados e a funcionalidade vivem separados.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-157">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="dc0e4-158">À medida que o setor se aproxima mais de microsserviços e de outras arquiteturas baseadas em nuvem, outras ferramentas de linguagem de tornam necessárias.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-158">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="dc0e4-159">O C# 8.0 expande esse vocabulário, para que você possa usar mais expressões de padrão em mais partes do seu código.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-159">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="dc0e4-160">Considere esses recursos quando seus dados e funcionalidades estiverem separados.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-160">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="dc0e4-161">Considere a correspondência de padrões quando seus algoritmos dependerem de um fato diferente do tipo de tempo de execução de um objeto.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-161">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="dc0e4-162">Essas técnicas fornecem outra maneira de expressar designs.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-162">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="dc0e4-163">Além dos novos padrões em novas partes, o C# 8.0 adiciona **padrões recursivos**.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-163">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="dc0e4-164">O resultado de qualquer expressão padrão é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-164">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="dc0e4-165">Um padrão recursivo é simplesmente uma expressão padrão aplicada à saída de outra expressão padrão.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-165">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="dc0e4-166">Expressões switch</span><span class="sxs-lookup"><span data-stu-id="dc0e4-166">Switch expressions</span></span>

<span data-ttu-id="dc0e4-167">Frequentemente, uma instrução [`switch`](../language-reference/keywords/switch.md) produz um valor em cada um de seus blocos `case`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-167">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="dc0e4-168">As **expressões switch** permitem que você use a sintaxe de expressão mais concisa.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-168">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="dc0e4-169">Há menos palavras-chave `case` e `break` repetidas, e menos chaves.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-169">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="dc0e4-170">Por exemplo, considere a enumeração a seguir que lista as cores do arco-íris:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-170">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="dc0e4-171">Se seu aplicativo definiu um tipo `RGBColor` que é construído a partir dos componentes `R`, `G` e `B`, você poderia converter um valor `Rainbow` em seus valores RGB usando o método a seguir que contém uma expressão de opção:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-171">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="dc0e4-172">Há vários aprimoramentos de sintaxe aqui:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-172">There are several syntax improvements here:</span></span>

- <span data-ttu-id="dc0e4-173">A variável vem antes da palavra-chave `switch`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-173">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="dc0e4-174">A ordem diferente facilita distinguir visualmente a expressão switch da instrução switch.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-174">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="dc0e4-175">Os elementos `case` e `:` são substituídos por `=>`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-175">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="dc0e4-176">É mais conciso e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-176">It's more concise and intuitive.</span></span>
- <span data-ttu-id="dc0e4-177">O caso `default` é substituído por um descarte `_`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-177">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="dc0e4-178">Os corpos são expressões, não instruções.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-178">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="dc0e4-179">Compare isso com o código equivalente usando a instrução clássica `switch`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-179">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="dc0e4-180">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="dc0e4-180">Property patterns</span></span>

<span data-ttu-id="dc0e4-181">O **padrão da propriedade** permite que você compare as propriedades do objeto examinado.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-181">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="dc0e4-182">Considere um site de comércio eletrônico que deve calcular o imposto da venda com base no endereço do comprador.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-182">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="dc0e4-183">Esse cálculo não é uma responsabilidade principal de uma classe `Address`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-183">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="dc0e4-184">Ele mudará ao longo do tempo, provavelmente com mais frequência do que as alterações de formato de endereço.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-184">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="dc0e4-185">O valor do imposto depende da propriedade `State` do endereço.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-185">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="dc0e4-186">O método a seguir usa o padrão de propriedade para calcular o imposto da venda de acordo com o endereço e o preço:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-186">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="dc0e4-187">A correspondência de padrão cria uma sintaxe concisa para expressar esse algoritmo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-187">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="dc0e4-188">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="dc0e4-188">Tuple patterns</span></span>

<span data-ttu-id="dc0e4-189">Alguns algoritmos dependem de várias entradas.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-189">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="dc0e4-190">**Padrões de tupla** permitem que você alterne com base em vários valores, expressadas como uma [tupla](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-190">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="dc0e4-191">O código a seguir mostra uma expressão de comutador para o jogo *pedra, papel, tesoura*:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-191">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="dc0e4-192">As mensagens indicam o vencedor.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-192">The messages indicate the winner.</span></span> <span data-ttu-id="dc0e4-193">O caso de descarte representa três combinações para empates ou outras entradas de texto.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-193">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="dc0e4-194">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="dc0e4-194">Positional patterns</span></span>

<span data-ttu-id="dc0e4-195">Alguns tipos incluem um método `Deconstruct` que desconstrói suas propriedades em variáveis discretas.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-195">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="dc0e4-196">Quando um método `Deconstruct` é acessível, você pode usar **padrões posicionais** para inspecionar as propriedades do objeto e usar essas propriedades para um padrão.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-196">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="dc0e4-197">Considere a seguinte classe `Point`, que inclui um método `Deconstruct` para criar variáveis discretas para `X` e `Y`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-197">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="dc0e4-198">Além disso, considere a seguinte enumeração que representa várias posições de um quadrante:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-198">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="dc0e4-199">O método a seguir usa o **padrão posicional** para extrair os valores de `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-199">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="dc0e4-200">Em seguida, ele usa uma cláusula `when` para determinar o `Quadrant` do ponto:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-200">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="dc0e4-201">O padrão de discard na opção anterior encontra a correspondência quando `x` ou `y` é 0, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-201">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="dc0e4-202">Uma expressão switch deve produzir um valor ou lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-202">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="dc0e4-203">Se não houver correspondência em nenhum dos casos, a expressão switch gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-203">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="dc0e4-204">O compilador gerará um aviso se você não cobrir todos os casos possíveis em sua expressão switch.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-204">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="dc0e4-205">Explore técnicas de correspondência de padrões neste [tutorial avançado sobre correspondência de padrões](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-205">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="dc0e4-206">Declarações using</span><span class="sxs-lookup"><span data-stu-id="dc0e4-206">Using declarations</span></span>

<span data-ttu-id="dc0e4-207">Uma **declaração using** é uma declaração de variável precedida pela palavra-chave `using`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-207">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="dc0e4-208">Ele informa ao compilador que a variável que está sendo declarada deve ser descartada ao final do escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-208">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="dc0e4-209">Por exemplo, considere o seguinte código que grava um arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-209">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="dc0e4-210">No exemplo anterior, o arquivo é descartado quando a chave de fechamento do método é atingida.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-210">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="dc0e4-211">Esse é o final do escopo no qual `file` é declarado.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-211">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="dc0e4-212">O código anterior equivale ao código a seguir que usa as [instruções using](../language-reference/keywords/using-statement.md) clássicas:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-212">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="dc0e4-213">No exemplo anterior, o arquivo é descartado quando a chave de fechamento associada à instrução `using` é atingida.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-213">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="dc0e4-214">Em ambos os casos, o compilador gera a chamada para `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-214">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="dc0e4-215">O compilador gera um erro se a expressão na instrução `using` não for descartável.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-215">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="dc0e4-216">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-216">Static local functions</span></span>

<span data-ttu-id="dc0e4-217">Agora você pode adicionar o modificador `static` para funções locais a fim de garantir que essa função local não capture (faça referência) às variáveis no escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-217">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="dc0e4-218">Essa ação gera `CS8421`, "Uma função local estática não pode conter uma referência à \<variable>".</span><span class="sxs-lookup"><span data-stu-id="dc0e4-218">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="dc0e4-219">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-219">Consider the following code.</span></span> <span data-ttu-id="dc0e4-220">A função local `LocalFunction` acessa a variável `y`, declarada no escopo delimitador (o método `M`).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-220">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="dc0e4-221">Portanto, `LocalFunction` não pode ser declarada com o modificador `static`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-221">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="dc0e4-222">O código a seguir contém uma função local estática.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-222">The following code contains a static local function.</span></span> <span data-ttu-id="dc0e4-223">Ela pode ser estática porque não acesse as variáveis no escopo delimitador:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-223">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="dc0e4-224">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="dc0e4-224">Disposable ref structs</span></span>

<span data-ttu-id="dc0e4-225">Uma `struct` declarada com o modificador `ref` não pode implementar quaisquer interfaces e, portanto, não pode implementar <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-225">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="dc0e4-226">Portanto, para permitir que uma `ref struct` seja descartada, ela deve ter um método `void Dispose()` acessível.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-226">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="dc0e4-227">Isso também se aplica às declarações `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-227">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="dc0e4-228">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="dc0e4-228">Nullable reference types</span></span>

<span data-ttu-id="dc0e4-229">Dentro de um contexto de anotação anulável, qualquer variável de um tipo de referência é considerado um **tipo de referência não anulável**.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-229">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="dc0e4-230">Se você quiser indicar que uma variável pode ser nula, acrescente o nome do tipo com o `?` para declarar a variável como um **tipo de referência anulável**.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-230">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="dc0e4-231">Para tipos de referência não anuláveis, o compilador usa a análise de fluxo para garantir que as variáveis locais sejam inicializadas como um valor não nulo quando declaradas.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-231">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="dc0e4-232">Os campos devem ser inicializados durante a construção.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-232">Fields must be initialized during construction.</span></span> <span data-ttu-id="dc0e4-233">O compilador gera um aviso se a variável não for definida por uma chamada para qualquer um dos construtores disponíveis ou por um inicializador.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-233">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="dc0e4-234">Além disso, os tipos de referência não anuláveis não podem receber um valor que possa ser nulo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-234">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="dc0e4-235">Os tipos de referência anuláveis não são verificados para garantir que não tenham sido atribuídos ou inicializados como nulos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-235">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="dc0e4-236">No entanto, o compilador usa a análise de fluxo para garantir que qualquer variável de um tipo de referência anulável passe por verificação com relação a um nulo antes de ser acessada ou atribuída a um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-236">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="dc0e4-237">Saiba mais sobre o recurso na visão geral sobre [Tipos de referência anuláveis](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-237">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="dc0e4-238">Experimente-o em um novo aplicativo neste [tutorial de tipos de referência anuláveis](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-238">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="dc0e4-239">Saiba mais sobre as etapas para migrar uma base de códigos existente para usar tipos de referência anuláveis no [tutorial sobre como migrar um aplicativo para usar tipos de referência anuláveis](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-239">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="dc0e4-240">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="dc0e4-240">Asynchronous streams</span></span>

<span data-ttu-id="dc0e4-241">A partir do C# 8.0, você pode criar e consumir fluxos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-241">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="dc0e4-242">Um método que retorna um fluxo assíncrono tem três propriedades:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-242">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="dc0e4-243">Ele é declarado com o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-243">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="dc0e4-244">Ela retorna um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-244">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="dc0e4-245">O método contém instruções `yield return` para retornar elementos sucessivos no fluxo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-245">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="dc0e4-246">O consumo de um fluxo assíncrono exige que você adicione a palavra-chave `await` antes da palavra-chave `foreach` quando você enumera os elementos do fluxo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-246">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="dc0e4-247">A adição da palavra-chave `await` exige o método que enumera o fluxo assíncrono seja declarado com o modificador `async` e retorne um tipo permitido para um método `async`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-247">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="dc0e4-248">Normalmente, isso significa retornar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-248">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="dc0e4-249">Também pode ser <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-249">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="dc0e4-250">Um método pode consumir e produzir um fluxo assíncrono, o que significa que retornaria um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-250">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="dc0e4-251">O código a seguir gera uma sequência de 0 a 19, esperando 100 ms entre a geração de cada número:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-251">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="dc0e4-252">Você enumeraria a sequência usando a instrução `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-252">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="dc0e4-253">Experimente você mesmo os fluxos assíncronos em nosso tutorial sobre como [criar e consumir fluxos assíncronos](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-253">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="dc0e4-254">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="dc0e4-254">Indices and ranges</span></span>

<span data-ttu-id="dc0e4-255">Índices e intervalos fornecem uma sintaxe sucinta para acessar elementos únicos ou intervalos em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-255">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="dc0e4-256">Esse suporte a idioma depende de dois novos tipos e de dois novos operadores:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-256">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="dc0e4-257"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-257"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="dc0e4-258">O índice do operador end `^`, que especifica que um índice é relativo ao final da sequência.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-258">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="dc0e4-259"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-259"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="dc0e4-260">O operador Range `..`, que especifica o início e o término de um intervalo como seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-260">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="dc0e4-261">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-261">Let's start with the rules for indexes.</span></span> <span data-ttu-id="dc0e4-262">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-262">Consider an array `sequence`.</span></span> <span data-ttu-id="dc0e4-263">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-263">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="dc0e4-264">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-264">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="dc0e4-265">Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-265">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="dc0e4-266">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-266">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="dc0e4-267">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-267">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="dc0e4-268">O início do intervalo é inclusivo, mas o final do intervalo é exclusivo, o que significa que o *início* está incluído no intervalo, mas o *final* não está incluído no intervalo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-268">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="dc0e4-269">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-269">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="dc0e4-270">Vamos analisar alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-270">Let's look at a few examples.</span></span> <span data-ttu-id="dc0e4-271">Considere a matriz a seguir, anotada com seu índice do início e do final:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-271">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="dc0e4-272">Recupere a última palavra com o índice `^1`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-272">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="dc0e4-273">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="dc0e4-273">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="dc0e4-274">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-274">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="dc0e4-275">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-275">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="dc0e4-276">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="dc0e4-276">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="dc0e4-277">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-277">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="dc0e4-278">O índice final `words[^0]` não está incluído:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-278">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="dc0e4-279">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-279">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="dc0e4-280">Você também pode declarar intervalos como variáveis:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-280">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="dc0e4-281">Em seguida, o intervalo pode ser usado dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-281">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="dc0e4-282">Não apenas as matrizes dão suporte a índices e intervalos.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-282">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="dc0e4-283">Você também pode usar índices e intervalos com [cadeia de caracteres](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-283">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="dc0e4-284">Para obter mais informações, consulte [suporte de tipo para índices e intervalos](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-284">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="dc0e4-285">Você pode explorar mais sobre índices e intervalos do tutorial sobre [índices e intervalos](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-285">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="dc0e4-286">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="dc0e4-286">Null-coalescing assignment</span></span>

<span data-ttu-id="dc0e4-287">C#8,0 apresenta o operador de atribuição de União nula `??=`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-287">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="dc0e4-288">Você pode usar o operador `??=` para atribuir o valor do seu operando à direita para seu operando à esquerda somente se o operando esquerdo for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-288">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="dc0e4-289">Para obter mais informações, consulte [?? e?? =](../language-reference/operators/null-coalescing-operator.md) artigo de operadores.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-289">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="dc0e4-290">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="dc0e4-290">Unmanaged constructed types</span></span>

<span data-ttu-id="dc0e4-291">No C# 7,3 e anterior, um tipo construído (um tipo que inclui pelo menos um argumento de tipo) não pode ser um [tipo não gerenciado](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-291">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) cannot be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="dc0e4-292">A partir C# de 8,0, um tipo de valor construído não será gerenciado se ele contiver campos apenas de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-292">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="dc0e4-293">Por exemplo, considerando a seguinte definição do tipo de `Coords<T>` genérico:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-293">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="dc0e4-294">o tipo de `Coords<int>` é um tipo não gerenciado em C# 8,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-294">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="dc0e4-295">Como para qualquer tipo não gerenciado, você pode criar um ponteiro para uma variável desse tipo ou [alocar um bloco de memória na pilha](../language-reference/operators/stackalloc.md) para instâncias desse tipo:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-295">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="dc0e4-296">Para obter mais informações, consulte [tipos não gerenciados](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="dc0e4-296">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="dc0e4-297">stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-297">Stackalloc in nested expressions</span></span>

<span data-ttu-id="dc0e4-298">A partir C# de 8,0, se o resultado de uma expressão [stackalloc](../language-reference/operators/stackalloc.md) for do tipo<xref:System.Span%601?displayProperty=nameWithType>ou<xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, você poderá usar a expressão`stackalloc`em outras expressões:</span><span class="sxs-lookup"><span data-stu-id="dc0e4-298">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="dc0e4-299">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="dc0e4-299">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="dc0e4-300">A ordem dos tokens de `$` e `@` em cadeias de caracteres idênticas [interpoladas](../language-reference/tokens/interpolated.md) pode ser qualquer: `$@"..."` e `@$"..."` são cadeias de caracteres textuais interpoladas válidas.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-300">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="dc0e4-301">Em versões C# anteriores, o token de `$` deve aparecer antes do token de `@`.</span><span class="sxs-lookup"><span data-stu-id="dc0e4-301">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
