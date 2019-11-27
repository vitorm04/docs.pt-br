---
title: Tipos de métodos de manipulação de cadeia de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346279"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres. Alguns dos métodos fazem parte da linguagem de Visual Basic e outros são inerentes à classe `String`.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic idioma e o .NET Framework  
 Visual Basic métodos são usados como funções inerentes do idioma. Eles podem ser usados sem qualificação em seu código. O exemplo a seguir mostra o uso típico de um comando de manipulação de cadeia de caracteres Visual Basic:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 Neste exemplo, a função `Mid` executa uma operação direta em `aString` e atribui o valor a `bString`.  
  
 Para obter uma lista de métodos de manipulação de cadeia de caracteres Visual Basic, consulte [Resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Métodos compartilhados e métodos de instância  
 Você também pode manipular cadeias de caracteres com os métodos da classe `String`. Há dois tipos de métodos em `String`: métodos *compartilhados* e métodos de *instância* .  
  
#### <a name="shared-methods"></a>Métodos compartilhados  
 Um método compartilhado é um método que deriva da própria classe `String` e não requer uma instância dessa classe para funcionar. Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de uma instância da classe `String`. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 No exemplo anterior, o método <xref:System.String.Copy%2A?displayProperty=nameWithType> é um método estático, que atua em uma expressão que é fornecida e atribui o valor resultante a `bString`.  
  
#### <a name="instance-methods"></a>Métodos de instância  
 Os métodos de instância, por outro lado, são provenientes de uma instância específica do `String` e devem ser qualificados com o nome da instância. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 Neste exemplo, o método <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método da instância de `String` (ou seja, `aString`). Ele executa uma operação em `aString` e atribui esse valor a `bString`.  
  
 Para obter mais informações, consulte a documentação da classe <xref:System.String>.  
  
## <a name="see-also"></a>Consulte também

- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
