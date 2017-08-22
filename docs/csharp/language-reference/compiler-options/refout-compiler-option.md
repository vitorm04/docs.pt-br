---
title: "-refout (Opções do compilador do C#)"
ms.date: 2017-08-08
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /refout
dev_langs:
- CSharp
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 81a2252314ef51b5dc01fddc081eb881aa4431a7
ms.openlocfilehash: b1516356bf7ec8f5716c0c4183148f675f2ffa78
ms.contentlocale: pt-br
ms.lasthandoff: 08/16/2017

---

# <a name="refout-c-compiler-options"></a>/refout (Opções do compilador do C#)

A opção **/refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado. Isso se converte em `metadataPeStream` na API de emissão.

## <a name="syntax"></a>Sintaxe

```console
/refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` O fipeath so assembly de referência. Geralmente, ele deve corresponder ao assembly principal. A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.

## <a name="remarks"></a>Comentários

Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos. O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).

Os assemblies de referência incluem um atributo `ReferenceAssembly` de nível de assembly. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Por causa desse atributo, os tempos de execução se recusarão a carregar assemblies de referência para execução (mas ainda podem ser carregados em modo somente reflexão). As ferramentas que se refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão, caso contrário, elas receberão um erro de typeload do tempo de execução.

Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:

- Um assembly de referência tem somente referências para o que ele precisa na superfície de API. Talvez o assembly real tenha outras referências relacionadas a implementações específicas. Por exemplo, o assembly de referência para `class C { private void M() { dynamic d = 1; ... } }` não referencia nenhum tipo necessário para `dynamic`.
- Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação. Se não houver nenhum atributo `InternalsVisibleTo`, faça o mesmo para os membros de função internos.
- Mas todos os tipos (incluindo tipos aninhados ou privados) são mantidos em assemblies de referência. Todos os atributos são mantidos (até mesmo os internos).
- Todos os métodos virtuais são mantidos. As implementações explícitas da interface são mantidas. As propriedades e eventos explicitamente implementados são mantidos, uma vez que seus acessadores são virtuais (e são, portanto, mantidos).
- Todos os campos de um struct são mantidos. (Este é um candidato para refinamento pós-c#-7.1)

As opções `/refout` e [`/refonly`](refonly-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

