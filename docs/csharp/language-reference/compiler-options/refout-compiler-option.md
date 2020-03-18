---
title: -refout (Opções do compilador do C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: f48316a1e6f657e3bd0190d269dfe0e875a833d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771754"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="b7540-102">-refout (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="b7540-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="b7540-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="b7540-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="b7540-104">Isso se converte em `metadataPeStream` na API de emissão.</span><span class="sxs-lookup"><span data-stu-id="b7540-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="b7540-105">Essa opção corresponde à propriedade de projeto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b7540-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7540-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7540-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="b7540-107">Argumentos</span><span class="sxs-lookup"><span data-stu-id="b7540-107">Arguments</span></span>

 <span data-ttu-id="b7540-108">`filepath` O fipeath so assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="b7540-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="b7540-109">Geralmente, ele deve corresponder ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="b7540-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="b7540-110">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="b7540-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7540-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7540-111">Remarks</span></span>

<span data-ttu-id="b7540-112">Os conjuntos de referência são um tipo especial de montagem que contém apenas a quantidade mínima de metadados necessários para representar a superfície pública da API da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="b7540-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="b7540-113">Eles incluem declarações para todos os membros que são significativas ao fazer referência a uma assembléia em ferramentas de construção, mas excluem todas as implementações de membros membros e declarações de membros privados que não tenham impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="b7540-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="b7540-114">Para obter mais informações, consulte [conjuntos de referência](../../../standard/assembly/reference-assemblies.md) no Guia .NET.</span><span class="sxs-lookup"><span data-stu-id="b7540-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="b7540-115">As `-refout` [`-refonly`](refonly-compiler-option.md) opções são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="b7540-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7540-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7540-116">See also</span></span>

- [<span data-ttu-id="b7540-117">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="b7540-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b7540-118">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="b7540-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
