---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582866"
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

Os assemblies de referência são assemblies somente de metadados que contêm metadados, mas nenhum código de implementação. Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos. Seus corpos de método são substituídos por uma única instrução de `throw null`. O motivo para usar `throw null` corpos de método (em oposição a nenhum corpo) é para que PEVerify possa executar e passar (Validando assim a integridade dos metadados).

Os assemblies de referência incluem um atributo [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) no nível do assembly. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Devido a esse atributo, os tempos de execução se recusam a carregar assemblies de referência para execução (mas eles ainda podem ser carregados em um contexto somente de reflexão). As ferramentas que refletem em assemblies precisam garantir que carreguem assemblies de referência como somente reflexão; caso contrário, o tempo de execução gera um <xref:System.BadImageFormatException>.

As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também

- [/refonly](refonly-compiler-option.md)
- [Compilador de linha de comando do Visual Basic](index.md)
- [Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)
