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
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771754"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="11076-102">-refout (Opções do compilador do C#)</span><span class="sxs-lookup"><span data-stu-id="11076-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="11076-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="11076-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="11076-104">Isso se converte em `metadataPeStream` na API de emissão.</span><span class="sxs-lookup"><span data-stu-id="11076-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="11076-105">Essa opção corresponde à propriedade de projeto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="11076-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="11076-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11076-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="11076-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="11076-107">Arguments</span></span>

 <span data-ttu-id="11076-108">`filepath` O fipeath so assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="11076-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="11076-109">Geralmente, ele deve corresponder ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="11076-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="11076-110">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="11076-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="11076-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="11076-111">Remarks</span></span>

<span data-ttu-id="11076-112">Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="11076-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="11076-113">Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="11076-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="11076-114">Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.</span><span class="sxs-lookup"><span data-stu-id="11076-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="11076-115">As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="11076-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="11076-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11076-116">See also</span></span>

- [<span data-ttu-id="11076-117">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="11076-117">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="11076-118">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="11076-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
