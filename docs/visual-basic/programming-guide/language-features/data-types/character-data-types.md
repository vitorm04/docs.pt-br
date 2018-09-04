---
title: Tipos de dados de caractere (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 3b031c6e3dc04637128f95ca8e922d3298981287
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553566"
---
# <a name="character-data-types-visual-basic"></a>Tipos de dados de caractere (Visual Basic)
O Visual Basic fornece *tipos de dados de caractere* para lidar com caracteres imprimível e que pode ser exibido. Enquanto ambos lidem com caracteres de Unicode `Char` contém um único caractere, enquanto `String` contém um número indefinido de caracteres.  
  
 Para uma tabela que exibe uma comparação lado a lado dos tipos de dados do Visual Basic, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Tipo char  
 O `Char` tipo de dados é um único caractere de Unicode de dois bytes (16 bits). Se uma variável sempre armazena exatamente um caractere, declare-o como `Char`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Cada valor possível em uma `Char` ou `String` variável é um *ponto de código*, ou código de caractere no conjunto de caracteres Unicode. Caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos de moeda, frações, diacríticos e símbolos matemáticos e técnicos.  
  
> [!NOTE]
>  O caractere Unicode definir os pontos de código u+D800 DFFF (55296 até 55551 em decimal) para as reservas *pares substitutos*, que exige dois valores de 16 bits para representar um único ponto de código. Um `Char` variável não pode armazenar um par substituto e um `String` usa duas posições para armazenar tal par.  
  
 Para obter mais informações, consulte [tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Tipo de cadeia de caracteres  
 O `String` tipo de dados é uma sequência de zero ou mais caracteres de Unicode (16 bits) de dois bytes. Se uma variável pode conter um número indefinido de caracteres, declare-o como `String`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Para obter mais informações, consulte [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
