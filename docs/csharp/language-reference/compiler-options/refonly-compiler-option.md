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
# <a name="-refonly-c-compiler-options"></a>-refonly (Opções do compilador do C#)

A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária. O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados. Essa opção corresponde à propriedade de projeto [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.

## <a name="syntax"></a>Sintaxe

```console
-refonly
```

## <a name="remarks"></a>Comentários

Os conjuntos de referência são um tipo especial de montagem que contém apenas a quantidade mínima de metadados necessários para representar a superfície pública da API da biblioteca. Eles incluem declarações para todos os membros que são significativas ao fazer referência a uma assembléia em ferramentas de construção, mas excluem todas as implementações de membros membros e declarações de membros privados que não tenham impacto observável em seu contrato de API. Para obter mais informações, consulte [conjuntos de referência](../../../standard/assembly/reference-assemblies.md) no Guia .NET.

As `-refonly` [`-refout`](refout-compiler-option.md) opções são mutuamente exclusivas.

## <a name="see-also"></a>Confira também

- [C# Opções de compilador](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
