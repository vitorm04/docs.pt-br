---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174251"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="77490-101">Mais grande: espaço em branco insignificado cortado de componentes em tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="77490-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="77490-102">A partir do ASP.NET Core 5,0 Preview 7, o compilador do Razor omite espaço em branco insignificante nos componentes mais importantes (arquivos *. Razor* ) no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="77490-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="77490-103">Para obter uma discussão, veja Issue [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="77490-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="77490-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="77490-104">Version introduced</span></span>

<span data-ttu-id="77490-105">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="77490-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="77490-106">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="77490-106">Old behavior</span></span>

<span data-ttu-id="77490-107">Nas versões 3. x do mais claro servidor e Webassembly do mais claro, o espaço em branco é respeitado no código-fonte de um componente.</span><span class="sxs-lookup"><span data-stu-id="77490-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="77490-108">Nós de texto somente em espaços em branco são renderizados no Modelo de Objeto do Documento do navegador (DOM) mesmo quando não há nenhum efeito visual.</span><span class="sxs-lookup"><span data-stu-id="77490-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="77490-109">Considere o seguinte código de componente mais interessante:</span><span class="sxs-lookup"><span data-stu-id="77490-109">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="77490-110">O exemplo anterior processa dois nós de espaço em branco:</span><span class="sxs-lookup"><span data-stu-id="77490-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="77490-111">Fora do `@foreach` bloco de código.</span><span class="sxs-lookup"><span data-stu-id="77490-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="77490-112">Em volta do `<li>` elemento.</span><span class="sxs-lookup"><span data-stu-id="77490-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="77490-113">Em volta da `@item.Text` saída.</span><span class="sxs-lookup"><span data-stu-id="77490-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="77490-114">Uma lista contendo 100 itens resulta em 402 nós de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="77490-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="77490-115">Isso é mais de metade de todos os nós renderizados, mesmo que nenhum dos nós de espaço em branco afete visualmente a saída renderizada.</span><span class="sxs-lookup"><span data-stu-id="77490-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="77490-116">Ao renderizar HTML estático para componentes, o espaço em branco dentro de uma marca não foi preservado.</span><span class="sxs-lookup"><span data-stu-id="77490-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="77490-117">Por exemplo, exiba a origem do seguinte componente:</span><span class="sxs-lookup"><span data-stu-id="77490-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="77490-118">O espaço em branco não é preservado.</span><span class="sxs-lookup"><span data-stu-id="77490-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="77490-119">A saída previamente renderizada é:</span><span class="sxs-lookup"><span data-stu-id="77490-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="77490-120">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="77490-120">New behavior</span></span>

<span data-ttu-id="77490-121">A menos que a `@preservewhitespace` diretiva seja usada com o valor `true` , os nós de espaço em branco serão removidos se:</span><span class="sxs-lookup"><span data-stu-id="77490-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="77490-122">Estão à esquerda ou à direita dentro de um elemento.</span><span class="sxs-lookup"><span data-stu-id="77490-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="77490-123">Estão à esquerda ou à direita dentro de um `RenderFragment` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="77490-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="77490-124">Por exemplo, o conteúdo filho que está sendo passado para outro componente.</span><span class="sxs-lookup"><span data-stu-id="77490-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="77490-125">Preceda ou siga um bloco de código C#, como `@if` e `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="77490-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="77490-126">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="77490-126">Reason for change</span></span>

<span data-ttu-id="77490-127">Uma meta para o mais claro no ASP.NET Core 5,0 é melhorar o desempenho da renderização e da diferenciação.</span><span class="sxs-lookup"><span data-stu-id="77490-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="77490-128">Nós de árvore de espaço em branco insignificantes consumidos até 40% do tempo de renderização em parâmetros de comparação.</span><span class="sxs-lookup"><span data-stu-id="77490-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="77490-129">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="77490-129">Recommended action</span></span>

<span data-ttu-id="77490-130">Na maioria dos casos, o layout visual do componente renderizado não é afetado.</span><span class="sxs-lookup"><span data-stu-id="77490-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="77490-131">No entanto, a remoção de espaço em branco pode afetar a saída renderizada ao usar uma regra CSS como `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="77490-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="77490-132">Para desabilitar essa otimização de desempenho e preservar o espaço em branco, execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="77490-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="77490-133">Adicione a `@preservewhitespace true` diretiva na parte superior do arquivo *. Razor* para aplicar a preferência a um componente específico.</span><span class="sxs-lookup"><span data-stu-id="77490-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="77490-134">Adicione a `@preservewhitespace true` diretiva dentro de um arquivo *_Imports. Razor* para aplicar a preferência a um subdiretório inteiro ou todo o projeto.</span><span class="sxs-lookup"><span data-stu-id="77490-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="77490-135">Na maioria dos casos, nenhuma ação é necessária, pois os aplicativos normalmente continuarão a se comportar normalmente (mas com mais rapidez).</span><span class="sxs-lookup"><span data-stu-id="77490-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="77490-136">Se a remoção de espaço em branco causar problemas para um componente específico, use esse `@preservewhitespace true` componente para desabilitar essa otimização.</span><span class="sxs-lookup"><span data-stu-id="77490-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="77490-137">Categoria</span><span class="sxs-lookup"><span data-stu-id="77490-137">Category</span></span>

<span data-ttu-id="77490-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="77490-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="77490-139">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="77490-139">Affected APIs</span></span>

<span data-ttu-id="77490-140">Nenhum</span><span class="sxs-lookup"><span data-stu-id="77490-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
