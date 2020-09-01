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
# <a name="-refout-c-compiler-options"></a>-refout (Opções do compilador do C#)

A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado. Isso se converte em `metadataPeStream` na API de emissão. Essa opção corresponde à propriedade de projeto [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) do MSBuild.

## <a name="syntax"></a>Sintaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Argumentos

 `filepath` O fipeath so assembly de referência. Geralmente, ele deve corresponder ao assembly principal. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.

## <a name="remarks"></a>Comentários

Os assemblies de referência são um tipo especial de assembly que contém apenas a quantidade mínima de metadados necessários para representar a superfície da API pública da biblioteca. Eles incluem declarações para todos os membros que são significativos ao referenciar um assembly em ferramentas de compilação, mas excluem todas as implementações de membro e declarações de membros privados que não têm impacto observável em seu contrato de API. Para obter mais informações, consulte [Reference Assemblies](../../../standard/assembly/reference-assemblies.md) in .net Guide.

As `-refout` [`-refonly`](refonly-compiler-option.md) Opções e são mutuamente exclusivas.

## <a name="see-also"></a>Confira também

- [Opções do compilador C#](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
