---
title: Tipos de dados (Visual Basic) de caractere | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7ce600fe188c94593e4c07e37883ca11f90d9ae5
ms.lasthandoff: 03/13/2017

---
# <a name="character-data-types-visual-basic"></a>Tipos de dados de caractere (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece *tipos de dados de caractere* para lidar com caracteres imprimível e pode ser exibido. Enquanto ambos lidem com caracteres Unicode, `Char` contém um único caractere enquanto `String` contém um número indefinido de caracteres.  
  
 Para uma tabela que exiba uma comparação lado a lado do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Tipo char  
 O `Char` tipo de dados é um caractere de Unicode único de dois bytes (16 bits). Se uma variável sempre armazena exatamente um caractere, declare-o como `Char`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes n º&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Cada valor possível em uma `Char` ou `String` variável é uma *ponto de código*, ou código de caractere no conjunto de caracteres Unicode. Caracteres Unicode incluem o conjunto de caracteres ASCII básico, várias outras letras do alfabeto, acentos, símbolos de moeda, frações, diacríticos e símbolos matemáticos e técnicos.  
  
> [!NOTE]
>  O caractere Unicode definido reserva os pontos de código entre D800 e DFFF (55296 até 55551 em decimal) para *pares substitutos*, que requerem dois valores de 16 bits para representar um único ponto de código. A `Char` variável não pode armazenar um par substituto e uma `String` usa duas posições para armazenar tal par.  
  
 Para obter mais informações, consulte [tipo de dados Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Tipo de cadeia de caracteres  
 O `String` tipo de dados é uma sequência de zero ou mais caracteres de Unicode (16 bits) de dois bytes. Se uma variável pode conter um número indefinido de caracteres, declare-o como `String`. Por exemplo:  
  
 [!code-vb[VbVbalrCharTypes n º&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Para obter mais informações, consulte [tipo de dados de cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
