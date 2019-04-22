---
title: Uso eficiente de tipos de dados (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 0b517bca3a9e296eb891e30df91c1d32eb357432
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830117"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Uso eficiente de tipos de dados (Visual Basic)
Variáveis não declaradas e as variáveis declaradas sem um tipo de dados são atribuídas a `Object` tipo de dados. Isso torna mais fácil escrever programas rapidamente, mas ele pode fazer com que eles sejam executados mais lentamente.  
  
## <a name="strong-typing"></a>Tipagem forte  
 Especificar tipos de dados para todas as variáveis é conhecido como *tipagem forte*. Usando a tipagem forte tem várias vantagens:  
  
-   Ele permite que o suporte do IntelliSense para as variáveis. Isso permite que você veja suas propriedades e outros membros conforme você digita no código.  
  
-   Ela tira proveito da verificação de tipo do compilador. Captura instruções que podem falhar em tempo de execução devido a erros, como estouro. Ela também captura chamadas para métodos em objetos que não dão suporte a eles.  
  
-   Isso resulta em uma execução mais rápida do seu código.  
  
## <a name="most-efficient-data-types"></a>Tipos de dados mais eficientes  
 Para variáveis que nunca contêm frações, os tipos de dados integrais são mais eficientes do que os tipos não integral. No Visual Basic `Integer` e `UInteger` são os tipos numéricos mais eficientes.  
  
 Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante de precisão dupla. No entanto, as operações com `Double` não são tão rápidos, assim como acontece com os tipos integrais como `Integer`.  
  
## <a name="specifying-data-type"></a>Especificando o tipo de dados  
 Use o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico. Você pode especificar simultaneamente seu nível de acesso usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, como no exemplo a seguir.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Conversão de caracteres  
 O `AscW` e `ChrW` funções operam em Unicode. Você deve usá-las preferencialmente a `Asc` e `Chr`, que devem traduzir dentro e fora de Unicode.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Usando o IntelliSense](/visualstudio/ide/using-intellisense)
