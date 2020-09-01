---
description: -refout (Opções do compilador do C#)
title: -refout (Opções do compilador do C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 424782e4607fea63130e95ab09a671c75fe1404d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128708"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="9c72a-103">-refout (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="9c72a-103">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="9c72a-104">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="9c72a-104">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="9c72a-105">Isso se converte em `metadataPeStream` na API de emissão.</span><span class="sxs-lookup"><span data-stu-id="9c72a-105">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="9c72a-106">Essa opção corresponde à propriedade de projeto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9c72a-106">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c72a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c72a-107">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="9c72a-108">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9c72a-108">Arguments</span></span>

 <span data-ttu-id="9c72a-109">`filepath` O fipeath so assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="9c72a-109">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="9c72a-110">Geralmente, ele deve corresponder ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="9c72a-110">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="9c72a-111">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="9c72a-111">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c72a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c72a-112">Remarks</span></span>

<span data-ttu-id="9c72a-113">Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9c72a-113">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="9c72a-114">Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="9c72a-114">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="9c72a-115">Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.</span><span class="sxs-lookup"><span data-stu-id="9c72a-115">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="9c72a-116">As `-refout` [`-refonly`](refonly-compiler-option.md) Opções e são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="9c72a-116">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c72a-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="9c72a-117">See also</span></span>

- [<span data-ttu-id="9c72a-118">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="9c72a-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9c72a-119">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="9c72a-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
