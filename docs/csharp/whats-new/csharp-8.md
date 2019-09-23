---
title: Novidades no C# 8.0 – Guia do C#
description: Obtenha uma visão geral dos novos recursos disponíveis no C# 8.0. Este artigo está atualizado com a versão prévia 5.
ms.date: 09/20/2019
ms.openlocfilehash: a434d1f7598bc3f6787f7466e48fb161db192761
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182403"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="b4698-104">Novidades no C# 8.0</span><span class="sxs-lookup"><span data-stu-id="b4698-104">What's new in C# 8.0</span></span>

<span data-ttu-id="b4698-105">Há vários aprimoramentos da linguagem C# que você já pode experimentar.</span><span class="sxs-lookup"><span data-stu-id="b4698-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="b4698-106">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4698-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="b4698-107">Membros da interface padrão</span><span class="sxs-lookup"><span data-stu-id="b4698-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="b4698-108">[Aprimoramentos de correspondência de padrões](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="b4698-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="b4698-109">Expressões Switch</span><span class="sxs-lookup"><span data-stu-id="b4698-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="b4698-110">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="b4698-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="b4698-111">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="b4698-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="b4698-112">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="b4698-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="b4698-113">Declarações using</span><span class="sxs-lookup"><span data-stu-id="b4698-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="b4698-114">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="b4698-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="b4698-115">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="b4698-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="b4698-116">Tipos de referência nula</span><span class="sxs-lookup"><span data-stu-id="b4698-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="b4698-117">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="b4698-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="b4698-118">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="b4698-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="b4698-119">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="b4698-119">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="b4698-120">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="b4698-120">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="b4698-121">stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="b4698-121">stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="b4698-122">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="b4698-122">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="b4698-123">Este artigo foi atualizado pela última vez para o C# 8.0 versão prévia 5.</span><span class="sxs-lookup"><span data-stu-id="b4698-123">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="b4698-124">O restante deste artigo descreve rapidamente esses recursos.</span><span class="sxs-lookup"><span data-stu-id="b4698-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="b4698-125">Quando houver artigos detalhados disponíveis, forneceremos links para esses tutoriais e visões gerais.</span><span class="sxs-lookup"><span data-stu-id="b4698-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="b4698-126">Você pode explorar esses recursos em seu ambiente usando a ferramenta global `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="b4698-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="b4698-127">Instale a ferramenta global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="b4698-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="b4698-128">Clone o repositório [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="b4698-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="b4698-129">Defina o diretório atual do subdiretório *csharp8* para o repositório *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="b4698-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="b4698-130">Execute `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="b4698-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="b4698-131">Membros somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4698-131">Readonly members</span></span>

<span data-ttu-id="b4698-132">É possível aplicar o modificador `readonly` a qualquer membro de um struct.</span><span class="sxs-lookup"><span data-stu-id="b4698-132">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="b4698-133">Ele indica que o membro não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="b4698-133">It indicates that the member does not modify state.</span></span> <span data-ttu-id="b4698-134">É mais granular do que aplicar o modificador `readonly` a uma declaração `struct`.</span><span class="sxs-lookup"><span data-stu-id="b4698-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="b4698-135">Considere o seguinte struct mutável:</span><span class="sxs-lookup"><span data-stu-id="b4698-135">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="b4698-136">Como a maioria dos structs, o método `ToString()` não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="b4698-136">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="b4698-137">É possível indicar isso adicionando o modificador `readonly` à declaração de `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="b4698-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="b4698-138">A alteração anterior gera um aviso do compilador, porque o `ToString` acessa a propriedade `Distance`, que não está marcada como `readonly`:</span><span class="sxs-lookup"><span data-stu-id="b4698-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="b4698-139">O compilador avisa quando há a necessidade de criar uma cópia de defesa.</span><span class="sxs-lookup"><span data-stu-id="b4698-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="b4698-140">A propriedade `Distance` não altera o estado, portanto, é possível corrigir esse aviso adicionando o modificador `readonly` à declaração:</span><span class="sxs-lookup"><span data-stu-id="b4698-140">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="b4698-141">Observe que o modificador `readonly` é necessário em uma propriedade somente leitura.</span><span class="sxs-lookup"><span data-stu-id="b4698-141">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="b4698-142">O compilador não pressupõe que os acessadores `get` não modificam o estado; é necessário declarar `readonly` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="b4698-142">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="b4698-143">O compilador impõe como regra que membros `readonly` não modificam o estado.</span><span class="sxs-lookup"><span data-stu-id="b4698-143">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="b4698-144">O método a seguir não será compilado, a menos que você remova o modificador `readonly`:</span><span class="sxs-lookup"><span data-stu-id="b4698-144">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="b4698-145">Esse recurso permite que você especifique sua intenção de design para que o compilador possa impô-la e faça otimizações com base nessa intenção.</span><span class="sxs-lookup"><span data-stu-id="b4698-145">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="b4698-146">Membros da interface padrão</span><span class="sxs-lookup"><span data-stu-id="b4698-146">Default interface members</span></span>

<span data-ttu-id="b4698-147">Agora é possível adicionar membros a interfaces e fornecer uma implementação para esses membros.</span><span class="sxs-lookup"><span data-stu-id="b4698-147">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="b4698-148">Esse recurso de linguagem permite que os autores de API adicionem métodos a uma interface em versões posteriores sem interromper a fonte ou a compatibilidade binária com implementações existentes dessa interface.</span><span class="sxs-lookup"><span data-stu-id="b4698-148">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="b4698-149">As implementações existentes *herdam* a implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="b4698-149">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="b4698-150">Esse recurso também permite que o C# interopere com APIs que direcionam o Android ou o Swift, que dão suporte a recursos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="b4698-150">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="b4698-151">Membros da interface padrão também permitem cenários semelhantes a um recurso de linguagem de “características”.</span><span class="sxs-lookup"><span data-stu-id="b4698-151">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="b4698-152">Os membros da interface padrão afetam muitos cenários e elementos de linguagem.</span><span class="sxs-lookup"><span data-stu-id="b4698-152">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="b4698-153">Nosso primeiro tutorial aborda [como atualizar uma interface com implementações padrão](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-153">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="b4698-154">Outros tutoriais e atualizações de referência chegarão a tempo para a versão geral.</span><span class="sxs-lookup"><span data-stu-id="b4698-154">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="b4698-155">Mais padrões em mais partes</span><span class="sxs-lookup"><span data-stu-id="b4698-155">More patterns in more places</span></span>

<span data-ttu-id="b4698-156">Com a **correspondência de padrões**, você recebe ferramentas para fornecer funcionalidades dependentes da forma em tipos de dados relacionados, mas diferentes.</span><span class="sxs-lookup"><span data-stu-id="b4698-156">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="b4698-157">O C# 7.0 introduziu uma sintaxe para padrões de tipo e padrões de constante usando a expressão [`is`](../language-reference/keywords/is.md) e a instrução [`switch`](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-157">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="b4698-158">Esses recursos representaram os primeiros passos em direção ao suporte a paradigmas de programação, em que os dados e a funcionalidade vivem separados.</span><span class="sxs-lookup"><span data-stu-id="b4698-158">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="b4698-159">À medida que o setor se aproxima mais de microsserviços e de outras arquiteturas baseadas em nuvem, outras ferramentas de linguagem de tornam necessárias.</span><span class="sxs-lookup"><span data-stu-id="b4698-159">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="b4698-160">O C# 8.0 expande esse vocabulário, para que você possa usar mais expressões de padrão em mais partes do seu código.</span><span class="sxs-lookup"><span data-stu-id="b4698-160">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="b4698-161">Considere esses recursos quando seus dados e funcionalidades estiverem separados.</span><span class="sxs-lookup"><span data-stu-id="b4698-161">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="b4698-162">Considere a correspondência de padrões quando seus algoritmos dependerem de um fato diferente do tipo de tempo de execução de um objeto.</span><span class="sxs-lookup"><span data-stu-id="b4698-162">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="b4698-163">Essas técnicas fornecem outra maneira de expressar designs.</span><span class="sxs-lookup"><span data-stu-id="b4698-163">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="b4698-164">Além dos novos padrões em novas partes, o C# 8.0 adiciona **padrões recursivos**.</span><span class="sxs-lookup"><span data-stu-id="b4698-164">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="b4698-165">O resultado de qualquer expressão padrão é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="b4698-165">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="b4698-166">Um padrão recursivo é simplesmente uma expressão padrão aplicada à saída de outra expressão padrão.</span><span class="sxs-lookup"><span data-stu-id="b4698-166">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="b4698-167">Expressões switch</span><span class="sxs-lookup"><span data-stu-id="b4698-167">switch expressions</span></span>

<span data-ttu-id="b4698-168">Frequentemente, uma instrução [`switch`](../language-reference/keywords/switch.md) produz um valor em cada um de seus blocos `case`.</span><span class="sxs-lookup"><span data-stu-id="b4698-168">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="b4698-169">As **expressões switch** permitem que você use a sintaxe de expressão mais concisa.</span><span class="sxs-lookup"><span data-stu-id="b4698-169">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="b4698-170">Há menos palavras-chave `case` e `break` repetidas, e menos chaves.</span><span class="sxs-lookup"><span data-stu-id="b4698-170">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="b4698-171">Por exemplo, considere a enumeração a seguir que lista as cores do arco-íris:</span><span class="sxs-lookup"><span data-stu-id="b4698-171">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="b4698-172">Se seu aplicativo definiu um tipo `RGBColor` que é construído a partir dos componentes `R`, `G` e `B`, você poderia converter um valor `Rainbow` em seus valores RGB usando o método a seguir que contém uma expressão de opção:</span><span class="sxs-lookup"><span data-stu-id="b4698-172">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="b4698-173">Há vários aprimoramentos de sintaxe aqui:</span><span class="sxs-lookup"><span data-stu-id="b4698-173">There are several syntax improvements here:</span></span>

- <span data-ttu-id="b4698-174">A variável vem antes da palavra-chave `switch`.</span><span class="sxs-lookup"><span data-stu-id="b4698-174">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="b4698-175">A ordem diferente facilita distinguir visualmente a expressão switch da instrução switch.</span><span class="sxs-lookup"><span data-stu-id="b4698-175">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="b4698-176">Os elementos `case` e `:` são substituídos por `=>`.</span><span class="sxs-lookup"><span data-stu-id="b4698-176">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="b4698-177">É mais conciso e intuitivo.</span><span class="sxs-lookup"><span data-stu-id="b4698-177">It's more concise and intuitive.</span></span>
- <span data-ttu-id="b4698-178">O caso `default` é substituído por um descarte `_`.</span><span class="sxs-lookup"><span data-stu-id="b4698-178">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="b4698-179">Os corpos são expressões, não instruções.</span><span class="sxs-lookup"><span data-stu-id="b4698-179">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="b4698-180">Compare isso com o código equivalente usando a instrução clássica `switch`:</span><span class="sxs-lookup"><span data-stu-id="b4698-180">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="b4698-181">Padrões da propriedade</span><span class="sxs-lookup"><span data-stu-id="b4698-181">Property patterns</span></span>

<span data-ttu-id="b4698-182">O **padrão da propriedade** permite que você compare as propriedades do objeto examinado.</span><span class="sxs-lookup"><span data-stu-id="b4698-182">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="b4698-183">Considere um site de comércio eletrônico que deve calcular o imposto da venda com base no endereço do comprador.</span><span class="sxs-lookup"><span data-stu-id="b4698-183">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="b4698-184">Esse cálculo não é uma responsabilidade principal de uma classe `Address`.</span><span class="sxs-lookup"><span data-stu-id="b4698-184">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="b4698-185">Ele mudará ao longo do tempo, provavelmente com mais frequência do que as alterações de formato de endereço.</span><span class="sxs-lookup"><span data-stu-id="b4698-185">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="b4698-186">O valor do imposto depende da propriedade `State` do endereço.</span><span class="sxs-lookup"><span data-stu-id="b4698-186">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="b4698-187">O método a seguir usa o padrão de propriedade para calcular o imposto da venda de acordo com o endereço e o preço:</span><span class="sxs-lookup"><span data-stu-id="b4698-187">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="b4698-188">A correspondência de padrão cria uma sintaxe concisa para expressar esse algoritmo.</span><span class="sxs-lookup"><span data-stu-id="b4698-188">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="b4698-189">Padrões de tupla</span><span class="sxs-lookup"><span data-stu-id="b4698-189">Tuple patterns</span></span>

<span data-ttu-id="b4698-190">Alguns algoritmos dependem de várias entradas.</span><span class="sxs-lookup"><span data-stu-id="b4698-190">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="b4698-191">**Padrões de tupla** permitem que você alterne com base em vários valores, expressadas como uma [tupla](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-191">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="b4698-192">O código a seguir mostra uma expressão de comutador para o jogo *pedra, papel, tesoura*:</span><span class="sxs-lookup"><span data-stu-id="b4698-192">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="b4698-193">As mensagens indicam o vencedor.</span><span class="sxs-lookup"><span data-stu-id="b4698-193">The messages indicate the winner.</span></span> <span data-ttu-id="b4698-194">O caso de descarte representa três combinações para empates ou outras entradas de texto.</span><span class="sxs-lookup"><span data-stu-id="b4698-194">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="b4698-195">Padrões posicionais</span><span class="sxs-lookup"><span data-stu-id="b4698-195">Positional patterns</span></span>

<span data-ttu-id="b4698-196">Alguns tipos incluem um método `Deconstruct` que desconstrói suas propriedades em variáveis discretas.</span><span class="sxs-lookup"><span data-stu-id="b4698-196">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="b4698-197">Quando um método `Deconstruct` é acessível, você pode usar **padrões posicionais** para inspecionar as propriedades do objeto e usar essas propriedades para um padrão.</span><span class="sxs-lookup"><span data-stu-id="b4698-197">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="b4698-198">Considere a seguinte classe `Point`, que inclui um método `Deconstruct` para criar variáveis discretas para `X` e `Y`:</span><span class="sxs-lookup"><span data-stu-id="b4698-198">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="b4698-199">Além disso, considere a seguinte enumeração que representa várias posições de um quadrante:</span><span class="sxs-lookup"><span data-stu-id="b4698-199">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="b4698-200">O método a seguir usa o **padrão posicional** para extrair os valores de `x` e `y`.</span><span class="sxs-lookup"><span data-stu-id="b4698-200">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="b4698-201">Em seguida, ele usa uma cláusula `when` para determinar o `Quadrant` do ponto:</span><span class="sxs-lookup"><span data-stu-id="b4698-201">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="b4698-202">O padrão de discard na opção anterior encontra a correspondência quando `x` ou `y` é 0, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="b4698-202">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="b4698-203">Uma expressão switch deve produzir um valor ou lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b4698-203">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="b4698-204">Se não houver correspondência em nenhum dos casos, a expressão switch gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b4698-204">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="b4698-205">O compilador gerará um aviso se você não cobrir todos os casos possíveis em sua expressão switch.</span><span class="sxs-lookup"><span data-stu-id="b4698-205">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="b4698-206">Explore técnicas de correspondência de padrões neste [tutorial avançado sobre correspondência de padrões](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-206">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="b4698-207">Declarações using</span><span class="sxs-lookup"><span data-stu-id="b4698-207">using declarations</span></span>

<span data-ttu-id="b4698-208">Uma **declaração using** é uma declaração de variável precedida pela palavra-chave `using`.</span><span class="sxs-lookup"><span data-stu-id="b4698-208">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="b4698-209">Ele informa ao compilador que a variável que está sendo declarada deve ser descartada ao final do escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="b4698-209">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="b4698-210">Por exemplo, considere o seguinte código que grava um arquivo de texto:</span><span class="sxs-lookup"><span data-stu-id="b4698-210">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="b4698-211">No exemplo anterior, o arquivo é descartado quando a chave de fechamento do método é atingida.</span><span class="sxs-lookup"><span data-stu-id="b4698-211">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="b4698-212">Esse é o final do escopo no qual `file` é declarado.</span><span class="sxs-lookup"><span data-stu-id="b4698-212">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="b4698-213">O código anterior equivale ao código a seguir que usa as [instruções using](../language-reference/keywords/using-statement.md) clássicas:</span><span class="sxs-lookup"><span data-stu-id="b4698-213">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="b4698-214">No exemplo anterior, o arquivo é descartado quando a chave de fechamento associada à instrução `using` é atingida.</span><span class="sxs-lookup"><span data-stu-id="b4698-214">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="b4698-215">Em ambos os casos, o compilador gera a chamada para `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="b4698-215">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="b4698-216">O compilador gera um erro se a expressão na instrução `using` não for descartável.</span><span class="sxs-lookup"><span data-stu-id="b4698-216">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="b4698-217">Funções locais estáticas</span><span class="sxs-lookup"><span data-stu-id="b4698-217">Static local functions</span></span>

<span data-ttu-id="b4698-218">Agora você pode adicionar o modificador `static` para funções locais a fim de garantir que essa função local não capture (faça referência) às variáveis no escopo delimitador.</span><span class="sxs-lookup"><span data-stu-id="b4698-218">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="b4698-219">Essa ação gera `CS8421`, "Uma função local estática não pode conter uma referência à \<variable>".</span><span class="sxs-lookup"><span data-stu-id="b4698-219">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="b4698-220">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4698-220">Consider the following code.</span></span> <span data-ttu-id="b4698-221">A função local `LocalFunction` acessa a variável `y`, declarada no escopo delimitador (o método `M`).</span><span class="sxs-lookup"><span data-stu-id="b4698-221">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="b4698-222">Portanto, `LocalFunction` não pode ser declarada com o modificador `static`:</span><span class="sxs-lookup"><span data-stu-id="b4698-222">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="b4698-223">O código a seguir contém uma função local estática.</span><span class="sxs-lookup"><span data-stu-id="b4698-223">The following code contains a static local function.</span></span> <span data-ttu-id="b4698-224">Ela pode ser estática porque não acesse as variáveis no escopo delimitador:</span><span class="sxs-lookup"><span data-stu-id="b4698-224">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="b4698-225">Estruturas ref descartáveis</span><span class="sxs-lookup"><span data-stu-id="b4698-225">Disposable ref structs</span></span>

<span data-ttu-id="b4698-226">Uma `struct` declarada com o modificador `ref` não pode implementar quaisquer interfaces e, portanto, não pode implementar <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="b4698-226">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="b4698-227">Portanto, para permitir que uma `ref struct` seja descartada, ela deve ter um método `void Dispose()` acessível.</span><span class="sxs-lookup"><span data-stu-id="b4698-227">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="b4698-228">Isso também se aplica às declarações `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="b4698-228">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="b4698-229">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="b4698-229">Nullable reference types</span></span>

<span data-ttu-id="b4698-230">Dentro de um contexto de anotação anulável, qualquer variável de um tipo de referência é considerado um **tipo de referência não anulável**.</span><span class="sxs-lookup"><span data-stu-id="b4698-230">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="b4698-231">Se você quiser indicar que uma variável pode ser nula, acrescente o nome do tipo com o `?` para declarar a variável como um **tipo de referência anulável**.</span><span class="sxs-lookup"><span data-stu-id="b4698-231">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="b4698-232">Para tipos de referência não anuláveis, o compilador usa a análise de fluxo para garantir que as variáveis locais sejam inicializadas como um valor não nulo quando declaradas.</span><span class="sxs-lookup"><span data-stu-id="b4698-232">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="b4698-233">Os campos devem ser inicializados durante a construção.</span><span class="sxs-lookup"><span data-stu-id="b4698-233">Fields must be initialized during construction.</span></span> <span data-ttu-id="b4698-234">O compilador gera um aviso se a variável não for definida por uma chamada para qualquer um dos construtores disponíveis ou por um inicializador.</span><span class="sxs-lookup"><span data-stu-id="b4698-234">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="b4698-235">Além disso, os tipos de referência não anuláveis não podem receber um valor que possa ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b4698-235">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="b4698-236">Os tipos de referência anuláveis não são verificados para garantir que não tenham sido atribuídos ou inicializados como nulos.</span><span class="sxs-lookup"><span data-stu-id="b4698-236">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="b4698-237">No entanto, o compilador usa a análise de fluxo para garantir que qualquer variável de um tipo de referência anulável passe por verificação com relação a um nulo antes de ser acessada ou atribuída a um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="b4698-237">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="b4698-238">Saiba mais sobre o recurso na visão geral sobre [Tipos de referência anuláveis](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-238">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="b4698-239">Experimente-o em um novo aplicativo neste [tutorial de tipos de referência anuláveis](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-239">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="b4698-240">Saiba mais sobre as etapas para migrar uma base de códigos existente para usar tipos de referência anuláveis no [tutorial sobre como migrar um aplicativo para usar tipos de referência anuláveis](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-240">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="b4698-241">Fluxos assíncronos</span><span class="sxs-lookup"><span data-stu-id="b4698-241">Asynchronous streams</span></span>

<span data-ttu-id="b4698-242">A partir do C# 8.0, você pode criar e consumir fluxos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b4698-242">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="b4698-243">Um método que retorna um fluxo assíncrono tem três propriedades:</span><span class="sxs-lookup"><span data-stu-id="b4698-243">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="b4698-244">Ele é declarado com o modificador `async`.</span><span class="sxs-lookup"><span data-stu-id="b4698-244">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="b4698-245">Ela retorna um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b4698-245">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="b4698-246">O método contém instruções `yield return` para retornar elementos sucessivos no fluxo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b4698-246">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="b4698-247">O consumo de um fluxo assíncrono exige que você adicione a palavra-chave `await` antes da palavra-chave `foreach` quando você enumera os elementos do fluxo.</span><span class="sxs-lookup"><span data-stu-id="b4698-247">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="b4698-248">A adição da palavra-chave `await` exige o método que enumera o fluxo assíncrono seja declarado com o modificador `async` e retorne um tipo permitido para um método `async`.</span><span class="sxs-lookup"><span data-stu-id="b4698-248">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="b4698-249">Normalmente, isso significa retornar um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b4698-249">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b4698-250">Também pode ser <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="b4698-250">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="b4698-251">Um método pode consumir e produzir um fluxo assíncrono, o que significa que retornaria um <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b4698-251">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="b4698-252">O código a seguir gera uma sequência de 0 a 19, esperando 100 ms entre a geração de cada número:</span><span class="sxs-lookup"><span data-stu-id="b4698-252">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="b4698-253">Você enumeraria a sequência usando a instrução `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="b4698-253">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="b4698-254">Experimente você mesmo os fluxos assíncronos em nosso tutorial sobre como [criar e consumir fluxos assíncronos](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-254">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="b4698-255">Índices e intervalos</span><span class="sxs-lookup"><span data-stu-id="b4698-255">Indices and ranges</span></span>

<span data-ttu-id="b4698-256">Intervalos e índices fornecem uma sintaxe sucinta para especificar subintervalos em uma matriz, [cadeia](../language-reference/builtin-types/reference-types.md#the-string-type)de <xref:System.Span%601>caracteres, <xref:System.ReadOnlySpan%601>ou.</span><span class="sxs-lookup"><span data-stu-id="b4698-256">Ranges and indices provide a succinct syntax for specifying subranges in an array, [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="b4698-257">Esse suporte a idioma depende de dois novos tipos e de dois novos operadores:</span><span class="sxs-lookup"><span data-stu-id="b4698-257">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="b4698-258"><xref:System.Index?displayProperty=nameWithType> representa um índice em uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b4698-258"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="b4698-259">O operador `^`, que especifica que um índice é relativo ao final da sequência.</span><span class="sxs-lookup"><span data-stu-id="b4698-259">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="b4698-260"><xref:System.Range?displayProperty=nameWithType> representa um subintervalo de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="b4698-260"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="b4698-261">O operador Range (`..`), que especifica o início e o final de um intervalo como seus operandos.</span><span class="sxs-lookup"><span data-stu-id="b4698-261">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="b4698-262">Vamos começar com as regras para índices.</span><span class="sxs-lookup"><span data-stu-id="b4698-262">Let's start with the rules for indexes.</span></span> <span data-ttu-id="b4698-263">Considere uma matriz `sequence`.</span><span class="sxs-lookup"><span data-stu-id="b4698-263">Consider an array `sequence`.</span></span> <span data-ttu-id="b4698-264">O índice `0` é o mesmo que `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="b4698-264">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="b4698-265">O índice `^0` é o mesmo que `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="b4698-265">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="b4698-266">Observe que `sequence[^0]` gera uma exceção, assim como `sequence[sequence.Length]` faz.</span><span class="sxs-lookup"><span data-stu-id="b4698-266">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="b4698-267">Para qualquer número `n`, o índice `^n` é o mesmo que `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="b4698-267">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="b4698-268">Um intervalo especifica o *início* e o *final* de um intervalo.</span><span class="sxs-lookup"><span data-stu-id="b4698-268">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="b4698-269">O início do intervalo é inclusivo, mas o final do intervalo é exclusivo, o que significa que o *início* está incluído no intervalo, mas o *final* não está incluído no intervalo.</span><span class="sxs-lookup"><span data-stu-id="b4698-269">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="b4698-270">O intervalo `[0..^0]` representa todo o intervalo, assim como `[0..sequence.Length]` representa todo o intervalo.</span><span class="sxs-lookup"><span data-stu-id="b4698-270">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="b4698-271">Vamos analisar alguns exemplos.</span><span class="sxs-lookup"><span data-stu-id="b4698-271">Let's look at a few examples.</span></span> <span data-ttu-id="b4698-272">Considere a matriz a seguir, anotada com seu índice do início e do final:</span><span class="sxs-lookup"><span data-stu-id="b4698-272">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="b4698-273">Recupere a última palavra com o índice `^1`:</span><span class="sxs-lookup"><span data-stu-id="b4698-273">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="b4698-274">O código a seguir cria um subintervalo com as palavras "quick", "brown" e "fox".</span><span class="sxs-lookup"><span data-stu-id="b4698-274">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="b4698-275">Ele inclui `words[1]` até `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="b4698-275">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="b4698-276">O elemento `words[4]` não está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="b4698-276">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="b4698-277">O código a seguir cria um subintervalo com "lazy" e "dog".</span><span class="sxs-lookup"><span data-stu-id="b4698-277">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="b4698-278">Ele inclui `words[^2]` e `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="b4698-278">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="b4698-279">O índice final `words[^0]` não está incluído:</span><span class="sxs-lookup"><span data-stu-id="b4698-279">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="b4698-280">Os exemplos a seguir criam intervalos abertos para o início, fim ou ambos:</span><span class="sxs-lookup"><span data-stu-id="b4698-280">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="b4698-281">Você também pode declarar intervalos como variáveis:</span><span class="sxs-lookup"><span data-stu-id="b4698-281">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="b4698-282">Em seguida, o intervalo pode ser usado dentro dos caracteres `[` e `]`:</span><span class="sxs-lookup"><span data-stu-id="b4698-282">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="b4698-283">Você pode explorar mais sobre índices e intervalos do tutorial sobre [índices e intervalos](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-283">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="b4698-284">Atribuição de União nula</span><span class="sxs-lookup"><span data-stu-id="b4698-284">Null-coalescing assignment</span></span>

<span data-ttu-id="b4698-285">C#8,0 apresenta o operador `??=`de atribuição de União nula.</span><span class="sxs-lookup"><span data-stu-id="b4698-285">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="b4698-286">Você pode usar o `??=` operador para atribuir o valor do seu operando à direita para seu operando à esquerda somente se o operando esquerdo for avaliado como. `null`</span><span class="sxs-lookup"><span data-stu-id="b4698-286">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(' ', numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="b4698-287">Para obter mais informações, consulte [?? e?? =](../language-reference/operators/null-coalescing-operator.md) artigo de operadores.</span><span class="sxs-lookup"><span data-stu-id="b4698-287">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="b4698-288">Tipos construídos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="b4698-288">Unmanaged constructed types</span></span>

<span data-ttu-id="b4698-289">No C# 7,3 e anterior, um tipo construído (um tipo que inclui pelo menos um argumento de tipo) não pode ser um [tipo não gerenciado](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-289">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) cannot be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="b4698-290">A partir C# de 8,0, um tipo de valor construído não será gerenciado se ele contiver campos apenas de tipos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b4698-290">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="b4698-291">Por exemplo, dada a seguinte definição do tipo genérico `Coords<T>` :</span><span class="sxs-lookup"><span data-stu-id="b4698-291">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="b4698-292">o `Coords<int>` tipo é um tipo não gerenciado em C# 8,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="b4698-292">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="b4698-293">Como para qualquer tipo não gerenciado, você pode criar um ponteiro para uma variável desse tipo ou [alocar um bloco de memória na pilha](../language-reference/operators/stackalloc.md) para instâncias desse tipo:</span><span class="sxs-lookup"><span data-stu-id="b4698-293">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="b4698-294">Para obter mais informações, consulte [tipos não gerenciados](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="b4698-294">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="b4698-295">stackalloc em expressões aninhadas</span><span class="sxs-lookup"><span data-stu-id="b4698-295">stackalloc in nested expressions</span></span>

<span data-ttu-id="b4698-296">A partir C# de 8,0, se o resultado de uma expressão [stackalloc](../language-reference/operators/stackalloc.md) <xref:System.Span%601?displayProperty=nameWithType> for do tipo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> ou, você poderá usar a `stackalloc` expressão em outras expressões:</span><span class="sxs-lookup"><span data-stu-id="b4698-296">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="b4698-297">Aprimoramento de cadeias de caracteres idênticas interpoladas</span><span class="sxs-lookup"><span data-stu-id="b4698-297">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="b4698-298">A `$` ordem dos tokens e `@` nas cadeias de caracteres `$@"..."` idênticas [interpoladas](../language-reference/tokens/interpolated.md) pode `@$"..."` ser any: e são cadeias de caracteres idênticas interpoladas válidas.</span><span class="sxs-lookup"><span data-stu-id="b4698-298">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="b4698-299">Em versões C# anteriores, o `$` token deve aparecer antes do `@` token.</span><span class="sxs-lookup"><span data-stu-id="b4698-299">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
