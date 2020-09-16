---
ms.openlocfilehash: edff55d540f08e8a9fd4d0687aaf6bd963ee3a84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539438"
---
### <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="6720e-101">Mais do que: RenderTreeFrame campos públicos ReadOnly se tornaram Propriedades</span><span class="sxs-lookup"><span data-stu-id="6720e-101">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="6720e-102">No ASP.NET Core 3,0 e 3,1, a <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> estrutura expôs vários `readonly public` campos, incluindo <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> , <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> e outros.</span><span class="sxs-lookup"><span data-stu-id="6720e-102">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="6720e-103">No ASP.NET Core 5,0 RC1 e versões posteriores, todos os `readonly public` campos foram alterados para `readonly public` Propriedades.</span><span class="sxs-lookup"><span data-stu-id="6720e-103">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="6720e-104">Essa alteração não afetará muitos desenvolvedores porque:</span><span class="sxs-lookup"><span data-stu-id="6720e-104">This change won't affect many developers because:</span></span>

* <span data-ttu-id="6720e-105">Qualquer aplicativo ou biblioteca que simplesmente usa `.razor` arquivos (ou até mesmo <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> chamadas manuais) para definir seus componentes não referenciaria esse tipo diretamente.</span><span class="sxs-lookup"><span data-stu-id="6720e-105">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="6720e-106">O `RenderTreeFrame` próprio tipo é considerado um detalhe de implementação, não destinado ao uso fora da estrutura.</span><span class="sxs-lookup"><span data-stu-id="6720e-106">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="6720e-107">ASP.NET Core 3,0 e posterior inclui um analisador que emite avisos do compilador se o tipo estiver sendo usado diretamente.</span><span class="sxs-lookup"><span data-stu-id="6720e-107">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="6720e-108">Mesmo se você fizer referência `RenderTreeFrame` diretamente, essa alteração será de quebra de binário, mas não de quebra de fonte.</span><span class="sxs-lookup"><span data-stu-id="6720e-108">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="6720e-109">Ou seja, o código-fonte existente será compilado e se comportará corretamente.</span><span class="sxs-lookup"><span data-stu-id="6720e-109">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="6720e-110">Você encontrará um problema apenas se estiver compilando em uma estrutura do .NET Core 3. x e, em seguida, executando esses binários no .NET 5,0 RC1 e no Framework posterior.</span><span class="sxs-lookup"><span data-stu-id="6720e-110">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="6720e-111">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).</span><span class="sxs-lookup"><span data-stu-id="6720e-111">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6720e-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6720e-112">Version introduced</span></span>

<span data-ttu-id="6720e-113">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="6720e-113">5.0 RC1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6720e-114">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="6720e-114">Old behavior</span></span>

<span data-ttu-id="6720e-115">Os membros públicos em `RenderTreeFrame` são definidos como campos.</span><span class="sxs-lookup"><span data-stu-id="6720e-115">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="6720e-116">Por exemplo, `renderTreeFrame.Sequence` e `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="6720e-116">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6720e-117">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="6720e-117">New behavior</span></span>

<span data-ttu-id="6720e-118">Os membros públicos em `RenderTreeFrame` são definidos como propriedades com os mesmos nomes de antes.</span><span class="sxs-lookup"><span data-stu-id="6720e-118">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="6720e-119">Por exemplo, `renderTreeFrame.Sequence` e `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="6720e-119">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="6720e-120">Se o código pré-compilado mais antigo não tiver sido recompilado desde essa alteração, ele poderá lançar uma exceção semelhante a *MissingFieldException: campo não encontrado: ' Microsoft. AspNetCore. Components. RenderTree. RenderTreeFrame. FrameType '*.</span><span class="sxs-lookup"><span data-stu-id="6720e-120">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6720e-121">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="6720e-121">Reason for change</span></span>

<span data-ttu-id="6720e-122">Essa alteração foi necessária para implementar melhorias de desempenho de alto impacto na renderização de componente mais incrivelmente no ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="6720e-122">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="6720e-123">Os mesmos níveis de segurança e encapsulamento são mantidos.</span><span class="sxs-lookup"><span data-stu-id="6720e-123">The same levels of safety and encapsulation are maintained.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6720e-124">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="6720e-124">Recommended action</span></span>

<span data-ttu-id="6720e-125">A maioria dos desenvolvedores não é afetada por essa mudança.</span><span class="sxs-lookup"><span data-stu-id="6720e-125">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="6720e-126">É mais provável que a alteração afete os autores de biblioteca e pacote, mas apenas em casos raros.</span><span class="sxs-lookup"><span data-stu-id="6720e-126">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="6720e-127">Especificamente, se você estiver desenvolvendo:</span><span class="sxs-lookup"><span data-stu-id="6720e-127">Specifically, if you're developing:</span></span>

* <span data-ttu-id="6720e-128">Um aplicativo e usar ASP.NET Core 3. x ou atualizar para o 5,0 RC1 ou posterior, você não precisa alterar seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="6720e-128">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="6720e-129">No entanto, se você depender de uma biblioteca atualizada para considerar essa alteração, precisará atualizar para uma versão mais recente dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="6720e-129">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="6720e-130">Uma biblioteca e deseja dar suporte apenas ao ASP.NET Core 5,0 RC1 ou posterior, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="6720e-130">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="6720e-131">Apenas verifique se o arquivo de projeto declara um `<TargetFramework>` valor de `net5.0` ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="6720e-131">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="6720e-132">Uma biblioteca e deseja dar suporte às ASP.NET Core 3. x *e* 5,0, determinar se o código lê os `RenderTreeFrame` Membros.</span><span class="sxs-lookup"><span data-stu-id="6720e-132">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="6720e-133">Por exemplo, avaliar `someRenderTreeFrame.FrameType` .</span><span class="sxs-lookup"><span data-stu-id="6720e-133">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="6720e-134">A maioria das bibliotecas não lê `RenderTreeFrame` Membros, incluindo bibliotecas que contêm `.razor` componentes.</span><span class="sxs-lookup"><span data-stu-id="6720e-134">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="6720e-135">Nesse caso, nenhuma ação é necessária.</span><span class="sxs-lookup"><span data-stu-id="6720e-135">In this case, no action is needed.</span></span>
  * <span data-ttu-id="6720e-136">No entanto, se sua biblioteca faz isso, você precisará de vários destinos para dar suporte a `netstandard2.1` e ao `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="6720e-136">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="6720e-137">Aplique as seguintes alterações no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="6720e-137">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="6720e-138">Substitua o `<TargetFramework>` elemento existente por `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .</span><span class="sxs-lookup"><span data-stu-id="6720e-138">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="6720e-139">Use uma `Microsoft.AspNetCore.Components` referência de pacote condicional para considerar as duas versões às quais você deseja dar suporte.</span><span class="sxs-lookup"><span data-stu-id="6720e-139">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="6720e-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6720e-140">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="6720e-141">Para obter mais esclarecimentos, consulte esta [diferença mostrando como @jsakamoto o já atualizou a `Toolbelt.Blazor.HeadElement` biblioteca](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span><span class="sxs-lookup"><span data-stu-id="6720e-141">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

#### <a name="category"></a><span data-ttu-id="6720e-142">Categoria</span><span class="sxs-lookup"><span data-stu-id="6720e-142">Category</span></span>

<span data-ttu-id="6720e-143">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6720e-143">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6720e-144">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6720e-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
