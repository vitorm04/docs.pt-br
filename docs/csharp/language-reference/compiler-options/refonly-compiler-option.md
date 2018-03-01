---
title: "-refonly (Opções do compilador do C#)"
ms.date: 07/08/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25b0f6e024e194dff641fd5069755d0ea112a50b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="be4d7-102">-refonly (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="be4d7-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="be4d7-103">A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária.</span><span class="sxs-lookup"><span data-stu-id="be4d7-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="be4d7-104">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="be4d7-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="be4d7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be4d7-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="be4d7-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="be4d7-106">Remarks</span></span>

<span data-ttu-id="be4d7-107">Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="be4d7-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="be4d7-108">O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="be4d7-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="be4d7-109">Os assemblies de referência incluem um atributo `ReferenceAssembly` de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="be4d7-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="be4d7-110">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="be4d7-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="be4d7-111">Por causa desse atributo, os tempos de execução se recusarão a carregar assemblies de referência para execução (mas ainda podem ser carregados em modo somente reflexão).</span><span class="sxs-lookup"><span data-stu-id="be4d7-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="be4d7-112">As ferramentas que se refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão, caso contrário, elas receberão um erro de typeload do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="be4d7-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="be4d7-113">Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:</span><span class="sxs-lookup"><span data-stu-id="be4d7-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="be4d7-114">Um assembly de referência tem somente referências para o que ele precisa na superfície de API.</span><span class="sxs-lookup"><span data-stu-id="be4d7-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="be4d7-115">Talvez o assembly real tenha outras referências relacionadas a implementações específicas.</span><span class="sxs-lookup"><span data-stu-id="be4d7-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="be4d7-116">Por exemplo, o assembly de referência para `class C { private void M() { dynamic d = 1; ... } }` não referencia nenhum tipo necessário para `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="be4d7-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="be4d7-117">Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação.</span><span class="sxs-lookup"><span data-stu-id="be4d7-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="be4d7-118">Se não houver nenhum atributo `InternalsVisibleTo`, faça o mesmo para os membros de função internos.</span><span class="sxs-lookup"><span data-stu-id="be4d7-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="be4d7-119">Mas todos os tipos (incluindo tipos aninhados ou privados) são mantidos em assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="be4d7-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="be4d7-120">Todos os atributos são mantidos (até mesmo os internos).</span><span class="sxs-lookup"><span data-stu-id="be4d7-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="be4d7-121">Todos os métodos virtuais são mantidos.</span><span class="sxs-lookup"><span data-stu-id="be4d7-121">All virtual methods are kept.</span></span> <span data-ttu-id="be4d7-122">As implementações explícitas da interface são mantidas.</span><span class="sxs-lookup"><span data-stu-id="be4d7-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="be4d7-123">As propriedades e eventos explicitamente implementados são mantidos, uma vez que seus acessadores são virtuais (e são, portanto, mantidos).</span><span class="sxs-lookup"><span data-stu-id="be4d7-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="be4d7-124">Todos os campos de um struct são mantidos.</span><span class="sxs-lookup"><span data-stu-id="be4d7-124">All fields of a struct are kept.</span></span> <span data-ttu-id="be4d7-125">(Este é um candidato para refinamento pós-c#-7.1)</span><span class="sxs-lookup"><span data-stu-id="be4d7-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="be4d7-126">As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="be4d7-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="be4d7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be4d7-127">See also</span></span>
 [<span data-ttu-id="be4d7-128">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="be4d7-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="be4d7-129">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="be4d7-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
