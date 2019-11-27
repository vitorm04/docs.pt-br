---
title: Como criar uma nova variável
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 2a2b5b8bef3b66f9727f0e65b61882186c007e94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353629"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Como criar uma nova variável (Visual Basic)

Você cria uma variável com uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

### <a name="to-create-a-new-variable"></a>Para criar uma nova variável

1. Declare a variável em uma instrução `Dim`.

    ```vb
    Dim newCustomer
    ```

2. Inclua especificações para as características da variável, como [privado](../../../../visual-basic/language-reference/modifiers/private.md), [estático](../../../../visual-basic/language-reference/modifiers/static.md), [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Para obter mais informações, consulte [características de elemento declaradas](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).

    ```vb
    Public Static newCustomer
    ```

    Você não precisará da palavra-chave `Dim` se usar outras palavras-chaves na declaração.

3. Siga as especificações com o nome da variável, que deve seguir Visual Basic regras e convenções. Para obter mais informações, consulte [nomes de elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

    ```vb
    Public Static newCustomer
    ```

4. Siga o nome com a [cláusula as](../../../../visual-basic/language-reference/statements/as-clause.md) para especificar o tipo de dados da variável.

    ```vb
    Public Static newCustomer As Customer
    ```

    Se você não especificar o tipo de dados, ele usará o padrão: `Object`.

5. Siga a cláusula `As` com um sinal de igual (`=`) e siga o sinal de igual com o valor inicial da variável.

    Visual Basic atribui o valor especificado à variável toda vez que executa a instrução `Dim`. Se você não especificar um valor inicial, Visual Basic atribuirá o valor inicial padrão para o tipo de dados da variável quando ele entrar pela primeira vez no código que contém a instrução `Dim`.

    Se a variável for um tipo de referência, você poderá criar uma instância de sua classe, incluindo a palavra-chave [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) na cláusula `As`. Se você não usar `New`, o valor inicial da variável será [Nothing](../../../../visual-basic/language-reference/nothing.md).

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a>Consulte também

- [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Instruções](../../../../visual-basic/language-reference/statements/index.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
