---
title: -refout
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 3649a24a52cc6a448ea7cf4d850915adf02147fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348647"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sintaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

`filepath`  
The path and filename of the reference assembly. It should generally be in a sub-folder of the primary assembly. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal. All folders in `filepath` must exist; the compiler does not create them.

## <a name="remarks"></a>Comentários

Visual Basic supports the `-refout` switch starting with version 15.3.

Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface. They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract. For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também

- [/refonly](refonly-compiler-option.md)
- [Compilador de linha de comando do Visual Basic](index.md)
- [Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)
