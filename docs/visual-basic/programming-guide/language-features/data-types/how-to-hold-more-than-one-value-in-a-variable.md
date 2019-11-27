---
title: Como manter mais de um valor em uma variável
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350017"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Como manter mais de um valor em uma variável (Visual Basic)

Uma variável contém mais de um valor se você declará-lo para ser de um *tipo de dados composto*.

[Os tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem estruturas, matrizes e classes. Uma variável de um tipo de dados de composição pode conter uma combinação de tipos de dados elementares e outros tipos compostos. Estruturas e classes podem conter código, bem como dados.

## <a name="to-hold-more-than-one-value-in-a-variable"></a>Para conter mais de um valor em uma variável

1. Determine o tipo de dados composto que você deseja usar para a variável.

2. Se o tipo de dados composto ainda não estiver definido, defina-o para que sua variável possa usá-lo.

    - Defina uma estrutura com uma [instrução de estrutura](../../../../visual-basic/language-reference/statements/structure-statement.md).

    - Defina uma matriz com uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).

    - Defina uma classe com uma [instrução de classe](../../../../visual-basic/language-reference/statements/class-statement.md).

3. Declare sua variável com uma instrução `Dim`.

4. Siga o nome da variável com uma cláusula `As`.

5. Siga a palavra-chave `As` com o nome do tipo de dados composto apropriado.

## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
