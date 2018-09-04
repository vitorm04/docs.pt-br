---
title: Como manter mais de um valor em uma variável (Visual Basic)
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
ms.openlocfilehash: 781f56c7e710f5130d821ca4796398379dfa4c6e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517957"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Como manter mais de um valor em uma variável (Visual Basic)
Uma variável contém mais de um valor se você declará-la para ser de um *tipo de dados composto*.  
  
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem classes, matrizes e estruturas. Uma variável de um tipo de dados composto pode conter uma combinação de tipos de dados elementares e outros tipos compostos. Estruturas e classes podem conter código, bem como dados.  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>Para manter mais de um valor em uma variável  
  
1.  Determine que tipo de dados compostos que você deseja usar para sua variável.  
  
2.  Se o tipo de dados compostos já não estiver definido, defini-lo para que sua variável possa usá-lo.  
  
    -   Definir uma estrutura com um [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Definir uma matriz com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Defina uma classe com um [declaração de classe](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Declare a variável com um `Dim` instrução.  
  
4.  Siga o nome da variável com um `As` cláusula.  
  
5.  Siga o `As` palavra-chave com o nome do tipo de dados compostos apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)  
 [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
