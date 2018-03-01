---
title: "-refout (Opções do compilador do C#)"
ms.date: 08/08/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbae6f461304c37ba2ef10da16b5d520377bb225
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="4417d-102">-refout (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="4417d-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="4417d-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="4417d-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="4417d-104">Isso se converte em `metadataPeStream` na API de emissão.</span><span class="sxs-lookup"><span data-stu-id="4417d-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="4417d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4417d-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="4417d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4417d-106">Arguments</span></span>

 <span data-ttu-id="4417d-107">`filepath` O fipeath so assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="4417d-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="4417d-108">Geralmente, ele deve corresponder ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="4417d-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="4417d-109">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="4417d-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="4417d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4417d-110">Remarks</span></span>

<span data-ttu-id="4417d-111">Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="4417d-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="4417d-112">O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="4417d-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="4417d-113">Os assemblies de referência incluem um atributo `ReferenceAssembly` de nível de assembly.</span><span class="sxs-lookup"><span data-stu-id="4417d-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="4417d-114">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="4417d-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="4417d-115">Por causa desse atributo, os tempos de execução se recusarão a carregar assemblies de referência para execução (mas ainda podem ser carregados em modo somente reflexão).</span><span class="sxs-lookup"><span data-stu-id="4417d-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="4417d-116">As ferramentas que se refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão, caso contrário, elas receberão um erro de typeload do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4417d-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="4417d-117">Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:</span><span class="sxs-lookup"><span data-stu-id="4417d-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="4417d-118">Um assembly de referência tem somente referências para o que ele precisa na superfície de API.</span><span class="sxs-lookup"><span data-stu-id="4417d-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="4417d-119">Talvez o assembly real tenha outras referências relacionadas a implementações específicas.</span><span class="sxs-lookup"><span data-stu-id="4417d-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="4417d-120">Por exemplo, o assembly de referência para `class C { private void M() { dynamic d = 1; ... } }` não referencia nenhum tipo necessário para `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="4417d-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="4417d-121">Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação.</span><span class="sxs-lookup"><span data-stu-id="4417d-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="4417d-122">Se não houver nenhum atributo `InternalsVisibleTo`, faça o mesmo para os membros de função internos.</span><span class="sxs-lookup"><span data-stu-id="4417d-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="4417d-123">Mas todos os tipos (incluindo tipos aninhados ou privados) são mantidos em assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="4417d-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="4417d-124">Todos os atributos são mantidos (até mesmo os internos).</span><span class="sxs-lookup"><span data-stu-id="4417d-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="4417d-125">Todos os métodos virtuais são mantidos.</span><span class="sxs-lookup"><span data-stu-id="4417d-125">All virtual methods are kept.</span></span> <span data-ttu-id="4417d-126">As implementações explícitas da interface são mantidas.</span><span class="sxs-lookup"><span data-stu-id="4417d-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="4417d-127">As propriedades e eventos explicitamente implementados são mantidos, uma vez que seus acessadores são virtuais (e são, portanto, mantidos).</span><span class="sxs-lookup"><span data-stu-id="4417d-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="4417d-128">Todos os campos de um struct são mantidos.</span><span class="sxs-lookup"><span data-stu-id="4417d-128">All fields of a struct are kept.</span></span> <span data-ttu-id="4417d-129">(Este é um candidato para refinamento pós-c#-7.1)</span><span class="sxs-lookup"><span data-stu-id="4417d-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="4417d-130">As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="4417d-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="4417d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4417d-131">See Also</span></span>
 [<span data-ttu-id="4417d-132">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="4417d-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4417d-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="4417d-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
