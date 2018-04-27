---
title: Tipos de dados de caractere (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dca9cde0af08c4113ea9a4644efa40a721b4d9b1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="character-data-types-visual-basic"></a>Tipos de dados de caractere (Visual Basic)
Visual Basic fornece *tipos de dados de caractere* para lidar com caracteres imprimível e pode ser exibido. Enquanto ambos lidem com caracteres Unicode, `Char` contém um único caractere enquanto `String` contém um número indefinido de caracteres.  
  
 Para uma tabela que exibe uma comparação lado a lado dos tipos de dados do Visual Basic, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Tipo char  
 O `Char` tipo de dados é um único caractere de Unicode de dois bytes (16 bits). Se uma variável sempre armazena exatamente um caractere, declare-o como `Char`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Cada valor possível em um `Char` ou `String` variável é uma *ponto de código*, ou código de caractere no conjunto de caracteres Unicode. Caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos de moeda, frações, diacríticos e símbolos matemáticos e técnicos.  
  
> [!NOTE]
>  O caractere Unicode definir os pontos de código D800 e DFFF (55296 até 55551 em decimal) para as reservas *pares substitutos*, que exigem dois valores de 16 bits para representar um único ponto de código. Um `Char` variável não pode conter um par substituto e um `String` usa duas posições para armazenar tal par.  
  
 Para obter mais informações, consulte [tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Tipo de cadeia de caracteres  
 O `String` tipo de dados é uma sequência de caracteres de Unicode do zero ou mais de dois bytes (16 bits). Se uma variável pode conter um número indefinido de caracteres, declare-o como `String`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Para obter mais informações, consulte [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
