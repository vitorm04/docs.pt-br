---
title: Tipos de dados de caractere
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346389"
---
# <a name="character-data-types-visual-basic"></a>Tipos de dados de caractere (Visual Basic)
Visual Basic fornece *tipos de dados de caractere* para lidar com caracteres imprimíveis e exibíveis. Embora ambos lidem com caracteres Unicode, `Char` mantém um único caractere, enquanto `String` contém um número indefinido de caracteres.  
  
 Para uma tabela que exibe uma comparação lado a lado do Visual Basic tipos de dados, consulte tipos de [dados](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Tipo de caractere  
 O tipo de dados `Char` é um caractere Unicode único de dois bytes (16 bits). Se uma variável sempre armazenar exatamente um caractere, declare-a como `Char`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Cada valor possível em uma variável `Char` ou `String` é um *ponto de código*, ou código de caractere, no conjunto de caracteres Unicode. Os caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos monetários, frações, sinais diacríticos e símbolos matemáticos e técnicos.  
  
> [!NOTE]
> O conjunto de caracteres Unicode reserva os pontos de código D800 por meio de DFFF (55296 a 55551 decimal) para *pares substitutos*, que exigem valores de 2 16 bits para representar um único ponto de código. Uma variável `Char` não pode conter um par substituto e uma `String` usa duas posições para manter esse par.  
  
 Para obter mais informações, consulte [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Tipo de cadeia de caracteres  
 O tipo de dados `String` é uma sequência de zero ou mais caracteres Unicode de dois bytes (16 bits). Se uma variável puder conter um número indefinido de caracteres, declare-a como `String`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Para obter mais informações, consulte [cadeia de caracteres tipo de dados](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
