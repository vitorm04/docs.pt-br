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
# <a name="-refout-c-compiler-options"></a>-refout (Opções do compilador do C#)

A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado. Isso se converte em `metadataPeStream` na API de emissão. Essa opção corresponde à propriedade de projeto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.

## <a name="syntax"></a>Sintaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Argumentos

 `filepath` O fipeath so assembly de referência. Geralmente, ele deve corresponder ao assembly principal. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.

## <a name="remarks"></a>Comentários

Os conjuntos de referência são um tipo especial de montagem que contém apenas a quantidade mínima de metadados necessários para representar a superfície pública da API da biblioteca. Eles incluem declarações para todos os membros que são significativas ao fazer referência a uma assembléia em ferramentas de construção, mas excluem todas as implementações de membros membros e declarações de membros privados que não tenham impacto observável em seu contrato de API. Para obter mais informações, consulte [conjuntos de referência](../../../standard/assembly/reference-assemblies.md) no Guia .NET.

As `-refout` [`-refonly`](refonly-compiler-option.md) opções são mutuamente exclusivas.

## <a name="see-also"></a>Confira também

- [C# Opções de compilador](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
