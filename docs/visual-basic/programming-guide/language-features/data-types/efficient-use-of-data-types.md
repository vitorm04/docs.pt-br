---
title: Uso eficiente de tipos de dados (Visual Basic) | Documentos do Microsoft
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
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
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
ms.openlocfilehash: b81a1c81d970beee32925c3f2fe6ca3bcad79151
ms.lasthandoff: 03/13/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a>Uso eficiente de tipos de dados (Visual Basic)
Variáveis não declaradas e declaradas sem um tipo de dados são atribuídas a `Object` tipo de dados. Isso facilita escrever programas rapidamente, mas ele pode fazer com que sejam executados mais lentamente.  
  
## <a name="strong-typing"></a>Tipagem forte  
 Especificar tipos de dados para todas as variáveis é conhecido como *tipagem forte*. Usar tipagem forte apresenta várias vantagens:  
  
-   Ela permite suporte IntelliSense para suas variáveis. Isso permite que você veja suas propriedades e outros membros conforme você digita no código.  
  
-   Tira proveito da verificação de tipo do compilador. Captura instruções que podem falhar em tempo de execução devido a erros como overflow. Ele também captura chamadas para métodos em objetos que não oferecem suporte a eles.  
  
-   Isso resulta em execução mais rápida do seu código.  
  
## <a name="most-efficient-data-types"></a>Tipos de dados mais eficientes  
 Para variáveis que nunca contêm frações, os tipos de dados integrais são mais eficientes do que os tipos não integral. Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` e `UInteger` são os tipos numéricos mais eficientes.  
  
 Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante de precisão dupla. No entanto, operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.  
  
## <a name="specifying-data-type"></a>Especificando o tipo de dados  
 Use o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico. Você pode especificar simultaneamente seu nível de acesso usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), ou [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, como no exemplo a seguir.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Conversão de caracteres  
 O `AscW` e `ChrW` funções operam em Unicode. Você deve usá-las preferencialmente a `Asc` e `Chr`, que devem traduzir de e para Unicode.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Usando o IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)
