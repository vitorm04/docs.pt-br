---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653527"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Sintaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` O caminho e nome do arquivo do assembly de referência. Geralmente, ele deve ser em uma subpasta do assembly principal. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal. Todas as pastas no `filepath` devem existir; o compilador não criá-los. 

## <a name="remarks"></a>Comentários

Visual Basic oferece suporte a `-refout` alternar a partir da versão 15,3.

Assemblies de referência são somente metadados assemblies que contêm metadados, mas nenhum código de implementação. Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos. O corpo de método é substituído por um único `throw null` instrução. O motivo para usar `throw null` corpos de método (em vez de nenhum corpo) é que PEVerify pode executar e passar (Validando a integridade dos metadados).

Assemblies de referência incluem um nível de conjunto [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Devido a esse atributo, tempos de execução recusam carregar assemblies de referência de execução (mas ainda pode ser carregados em um contexto exclusivo de reflexão). Ferramentas que refletem em assemblies precisam garantir que eles carregam assemblies de referência como somente reflexão; Caso contrário, o tempo de execução gera um <xref:System.BadImageFormatException>.

As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também
[-refonly](refonly-compiler-option.md)   
[Compilador de linha de comando do Visual Basic](index.md)  
[Linhas de Comando de Compilação de Exemplo](sample-compilation-command-lines.md)  

