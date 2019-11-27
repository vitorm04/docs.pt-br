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
O caminho e o nome do arquivo do assembly de referência. Em geral, ele deve estar em uma subpasta do assembly primário. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal. Todas as pastas no `filepath` devem existir; o compilador não os cria.

## <a name="remarks"></a>Comentários

Visual Basic dá suporte à opção de `-refout` a partir da versão 15,3.

Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca. Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API. Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.

As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também

- [/refonly](refonly-compiler-option.md)
- [Compilador de linha de comando do Visual Basic](index.md)
- [Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)
