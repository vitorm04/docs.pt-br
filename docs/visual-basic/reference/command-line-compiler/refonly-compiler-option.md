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
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly. O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sintaxe

```console
-refonly
```

## <a name="remarks"></a>Comentários

Visual Basic supports the `-refonly` switch starting with version 15.3.

Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface. They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract. For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também

- [/refout](refout-compiler-option.md)
- [Compilador de linha de comando do Visual Basic](index.md)
- [Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)
