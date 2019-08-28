---
title: -refonly (Opções do compilador do C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606489"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="acb6f-102">-refonly (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="acb6f-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="acb6f-103">A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária.</span><span class="sxs-lookup"><span data-stu-id="acb6f-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="acb6f-104">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="acb6f-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="acb6f-105">Essa opção corresponde à propriedade de projeto [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="acb6f-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="acb6f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="acb6f-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="acb6f-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="acb6f-107">Remarks</span></span>

<span data-ttu-id="acb6f-108">Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="acb6f-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="acb6f-109">O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="acb6f-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="acb6f-110">Os assemblies de referência incluem um atributo `ReferenceAssembly` de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="acb6f-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="acb6f-111">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="acb6f-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="acb6f-112">Por causa desse atributo, os tempos de execução se recusarão a carregar assemblies de referência para execução (mas ainda podem ser carregados em modo somente reflexão).</span><span class="sxs-lookup"><span data-stu-id="acb6f-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="acb6f-113">As ferramentas que se refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão, caso contrário, elas receberão um erro de typeload do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="acb6f-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="acb6f-114">Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:</span><span class="sxs-lookup"><span data-stu-id="acb6f-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="acb6f-115">Um assembly de referência tem somente referências para o que ele precisa na superfície de API.</span><span class="sxs-lookup"><span data-stu-id="acb6f-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="acb6f-116">Talvez o assembly real tenha outras referências relacionadas a implementações específicas.</span><span class="sxs-lookup"><span data-stu-id="acb6f-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="acb6f-117">Por exemplo, o assembly de referência para `class C { private void M() { dynamic d = 1; ... } }` não referencia nenhum tipo necessário para `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="acb6f-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="acb6f-118">Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação.</span><span class="sxs-lookup"><span data-stu-id="acb6f-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="acb6f-119">Se não houver nenhum atributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, faça o mesmo para os membros de função internos.</span><span class="sxs-lookup"><span data-stu-id="acb6f-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="acb6f-120">Mas todos os tipos (incluindo tipos aninhados ou privados) são mantidos em assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="acb6f-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="acb6f-121">Todos os atributos são mantidos (até mesmo os internos).</span><span class="sxs-lookup"><span data-stu-id="acb6f-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="acb6f-122">Todos os métodos virtuais são mantidos.</span><span class="sxs-lookup"><span data-stu-id="acb6f-122">All virtual methods are kept.</span></span> <span data-ttu-id="acb6f-123">As implementações explícitas da interface são mantidas.</span><span class="sxs-lookup"><span data-stu-id="acb6f-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="acb6f-124">As propriedades e eventos explicitamente implementados são mantidos, uma vez que seus acessadores são virtuais (e são, portanto, mantidos).</span><span class="sxs-lookup"><span data-stu-id="acb6f-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="acb6f-125">Todos os campos de um struct são mantidos.</span><span class="sxs-lookup"><span data-stu-id="acb6f-125">All fields of a struct are kept.</span></span> <span data-ttu-id="acb6f-126">(Este é um candidato para refinamento pós-c#-7.1)</span><span class="sxs-lookup"><span data-stu-id="acb6f-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="acb6f-127">As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="acb6f-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="acb6f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acb6f-128">See also</span></span>

- [<span data-ttu-id="acb6f-129">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="acb6f-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="acb6f-130">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="acb6f-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
