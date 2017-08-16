---
title: "Tipos de métodos de manipulação de cadeia de caracteres no Visual Basic | Documentos do Microsoft"
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
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
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
ms.openlocfilehash: 349cfdb3e31225f6aeba90ac29aa1c66e37c7e11
ms.lasthandoff: 03/13/2017

---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres. Alguns dos métodos fazem parte do [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] idioma e outros são inerentes a `String` classe.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Linguagem Visual Basic e o .NET Framework  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]métodos são usados como sendo funções inerentes da linguagem. Eles podem ser usados sem qualificação no seu código. O exemplo a seguir mostra o uso típico de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] comando de manipulação de cadeia de caracteres:  
  
 [!code-vb[VbVbalrStrings&#44;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Neste exemplo, o `Mid` função executa uma operação em `aString` e atribui o valor para `bString`.  
  
 Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Métodos compartilhados e métodos de instância  
 Você também pode manipular cadeias de caracteres com os métodos de `String` classe. Há dois tipos de métodos em `String`: *compartilhado* métodos e *instância* métodos.  
  
#### <a name="shared-methods"></a>Métodos compartilhados  
 Um método compartilhado é um método que deriva de `String` classe em si e não requer uma instância da classe para funcionar. Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de usar uma instância do `String` classe. Por exemplo:  
  
 [!code-vb[45 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=fullName>método é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.</xref:System.String.Copy%2A?displayProperty=fullName>  
  
#### <a name="instance-methods"></a>Métodos de instância  
 Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância. Por exemplo:  
  
 [!code-vb[46 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=fullName>método é um método de instância de `String` (ou seja, `aString`).</xref:System.String.Substring%2A?displayProperty=fullName> Ele realiza uma operação em `aString` e atribui o valor para `bString`.  
  
 Para obter mais informações, consulte a documentação para a <xref:System.String>classe.</xref:System.String>  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
