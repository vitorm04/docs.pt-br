---
title: Diretrizes de design de componente do F#
description: 'Conheça as diretrizes para escrever componentes F # destinados para consumo por outros chamadores.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209130"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="212d5-103">Diretrizes de design de componente do F#</span><span class="sxs-lookup"><span data-stu-id="212d5-103">F# component design guidelines</span></span>

<span data-ttu-id="212d5-104">Este documento é um conjunto de diretrizes de design de componentes para programação em F #, com base nas diretrizes de design de componente F #, v14, Microsoft Research e uma versão que foi originalmente organizada e mantida pelo F # Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="212d5-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="212d5-105">Este documento pressupõe que você esteja familiarizado com a programação em F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="212d5-106">Muitos agradecimentos à comunidade do F # por suas contribuições e comentários úteis sobre várias versões deste guia.</span><span class="sxs-lookup"><span data-stu-id="212d5-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="212d5-107">Visão geral</span><span class="sxs-lookup"><span data-stu-id="212d5-107">Overview</span></span>

<span data-ttu-id="212d5-108">Este documento analisa alguns dos problemas relacionados ao design e à codificação de componentes do F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="212d5-109">Um componente pode significar qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="212d5-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="212d5-110">Uma camada em seu projeto F # que tem consumidores externos dentro desse projeto.</span><span class="sxs-lookup"><span data-stu-id="212d5-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="212d5-111">Uma biblioteca destinada ao consumo pelo código F # nos limites do assembly.</span><span class="sxs-lookup"><span data-stu-id="212d5-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="212d5-112">Uma biblioteca destinada ao consumo por qualquer linguagem .NET entre limites de assembly.</span><span class="sxs-lookup"><span data-stu-id="212d5-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="212d5-113">Uma biblioteca destinada à distribuição por meio de um repositório de pacotes, como o [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="212d5-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="212d5-114">As técnicas descritas neste artigo seguem os [cinco princípios de um bom código F #](index.md#five-principles-of-good-f-code)e, portanto, utilizam a programação funcional e de objeto conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="212d5-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="212d5-115">Independentemente da metodologia, o componente e o designer de biblioteca enfrentam vários problemas práticos e prosaicass ao tentar criar uma API que seja mais fácil de ser usada pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="212d5-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="212d5-116">A aplicação do Conscientious das [diretrizes de design da biblioteca do .net](../../standard/design-guidelines/index.md) orientará você na criação de um conjunto consistente de APIs que são agradáveis de consumir.</span><span class="sxs-lookup"><span data-stu-id="212d5-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="212d5-117">Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="212d5-117">General guidelines</span></span>

<span data-ttu-id="212d5-118">Há algumas diretrizes universais que se aplicam a bibliotecas F #, independentemente do público-alvo da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="212d5-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="212d5-119">Conheça as diretrizes de design de biblioteca do .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="212d5-120">Independentemente do tipo de codificação F # que você está fazendo, é importante ter um conhecimento prático das [diretrizes de design da biblioteca do .net](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="212d5-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="212d5-121">A maioria dos outros programadores F # e .NET estará familiarizado com essas diretrizes e esperará que o código .NET esteja em conformidade com eles.</span><span class="sxs-lookup"><span data-stu-id="212d5-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="212d5-122">As diretrizes de design de biblioteca do .NET fornecem orientação geral sobre Nomenclatura, criação de classes e interfaces, design de Membros (Propriedades, métodos, eventos, etc.) e muito mais, e são um ponto de referência útil para uma variedade de diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="212d5-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="212d5-123">Adicionar comentários de documentação XML ao seu código</span><span class="sxs-lookup"><span data-stu-id="212d5-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="212d5-124">A documentação XML em APIs públicas garante que os usuários possam obter excelentes IntelliSense e Quickinfo ao usar esses tipos e membros e habilitar a criação de arquivos de documentação para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="212d5-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="212d5-125">Consulte a [documentação XML](../language-reference/xml-documentation.md) sobre várias marcas XML que podem ser usadas para marcação adicional nos comentários do xmlDoc.</span><span class="sxs-lookup"><span data-stu-id="212d5-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="212d5-126">Você pode usar os comentários XML de forma abreviada ( `/// comment` ) ou os comentários XML padrão ( `///<summary>comment</summary>` ).</span><span class="sxs-lookup"><span data-stu-id="212d5-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="212d5-127">Considere o uso de arquivos de assinatura explícitos (. FSI) para APIs estáveis de biblioteca e componente</span><span class="sxs-lookup"><span data-stu-id="212d5-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="212d5-128">O uso de arquivos de assinaturas explícitas em uma biblioteca F # fornece um resumo sucinta da API pública, que ajuda a garantir que você conheça a superfície pública completa da biblioteca e fornece uma separação clara entre a documentação pública e os detalhes de implementação interna.</span><span class="sxs-lookup"><span data-stu-id="212d5-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="212d5-129">Os arquivos de assinatura adicionam o conflito à alteração da API pública, exigindo que sejam feitas alterações nos arquivos de implementação e de assinatura.</span><span class="sxs-lookup"><span data-stu-id="212d5-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="212d5-130">Como resultado, os arquivos de assinatura normalmente devem ser introduzidos apenas quando uma API se tornar solidificou e não se esperar mais mudar significativamente.</span><span class="sxs-lookup"><span data-stu-id="212d5-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="212d5-131">Sempre siga as práticas recomendadas para usar cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="212d5-132">Siga [as práticas recomendadas para usar cadeias de caracteres em diretrizes .net](../../standard/base-types/best-practices-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="212d5-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="212d5-133">Em particular, sempre declare explicitamente a *intenção cultural* na conversão e na comparação de cadeias de caracteres (quando aplicável).</span><span class="sxs-lookup"><span data-stu-id="212d5-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="212d5-134">Diretrizes para bibliotecas voltadas para o F #</span><span class="sxs-lookup"><span data-stu-id="212d5-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="212d5-135">Esta seção apresenta as recomendações para o desenvolvimento de bibliotecas públicas do F #; ou seja, bibliotecas que expõem APIs públicas que devem ser consumidas por desenvolvedores de F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="212d5-136">Há uma variedade de recomendações de design de biblioteca aplicáveis especificamente ao F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="212d5-137">Na ausência das recomendações específicas que se seguem, as diretrizes de design da biblioteca do .NET são as orientações de fallback.</span><span class="sxs-lookup"><span data-stu-id="212d5-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="212d5-138">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="212d5-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="212d5-139">Usar convenções de nomenclatura e uso do .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="212d5-140">A tabela a seguir segue as convenções de nomenclatura e de capitalização do .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="212d5-141">Há pequenas adições a também incluem construções F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="212d5-142">Constructo</span><span class="sxs-lookup"><span data-stu-id="212d5-142">Construct</span></span> | <span data-ttu-id="212d5-143">Caixa</span><span class="sxs-lookup"><span data-stu-id="212d5-143">Case</span></span> | <span data-ttu-id="212d5-144">Parte</span><span class="sxs-lookup"><span data-stu-id="212d5-144">Part</span></span> | <span data-ttu-id="212d5-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="212d5-145">Examples</span></span> | <span data-ttu-id="212d5-146">Observações</span><span class="sxs-lookup"><span data-stu-id="212d5-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="212d5-147">Tipos concretos</span><span class="sxs-lookup"><span data-stu-id="212d5-147">Concrete types</span></span> | <span data-ttu-id="212d5-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-148">PascalCase</span></span> | <span data-ttu-id="212d5-149">Substantivo/adjetivo</span><span class="sxs-lookup"><span data-stu-id="212d5-149">Noun/ adjective</span></span> | <span data-ttu-id="212d5-150">Lista, dupla, complexa</span><span class="sxs-lookup"><span data-stu-id="212d5-150">List, Double, Complex</span></span> | <span data-ttu-id="212d5-151">Os tipos concretos são structs, classes, enumerações, delegados, registros e uniões.</span><span class="sxs-lookup"><span data-stu-id="212d5-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="212d5-152">Embora os nomes de tipo sejam tradicionalmente minúsculos em OCaml, o F # adotou o esquema de nomenclatura .NET para tipos.</span><span class="sxs-lookup"><span data-stu-id="212d5-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="212d5-153">DLLs</span><span class="sxs-lookup"><span data-stu-id="212d5-153">DLLs</span></span>           | <span data-ttu-id="212d5-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-154">PascalCase</span></span> |                 | <span data-ttu-id="212d5-155">Fabrikam. Core. dll</span><span class="sxs-lookup"><span data-stu-id="212d5-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="212d5-156">Marcas Union</span><span class="sxs-lookup"><span data-stu-id="212d5-156">Union tags</span></span>     | <span data-ttu-id="212d5-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-157">PascalCase</span></span> | <span data-ttu-id="212d5-158">Substantivo</span><span class="sxs-lookup"><span data-stu-id="212d5-158">Noun</span></span> | <span data-ttu-id="212d5-159">Alguns, adicionar, sucesso</span><span class="sxs-lookup"><span data-stu-id="212d5-159">Some, Add, Success</span></span> | <span data-ttu-id="212d5-160">Não use um prefixo em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="212d5-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="212d5-161">Opcionalmente, use um prefixo quando interno, como`type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="212d5-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="212d5-162">Evento</span><span class="sxs-lookup"><span data-stu-id="212d5-162">Event</span></span>          | <span data-ttu-id="212d5-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-163">PascalCase</span></span> | <span data-ttu-id="212d5-164">Verbo</span><span class="sxs-lookup"><span data-stu-id="212d5-164">Verb</span></span> | <span data-ttu-id="212d5-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="212d5-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="212d5-166">Exceções</span><span class="sxs-lookup"><span data-stu-id="212d5-166">Exceptions</span></span>     | <span data-ttu-id="212d5-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-167">PascalCase</span></span> |      | <span data-ttu-id="212d5-168">WebException</span><span class="sxs-lookup"><span data-stu-id="212d5-168">WebException</span></span> | <span data-ttu-id="212d5-169">O nome deve terminar com "Exception".</span><span class="sxs-lookup"><span data-stu-id="212d5-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="212d5-170">Campo</span><span class="sxs-lookup"><span data-stu-id="212d5-170">Field</span></span>          | <span data-ttu-id="212d5-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-171">PascalCase</span></span> | <span data-ttu-id="212d5-172">Substantivo</span><span class="sxs-lookup"><span data-stu-id="212d5-172">Noun</span></span> | <span data-ttu-id="212d5-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="212d5-173">CurrentName</span></span>  | |
| <span data-ttu-id="212d5-174">Tipos de interface</span><span class="sxs-lookup"><span data-stu-id="212d5-174">Interface types</span></span> |  <span data-ttu-id="212d5-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-175">PascalCase</span></span> | <span data-ttu-id="212d5-176">Substantivo/adjetivo</span><span class="sxs-lookup"><span data-stu-id="212d5-176">Noun/ adjective</span></span> | <span data-ttu-id="212d5-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="212d5-177">IDisposable</span></span> | <span data-ttu-id="212d5-178">O nome deve começar com "I".</span><span class="sxs-lookup"><span data-stu-id="212d5-178">Name should start with "I".</span></span> |
| <span data-ttu-id="212d5-179">Método</span><span class="sxs-lookup"><span data-stu-id="212d5-179">Method</span></span> |  <span data-ttu-id="212d5-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-180">PascalCase</span></span> |  <span data-ttu-id="212d5-181">Verbo</span><span class="sxs-lookup"><span data-stu-id="212d5-181">Verb</span></span> | <span data-ttu-id="212d5-182">ToString</span><span class="sxs-lookup"><span data-stu-id="212d5-182">ToString</span></span> | |
| <span data-ttu-id="212d5-183">Namespace</span><span class="sxs-lookup"><span data-stu-id="212d5-183">Namespace</span></span> | <span data-ttu-id="212d5-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-184">PascalCase</span></span> | | <span data-ttu-id="212d5-185">Microsoft. FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="212d5-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="212d5-186">Geralmente `<Organization>.<Technology>[.<Subnamespace>]` , use, embora descarte a organização, se a tecnologia for independente da organização.</span><span class="sxs-lookup"><span data-stu-id="212d5-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="212d5-187">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="212d5-187">Parameters</span></span> | <span data-ttu-id="212d5-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="212d5-188">camelCase</span></span> | <span data-ttu-id="212d5-189">Substantivo</span><span class="sxs-lookup"><span data-stu-id="212d5-189">Noun</span></span> |  <span data-ttu-id="212d5-190">typeName, transformar, intervalo</span><span class="sxs-lookup"><span data-stu-id="212d5-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="212d5-191">permitir valores (internos)</span><span class="sxs-lookup"><span data-stu-id="212d5-191">let values (internal)</span></span> | <span data-ttu-id="212d5-192">camelCase ou PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-192">camelCase or PascalCase</span></span> | <span data-ttu-id="212d5-193">Substantivo/verbo</span><span class="sxs-lookup"><span data-stu-id="212d5-193">Noun/ verb</span></span> |  <span data-ttu-id="212d5-194">GetValue, myTable</span><span class="sxs-lookup"><span data-stu-id="212d5-194">getValue, myTable</span></span> |
| <span data-ttu-id="212d5-195">permitir valores (externos)</span><span class="sxs-lookup"><span data-stu-id="212d5-195">let values (external)</span></span> | <span data-ttu-id="212d5-196">camelCase ou PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-196">camelCase or PascalCase</span></span> | <span data-ttu-id="212d5-197">Substantivo/verbo</span><span class="sxs-lookup"><span data-stu-id="212d5-197">Noun/verb</span></span>  | <span data-ttu-id="212d5-198">Lista. map, datas. hoje</span><span class="sxs-lookup"><span data-stu-id="212d5-198">List.map, Dates.Today</span></span> | <span data-ttu-id="212d5-199">os valores de Let associados são geralmente públicos quando os padrões de design funcional tradicionais são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="212d5-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="212d5-200">No entanto, geralmente use PascalCase quando o identificador puder ser usado de outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="212d5-201">Propriedade</span><span class="sxs-lookup"><span data-stu-id="212d5-201">Property</span></span>  | <span data-ttu-id="212d5-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="212d5-202">PascalCase</span></span>  | <span data-ttu-id="212d5-203">Substantivo/adjetivo</span><span class="sxs-lookup"><span data-stu-id="212d5-203">Noun/ adjective</span></span>  | <span data-ttu-id="212d5-204">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="212d5-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="212d5-205">As propriedades boolianas geralmente usam e podem e devem ser afirmativo, como em IsEndOfFile, e não IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="212d5-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="212d5-206">Evitar abreviações</span><span class="sxs-lookup"><span data-stu-id="212d5-206">Avoid abbreviations</span></span>

<span data-ttu-id="212d5-207">As diretrizes do .NET desestimulam o uso de abreviações (por exemplo, "uso `OnButtonClick` em vez de `OnBtnClick` ").</span><span class="sxs-lookup"><span data-stu-id="212d5-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="212d5-208">Abreviações comuns, como `Async` para "Asynchronous", são toleradas.</span><span class="sxs-lookup"><span data-stu-id="212d5-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="212d5-209">Essa diretriz é, às vezes, ignorada para a programação funcional; por exemplo, `List.iter` usa uma abreviação para "iterar".</span><span class="sxs-lookup"><span data-stu-id="212d5-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="212d5-210">Por esse motivo, o uso de abreviações tende a ser tolerado a um grau maior na programação F #-to-F #, mas ainda deve ser evitado em geral no design de componentes públicos.</span><span class="sxs-lookup"><span data-stu-id="212d5-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="212d5-211">Evitar colisões de nome com maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="212d5-211">Avoid casing name collisions</span></span>

<span data-ttu-id="212d5-212">As diretrizes do .NET dizem que o uso de maiúsculas e minúsculas não pode ser usado para desambiguar colisões de nomes, pois alguns idiomas de cliente (por exemplo, Visual Basic) não diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="212d5-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="212d5-213">Use acrônimos quando apropriado</span><span class="sxs-lookup"><span data-stu-id="212d5-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="212d5-214">Acrônimos como XML não são abreviações e são amplamente usados em bibliotecas .NET em formato não capitalizado (XML).</span><span class="sxs-lookup"><span data-stu-id="212d5-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="212d5-215">Apenas acrônimos conhecidos e amplamente reconhecidos devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="212d5-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="212d5-216">Usar PascalCase para nomes de parâmetro genéricos</span><span class="sxs-lookup"><span data-stu-id="212d5-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="212d5-217">Use PascalCase para nomes de parâmetro genéricos em APIs públicas, incluindo as bibliotecas voltadas para o F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="212d5-218">Em particular, use nomes como `T` , `U` , `T1` , `T2` para parâmetros genéricos arbitrários e quando nomes específicos fizerem sentido; em seguida, para bibliotecas em F #, use nomes como `Key` , `Value` , `Arg` mas não por exemplo, `TKey` ).</span><span class="sxs-lookup"><span data-stu-id="212d5-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="212d5-219">Usar PascalCase ou camelCase para funções e valores públicos em módulos F #</span><span class="sxs-lookup"><span data-stu-id="212d5-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="212d5-220">camelCase é usado para funções públicas que são projetadas para serem usadas não qualificadas (por exemplo, `invalidArg` ) e para as "funções de coleção padrão" (por exemplo, List. map).</span><span class="sxs-lookup"><span data-stu-id="212d5-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="212d5-221">Em ambos os casos, os nomes de função funcionam de forma muito parecida com palavras-chave no idioma.</span><span class="sxs-lookup"><span data-stu-id="212d5-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="212d5-222">Design de objeto, tipo e módulo</span><span class="sxs-lookup"><span data-stu-id="212d5-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="212d5-223">Usar namespaces ou módulos para conter seus tipos e módulos</span><span class="sxs-lookup"><span data-stu-id="212d5-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="212d5-224">Cada arquivo F # em um componente deve começar com uma declaração de namespace ou uma declaração de módulo.</span><span class="sxs-lookup"><span data-stu-id="212d5-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="212d5-225">ou</span><span class="sxs-lookup"><span data-stu-id="212d5-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="212d5-226">As diferenças entre usar módulos e namespaces para organizar o código no nível superior são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="212d5-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="212d5-227">Namespaces podem abranger vários arquivos</span><span class="sxs-lookup"><span data-stu-id="212d5-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="212d5-228">Namespaces não podem conter funções F #, a menos que estejam dentro de um módulo interno</span><span class="sxs-lookup"><span data-stu-id="212d5-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="212d5-229">O código para qualquer módulo fornecido deve estar contido em um único arquivo</span><span class="sxs-lookup"><span data-stu-id="212d5-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="212d5-230">Módulos de nível superior podem conter funções F # sem a necessidade de um módulo interno</span><span class="sxs-lookup"><span data-stu-id="212d5-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="212d5-231">A escolha entre um namespace ou módulo de nível superior afeta a forma compilada do código e, portanto, afetará a exibição de outras linguagens do .NET caso sua API seja eventualmente consumida fora do código F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="212d5-232">Usar métodos e propriedades para operações intrínsecas a tipos de objeto</span><span class="sxs-lookup"><span data-stu-id="212d5-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="212d5-233">Ao trabalhar com objetos, é melhor garantir que a funcionalidade de consumo seja implementada como métodos e propriedades nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="212d5-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="212d5-234">A maior parte da funcionalidade para um determinado membro não precisa necessariamente ser implementada nesse membro, mas a parte consumível dessa funcionalidade deve ser.</span><span class="sxs-lookup"><span data-stu-id="212d5-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="212d5-235">Usar classes para encapsular o estado mutável</span><span class="sxs-lookup"><span data-stu-id="212d5-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="212d5-236">Em F #, isso só precisa ser feito quando esse estado ainda não é encapsulado por outro constructo de linguagem, como um fechamento, uma expressão de sequência ou uma computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="212d5-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="212d5-237">Usar interfaces para agrupar operações relacionadas</span><span class="sxs-lookup"><span data-stu-id="212d5-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="212d5-238">Use tipos de interface para representar um conjunto de operações.</span><span class="sxs-lookup"><span data-stu-id="212d5-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="212d5-239">Isso é preferível a outras opções, como tuplas de funções ou registros de funções.</span><span class="sxs-lookup"><span data-stu-id="212d5-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="212d5-240">Em preferência a:</span><span class="sxs-lookup"><span data-stu-id="212d5-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="212d5-241">As interfaces são conceitos de primeira classe no .NET, que você pode usar para obter o que o transmissão functors normalmente daria a você.</span><span class="sxs-lookup"><span data-stu-id="212d5-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="212d5-242">Além disso, eles podem ser usados para codificar tipos Existential em seu programa, quais registros de funções não podem.</span><span class="sxs-lookup"><span data-stu-id="212d5-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="212d5-243">Usar um módulo para agrupar funções que atuam em coleções</span><span class="sxs-lookup"><span data-stu-id="212d5-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="212d5-244">Ao definir um tipo de coleção, considere fornecer um conjunto padrão de operações como `CollectionType.map` e `CollectionType.iter` ) para novos tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="212d5-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="212d5-245">Se você incluir esse módulo, siga as convenções de nomenclatura padrão para as funções encontradas no FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="212d5-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="212d5-246">Use um módulo para agrupar funções para funções comuns e canônicas, especialmente em bibliotecas de matemática e DSL</span><span class="sxs-lookup"><span data-stu-id="212d5-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="212d5-247">Por exemplo, `Microsoft.FSharp.Core.Operators` é uma coleção aberta automaticamente de funções de nível superior (como `abs` e `sin` ) fornecida por FSharp. Core. dll.</span><span class="sxs-lookup"><span data-stu-id="212d5-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="212d5-248">Da mesma forma, uma biblioteca de estatísticas pode incluir um módulo com funções `erf` e `erfc` , em que esse módulo foi projetado para ser aberto explicitamente ou automaticamente.</span><span class="sxs-lookup"><span data-stu-id="212d5-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="212d5-249">Considere usar RequireQualifiedAccess e aplicar cuidadosamente os atributos AutoOpen</span><span class="sxs-lookup"><span data-stu-id="212d5-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="212d5-250">A adição do `[<RequireQualifiedAccess>]` atributo a um módulo indica que o módulo pode não estar aberto e que as referências aos elementos do módulo exigem acesso qualificado explícito.</span><span class="sxs-lookup"><span data-stu-id="212d5-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="212d5-251">Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="212d5-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="212d5-252">Isso é útil quando as funções e os valores no módulo têm nomes que provavelmente estão em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="212d5-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="212d5-253">Exigir acesso qualificado pode aumentar muito a manutenção e o evolucionabilidade de longo prazo de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="212d5-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="212d5-254">Adicionar o `[<AutoOpen>]` atributo a um módulo significa que o módulo será aberto quando o namespace recipiente for aberto.</span><span class="sxs-lookup"><span data-stu-id="212d5-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="212d5-255">O `[<AutoOpen>]` atributo também pode ser aplicado a um assembly para indicar um módulo que é aberto automaticamente quando o assembly é referenciado.</span><span class="sxs-lookup"><span data-stu-id="212d5-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="212d5-256">Por exemplo, uma biblioteca de estatísticas **MathsHeaven. Statistics** pode conter `module MathsHeaven.Statistics.Operators` funções contendo `erf` e `erfc` .</span><span class="sxs-lookup"><span data-stu-id="212d5-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="212d5-257">É razoável marcar esse módulo como `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="212d5-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="212d5-258">Isso significa `open MathsHeaven.Statistics` também abrir esse módulo e colocar os nomes `erf` e o `erfc` escopo.</span><span class="sxs-lookup"><span data-stu-id="212d5-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="212d5-259">Outro bom uso do `[<AutoOpen>]` é para módulos que contêm métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="212d5-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="212d5-260">O uso excessivo de `[<AutoOpen>]` clientes potenciais para namespaces poluidos e o atributo deve ser usado com cuidado.</span><span class="sxs-lookup"><span data-stu-id="212d5-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="212d5-261">Para bibliotecas específicas em domínios específicos, o uso criterioso de `[<AutoOpen>]` pode levar a uma melhor usabilidade.</span><span class="sxs-lookup"><span data-stu-id="212d5-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="212d5-262">Considere definir membros de operador em classes em que o uso de operadores conhecidos é apropriado</span><span class="sxs-lookup"><span data-stu-id="212d5-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="212d5-263">Às vezes, as classes são usadas para modelar construções matemáticas, como vetores.</span><span class="sxs-lookup"><span data-stu-id="212d5-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="212d5-264">Quando o domínio que está sendo modelado tem operadores bem conhecidos, defini-los como membros intrínsecos à classe é útil.</span><span class="sxs-lookup"><span data-stu-id="212d5-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="212d5-265">Esta orientação corresponde às diretrizes gerais do .NET para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="212d5-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="212d5-266">No entanto, ele também pode ser importante na codificação F #, pois isso permite que esses tipos sejam usados em conjunto com funções e métodos F # com restrições de membro, como List. sumBy.</span><span class="sxs-lookup"><span data-stu-id="212d5-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="212d5-267">Considere o uso de CompiledName para fornecer um. Nome amigável para rede para outros consumidores de linguagem .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="212d5-268">Às vezes, talvez você queira nomear algo em um estilo para consumidores de F # (como um membro estático em letras minúsculas para que ele apareça como se fosse uma função associada a um módulo), mas tenha um estilo diferente para o nome quando ele for compilado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="212d5-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="212d5-269">Você pode usar o `[<CompiledName>]` atributo para fornecer um estilo diferente para o código que não seja F # consumindo o assembly.</span><span class="sxs-lookup"><span data-stu-id="212d5-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="212d5-270">Usando o `[<CompiledName>]` , você pode usar as convenções de nomenclatura do .net para consumidores que não são do F # do assembly.</span><span class="sxs-lookup"><span data-stu-id="212d5-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="212d5-271">Use a sobrecarga de método para funções de membro, se isso fornecer uma API mais simples</span><span class="sxs-lookup"><span data-stu-id="212d5-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="212d5-272">A sobrecarga do método é uma ferramenta poderosa para simplificar uma API que pode precisar executar uma funcionalidade semelhante, mas com opções ou argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="212d5-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="212d5-273">Em F #, é mais comum sobrecarregar o número de argumentos em vez de tipos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="212d5-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="212d5-274">Oculte as representações de tipos de registro e União se o design desses tipos for provavelmente evoluir</span><span class="sxs-lookup"><span data-stu-id="212d5-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="212d5-275">Evite revelar representações concretas de objetos.</span><span class="sxs-lookup"><span data-stu-id="212d5-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="212d5-276">Por exemplo, a representação concreta dos <xref:System.DateTime> valores não é revelada pela API pública externa do design da biblioteca do .net.</span><span class="sxs-lookup"><span data-stu-id="212d5-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="212d5-277">Em tempo de execução, o Common Language Runtime sabe a implementação confirmada que será usada durante toda a execução.</span><span class="sxs-lookup"><span data-stu-id="212d5-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="212d5-278">No entanto, o código compilado não pega as dependências na representação concreta.</span><span class="sxs-lookup"><span data-stu-id="212d5-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="212d5-279">Evite o uso da herança de implementação para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="212d5-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="212d5-280">Em F #, a herança de implementação raramente é usada.</span><span class="sxs-lookup"><span data-stu-id="212d5-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="212d5-281">Além disso, as hierarquias de herança geralmente são complexas e difíceis de alterar quando novos requisitos chegam.</span><span class="sxs-lookup"><span data-stu-id="212d5-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="212d5-282">A implementação de herança ainda existe em F # para compatibilidade e casos raros em que é a melhor solução para um problema, mas técnicas alternativas devem ser buscadas em seus programas em F # durante a criação de polimorfismo, como implementação de interface.</span><span class="sxs-lookup"><span data-stu-id="212d5-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="212d5-283">Assinaturas de funções e membros</span><span class="sxs-lookup"><span data-stu-id="212d5-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="212d5-284">Usar tuplas para valores de retorno ao retornar um pequeno número de vários valores não relacionados</span><span class="sxs-lookup"><span data-stu-id="212d5-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="212d5-285">Este é um bom exemplo do uso de uma tupla em um tipo de retorno:</span><span class="sxs-lookup"><span data-stu-id="212d5-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="212d5-286">Para tipos de retorno que contêm muitos componentes ou onde os componentes estão relacionados a uma única entidade identificável, considere usar um tipo nomeado em vez de uma tupla.</span><span class="sxs-lookup"><span data-stu-id="212d5-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="212d5-287">Usar `Async<T>` para programação assíncrona em limites de API F #</span><span class="sxs-lookup"><span data-stu-id="212d5-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="212d5-288">Se houver uma operação síncrona correspondente chamada `Operation` que retorna um `T` , a operação assíncrona deverá ser nomeada `AsyncOperation` se retornar `Async<T>` ou `OperationAsync` se retornar `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="212d5-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="212d5-289">Para tipos .NET comumente usados que expõem os métodos Begin/End, considere usar `Async.FromBeginEnd` o para gravar métodos de extensão como uma fachada para fornecer o modelo de programação de F # Async para essas APIs .net.</span><span class="sxs-lookup"><span data-stu-id="212d5-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="212d5-290">Exceções</span><span class="sxs-lookup"><span data-stu-id="212d5-290">Exceptions</span></span>

<span data-ttu-id="212d5-291">Consulte [Gerenciamento de erros](conventions.md#error-management) para saber mais sobre o uso apropriado de exceções, resultados e opções.</span><span class="sxs-lookup"><span data-stu-id="212d5-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="212d5-292">Membros de extensão</span><span class="sxs-lookup"><span data-stu-id="212d5-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="212d5-293">Aplicar cuidadosamente membros de extensão F # em componentes F #-to-F #</span><span class="sxs-lookup"><span data-stu-id="212d5-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="212d5-294">Os membros de extensão F # geralmente devem ser usados apenas para operações que estão no fechamento de operações intrínsecas associadas a um tipo na maioria dos seus modos de uso.</span><span class="sxs-lookup"><span data-stu-id="212d5-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="212d5-295">Um uso comum é fornecer APIs que são mais idiomática a F # para vários tipos .NET:</span><span class="sxs-lookup"><span data-stu-id="212d5-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="212d5-296">Tipos de União</span><span class="sxs-lookup"><span data-stu-id="212d5-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="212d5-297">Usar uniões discriminadas em vez de hierarquias de classe para dados estruturados em árvore</span><span class="sxs-lookup"><span data-stu-id="212d5-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="212d5-298">As estruturas do tipo árvore são definidas recursivamente.</span><span class="sxs-lookup"><span data-stu-id="212d5-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="212d5-299">Isso é estranho com a herança, mas elegante com uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="212d5-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="212d5-300">A representação de dados do tipo árvore com uniões discriminadas também permite que você se beneficie da exaustivaidade na correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="212d5-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="212d5-301">Use `[<RequireQualifiedAccess>]` em tipos de União cujos nomes de caso não sejam exclusivos o suficiente</span><span class="sxs-lookup"><span data-stu-id="212d5-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="212d5-302">Você pode se deparar em um domínio em que o mesmo nome seja o melhor para coisas diferentes, como casos de União discriminados.</span><span class="sxs-lookup"><span data-stu-id="212d5-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="212d5-303">Você pode usar `[<RequireQualifiedAccess>]` para desambiguar nomes de casos para evitar o disparo de erros confusos devido ao sombreamento dependente da ordem das `open` instruções</span><span class="sxs-lookup"><span data-stu-id="212d5-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="212d5-304">Ocultar as representações de uniões discriminadas para APIs compatíveis com binários se o design desses tipos for provavelmente evoluir</span><span class="sxs-lookup"><span data-stu-id="212d5-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="212d5-305">Tipos de União dependem de formulários de correspondência de padrão F # para um modelo de programação sucinto.</span><span class="sxs-lookup"><span data-stu-id="212d5-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="212d5-306">Conforme mencionado anteriormente, você deve evitar revelar representações concretas de dados se o design desses tipos for provavelmente evoluir.</span><span class="sxs-lookup"><span data-stu-id="212d5-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="212d5-307">Por exemplo, a representação de uma união discriminada pode ser ocultada usando uma declaração privada ou interna, ou usando um arquivo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="212d5-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="212d5-308">Se você revelar as uniões discriminadas indiscriminadamente, poderá achar difícil fazer a versão da biblioteca sem quebrar o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="212d5-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="212d5-309">Em vez disso, considere revelar um ou mais padrões ativos para permitir a correspondência de padrões sobre os valores de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="212d5-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="212d5-310">Os padrões ativos fornecem uma maneira alternativa de fornecer aos consumidores de F # uma correspondência de padrões e, ao mesmo tempo, evitar expor tipos de União F # diretamente.</span><span class="sxs-lookup"><span data-stu-id="212d5-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="212d5-311">Funções embutidas e restrições de membro</span><span class="sxs-lookup"><span data-stu-id="212d5-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="212d5-312">Definir algoritmos numéricos genéricos usando funções embutidas com restrições de membro implícitas e tipos genéricos resolvidos estaticamente</span><span class="sxs-lookup"><span data-stu-id="212d5-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="212d5-313">As restrições de membro aritméticos e as restrições de comparação F # são um padrão para a programação F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="212d5-314">Por exemplo, considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="212d5-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="212d5-315">O tipo dessa função é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="212d5-316">Essa é uma função adequada para uma API pública em uma biblioteca matemática.</span><span class="sxs-lookup"><span data-stu-id="212d5-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="212d5-317">Evite usar restrições de membro para simular classes de tipo e digitação pato</span><span class="sxs-lookup"><span data-stu-id="212d5-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="212d5-318">É possível simular "digitação pato" usando restrições de membro F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="212d5-319">No entanto, os membros que fazem uso dele não devem ser usados em geral em designs de biblioteca F #-to-F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="212d5-320">Isso ocorre porque os designs de biblioteca baseados em restrições implícitas desconhecidas ou não padrão tendem a fazer com que o código do usuário se torne inflexível e esteja vinculado a um padrão de estrutura específico.</span><span class="sxs-lookup"><span data-stu-id="212d5-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="212d5-321">Além disso, há uma boa chance de que o uso intensivo de restrições de membro dessa maneira possa resultar em tempos de compilação muito longos.</span><span class="sxs-lookup"><span data-stu-id="212d5-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="212d5-322">Definições de operador</span><span class="sxs-lookup"><span data-stu-id="212d5-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="212d5-323">Evite definir operadores simbólicos personalizados</span><span class="sxs-lookup"><span data-stu-id="212d5-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="212d5-324">Os operadores personalizados são essenciais em algumas situações e são dispositivos de notação altamente úteis dentro de um grande corpo de código de implementação.</span><span class="sxs-lookup"><span data-stu-id="212d5-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="212d5-325">Para novos usuários de uma biblioteca, as funções nomeadas costumam ser mais fáceis de usar.</span><span class="sxs-lookup"><span data-stu-id="212d5-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="212d5-326">Além disso, os operadores simbólicos personalizados podem ser difíceis de documentar e os usuários acham mais difícil procurar ajuda nos operadores, devido a limitações existentes nos mecanismos IDE e de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="212d5-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="212d5-327">Como resultado, é melhor publicar sua funcionalidade como funções e membros nomeados e, além disso, expor os operadores para essa funcionalidade somente se os benefícios da notação superarem a documentação e o custo cognitiva de tê-los.</span><span class="sxs-lookup"><span data-stu-id="212d5-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="212d5-328">Unidades de medida</span><span class="sxs-lookup"><span data-stu-id="212d5-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="212d5-329">Use cuidadosamente as unidades de medida para a segurança de tipo adicionado no código F #</span><span class="sxs-lookup"><span data-stu-id="212d5-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="212d5-330">Informações adicionais de digitação para unidades de medida são apagadas quando exibidas por outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="212d5-331">Lembre-se de que os componentes, as ferramentas e a reflexão do .NET verão tipos de unidades SANs.</span><span class="sxs-lookup"><span data-stu-id="212d5-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="212d5-332">Por exemplo, os consumidores do C# verão, `float` em vez de `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="212d5-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="212d5-333">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="212d5-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="212d5-334">Use cuidadosamente abreviações de tipo para simplificar o código F #</span><span class="sxs-lookup"><span data-stu-id="212d5-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="212d5-335">Componentes, ferramentas e reflexo do .NET não verão nomes abreviados para tipos.</span><span class="sxs-lookup"><span data-stu-id="212d5-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="212d5-336">O uso significativo das abreviações de tipo também pode fazer com que um domínio pareça mais complexo do que realmente é, o que poderia confundir os consumidores.</span><span class="sxs-lookup"><span data-stu-id="212d5-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="212d5-337">Evite abreviações de tipo para tipos públicos cujos membros e propriedades devam ser intrinsecamente diferentes para aqueles disponíveis no tipo que está sendo abreviado</span><span class="sxs-lookup"><span data-stu-id="212d5-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="212d5-338">Nesse caso, o tipo que está sendo abreviado revela muito sobre a representação do tipo real que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="212d5-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="212d5-339">Em vez disso, considere encapsular a abreviação em um tipo de classe ou uma união discriminada de caso único (ou, quando o desempenho for essencial, considere usar um tipo de struct para encapsular a abreviação).</span><span class="sxs-lookup"><span data-stu-id="212d5-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="212d5-340">Por exemplo, é tentador definir um mapa múltiplo como um caso especial de um mapa F #, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="212d5-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="212d5-341">No entanto, as operações de notação de ponto lógico nesse tipo não são as mesmas que as operações em um mapa – por exemplo, é razoável que o mapa do operador de pesquisa. [chave] retorna a lista vazia se a chave não estiver no dicionário, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="212d5-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="212d5-342">Diretrizes para bibliotecas para uso de outras linguagens do .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="212d5-343">Ao criar bibliotecas para uso de outras linguagens do .NET, é importante aderir às diretrizes de [design da biblioteca do .net](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="212d5-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="212d5-344">Neste documento, essas bibliotecas são rotuladas como bibliotecas de .NET da baunilha, em oposição às bibliotecas voltadas para o F # que usam construções F # sem restrição.</span><span class="sxs-lookup"><span data-stu-id="212d5-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="212d5-345">A criação de bibliotecas .NET da baunilha significa fornecer APIs familiares e idiomática consistentes com o restante dos .NET Framework minimizando o uso de construções específicas de F # na API pública.</span><span class="sxs-lookup"><span data-stu-id="212d5-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="212d5-346">As regras são explicadas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="212d5-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="212d5-347">Namespace e tipo design (para bibliotecas para uso de outras linguagens .NET)</span><span class="sxs-lookup"><span data-stu-id="212d5-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="212d5-348">Aplicar as convenções de nomenclatura do .NET à API pública de seus componentes</span><span class="sxs-lookup"><span data-stu-id="212d5-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="212d5-349">Preste atenção especial ao uso de nomes abreviados e das diretrizes de capitalização do .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="212d5-350">Usar namespaces, tipos e membros como a estrutura organizacional principal para seus componentes</span><span class="sxs-lookup"><span data-stu-id="212d5-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="212d5-351">Todos os arquivos que contêm a funcionalidade pública devem começar com uma `namespace` declaração e as únicas entidades voltadas para o público em namespaces devem ser tipos.</span><span class="sxs-lookup"><span data-stu-id="212d5-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="212d5-352">Não use módulos F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-352">Do not use F# modules.</span></span>

<span data-ttu-id="212d5-353">Use módulos não públicos para manter o código de implementação, tipos de utilitário e funções de utilitário.</span><span class="sxs-lookup"><span data-stu-id="212d5-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="212d5-354">Os tipos estáticos devem ser preferidos em relação aos módulos, pois permitem a evolução futura da API usar sobrecarga e outros conceitos de design de API do .NET que não podem ser usados em módulos F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="212d5-355">Por exemplo, no lugar da seguinte API pública:</span><span class="sxs-lookup"><span data-stu-id="212d5-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="212d5-356">Em vez disso, considere:</span><span class="sxs-lookup"><span data-stu-id="212d5-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="212d5-357">Use os tipos de registro F # nas APIs do .NET da baunilha se o design dos tipos não evoluir</span><span class="sxs-lookup"><span data-stu-id="212d5-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="212d5-358">Os tipos de registro F # são compilados em uma classe .NET simples.</span><span class="sxs-lookup"><span data-stu-id="212d5-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="212d5-359">Elas são adequadas para alguns tipos simples e estáveis em APIs.</span><span class="sxs-lookup"><span data-stu-id="212d5-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="212d5-360">Considere o uso `[<NoEquality>]` dos `[<NoComparison>]` atributos e para suprimir a geração automática de interfaces.</span><span class="sxs-lookup"><span data-stu-id="212d5-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="212d5-361">Além disso, evite usar campos de registro mutáveis nas APIs do .NET da baunilha, pois eles expõem um campo público.</span><span class="sxs-lookup"><span data-stu-id="212d5-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="212d5-362">Sempre considere se uma classe forneceria uma opção mais flexível para a evolução futura da API.</span><span class="sxs-lookup"><span data-stu-id="212d5-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="212d5-363">Por exemplo, o código F # a seguir expõe a API pública para um consumidor de C#:</span><span class="sxs-lookup"><span data-stu-id="212d5-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="212d5-364">F#:</span><span class="sxs-lookup"><span data-stu-id="212d5-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="212d5-365">C#:</span><span class="sxs-lookup"><span data-stu-id="212d5-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="212d5-366">Ocultar a representação dos tipos de União F # nas APIs do .NET da baunilha</span><span class="sxs-lookup"><span data-stu-id="212d5-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="212d5-367">Tipos de União f # geralmente não são usados em limites de componentes, mesmo para codificação F # para F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="212d5-368">Eles são um dispositivo de implementação excelente quando usados internamente em componentes e bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="212d5-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="212d5-369">Ao criar uma API .NET da baunilha, considere ocultar a representação de um tipo Union usando uma declaração particular ou um arquivo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="212d5-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="212d5-370">Você também pode aumentar os tipos que usam uma representação Union internamente com membros para fornecer um desejado. API voltada para o .net.</span><span class="sxs-lookup"><span data-stu-id="212d5-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="212d5-371">Criar GUI e outros componentes usando os padrões de design da estrutura</span><span class="sxs-lookup"><span data-stu-id="212d5-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="212d5-372">Há muitas estruturas diferentes disponíveis no .NET, como WinForms, WPF e ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="212d5-373">As convenções de nomenclatura e design para cada uma devem ser usadas se você estiver criando componentes para uso nessas estruturas.</span><span class="sxs-lookup"><span data-stu-id="212d5-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="212d5-374">Por exemplo, para a programação do WPF, adote os padrões de design do WPF para as classes que você está projetando.</span><span class="sxs-lookup"><span data-stu-id="212d5-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="212d5-375">Para modelos na programação de interface do usuário, use padrões de design, como eventos e coleções baseadas em notificação, como aqueles encontrados no <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="212d5-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="212d5-376">Design de objeto e membro (para bibliotecas para uso de outras linguagens do .NET)</span><span class="sxs-lookup"><span data-stu-id="212d5-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="212d5-377">Usar o atributo CLIEvent para expor eventos .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="212d5-378">Construa um `DelegateEvent` com um tipo de delegado .net específico que usa um objeto e `EventArgs` (em vez de um `Event` , que usa apenas o `FSharpHandler` tipo por padrão) para que os eventos sejam publicados da maneira familiar para outras linguagens .net.</span><span class="sxs-lookup"><span data-stu-id="212d5-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="212d5-379">Expor operações assíncronas como métodos que retornam tarefas .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="212d5-380">As tarefas são usadas no .NET para representar Computações assíncronas ativas.</span><span class="sxs-lookup"><span data-stu-id="212d5-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="212d5-381">As tarefas estão em geral menos composições que objetos F # `Async<T>` , já que representam tarefas "já em execução" e não podem ser compostas de maneiras que executam composição paralela ou que ocultam a propagação de sinais de cancelamento e outros parâmetros contextuais.</span><span class="sxs-lookup"><span data-stu-id="212d5-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="212d5-382">No entanto, apesar disso, os métodos que retornam tarefas são a representação padrão da programação assíncrona no .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="212d5-383">Geralmente, você também desejará aceitar um token de cancelamento explícito:</span><span class="sxs-lookup"><span data-stu-id="212d5-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="212d5-384">Usar tipos de delegado do .NET em vez de tipos de função F #</span><span class="sxs-lookup"><span data-stu-id="212d5-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="212d5-385">Aqui "tipos de função F #" significam tipos de "seta" como `int -> int` .</span><span class="sxs-lookup"><span data-stu-id="212d5-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="212d5-386">Em vez disso:</span><span class="sxs-lookup"><span data-stu-id="212d5-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="212d5-387">Faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="212d5-388">O tipo de função F # aparece como `class FSharpFunc<T,U>` em outras linguagens .net e é menos adequado para recursos de linguagem e ferramentas que compreendem tipos delegados.</span><span class="sxs-lookup"><span data-stu-id="212d5-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="212d5-389">Ao criar um método de ordem superior direcionado .NET Framework 3,5 ou superior, os `System.Func` `System.Action` delegados e são as APIs certas para publicar para permitir que os desenvolvedores do .net consumam essas APIs de maneira baixa-fricção.</span><span class="sxs-lookup"><span data-stu-id="212d5-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="212d5-390">(Ao direcionar .NET Framework 2,0, os tipos delegados definidos pelo sistema são mais limitados; considere usar tipos delegados predefinidos, como `System.Converter<T,U>` ou definir um tipo de delegado específico.)</span><span class="sxs-lookup"><span data-stu-id="212d5-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="212d5-391">No lado do inverso, os delegados do .NET não são naturais para bibliotecas voltadas para o F # (consulte a próxima seção sobre bibliotecas em F #).</span><span class="sxs-lookup"><span data-stu-id="212d5-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="212d5-392">Como resultado, uma estratégia de implementação comum ao desenvolver métodos de ordem superior para as bibliotecas do .NET da baunilha é criar toda a implementação usando tipos de função F # e, em seguida, criar a API pública usando delegados como uma fachada fina sobre a implementação real de F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="212d5-393">Use o padrão TryGetValue em vez de retornar valores de opção F # e prefira o sobrecarregamento de método para usar valores de opção F # como argumentos</span><span class="sxs-lookup"><span data-stu-id="212d5-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="212d5-394">Os padrões comuns de uso para o tipo de opção F # em APIs são melhor implementados nas APIs do .NET da baunilha usando técnicas de design padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="212d5-395">Em vez de retornar um valor de opção de F #, considere usar o tipo de retorno bool mais um parâmetro out como no padrão "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="212d5-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="212d5-396">E em vez de usar valores de opção F # como parâmetros, considere o uso de sobrecarga de método ou argumentos opcionais.</span><span class="sxs-lookup"><span data-stu-id="212d5-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="212d5-397">Use os tipos de interface de coleção do .NET IEnumerable \< T \> e IDictionary \< Key, valor \> para parâmetros e valores de retorno</span><span class="sxs-lookup"><span data-stu-id="212d5-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="212d5-398">Evite o uso de tipos de coleção concretos, como matrizes .NET `T[]` , tipos F # `list<T>` `Map<Key,Value>` e `Set<T>` tipos de coleção concretos .NET `Dictionary<Key,Value>` , como.</span><span class="sxs-lookup"><span data-stu-id="212d5-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="212d5-399">As diretrizes de design de biblioteca do .NET têm bons conselhos sobre quando usar vários tipos de coleção como o `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="212d5-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="212d5-400">Um pouco de uso de matrizes ( `T[]` ) é aceitável em algumas circunstâncias, no aterramento de desempenho.</span><span class="sxs-lookup"><span data-stu-id="212d5-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="212d5-401">Observe especialmente que `seq<T>` é apenas o alias F # para `IEnumerable<T>` e, portanto, seq é geralmente um tipo apropriado para uma API .NET da baunilha.</span><span class="sxs-lookup"><span data-stu-id="212d5-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="212d5-402">Em vez de listas F #:</span><span class="sxs-lookup"><span data-stu-id="212d5-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="212d5-403">Usar sequências F #:</span><span class="sxs-lookup"><span data-stu-id="212d5-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="212d5-404">Use o tipo de unidade como o único tipo de entrada de um método para definir um método de argumento zero ou como o único tipo de retorno para definir um método de retorno nulo</span><span class="sxs-lookup"><span data-stu-id="212d5-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="212d5-405">Evite outros usos do tipo de unidade.</span><span class="sxs-lookup"><span data-stu-id="212d5-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="212d5-406">Eles são bons:</span><span class="sxs-lookup"><span data-stu-id="212d5-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="212d5-407">Isso é inadequado:</span><span class="sxs-lookup"><span data-stu-id="212d5-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="212d5-408">Verificar valores nulos nos limites da API .NET da baunilha</span><span class="sxs-lookup"><span data-stu-id="212d5-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="212d5-409">O código de implementação de F # tende a ter menos valores nulos, devido a padrões de design imutáveis e restrições no uso de literais nulos para tipos F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="212d5-410">Outras linguagens .NET geralmente usam NULL como um valor com muito mais frequência.</span><span class="sxs-lookup"><span data-stu-id="212d5-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="212d5-411">Por isso, o código F # que está expondo uma API .NET da baunilha deve verificar os parâmetros de NULL no limite da API e impedir que esses valores fluam mais profundamente no código de implementação do F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="212d5-412">A `isNull` função ou o padrão correspondente no `null` padrão pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="212d5-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="212d5-413">Evite usar tuplas como valores de retorno</span><span class="sxs-lookup"><span data-stu-id="212d5-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="212d5-414">Em vez disso, prefira retornar um tipo nomeado contendo os dados agregados ou usar parâmetros de saída para retornar vários valores.</span><span class="sxs-lookup"><span data-stu-id="212d5-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="212d5-415">Embora exista tuplas e tuplas de struct no .NET (incluindo suporte a linguagem C# para tuplas struct), elas geralmente não fornecem a API ideal e esperada para desenvolvedores .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="212d5-416">Evitar o uso de currying de parâmetros</span><span class="sxs-lookup"><span data-stu-id="212d5-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="212d5-417">Em vez disso, use as convenções de chamada .NET `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="212d5-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="212d5-418">Dica: se você estiver criando bibliotecas para uso a partir de qualquer linguagem .NET, não há nenhum substituto para realmente fazer um C# experimental e Visual Basic programação para garantir que suas bibliotecas "fiquem corretas" nessas linguagens.</span><span class="sxs-lookup"><span data-stu-id="212d5-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="212d5-419">Você também pode usar ferramentas como o reflector do .NET e o pesquisador de objetos do Visual Studio para garantir que as bibliotecas e sua documentação apareçam conforme o esperado para os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="212d5-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="212d5-420">Apêndice</span><span class="sxs-lookup"><span data-stu-id="212d5-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="212d5-421">Exemplo de ponta a ponta de criação de código F # para uso por outras linguagens .NET</span><span class="sxs-lookup"><span data-stu-id="212d5-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="212d5-422">Considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="212d5-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="212d5-423">O tipo F # inferido dessa classe é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="212d5-424">Vamos dar uma olhada em como esse tipo F # aparece para um programador usando outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="212d5-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="212d5-425">Por exemplo, a "assinatura" aproximada do C# é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="212d5-426">Há alguns pontos importantes a serem observados sobre como F # representa construções aqui.</span><span class="sxs-lookup"><span data-stu-id="212d5-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="212d5-427">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="212d5-427">For example:</span></span>

* <span data-ttu-id="212d5-428">Metadados como nomes de argumentos foram preservados.</span><span class="sxs-lookup"><span data-stu-id="212d5-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="212d5-429">Os métodos F # que usam dois argumentos se tornam métodos C# que usam dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="212d5-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="212d5-430">Funções e listas se tornam referências a tipos correspondentes na biblioteca F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="212d5-431">O código a seguir mostra como ajustar esse código para levar essas coisas em conta.</span><span class="sxs-lookup"><span data-stu-id="212d5-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="212d5-432">O tipo F # inferido do código é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="212d5-433">A assinatura do C# agora é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="212d5-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="212d5-434">As correções feitas para preparar esse tipo para uso como parte de uma biblioteca .NET da baunilha são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="212d5-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="212d5-435">Ajustou vários nomes: `Point1` ,, `n` `l` , e tornou-se `f` `RadialPoint` , `count` , `factor` e `transform` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="212d5-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="212d5-436">Usou um tipo de retorno de `seq<RadialPoint>` em vez de `RadialPoint list` alterando uma construção de lista usando `[ ... ]` para uma construção de sequência usando `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="212d5-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="212d5-437">Usado o tipo de delegado do .NET `System.Func` em vez de um tipo de função F #.</span><span class="sxs-lookup"><span data-stu-id="212d5-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="212d5-438">Isso torna muito mais fácil consumir em código C#.</span><span class="sxs-lookup"><span data-stu-id="212d5-438">This makes it far nicer to consume in C# code.</span></span>
