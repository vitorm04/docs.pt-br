---
description: -refonly (Opções do compilador do C#)
title: -refonly (Opções do compilador do C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: f9a92462203bedff93a4a711ca8742465b7a561c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124741"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="7a53b-103">-refonly (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="7a53b-103">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="7a53b-104">A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária.</span><span class="sxs-lookup"><span data-stu-id="7a53b-104">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="7a53b-105">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="7a53b-105">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="7a53b-106">Essa opção corresponde à propriedade de projeto [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7a53b-106">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a53b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a53b-107">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="7a53b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a53b-108">Remarks</span></span>

<span data-ttu-id="7a53b-109">Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7a53b-109">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="7a53b-110">Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="7a53b-110">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="7a53b-111">Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.</span><span class="sxs-lookup"><span data-stu-id="7a53b-111">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="7a53b-112">As `-refonly` [`-refout`](refout-compiler-option.md) Opções e são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="7a53b-112">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a53b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a53b-113">See also</span></span>

- [<span data-ttu-id="7a53b-114">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="7a53b-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7a53b-115">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="7a53b-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
