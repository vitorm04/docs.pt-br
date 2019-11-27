---
title: Como criar uma variável que não se altera no valor
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348641"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Como criar uma variável que não se altera no valor (Visual Basic)

A noção de uma variável que não altera seu valor pode parecer ser contraditória. Mas há situações em que uma constante não é viável e é útil ter uma variável com um valor fixo. Nesse caso, você pode definir uma variável de membro com a palavra-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

Você não pode usar a [instrução const](../../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribuir um valor constante nas seguintes circunstâncias:

- A instrução `Const` não aceita o tipo de dados que você deseja usar

- Você não conhece o valor no tempo de compilação

- Não é possível calcular o valor constante no tempo de compilação

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Para criar uma variável que não é alterada no valor

1. Em nível de módulo, declare uma variável de membro com a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)e inclua a palavra-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .

    ```vb
    Dim ReadOnly timeStarted
    ```

    Você pode especificar `ReadOnly` apenas em uma variável de membro. Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.

2. Se você puder calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização na instrução `Dim`. Siga a [cláusula as com](../../../../visual-basic/language-reference/statements/as-clause.md) um sinal de igual (`=`), seguido por uma expressão. Verifique se o compilador pode avaliar essa expressão como um valor constante.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Você pode atribuir um valor a uma variável `ReadOnly` apenas uma vez. Depois de fazer isso, nenhum código pode alterar seu valor.

    Se você não souber o valor em tempo de compilação, ou não puder computar em tempo de compilação em uma única instrução, ainda poderá atribuí-lo em tempo de execução em um construtor. Para fazer isso, você deve declarar a variável `ReadOnly` no nível de classe ou estrutura. No construtor para essa classe ou estrutura, calcule o valor fixo da variável e atribua-o à variável antes de retornar do construtor.

## <a name="see-also"></a>Consulte também

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)
