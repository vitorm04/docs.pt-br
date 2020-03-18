---
title: -refonly (Opções do compilador do C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 856b65d3b2217dbe5d53ecda00723b47247d80a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72773847"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="8d2e2-102">-refonly (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="8d2e2-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="8d2e2-103">A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="8d2e2-104">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="8d2e2-105">Essa opção corresponde à propriedade de projeto [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d2e2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d2e2-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="8d2e2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d2e2-107">Remarks</span></span>

<span data-ttu-id="8d2e2-108">Os conjuntos de referência são um tipo especial de montagem que contém apenas a quantidade mínima de metadados necessários para representar a superfície pública da API da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="8d2e2-109">Eles incluem declarações para todos os membros que são significativas ao fazer referência a uma assembléia em ferramentas de construção, mas excluem todas as implementações de membros membros e declarações de membros privados que não tenham impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="8d2e2-110">Para obter mais informações, consulte [conjuntos de referência](../../../standard/assembly/reference-assemblies.md) no Guia .NET.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="8d2e2-111">As `-refonly` [`-refout`](refout-compiler-option.md) opções são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="8d2e2-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d2e2-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="8d2e2-112">See also</span></span>

- [<span data-ttu-id="8d2e2-113">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="8d2e2-113">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="8d2e2-114">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="8d2e2-114">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
