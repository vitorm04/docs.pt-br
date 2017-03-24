---
title: "Como: controlar a disponibilidade de uma variável (Visual Basic) | Documentos do Microsoft"
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
- access levels, declared elements
- Private keyword, accessing variables
- access levels, variables
- Public keyword, accessing variables
- Friend keyword, accessing variables
- variables [Visual Basic], access level
- declared elements, access level
- Protected keyword, accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 3c36fbc20ea6ce5083d01cb949f3782d6992c7d2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Como controlar a disponibilidade de uma variável (Visual Basic)
Controlar a disponibilidade de uma variável especificando seu *nível de acesso*. O nível de acesso determina qual código tem permissão para ler ou gravar na variável.  
  
-   *Variáveis de membro* (definida no nível de módulo e fora de qualquer procedimento) padrão para acesso público, o que significa que qualquer código que pode vê-los pode acessá-los. Você pode alterar isso, especificando um modificador de acesso.  
  
-   *Variáveis locais* (definido dentro de um procedimento) nominais têm acesso público, embora somente o código dentro de seu procedimento possa acessá-los. Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.  
  
 Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Acesso privado e público  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Para fazer uma variável acessível somente dentro do seu módulo, classe ou estrutura  
  
1.  Local de [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dele.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Para tornar acessível de qualquer código que possa vê-la uma variável  
  
1.  Para uma variável de membro, coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável de qualquer código que interopera com o assembly.  
  
 -ou-  
  
1.  Para uma variável local, coloque o `Dim` instrução para a variável dentro de um procedimento.  
  
2.  Não inclua o `Public` palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do procedimento, mas não de fora dele.  
  
## <a name="protected-and-friend-access"></a>Protegidos e o acesso de amigo  
 Você pode limitar o nível de acesso de uma variável para sua classe e quaisquer classes derivadas, ou seu assembly. Você também pode especificar a união dessas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly. Especificar essa união combinando o `Protected` e `Friend` palavras-chave na mesma declaração.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Para fazer uma variável acessível somente dentro de sua classe e quaisquer classes derivadas  
  
1.  Local de `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.  
  
2.  Incluir o [protegido](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro da classe, bem como do qualquer classe derivada dela, mas não de fora de qualquer classe na cadeia de derivação.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Para fazer uma variável acessível somente dentro do mesmo assembly  
  
1.  Local de `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2.  Incluir o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave no `Dim` instrução.  
  
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
 A configuração mais restritiva do nível de acesso de uma variável, menores as chances de código mal-intencionado pode fazer inadequado usá-lo.  
  
## <a name="see-also"></a>Consulte também  
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Público](../../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Privado](../../../../visual-basic/language-reference/modifiers/private.md)
