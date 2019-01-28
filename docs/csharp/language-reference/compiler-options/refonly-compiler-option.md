---
title: -refonly (Opções do compilador do C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 06b246d6e5831563389efa402ccb6a942430efa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589721"
---
# <a name="-refonly-c-compiler-options"></a>-refonly (Opções do compilador do C#)

A opção **-refonly** indica que um assembly de referência deve ser gerado em vez de um assembly de implementação, como a saída primária. O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.

## <a name="syntax"></a>Sintaxe

```console
-refonly
```

## <a name="remarks"></a>Comentários

Os assemblies somente de metadados têm seus corpos de método substituídos por um único corpo `throw null`, mas incluem todos os membros, exceto tipos anônimos. O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).

Os assemblies de referência incluem um atributo `ReferenceAssembly` de nível de assembly. Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo). Por causa desse atributo, os tempos de execução se recusarão a carregar assemblies de referência para execução (mas ainda podem ser carregados em modo somente reflexão). As ferramentas que se refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão, caso contrário, elas receberão um erro de typeload do tempo de execução.

Os assemblies de referência removem ainda mais metadados (membros particulares) de assemblies somente de metadados:

- Um assembly de referência tem somente referências para o que ele precisa na superfície de API. Talvez o assembly real tenha outras referências relacionadas a implementações específicas. Por exemplo, o assembly de referência para `class C { private void M() { dynamic d = 1; ... } }` não referencia nenhum tipo necessário para `dynamic`.
- Membros de função privados (métodos, propriedades e eventos) são removidos nos casos em que sua remoção não afeta nitidamente a compilação. Se não houver nenhum atributo `InternalsVisibleTo`, faça o mesmo para os membros de função internos.
- Mas todos os tipos (incluindo tipos aninhados ou privados) são mantidos em assemblies de referência. Todos os atributos são mantidos (até mesmo os internos).
- Todos os métodos virtuais são mantidos. As implementações explícitas da interface são mantidas. As propriedades e eventos explicitamente implementados são mantidos, uma vez que seus acessadores são virtuais (e são, portanto, mantidos).
- Todos os campos de um struct são mantidos. (Este é um candidato para refinamento pós-c#-7.1)

As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
