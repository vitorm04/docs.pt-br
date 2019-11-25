---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348572"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="a040f-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a040f-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="a040f-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span><span class="sxs-lookup"><span data-stu-id="a040f-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="a040f-104">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="a040f-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="a040f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a040f-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="a040f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a040f-106">Remarks</span></span>

<span data-ttu-id="a040f-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span><span class="sxs-lookup"><span data-stu-id="a040f-107">Visual Basic supports the `-refonly` switch starting with version 15.3.</span></span>

<span data-ttu-id="a040f-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span><span class="sxs-lookup"><span data-stu-id="a040f-108">Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface.</span></span> <span data-ttu-id="a040f-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span><span class="sxs-lookup"><span data-stu-id="a040f-109">They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract.</span></span> <span data-ttu-id="a040f-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span><span class="sxs-lookup"><span data-stu-id="a040f-110">For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.</span></span>

<span data-ttu-id="a040f-111">As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="a040f-111">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="a040f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a040f-112">See also</span></span>

- [<span data-ttu-id="a040f-113">/refout</span><span class="sxs-lookup"><span data-stu-id="a040f-113">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="a040f-114">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a040f-114">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a040f-115">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="a040f-115">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
