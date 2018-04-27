---
title: Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3677c8a23e956716af4357fe79041fc96f4014f2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Tipos de métodos de manipulação da cadeia de caracteres no Visual Basic
Há várias maneiras diferentes de analisar e manipular suas cadeias de caracteres. Alguns dos métodos fazem parte da linguagem do Visual Basic e outros são inerentes a `String` classe.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Linguagem Visual Basic e o .NET Framework  
 Métodos do Visual Basic são usados como sendo funções inerentes da linguagem. Eles podem ser usados sem qualificação no seu código. O exemplo a seguir mostra o uso típico de um comando de manipulação de cadeia de caracteres do Visual Basic:  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 Neste exemplo, o `Mid` função executa uma operação em `aString` e atribui o valor a ser `bString`.  
  
 Para obter uma lista de métodos de manipulação de cadeia de caracteres do Visual Basic, consulte [resumo de manipulação de cadeia de caracteres](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Métodos compartilhados e métodos de instância  
 Você também pode manipular cadeias de caracteres com os métodos do `String` classe. Há dois tipos de métodos em `String`: *compartilhado* métodos e *instância* métodos.  
  
#### <a name="shared-methods"></a>Métodos compartilhados  
 Um método compartilhado é um método que deriva de `String` classe em si e não requer uma instância da classe para funcionar. Esses métodos podem ser qualificados com o nome da classe (`String`) em vez de com uma instância do `String` classe. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 No exemplo anterior, o <xref:System.String.Copy%2A?displayProperty=nameWithType> é um método estático, que age sobre uma expressão fornecida e atribui o valor resultante para `bString`.  
  
#### <a name="instance-methods"></a>Métodos de instância  
 Métodos de instância, por outro lado, derivam de uma determinada instância de `String` e devem ser qualificados com o nome da instância. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 Neste exemplo, o <xref:System.String.Substring%2A?displayProperty=nameWithType> é um método de instância de `String` (ou seja, `aString`). Ele executa uma operação em `aString` e atribui o valor para `bString`.  
  
 Para obter mais informações, consulte a documentação para o <xref:System.String> classe.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
