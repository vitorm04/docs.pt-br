---
title: F#diretrizes de design do componente
description: Saiba as diretrizes para gravação F# componentes destinadas ao consumo por outros chamadores.
ms.date: 05/14/2018
ms.openlocfilehash: bc8d4908912c4630f649ba30593d43a557278efa
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145667"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="d63ff-103">F#diretrizes de design do componente</span><span class="sxs-lookup"><span data-stu-id="d63ff-103">F# component design guidelines</span></span>

<span data-ttu-id="d63ff-104">Este documento é um conjunto de diretrizes de design do componente para F# de programação, com base no F# diretrizes de Design do componente, v14, Microsoft Research, e [outra versão](https://fsharp.org/specs/component-design-guidelines/) originalmente coletados e mantidos pelo F# Software Foundation.</span><span class="sxs-lookup"><span data-stu-id="d63ff-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="d63ff-105">Este documento pressupõe que você esteja familiarizado com F# de programação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="d63ff-106">Muitos agradecimentos para os F# comunidade por suas contribuições e comentários úteis em diversas versões deste guia.</span><span class="sxs-lookup"><span data-stu-id="d63ff-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="d63ff-107">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d63ff-107">Overview</span></span>

<span data-ttu-id="d63ff-108">Este documento aborda alguns dos problemas relacionados ao F# componente design e codificação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="d63ff-109">Um componente pode significar qualquer um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d63ff-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="d63ff-110">Uma camada em seu F# projeto que tem os consumidores externos dentro desse projeto.</span><span class="sxs-lookup"><span data-stu-id="d63ff-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="d63ff-111">Uma biblioteca destinada ao consumo por F# código em limites de assembly.</span><span class="sxs-lookup"><span data-stu-id="d63ff-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="d63ff-112">Uma biblioteca destinada ao consumo por qualquer linguagem .NET em limites de assembly.</span><span class="sxs-lookup"><span data-stu-id="d63ff-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="d63ff-113">Uma biblioteca destinada para distribuição por meio de um repositório de pacotes, tais como [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="d63ff-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="d63ff-114">Técnicas descritas neste artigo seguem o [cinco princípios bom F# código](index.md#five-principles-of-good-f-code)e, portanto, utilizar ambos funcional e objeto de programação conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="d63ff-115">Independentemente da metodologia, o designer de componente e a biblioteca de faces de inúmeros problemas práticos e prosaicas ao tentar criar uma API que pode ser usada com mais facilidade pelos desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d63ff-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="d63ff-116">Aplicativo tem consciência do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md) conduzam para a criação de um conjunto consistente de APIs que são agradáveis consumir.</span><span class="sxs-lookup"><span data-stu-id="d63ff-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="d63ff-117">Diretrizes gerais</span><span class="sxs-lookup"><span data-stu-id="d63ff-117">General guidelines</span></span>

<span data-ttu-id="d63ff-118">Há algumas diretrizes universais que se aplicam a F# bibliotecas, independentemente do público-alvo para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d63ff-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="d63ff-119">Saiba as diretrizes de Design de biblioteca do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="d63ff-120">Independentemente do tipo de F# de codificação que está fazendo, é importante ter um conhecimento prático do [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="d63ff-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="d63ff-121">A maioria dos outros F# e os programadores do .NET estar familiarizado com essas diretrizes e esperar que o código .NET em conformidade com a eles.</span><span class="sxs-lookup"><span data-stu-id="d63ff-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="d63ff-122">Diretrizes de Design da biblioteca do .NET fornecem diretrizes gerais sobre nomenclatura, projetando classes e interfaces, design de membro (propriedades, métodos, eventos, etc.) e muito mais e são um útil primeiro ponto de referência para uma variedade de diretrizes de design.</span><span class="sxs-lookup"><span data-stu-id="d63ff-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="d63ff-123">Adicionar comentários de documentação XML ao seu código</span><span class="sxs-lookup"><span data-stu-id="d63ff-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="d63ff-124">Documentação XML nas APIs públicas Certifique-se de que os usuários podem obter excelente Intellisense e em Informaçãorápida, ao usar esses tipos e membros e habilitar compilar documentação arquivos para a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d63ff-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="d63ff-125">Consulte a [documentação XML](../language-reference/xml-documentation.md) sobre várias marcas xml que podem ser usadas para marcação adicional dentro de comentários xmldoc.</span><span class="sxs-lookup"><span data-stu-id="d63ff-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="d63ff-126">Você pode usar os comentários XML de forma abreviada (`/// comment`), ou comentários XML padrão (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="d63ff-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="d63ff-127">Considere o uso de arquivos de assinatura explícita (. FSI) para a biblioteca estável e APIs de componente</span><span class="sxs-lookup"><span data-stu-id="d63ff-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="d63ff-128">Usando arquivos de assinaturas explícita em uma F# biblioteca fornece um resumo sucinto do API pública, que ajuda a garantir que você saiba público completo superfície da sua biblioteca fornece uma separação clara entre a documentação do pública e interno detalhes de implementação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="d63ff-129">Observe que os arquivos de assinatura adicione atrito para alterar a API pública, exigindo que alterações sejam feitas em arquivos de implementação e a assinatura.</span><span class="sxs-lookup"><span data-stu-id="d63ff-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="d63ff-130">Como resultado, arquivos de assinatura devem normalmente ser introduzidos somente quando uma API se tornam solidificou e não deve ser alterado significativamente.</span><span class="sxs-lookup"><span data-stu-id="d63ff-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="d63ff-131">Sempre siga práticas recomendadas para usar cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="d63ff-132">Siga [práticas recomendadas para usar cadeias de caracteres no .NET](../../standard/base-types/best-practices-strings.md) diretrizes.</span><span class="sxs-lookup"><span data-stu-id="d63ff-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="d63ff-133">Em particular, sempre especificar claramente *intenção cultura* na conversão e comparação de cadeias de caracteres (quando aplicável).</span><span class="sxs-lookup"><span data-stu-id="d63ff-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="d63ff-134">Diretrizes para F#-voltado para a bibliotecas</span><span class="sxs-lookup"><span data-stu-id="d63ff-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="d63ff-135">Esta seção apresenta recomendações para o desenvolvimento público F#-voltado para a bibliotecas; ou seja, as bibliotecas expondo as APIs públicas que se destinam a serem consumidos por F# os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d63ff-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="d63ff-136">Há uma variedade de recomendações de design de bibliotecas aplicáveis especificamente ao F#.</span><span class="sxs-lookup"><span data-stu-id="d63ff-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="d63ff-137">Na ausência das recomendações específicas que seguem, as diretrizes de Design de biblioteca do .NET são as diretrizes de fallback.</span><span class="sxs-lookup"><span data-stu-id="d63ff-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="d63ff-138">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="d63ff-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="d63ff-139">Usar convenções de nomenclatura e capitalização do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="d63ff-140">A tabela a seguir segue as convenções de nomenclatura e capitalização do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="d63ff-141">Há adições pequenas para incluir também as F# constrói.</span><span class="sxs-lookup"><span data-stu-id="d63ff-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="d63ff-142">Constructo</span><span class="sxs-lookup"><span data-stu-id="d63ff-142">Construct</span></span> | <span data-ttu-id="d63ff-143">Caso</span><span class="sxs-lookup"><span data-stu-id="d63ff-143">Case</span></span> | <span data-ttu-id="d63ff-144">Parte</span><span class="sxs-lookup"><span data-stu-id="d63ff-144">Part</span></span> | <span data-ttu-id="d63ff-145">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d63ff-145">Examples</span></span> | <span data-ttu-id="d63ff-146">Observações</span><span class="sxs-lookup"><span data-stu-id="d63ff-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="d63ff-147">Tipos concretos</span><span class="sxs-lookup"><span data-stu-id="d63ff-147">Concrete types</span></span> | <span data-ttu-id="d63ff-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-148">PascalCase</span></span> | <span data-ttu-id="d63ff-149">Substantivo / adjetivas</span><span class="sxs-lookup"><span data-stu-id="d63ff-149">Noun/ adjective</span></span> | <span data-ttu-id="d63ff-150">Lista, Double, complexo</span><span class="sxs-lookup"><span data-stu-id="d63ff-150">List, Double, Complex</span></span> | <span data-ttu-id="d63ff-151">Tipos concretos são estruturas, classes, enumerações, delegados, registros e uniões.</span><span class="sxs-lookup"><span data-stu-id="d63ff-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="d63ff-152">Embora os nomes de tipo são tradicionalmente minúsculos no OCaml, F# adotou o esquema de nomenclatura do .NET para tipos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="d63ff-153">DLLs</span><span class="sxs-lookup"><span data-stu-id="d63ff-153">DLLs</span></span>           | <span data-ttu-id="d63ff-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-154">PascalCase</span></span> |                 | <span data-ttu-id="d63ff-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="d63ff-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="d63ff-156">Marcas de união</span><span class="sxs-lookup"><span data-stu-id="d63ff-156">Union tags</span></span>     | <span data-ttu-id="d63ff-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-157">PascalCase</span></span> | <span data-ttu-id="d63ff-158">Substantivo</span><span class="sxs-lookup"><span data-stu-id="d63ff-158">Noun</span></span> | <span data-ttu-id="d63ff-159">Alguns, adicionar, sucesso</span><span class="sxs-lookup"><span data-stu-id="d63ff-159">Some, Add, Success</span></span> | <span data-ttu-id="d63ff-160">Não use um prefixo em APIs públicas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="d63ff-161">Opcionalmente, use um prefixo ao internos, como ' Digite equipes = TAlpha</span><span class="sxs-lookup"><span data-stu-id="d63ff-161">Optionally use a prefix when internal, such as \`type Teams = TAlpha</span></span> | <span data-ttu-id="d63ff-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="d63ff-162">TBeta</span></span> | <span data-ttu-id="d63ff-163">TDelta.'</span><span class="sxs-lookup"><span data-stu-id="d63ff-163">TDelta.\`</span></span> |
| <span data-ttu-id="d63ff-164">evento</span><span class="sxs-lookup"><span data-stu-id="d63ff-164">Event</span></span>          | <span data-ttu-id="d63ff-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-165">PascalCase</span></span> | <span data-ttu-id="d63ff-166">Verbo</span><span class="sxs-lookup"><span data-stu-id="d63ff-166">Verb</span></span> | <span data-ttu-id="d63ff-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="d63ff-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="d63ff-168">Exceções</span><span class="sxs-lookup"><span data-stu-id="d63ff-168">Exceptions</span></span>     | <span data-ttu-id="d63ff-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-169">PascalCase</span></span> |      | <span data-ttu-id="d63ff-170">WebException</span><span class="sxs-lookup"><span data-stu-id="d63ff-170">WebException</span></span> | <span data-ttu-id="d63ff-171">Nome deve terminar com "Exception".</span><span class="sxs-lookup"><span data-stu-id="d63ff-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="d63ff-172">Campo</span><span class="sxs-lookup"><span data-stu-id="d63ff-172">Field</span></span>          | <span data-ttu-id="d63ff-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-173">PascalCase</span></span> | <span data-ttu-id="d63ff-174">Substantivo</span><span class="sxs-lookup"><span data-stu-id="d63ff-174">Noun</span></span> | <span data-ttu-id="d63ff-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="d63ff-175">CurrentName</span></span>  | |
| <span data-ttu-id="d63ff-176">Tipos de interface</span><span class="sxs-lookup"><span data-stu-id="d63ff-176">Interface types</span></span> |  <span data-ttu-id="d63ff-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-177">PascalCase</span></span> | <span data-ttu-id="d63ff-178">Substantivo / adjetivas</span><span class="sxs-lookup"><span data-stu-id="d63ff-178">Noun/ adjective</span></span> | <span data-ttu-id="d63ff-179">IDisposable</span><span class="sxs-lookup"><span data-stu-id="d63ff-179">IDisposable</span></span> | <span data-ttu-id="d63ff-180">Nome deve começar com "I".</span><span class="sxs-lookup"><span data-stu-id="d63ff-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="d63ff-181">Método</span><span class="sxs-lookup"><span data-stu-id="d63ff-181">Method</span></span> |  <span data-ttu-id="d63ff-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-182">PascalCase</span></span> |  <span data-ttu-id="d63ff-183">Verbo</span><span class="sxs-lookup"><span data-stu-id="d63ff-183">Verb</span></span> | <span data-ttu-id="d63ff-184">ToString</span><span class="sxs-lookup"><span data-stu-id="d63ff-184">ToString</span></span> | |
| <span data-ttu-id="d63ff-185">Namespace</span><span class="sxs-lookup"><span data-stu-id="d63ff-185">Namespace</span></span> | <span data-ttu-id="d63ff-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-186">PascalCase</span></span> | | <span data-ttu-id="d63ff-187">FSharp</span><span class="sxs-lookup"><span data-stu-id="d63ff-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="d63ff-188">Geralmente usam `<Organization>.<Technology>[.<Subnamespace>]`, porém descartar a organização se a tecnologia é independente da organização.</span><span class="sxs-lookup"><span data-stu-id="d63ff-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="d63ff-189">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d63ff-189">Parameters</span></span> | <span data-ttu-id="d63ff-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-190">camelCase</span></span> | <span data-ttu-id="d63ff-191">Substantivo</span><span class="sxs-lookup"><span data-stu-id="d63ff-191">Noun</span></span> |  <span data-ttu-id="d63ff-192">typeName, transform, intervalo</span><span class="sxs-lookup"><span data-stu-id="d63ff-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="d63ff-193">permitir que os valores (internos)</span><span class="sxs-lookup"><span data-stu-id="d63ff-193">let values (internal)</span></span> | <span data-ttu-id="d63ff-194">camelCase ou PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-194">camelCase or PascalCase</span></span> | <span data-ttu-id="d63ff-195">Substantivo / verbo</span><span class="sxs-lookup"><span data-stu-id="d63ff-195">Noun/ verb</span></span> |  <span data-ttu-id="d63ff-196">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="d63ff-196">getValue, myTable</span></span> |
| <span data-ttu-id="d63ff-197">permitir que os valores (externo)</span><span class="sxs-lookup"><span data-stu-id="d63ff-197">let values (external)</span></span> | <span data-ttu-id="d63ff-198">camelCase ou PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-198">camelCase or PascalCase</span></span> | <span data-ttu-id="d63ff-199">Substantivo/verbo</span><span class="sxs-lookup"><span data-stu-id="d63ff-199">Noun/verb</span></span>  | <span data-ttu-id="d63ff-200">List. map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="d63ff-200">List.map, Dates.Today</span></span> | <span data-ttu-id="d63ff-201">valores de associação let costumam ser públicos ao seguir padrões de design funcional tradicional.</span><span class="sxs-lookup"><span data-stu-id="d63ff-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="d63ff-202">No entanto, geralmente use PascalCase quando o identificador pode ser usado em outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="d63ff-203">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d63ff-203">Property</span></span>  | <span data-ttu-id="d63ff-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="d63ff-204">PascalCase</span></span>  | <span data-ttu-id="d63ff-205">Substantivo / adjetivas</span><span class="sxs-lookup"><span data-stu-id="d63ff-205">Noun/ adjective</span></span>  | <span data-ttu-id="d63ff-206">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="d63ff-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="d63ff-207">Propriedades booleanas geralmente uso é e pode e deve ser afirmativa, como no IsEndOfFile, não IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="d63ff-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="d63ff-208">Evite abreviações</span><span class="sxs-lookup"><span data-stu-id="d63ff-208">Avoid abbreviations</span></span>

<span data-ttu-id="d63ff-209">As diretrizes do .NET não recomendamos o uso de abreviações de (por exemplo, "usar `OnButtonClick` em vez de `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="d63ff-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="d63ff-210">Abreviações comuns, tais como `Async` "Asynchronous", são tolerados.</span><span class="sxs-lookup"><span data-stu-id="d63ff-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="d63ff-211">Essa diretriz, às vezes, é ignorado para programação funcional; Por exemplo, `List.iter` usa uma abreviação de "iterar".</span><span class="sxs-lookup"><span data-stu-id="d63ff-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="d63ff-212">Por esse motivo, usando abreviações tende a ser tolerada para um nível mais alto no F#- para -F# de programação, mas ainda geralmente deve ser evitado no design do componente público.</span><span class="sxs-lookup"><span data-stu-id="d63ff-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="d63ff-213">Evitar colisões de nome de uso de maiusculas</span><span class="sxs-lookup"><span data-stu-id="d63ff-213">Avoid casing name collisions</span></span>

<span data-ttu-id="d63ff-214">As diretrizes do .NET dizem que a maiusculas e minúsculas sozinho não podem ser usado para resolver a ambiguidade de colisões de nome, já que alguns idiomas de cliente (por exemplo, o Visual Basic) diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="d63ff-215">Usar acrônimos quando apropriado</span><span class="sxs-lookup"><span data-stu-id="d63ff-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="d63ff-216">Acrônimos como XML não são abreviações e são amplamente usados nas bibliotecas do .NET no formulário uncapitalized (Xml).</span><span class="sxs-lookup"><span data-stu-id="d63ff-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="d63ff-217">Somente acrônimos amplamente reconhecidos, bem conhecidos, devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="d63ff-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="d63ff-218">Usar PascalCase para nomes de parâmetro genérico</span><span class="sxs-lookup"><span data-stu-id="d63ff-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="d63ff-219">Usar PascalCase para nomes de parâmetro genérico em APIs públicas, incluindo para F#-voltado para a bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="d63ff-220">Em particular, usar nomes como `T`, `U`, `T1`, `T2` para parâmetros genéricos arbitrários e quando os nomes específicos fazem sentido, em seguida, F#-bibliotecas voltado para usam nomes como `Key`, `Value`, `Arg` (mas não, por exemplo, `TKey`).</span><span class="sxs-lookup"><span data-stu-id="d63ff-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="d63ff-221">Usar PascalCase ou camelCase para funções públicas e valores em F# módulos</span><span class="sxs-lookup"><span data-stu-id="d63ff-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="d63ff-222">camelCase é usado para funções públicas que são projetadas para ser usado não-qualificados (por exemplo, `invalidArg`) e para as "funções de coleção padrão" (por exemplo, List. Map).</span><span class="sxs-lookup"><span data-stu-id="d63ff-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="d63ff-223">Em ambos os casos, os nomes de função muito atuam como palavras-chave na linguagem.</span><span class="sxs-lookup"><span data-stu-id="d63ff-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="d63ff-224">Design de objeto, o tipo e o módulo</span><span class="sxs-lookup"><span data-stu-id="d63ff-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="d63ff-225">Use módulos ou namespaces para conter seus tipos e módulos</span><span class="sxs-lookup"><span data-stu-id="d63ff-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="d63ff-226">Cada F# arquivo em um componente deve começar com uma declaração de namespace ou uma declaração de módulo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="d63ff-227">ou</span><span class="sxs-lookup"><span data-stu-id="d63ff-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="d63ff-228">As diferenças entre o uso de módulos e namespaces para organizar o código no nível superior são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="d63ff-229">Namespaces pode abranger vários arquivos</span><span class="sxs-lookup"><span data-stu-id="d63ff-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="d63ff-230">Namespaces não podem conter F# , a menos que eles estejam dentro de um módulo interno de funções</span><span class="sxs-lookup"><span data-stu-id="d63ff-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="d63ff-231">O código de qualquer módulo fornecido deve estar contido em um único arquivo</span><span class="sxs-lookup"><span data-stu-id="d63ff-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="d63ff-232">Módulos de nível superior podem conter F# funções sem a necessidade de um módulo interno</span><span class="sxs-lookup"><span data-stu-id="d63ff-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="d63ff-233">A escolha entre um namespace de nível superior ou um módulo afeta a forma compilada do código e, portanto, afetam o modo de exibição de outras linguagens .NET deve sua API, eventualmente, ser consumida fora do F# código.</span><span class="sxs-lookup"><span data-stu-id="d63ff-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="d63ff-234">Usar métodos e propriedades para operações intrínsecas para tipos de objeto</span><span class="sxs-lookup"><span data-stu-id="d63ff-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="d63ff-235">Ao trabalhar com objetos, é melhor garantir que a funcionalidade consumível seja implementada como métodos e propriedades no tipo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="d63ff-236">A maior parte da funcionalidade para um determinado membro necessariamente não precisa ser implementada em que o membro, mas a parte consumível parte dessa funcionalidade deve ser.</span><span class="sxs-lookup"><span data-stu-id="d63ff-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="d63ff-237">Use as classes para encapsular o estado mutável</span><span class="sxs-lookup"><span data-stu-id="d63ff-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="d63ff-238">No F#, isso só precisa ser feito onde que estado já não estiver encapsulado por outra construção de linguagem, como um fechamento, uma expressão de sequência ou uma computação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d63ff-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="d63ff-239">Usar interfaces para agrupar operações relacionadas</span><span class="sxs-lookup"><span data-stu-id="d63ff-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="d63ff-240">Use tipos de interface para representar um conjunto de operações.</span><span class="sxs-lookup"><span data-stu-id="d63ff-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="d63ff-241">Isso é preferível para outras opções, como as tuplas de funções ou registros de funções.</span><span class="sxs-lookup"><span data-stu-id="d63ff-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="d63ff-242">Preferencialmente a:</span><span class="sxs-lookup"><span data-stu-id="d63ff-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="d63ff-243">As interfaces são conceitos de primeira classe no .NET, que pode ser usado para alcançar o que Functors normalmente oferecerá a você.</span><span class="sxs-lookup"><span data-stu-id="d63ff-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="d63ff-244">Além disso, eles podem ser usados para codificar tipos existenciais em seu programa, que não é possível de registros de funções.</span><span class="sxs-lookup"><span data-stu-id="d63ff-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="d63ff-245">Usar um módulo para o grupo de funções que atuam em coleções</span><span class="sxs-lookup"><span data-stu-id="d63ff-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="d63ff-246">Quando você define um tipo de coleção, recomenda-se de fornecer um conjunto padrão de operações, como `CollectionType.map` e `CollectionType.iter`) para novos tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="d63ff-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="d63ff-247">Se você incluir um módulo desse tipo, siga as convenções de nomenclatura padrão para funções encontradas no FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="d63ff-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="d63ff-248">Usar um módulo para funções do grupo para funções comuns, canonical, especialmente em matemática e bibliotecas DSL</span><span class="sxs-lookup"><span data-stu-id="d63ff-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="d63ff-249">Por exemplo, `Microsoft.FSharp.Core.Operators` é uma coleção automaticamente aberta de funções de nível superior (como `abs` e `sin`) fornecida pelo FSharp.</span><span class="sxs-lookup"><span data-stu-id="d63ff-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="d63ff-250">Da mesma forma, uma biblioteca de estatísticas pode incluir um módulo com funções `erf` e `erfc`, em que esse módulo é projetado para ser aberto de forma explícita ou automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d63ff-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="d63ff-251">Considere o uso de RequireQualifiedAccess e aplicar cuidadosamente os atributos de AutoOpen</span><span class="sxs-lookup"><span data-stu-id="d63ff-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="d63ff-252">Adicionando o `[<RequireQualifiedAccess>]` atributo a um módulo indica que o módulo não pode ser aberto e que as referências aos elementos do módulo exigem explícita qualificados acesso.</span><span class="sxs-lookup"><span data-stu-id="d63ff-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="d63ff-253">Por exemplo, o `Microsoft.FSharp.Collections.List` módulo tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="d63ff-254">Isso é útil quando funções e valores no módulo têm nomes que têm probabilidade de entrar em conflito com nomes em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="d63ff-255">Exigir acesso qualificado pode aumentar muito a manutenção de longo prazo e a capacidade de evolução de uma biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d63ff-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="d63ff-256">Adicionando o `[<AutoOpen>]` atributo a um módulo significa que o módulo será aberto quando o namespace que a contém é aberto.</span><span class="sxs-lookup"><span data-stu-id="d63ff-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="d63ff-257">O `[<AutoOpen>]` atributo também pode ser aplicado a um assembly para indicar um módulo que é aberto automaticamente quando o assembly for referenciado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="d63ff-258">Por exemplo, uma biblioteca de estatísticas **MathsHeaven.Statistics** pode conter um `module MathsHeaven.Statistics.Operators` que contêm funções `erf` e `erfc`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="d63ff-259">É razoável marcar este módulo como `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="d63ff-260">Isso significa `open MathsHeaven.Statistics` também abrirá esse módulo e colocar os nomes `erf` e `erfc` dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="d63ff-261">Outro bom uso de `[<AutoOpen>]` é para módulos que contêm métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="d63ff-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="d63ff-262">Uso excessivo de `[<AutoOpen>]` leva a poluído namespaces e o atributo deve ser usada com cuidado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="d63ff-263">Para bibliotecas específicas em domínios específicos, uso criterioso de `[<AutoOpen>]` pode levar a melhor usabilidade.</span><span class="sxs-lookup"><span data-stu-id="d63ff-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="d63ff-264">Considere definir membros de operador em classes em que é apropriado usar operadores conhecidos</span><span class="sxs-lookup"><span data-stu-id="d63ff-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="d63ff-265">Às vezes, as classes são usadas para construções de matemáticas como vetores de modelo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="d63ff-266">Quando o domínio que está sendo modelado tem operadores conhecidos, defini-los como membros intrínsecos para a classe é útil.</span><span class="sxs-lookup"><span data-stu-id="d63ff-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="d63ff-267">Essa orientação corresponde a diretrizes gerais do .NET para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="d63ff-268">No entanto, ele pode ser adicionalmente importante em F# de codificação, pois isso permite que esses tipos a ser usado em conjunto com F# funções e métodos com restrições de membro, como List. sumby.</span><span class="sxs-lookup"><span data-stu-id="d63ff-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="d63ff-269">Considere o uso de CompiledName para fornecer um. Nome amigável para o NET para outros consumidores de linguagem do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="d63ff-270">Às vezes, talvez você queira atribuir um nome em um estilo para o F# consumidores (como um membro estático em minúsculas de modo que ele apareça como se fosse uma função associada de módulo), mas tem um estilo diferente para o nome quando ele é compilado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="d63ff-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="d63ff-271">Você pode usar o `[<CompiledName>]` atributo para fornecer um estilo diferente para não F# código que consome o assembly.</span><span class="sxs-lookup"><span data-stu-id="d63ff-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="d63ff-272">Usando `[<CompiledName>]`, você pode usar as convenções de nomenclatura do .NET para não F# consumidores do assembly.</span><span class="sxs-lookup"><span data-stu-id="d63ff-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="d63ff-273">Use a sobrecarga de método para funções de membro, se isso proporciona uma API mais simples</span><span class="sxs-lookup"><span data-stu-id="d63ff-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="d63ff-274">Sobrecarga de método é uma ferramenta poderosa para simplificar uma API que talvez seja necessário executar uma funcionalidade semelhante, mas com argumentos ou opções diferentes.</span><span class="sxs-lookup"><span data-stu-id="d63ff-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="d63ff-275">No F#, é mais comum de sobrecarga em número de argumentos em vez de tipos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="d63ff-276">Ocultar as representações de registro e os tipos de união, se o design desses tipos é provavelmente a evoluir</span><span class="sxs-lookup"><span data-stu-id="d63ff-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="d63ff-277">Evite revelar concretas representações de objetos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="d63ff-278">Por exemplo, a representação concreta do <xref:System.DateTime> valores não serão revelados pela API externa, público do design da biblioteca do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="d63ff-279">Em tempo de execução, o Common Language Runtime sabe a implementação de confirmado que será usada em toda a execução.</span><span class="sxs-lookup"><span data-stu-id="d63ff-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="d63ff-280">No entanto, código compilado não próprio acompanhar dependências na representação concreta.</span><span class="sxs-lookup"><span data-stu-id="d63ff-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="d63ff-281">Evite o uso de herança de implementação para extensibilidade</span><span class="sxs-lookup"><span data-stu-id="d63ff-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="d63ff-282">No F#, herança de implementação é raramente usada.</span><span class="sxs-lookup"><span data-stu-id="d63ff-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="d63ff-283">Além disso, hierarquias de herança costumam ser complexos e difíceis de alterar a chegada de novos requisitos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="d63ff-284">Implementação da herança ainda existe no F# para compatibilidade e raros casos em que é a melhor solução para um problema, mas devem ser procuradas técnicas alternativas no seu F# ao projetar para polimorfismo, como a interface de programas implementação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="d63ff-285">Assinaturas de função e membro</span><span class="sxs-lookup"><span data-stu-id="d63ff-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="d63ff-286">Usar tuplas para valores de retorno ao retornar um número pequeno de vários valores não relacionados</span><span class="sxs-lookup"><span data-stu-id="d63ff-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="d63ff-287">Eis um bom exemplo de como usar uma tupla em um tipo de retorno:</span><span class="sxs-lookup"><span data-stu-id="d63ff-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="d63ff-288">Para retornar os tipos que contém vários componentes ou onde os componentes estão relacionados a uma única entidade identificável, considere o uso de um tipo nomeado, em vez de uma tupla.</span><span class="sxs-lookup"><span data-stu-id="d63ff-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="d63ff-289">Use `Async<T>` para assíncrono de programação em F# limites de API</span><span class="sxs-lookup"><span data-stu-id="d63ff-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="d63ff-290">Se há uma operação síncrona correspondente denominada `Operation` que retorna um `T`, em seguida, a operação assíncrona deve ser nomeada `AsyncOperation` se ele retornar `Async<T>` ou `OperationAsync` se ele retornar `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="d63ff-291">Para tipos .NET comumente usados que expõem métodos Begin/End, considere o uso `Async.FromBeginEnd` escrever métodos de extensão como uma fachada para fornecer a F# modelo de programação assíncrona para as APIs do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="d63ff-292">Exceções</span><span class="sxs-lookup"><span data-stu-id="d63ff-292">Exceptions</span></span>

<span data-ttu-id="d63ff-293">Ver [gerenciamento de erro](conventions.md#error-management) para saber mais sobre o uso apropriado de exceções, resultados e opções.</span><span class="sxs-lookup"><span data-stu-id="d63ff-293">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="d63ff-294">Membros de extensão</span><span class="sxs-lookup"><span data-stu-id="d63ff-294">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="d63ff-295">Aplicar cuidadosamente F# membros de extensão em F#- para -F# componentes</span><span class="sxs-lookup"><span data-stu-id="d63ff-295">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="d63ff-296">F#membros de extensão, geralmente, só devem ser usados para operações que estão no fechamento de operações intrínseco associado ao tipo na maioria dos seus modos de uso.</span><span class="sxs-lookup"><span data-stu-id="d63ff-296">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="d63ff-297">Um uso comum é fornecer APIs que são mais expressões idiomáticas para F# para vários tipos de .NET:</span><span class="sxs-lookup"><span data-stu-id="d63ff-297">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="d63ff-298">Tipos de união</span><span class="sxs-lookup"><span data-stu-id="d63ff-298">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="d63ff-299">Use as uniões discriminadas em vez de hierarquias de classe para dados estruturados em árvore</span><span class="sxs-lookup"><span data-stu-id="d63ff-299">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="d63ff-300">Estruturas de árvore são definida de forma recursiva.</span><span class="sxs-lookup"><span data-stu-id="d63ff-300">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="d63ff-301">Isso é estranho com herança, mas elegante com uniões discriminadas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-301">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="d63ff-302">Que representa dados de árvore com uniões discriminadas também permite que você se beneficie dos exhaustiveness na correspondência de padrão.</span><span class="sxs-lookup"><span data-stu-id="d63ff-302">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="d63ff-303">Use `[<RequireQualifiedAccess>]` em tipos de união cujos nomes com maiusculas não são suficientemente exclusivos</span><span class="sxs-lookup"><span data-stu-id="d63ff-303">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="d63ff-304">Você pode encontrar em um domínio em que o mesmo nome é o nome melhor para coisas diferentes, como casos de união discriminada.</span><span class="sxs-lookup"><span data-stu-id="d63ff-304">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="d63ff-305">Você pode usar `[<RequireQualifiedAccess>]` para resolver a ambiguidade de nomes com maiusculas para evitar disparar erros confusos devido ao sombreamento dependentes a ordenação de `open` instruções</span><span class="sxs-lookup"><span data-stu-id="d63ff-305">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="d63ff-306">Ocultar as representações de uniões discriminadas binário APIs compatíveis, se o design desses tipos é provavelmente a evoluir</span><span class="sxs-lookup"><span data-stu-id="d63ff-306">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="d63ff-307">Tipos de uniões dependem da F# formulários de correspondência para um modelo de programação sucinto.</span><span class="sxs-lookup"><span data-stu-id="d63ff-307">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="d63ff-308">Conforme mencionado anteriormente, você deve evitar revelar representações de dados concretos se o design desses tipos é provavelmente a evoluir.</span><span class="sxs-lookup"><span data-stu-id="d63ff-308">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="d63ff-309">Por exemplo, a representação de uma união discriminada pode ficar oculto usando uma declaração privada ou interna, ou usando um arquivo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d63ff-309">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="d63ff-310">Se você revelar as uniões discriminadas indiscriminadamente, talvez seja difícil versão sua biblioteca sem quebrar o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="d63ff-310">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="d63ff-311">Em vez disso, considere a possibilidade de revelar um ou mais padrões de Active Directory para permitir que a correspondência de valores do seu tipo.</span><span class="sxs-lookup"><span data-stu-id="d63ff-311">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="d63ff-312">Padrões de Active Directory fornecem uma maneira alternativa para fornecer F# consumidores com correspondência de padrões, evitando a exposição de F# diretamente os tipos de união.</span><span class="sxs-lookup"><span data-stu-id="d63ff-312">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="d63ff-313">Funções embutidas e restrições de membro</span><span class="sxs-lookup"><span data-stu-id="d63ff-313">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="d63ff-314">Definir os algoritmos genéricos numéricos, usando as funções embutidas com restrições de membro implícito e tipos genéricos estaticamente resolvidos</span><span class="sxs-lookup"><span data-stu-id="d63ff-314">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="d63ff-315">Restrições de aritmética de membro e F# restrições de comparação são um padrão para F# de programação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-315">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="d63ff-316">Por exemplo, considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d63ff-316">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="d63ff-317">O tipo dessa função é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-317">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="d63ff-318">Essa é uma função adequada para uma API pública em uma biblioteca de matemática.</span><span class="sxs-lookup"><span data-stu-id="d63ff-318">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="d63ff-319">Evite usar restrições de membro para simular classes de tipo e a digitação pato</span><span class="sxs-lookup"><span data-stu-id="d63ff-319">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="d63ff-320">É possível simular "tipagem pato" usando F# restrições de membro.</span><span class="sxs-lookup"><span data-stu-id="d63ff-320">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="d63ff-321">No entanto, os membros que fazem usam dessa não está em geral deve ser usado em F#- para -F# projetos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d63ff-321">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="d63ff-322">Isso ocorre porque os designs de biblioteca com base nas restrições implícitas desconhecidas ou não-padrão tendem a fazer com que o código de usuário para se tornar inflexíveis e são associados ao padrão de uma determinada estrutura.</span><span class="sxs-lookup"><span data-stu-id="d63ff-322">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="d63ff-323">Além disso, há uma boa chance de que o uso intenso de restrições de membro dessa maneira pode resultar em tempos de compilação muito longos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-323">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="d63ff-324">Definições de operador</span><span class="sxs-lookup"><span data-stu-id="d63ff-324">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="d63ff-325">Evite definir operadores simbólicos personalizados</span><span class="sxs-lookup"><span data-stu-id="d63ff-325">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="d63ff-326">Operadores personalizados são essenciais em algumas situações e são altamente úteis dispositivos da notação dentro de uma grande quantidade de código de implementação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-326">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="d63ff-327">Para novos usuários de uma biblioteca, geralmente são mais fáceis de usar funções nomeadas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-327">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="d63ff-328">Além disso, operadores simbólicos personalizados podem ser difíceis de documento e usuários acham mais difícil pesquisar a Ajuda em operadores, devido a limitações existentes no IDE, mecanismos de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d63ff-328">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="d63ff-329">Como resultado, é melhor publicar sua funcionalidade como funções nomeadas e membros e Além disso, expor operadores para essa funcionalidade somente se os benefícios da notação superam a documentação e cognitivo custo de tê-los.</span><span class="sxs-lookup"><span data-stu-id="d63ff-329">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="d63ff-330">Unidades de medida</span><span class="sxs-lookup"><span data-stu-id="d63ff-330">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="d63ff-331">Cuidadosamente, usar unidades de medida para a segurança de tipo adicionado no F# código</span><span class="sxs-lookup"><span data-stu-id="d63ff-331">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="d63ff-332">Informações adicionais de digitação para unidades de medida são apagadas quando visualizado por outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-332">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="d63ff-333">Lembre-se de que a reflexão, ferramentas e componentes do .NET verá tipos sans unidades.</span><span class="sxs-lookup"><span data-stu-id="d63ff-333">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="d63ff-334">Por exemplo, verá os consumidores de c# `float` em vez de `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-334">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="d63ff-335">Abreviações de tipo</span><span class="sxs-lookup"><span data-stu-id="d63ff-335">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="d63ff-336">Usar cuidadosamente as abreviações de tipo para simplificar o F# código</span><span class="sxs-lookup"><span data-stu-id="d63ff-336">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="d63ff-337">Reflexão, ferramentas e componentes do .NET não verá os nomes abreviados para tipos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-337">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="d63ff-338">Uso significativo de abreviações de tipo também pode fazer um domínio aparecem mais complicado do que realmente é, que poderia confundir os consumidores.</span><span class="sxs-lookup"><span data-stu-id="d63ff-338">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="d63ff-339">Evite abreviações de tipo para tipos públicos cujos membros e propriedades devem ser intrinsecamente diferentes daqueles disponíveis no tipo que está sendo abreviado</span><span class="sxs-lookup"><span data-stu-id="d63ff-339">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="d63ff-340">Nesse caso, o tipo que está sendo abreviado revela muito sobre a representação do tipo real que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="d63ff-340">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="d63ff-341">Em vez disso, considere o encapsulamento a abreviação em um tipo de classe ou uma união discriminada de caso único (ou, quando o desempenho é essencial, considere o uso de um tipo de struct para encapsular a abreviação).</span><span class="sxs-lookup"><span data-stu-id="d63ff-341">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="d63ff-342">Por exemplo, é tentador para definir um mapa com vários como um caso especial de um F# mapear, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d63ff-342">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="d63ff-343">No entanto, as operações lógicas de notação de ponto nesse tipo não são o mesmo que as operações em um mapa – por exemplo, é razoável de que o operador de pesquisa de mapa. uma lista vazia se a chave não estiver no dicionário, em vez de gerar uma exceção de retorno [chave].</span><span class="sxs-lookup"><span data-stu-id="d63ff-343">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d63ff-344">Diretrizes para as bibliotecas de uso de outras linguagens .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-344">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="d63ff-345">Durante a criação de bibliotecas para uso de outras linguagens .NET, é importante aderir à [diretrizes de Design de biblioteca do .NET](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="d63ff-345">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="d63ff-346">Neste documento, essas bibliotecas são rotuladas como baunilha bibliotecas do .NET, em vez de F#-voltado para a bibliotecas que usam F# constrói sem restrição.</span><span class="sxs-lookup"><span data-stu-id="d63ff-346">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="d63ff-347">Criar bibliotecas .NET de baunilha significa fornecendo familiar e expressões idiomáticas APIs consistentes com o restante do .NET Framework, minimizando o uso de F#-construções específicas na API pública.</span><span class="sxs-lookup"><span data-stu-id="d63ff-347">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="d63ff-348">As regras são explicadas nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="d63ff-348">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d63ff-349">Namespace e tipo de design (para as bibliotecas de uso de outras linguagens .NET)</span><span class="sxs-lookup"><span data-stu-id="d63ff-349">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="d63ff-350">Aplicar as convenções de nomenclatura do .NET para a API pública de seus componentes</span><span class="sxs-lookup"><span data-stu-id="d63ff-350">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="d63ff-351">Preste atenção especial para o uso de nomes abreviados e as diretrizes de maiusculas e minúsculas do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-351">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="d63ff-352">Usar namespaces, tipos e membros como a estrutura organizacional primária para os componentes</span><span class="sxs-lookup"><span data-stu-id="d63ff-352">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="d63ff-353">Todos os arquivos que contém a funcionalidade pública devem começar com um `namespace` declaração e as únicas entidades voltados ao público em namespaces devem ser tipos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-353">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="d63ff-354">Não use F# módulos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-354">Do not use F# modules.</span></span>

<span data-ttu-id="d63ff-355">Use módulos de não-públicos para manter o código de implementação, utilitário tipos e funções de utilitário.</span><span class="sxs-lookup"><span data-stu-id="d63ff-355">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="d63ff-356">Tipos estáticos devem ser preferenciais em vez de módulos, já que permitem futura evolução da API para usar a sobrecarga e outros conceitos de design .NET API que não podem ser usados dentro do F# módulos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-356">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="d63ff-357">Por exemplo, em vez da API pública do seguinte:</span><span class="sxs-lookup"><span data-stu-id="d63ff-357">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="d63ff-358">Considere em vez disso:</span><span class="sxs-lookup"><span data-stu-id="d63ff-358">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="d63ff-359">Use F# tipos de registro no baunilha APIs .NET se o design dos tipos não evoluir</span><span class="sxs-lookup"><span data-stu-id="d63ff-359">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="d63ff-360">F#tipos de registro seja compilado para uma classe simples do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-360">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="d63ff-361">Eles são adequados para alguns tipos simples e estáveis em APIs.</span><span class="sxs-lookup"><span data-stu-id="d63ff-361">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="d63ff-362">Você deve considerar usar o `[<NoEquality>]` e `[<NoComparison>]` atributos para suprimir a geração automática de interfaces.</span><span class="sxs-lookup"><span data-stu-id="d63ff-362">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="d63ff-363">Além disso, evite usar campos de registro mutável em baunilha APIs .NET como esses expõe um campo público.</span><span class="sxs-lookup"><span data-stu-id="d63ff-363">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="d63ff-364">Sempre considere se uma classe forneceria uma opção mais flexível para futura evolução da API.</span><span class="sxs-lookup"><span data-stu-id="d63ff-364">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="d63ff-365">Por exemplo, a seguinte F# código expõe a API pública para um C# consumidor:</span><span class="sxs-lookup"><span data-stu-id="d63ff-365">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="d63ff-366">F#:</span><span class="sxs-lookup"><span data-stu-id="d63ff-366">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="d63ff-367">C#:</span><span class="sxs-lookup"><span data-stu-id="d63ff-367">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="d63ff-368">Ocultar a representação de F# tipos de união em baunilha APIs do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-368">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="d63ff-369">F#tipos de união não são comumente usados nos limites do componente, mesmo para F#- para -F# de codificação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-369">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="d63ff-370">Eles são um dispositivo de implementação excelente quando usado internamente em componentes e bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-370">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="d63ff-371">Ao criar uma API .NET de baunilha, considere ocultando a representação de um tipo de união, usando uma declaração particular ou um arquivo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="d63ff-371">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="d63ff-372">Você também poderá aumentar os tipos que usam uma representação de união internamente com membros para fornecer um desejado. NET voltado para a API.</span><span class="sxs-lookup"><span data-stu-id="d63ff-372">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="d63ff-373">Design de interface gráfica do usuário e outros componentes usando os padrões de design do framework</span><span class="sxs-lookup"><span data-stu-id="d63ff-373">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="d63ff-374">Há muitas estruturas diferentes dentro do .NET, como WinForms, WPF e ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-374">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="d63ff-375">Convenções de nomenclatura e design para cada um devem ser usadas se você estiver criando componentes para uso em dessas estruturas.</span><span class="sxs-lookup"><span data-stu-id="d63ff-375">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="d63ff-376">Por exemplo, para o WPF em programação, adote padrões de design do WPF para as classes que você está criando.</span><span class="sxs-lookup"><span data-stu-id="d63ff-376">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="d63ff-377">Para modelos na programação de interface do usuário, use os padrões de design, como eventos e baseada em notificação coleções como aquelas encontradas no <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="d63ff-377">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="d63ff-378">Design de objetos e membros (para as bibliotecas de uso de outras linguagens .NET)</span><span class="sxs-lookup"><span data-stu-id="d63ff-378">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="d63ff-379">Usar o atributo CLIEvent para expor eventos .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-379">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="d63ff-380">Construir uma `DelegateEvent` com um .NET específica o tipo que usa um objeto de delegado e `EventArgs` (em vez de uma `Event`, que usa apenas o `FSharpHandler` tipo por padrão) para que os eventos são publicados da forma familiar para outras linguagens .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-380">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="d63ff-381">Expor operações assíncronas como métodos que retornam tarefas do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-381">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="d63ff-382">As tarefas são usadas em .NET para representar as computações assíncronas Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d63ff-382">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="d63ff-383">Tarefas são em geral composicional menor que F# `Async<T>` objetos, uma vez que eles representam tarefas "já em execução" e não podem ser compostos juntas de maneiras que realizar a composição paralela ou que oculte a propagação de sinais de cancelamento e outros parâmetros contextuais.</span><span class="sxs-lookup"><span data-stu-id="d63ff-383">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="d63ff-384">No entanto, apesar disso, os métodos que retornam tarefas são a representação padrão de programação assíncrona no .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-384">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="d63ff-385">Com frequência, você irá também deseja aceitar um token de cancelamento explícita:</span><span class="sxs-lookup"><span data-stu-id="d63ff-385">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="d63ff-386">Usar tipos de delegados do .NET em vez de F# tipos de função</span><span class="sxs-lookup"><span data-stu-id="d63ff-386">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="d63ff-387">Veja "F# tipos de função" significa que os tipos de "seta" como `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-387">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="d63ff-388">Em vez disto:</span><span class="sxs-lookup"><span data-stu-id="d63ff-388">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="d63ff-389">Faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d63ff-389">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="d63ff-390">O F# tipo de função é exibido como `class FSharpFunc<T,U>` para outras linguagens .NET e é menos adequada para recursos de linguagem e ferramentas que entender os tipos de delegado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-390">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="d63ff-391">Ao criar um método de ordem superior direcionados ao .NET Framework 3.5 ou posterior, o `System.Func` e `System.Action` os delegados são as APIs certas para publicar para permitir que os desenvolvedores de .NET consumir essas APIs de uma maneira de baixo atrito.</span><span class="sxs-lookup"><span data-stu-id="d63ff-391">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="d63ff-392">(Ao direcionar o .NET Framework 2.0, os tipos de delegado definido pelo sistema são mais limitados; considere o uso de tipos de delegado predefinidos, como `System.Converter<T,U>` ou definindo um tipo de delegado específico.)</span><span class="sxs-lookup"><span data-stu-id="d63ff-392">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="d63ff-393">Por outro lado, os delegados do .NET não são naturais para F#-voltados para bibliotecas (consulte a próxima seção sobre F#-voltados para bibliotecas).</span><span class="sxs-lookup"><span data-stu-id="d63ff-393">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="d63ff-394">Como resultado, uma estratégia de implementação comum ao desenvolver métodos de ordem superior para bibliotecas .NET de baunilha é criar todos os implementação usando F# tipos de função e, em seguida, crie a API pública usando delegados como uma fachada fina sobre o real F#implementação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-394">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="d63ff-395">Usar o padrão de TryGetValue em vez de retornar F# valores de opção e preferir a sobrecarga de método para tirar F# valores como argumentos de opção</span><span class="sxs-lookup"><span data-stu-id="d63ff-395">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="d63ff-396">Padrões comuns de uso para o F# tipo de opção em APIs são melhores implementado em baunilha APIs do .NET usando o .NET standard técnicas de design.</span><span class="sxs-lookup"><span data-stu-id="d63ff-396">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="d63ff-397">Em vez de retornar um F# valor de opção, considere usar o tipo de retorno booleano além de um parâmetro de saída como o padrão de "TryGetValue".</span><span class="sxs-lookup"><span data-stu-id="d63ff-397">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="d63ff-398">E, em vez de usar F# valores como parâmetros de opção, considere o uso de argumentos opcionais ou sobrecarga de método.</span><span class="sxs-lookup"><span data-stu-id="d63ff-398">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="d63ff-399">Usar a interface de coleção do .NET tipos IEnumerable\<T\> e IDictionary\<da chave, valor\> para parâmetros e valores de retorno</span><span class="sxs-lookup"><span data-stu-id="d63ff-399">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="d63ff-400">Evite o uso de tipos de coleção concretos, como as matrizes do .NET `T[]`, F# tipos `list<T>`, `Map<Key,Value>` e `Set<T>`, e tipos de coleção concreta do .NET, como `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-400">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="d63ff-401">Diretrizes de Design da biblioteca do .NET ter bons conselhos sobre quando usar vários tipos de coleção, como `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-401">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="d63ff-402">Algum uso de matrizes (`T[]`) é aceitável em algumas circunstâncias, em razão de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d63ff-402">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="d63ff-403">Observe especialmente `seq<T>` é apenas o F# alias do `IEnumerable<T>`, e, portanto, seq costuma ser um tipo apropriado para uma API .NET de baunilha.</span><span class="sxs-lookup"><span data-stu-id="d63ff-403">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="d63ff-404">Em vez de F# lista:</span><span class="sxs-lookup"><span data-stu-id="d63ff-404">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="d63ff-405">Use F# sequências:</span><span class="sxs-lookup"><span data-stu-id="d63ff-405">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="d63ff-406">Usar o tipo de unidade como o único tipo de entrada de um método para definir um método de argumento de zero ou como o único tipo de retorno para definir um método de retorno void</span><span class="sxs-lookup"><span data-stu-id="d63ff-406">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="d63ff-407">Evite a outros usos do tipo de unidade.</span><span class="sxs-lookup"><span data-stu-id="d63ff-407">Avoid other uses of the unit type.</span></span> <span data-ttu-id="d63ff-408">Essas são boas:</span><span class="sxs-lookup"><span data-stu-id="d63ff-408">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="d63ff-409">Isso é ruim:</span><span class="sxs-lookup"><span data-stu-id="d63ff-409">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="d63ff-410">Verificar valores nulos em baunilha limites de API do .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-410">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="d63ff-411">F#código de implementação tende a ter menos valores nulos, devido a padrões de design imutável e restrições no uso de literais nulas para F# tipos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-411">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="d63ff-412">Outras linguagens .NET geralmente usam nulo como um valor muito mais frequência.</span><span class="sxs-lookup"><span data-stu-id="d63ff-412">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="d63ff-413">Por isso, F# código que expõe uma API .NET de baunilha deve verificar parâmetros de null no limite da API e impedir que esses valores fluindo profunda o F# código de implementação.</span><span class="sxs-lookup"><span data-stu-id="d63ff-413">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="d63ff-414">O `isNull` função ou correspondência de padrão no `null` padrão pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-414">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="d63ff-415">Evite usar tuplas como valores de retorno</span><span class="sxs-lookup"><span data-stu-id="d63ff-415">Avoid using tuples as return values</span></span>

<span data-ttu-id="d63ff-416">Em vez disso, prefira retornando um tipo nomeado que contém os dados de agregação, ou usando os parâmetros de saída para retornar vários valores.</span><span class="sxs-lookup"><span data-stu-id="d63ff-416">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="d63ff-417">Embora existam, tuplas e tuplas de struct, no .NET (incluindo suporte à linguagem c# tuplas de struct), eles geralmente não fornecerá a API ideal e esperada para desenvolvedores do .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-417">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="d63ff-418">Evite o uso de currying de parâmetros</span><span class="sxs-lookup"><span data-stu-id="d63ff-418">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="d63ff-419">Em vez disso, use o .NET de convenções de chamada ``Method(arg1,arg2,…,argN)``.</span><span class="sxs-lookup"><span data-stu-id="d63ff-419">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="d63ff-420">Dica: Se você estiver criando bibliotecas para uso em qualquer linguagem .NET, não há nenhum substituto para realmente fazer algumas experimental C# e para garantir que suas bibliotecas "sensação à direita" dessas linguagens de programação Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d63ff-420">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="d63ff-421">Você também pode usar ferramentas como o .NET Reflector e o Pesquisador de objetos do Visual Studio para garantir que as bibliotecas e sua documentação aparecem conforme o esperado para os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="d63ff-421">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="d63ff-422">Anexo</span><span class="sxs-lookup"><span data-stu-id="d63ff-422">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="d63ff-423">Exemplo de ponta a ponta da criação F# código para uso por outras linguagens .NET</span><span class="sxs-lookup"><span data-stu-id="d63ff-423">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="d63ff-424">Considere a seguinte classe:</span><span class="sxs-lookup"><span data-stu-id="d63ff-424">Consider the following class:</span></span>

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

<span data-ttu-id="d63ff-425">Inferido F# tipo dessa classe é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d63ff-425">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="d63ff-426">Vamos dar uma olhada em como isso F# tipo será exibido para um programador usando outra linguagem .NET.</span><span class="sxs-lookup"><span data-stu-id="d63ff-426">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="d63ff-427">Por exemplo, o aproximado c# "assinatura" é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-427">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="d63ff-428">Há alguns pontos importantes a observar sobre como F# representa constrói aqui.</span><span class="sxs-lookup"><span data-stu-id="d63ff-428">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="d63ff-429">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d63ff-429">For example:</span></span>

* <span data-ttu-id="d63ff-430">Metadados, como nomes de argumentos foi preservado.</span><span class="sxs-lookup"><span data-stu-id="d63ff-430">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="d63ff-431">F#métodos que usam dois argumentos que se tornam C# métodos que usam dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="d63ff-431">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="d63ff-432">Funções e listas se tornam as referências a tipos correspondentes no F# biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d63ff-432">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="d63ff-433">O código a seguir mostra como ajustar este código para levar tudo isso em conta.</span><span class="sxs-lookup"><span data-stu-id="d63ff-433">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="d63ff-434">Inferido F# tipo de código é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-434">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="d63ff-435">A assinatura c# agora é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-435">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="d63ff-436">As correções feitas para preparar esse tipo para uso como parte de uma biblioteca .NET baunilha são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d63ff-436">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="d63ff-437">Ajustado diversos nomes: `Point1`, `n`, `l`, e `f` se tornou `RadialPoint`, `count`, `factor`, e `transform`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d63ff-437">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="d63ff-438">Usado um tipo de retorno `seq<RadialPoint>` em vez de `RadialPoint list` alterando uma construção de lista usando `[ ... ]` para uma construção de sequência usando `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="d63ff-438">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="d63ff-439">Usado o tipo de delegado do .NET `System.Func` em vez de um F# tipo de função.</span><span class="sxs-lookup"><span data-stu-id="d63ff-439">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="d63ff-440">Isso torna muito mais agradável consumir em código c#.</span><span class="sxs-lookup"><span data-stu-id="d63ff-440">This makes it far nicer to consume in C# code.</span></span>
