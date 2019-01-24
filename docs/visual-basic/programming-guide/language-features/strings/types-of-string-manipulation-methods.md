---
title: Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: fa579303ad268a88269f360bdf626f9590c5d6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648489"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres. Alguns dos métodos fazem parte da linguagem Visual Basic, e outros são inerentes a `String` classe.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Linguagem Visual Basic e o .NET Framework  
 Métodos de Visual Basic são usados como funções inerentes da linguagem. Eles podem ser usados sem qualificação no seu código. O exemplo a seguir mostra um uso típico de um comando de manipulação de cadeia de caracteres do Visual Basic:  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Neste exemplo, o `Mid` função executa uma operação no `aString` e atribui o valor a ser `bString`.  
  
 Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Métodos compartilhados e métodos de instância  
 Você também pode manipular cadeias de caracteres com os métodos do `String` classe. Há dois tipos de métodos em `String`: *compartilhada* métodos e *instância* métodos.  
  
#### <a name="shared-methods"></a>Métodos compartilhados  
 Um método compartilhado é um método que deriva de `String` própria classe e não requer uma instância da classe para funcionar. Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de usar uma instância da `String` classe. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=nameWithType> método é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.  
  
#### <a name="instance-methods"></a>Métodos de instância  
 Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método da instância do `String` (ou seja, `aString`). Ele executa uma operação em `aString` e atribui o valor para `bString`.  
  
 Para obter mais informações, consulte a documentação para o <xref:System.String> classe.  
  
## <a name="see-also"></a>Consulte também
- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
