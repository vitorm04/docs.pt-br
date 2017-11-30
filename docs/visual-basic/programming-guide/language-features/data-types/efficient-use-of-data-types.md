---
title: Uso eficiente de tipos de dados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e13a1d61aacb06eb336c39aab969847127dfc67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Uso eficiente de tipos de dados (Visual Basic)
Variáveis não declaradas e declaradas sem um tipo de dados são atribuídas a `Object` tipo de dados. Isso facilita escrever programas rapidamente, mas isso pode causar a execução mais lenta.  
  
## <a name="strong-typing"></a>Tipagem forte  
 Especificar tipos de dados para todas as variáveis é conhecido como *tipagem forte*. Usar tipagem forte apresenta várias vantagens:  
  
-   Ele permite o suporte ao IntelliSense para suas variáveis. Isso permite que você veja suas propriedades e outros membros conforme você digita no código.  
  
-   Tira proveito da verificação de tipo do compilador. Captura instruções que podem falhar em tempo de execução devido a erros, como o estouro. Também captura chamadas para métodos em objetos que não dão suporte a eles.  
  
-   Isso resulta em execução mais rápida do seu código.  
  
## <a name="most-efficient-data-types"></a>Tipos de dados mais eficientes  
 Para variáveis que nunca contêm frações, os tipos de dados integrais são mais eficientes do que os tipos não integral. Em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` e `UInteger` são os tipos numéricos mais eficientes.  
  
 Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante de precisão dupla. No entanto, as operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.  
  
## <a name="specifying-data-type"></a>Especificar o tipo de dados  
 Use o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico. Você pode especificar simultaneamente seu nível de acesso usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, como no exemplo a seguir.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Conversão de caracteres  
 O `AscW` e `ChrW` funções operam em Unicode. Você deve usá-las preferencialmente a `Asc` e `Chr`, que devem traduzir de e para Unicode.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tipos de Dados Numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Usando o IntelliSense](/visualstudio/ide/using-intellisense)
