---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775557"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="434da-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="434da-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="434da-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="434da-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="434da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="434da-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="434da-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="434da-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="434da-106">O caminho e o nome do arquivo do assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="434da-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="434da-107">Em geral, ele deve estar em uma subpasta do assembly primário.</span><span class="sxs-lookup"><span data-stu-id="434da-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="434da-108">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="434da-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="434da-109">Todas as pastas no `filepath` devem existir; o compilador não os cria.</span><span class="sxs-lookup"><span data-stu-id="434da-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="434da-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="434da-110">Remarks</span></span>

<span data-ttu-id="434da-111">Visual Basic dá suporte à opção de `-refout` a partir da versão 15,3.</span><span class="sxs-lookup"><span data-stu-id="434da-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="434da-112">Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="434da-112">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="434da-113">Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API.</span><span class="sxs-lookup"><span data-stu-id="434da-113">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="434da-114">Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.</span><span class="sxs-lookup"><span data-stu-id="434da-114">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="434da-115">As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="434da-115">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="434da-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="434da-116">See also</span></span>

- [<span data-ttu-id="434da-117">/refonly</span><span class="sxs-lookup"><span data-stu-id="434da-117">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="434da-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="434da-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="434da-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="434da-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
