---
title: "Como controlar a disponibilidade de uma variável (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Como controlar a disponibilidade de uma variável (Visual Basic)
Controlar a disponibilidade de uma variável especificando seu *nível de acesso*. O nível de acesso determina qual código tem permissão para ler ou gravar para a variável.  
  
-   *Variáveis de membro* (definido no nível de módulo e fora de qualquer procedimento) padrão para acesso público, o que significa que qualquer código que pode vê-los pode acessá-los. Você pode alterar isso, especificando um modificador de acesso.  
  
-   *Variáveis locais* (definido dentro de um procedimento) tem uma acesso público, embora somente o código dentro do seu procedimento pode acessá-los. Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.  
  
 Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Acesso privado e público  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Para disponibilizar uma variável somente de dentro de seu módulo, classe ou estrutura  
  
1.  Coloque o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Para disponibilizar uma variável de qualquer código que pode vê-lo  
  
1.  Para uma variável de membro, coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável de qualquer código que interage com seu assembly.  
  
 -ou-  
  
1.  Para uma variável local, coloque o `Dim` instrução para a variável dentro de um procedimento.  
  
2.  Não inclua o `Public` palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do procedimento, mas não de fora.  
  
## <a name="protected-and-friend-access"></a>Protegido e o acesso Friend  
 Você pode limitar o nível de acesso de uma variável para sua classe e qualquer classe derivada ou seu assembly. Você também pode especificar a união dessas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly. Especifique esta união combinando o `Protected` e `Friend` palavras-chave na mesma declaração.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Para disponibilizar uma variável somente de dentro de sua classe e todas as classes derivadas  
  
1.  Coloque o `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.  
  
2.  Incluir o [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar para a variável em qualquer lugar dentro da classe, bem como no qualquer classe derivada dela, mas não de fora de qualquer classe na cadeia de derivação.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Para disponibilizar uma variável somente de dentro do mesmo assembly  
  
1.  Coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, bem como qualquer código no mesmo assembly, mas não de fora do assembly.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra as declarações de variáveis com `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private` níveis de acesso. Observe que, quando o `Dim` instrução Especifica um nível de acesso, você não precisa incluir o `Dim` palavra-chave.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A configuração mais restritiva o nível de acesso de uma variável, menores as chances de código mal-intencionado pode fazer inadequado usá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Público](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privado](../../../../visual-basic/language-reference/modifiers/private.md)
