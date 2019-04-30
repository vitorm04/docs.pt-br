---
title: 'Como: Controlar a disponibilidade de uma variável (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: fb400b113e3f3305f5b724734b2bf9aa9425d03f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943345"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Como: Controlar a disponibilidade de uma variável (Visual Basic)
Controlar a disponibilidade de uma variável especificando seu *nível de acesso*. O nível de acesso determina qual código tem permissão para ler ou gravar na variável.  
  
- *Variáveis de membro* (definida no nível de módulo e fora de qualquer procedimento) padrão de acesso público, o que significa que qualquer código que pode vê-los pode acessá-los. Você pode alterar isso especificando um modificador de acesso.  
  
- *Variáveis locais* (definido dentro de um procedimento) nominalmente têm acesso público, embora somente o código dentro de seu procedimento pode acessá-los. Você não pode alterar o nível de acesso de uma variável local, mas você pode alterar o nível de acesso do procedimento que o contém.  
  
 Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Acesso privado e público  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Para fazer uma variável acessível somente dentro de seu módulo, classe ou estrutura  
  
1. Coloque o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2. Incluir o [privados](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, mas não de fora dela.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Para tornar acessível de qualquer código que pode vê-lo uma variável  
  
1. Para uma variável de membro, coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2. Incluir o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável de qualquer código que interopera com o assembly.  
  
 - ou -  
  
1. Para obter uma variável local, coloque o `Dim` instrução para a variável dentro de um procedimento.  
  
2. Não inclua o `Public` palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do procedimento, mas não de fora dela.  
  
## <a name="protected-and-friend-access"></a>Protegido e o acesso de amigo  
 Você pode limitar o nível de acesso de uma variável para sua classe e quaisquer classes derivadas, ou para seu assembly. Você também pode especificar a união dessas limitações, que permite o acesso do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly. Especifique esta união combinando as `Protected` e `Friend` palavras-chave na mesma declaração.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Para fazer uma variável acessível somente dentro de sua classe e quaisquer classes derivadas  
  
1. Coloque o `Dim` instrução para a variável dentro de uma classe, mas fora de qualquer procedimento.  
  
2. Incluir o [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar para a variável em qualquer lugar dentro da classe, bem como de dentro de qualquer classe derivada dele, mas não de fora de qualquer classe na cadeia de derivação.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Para fazer uma variável acessíveis somente de dentro do mesmo assembly  
  
1. Coloque o `Dim` instrução para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2. Incluir o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) palavra-chave no `Dim` instrução.  
  
     Você pode ler ou gravar a variável em qualquer lugar dentro do módulo, classe ou estrutura, bem como de qualquer código no mesmo assembly, mas não de fora do assembly.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra as declarações de variáveis com `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private` níveis de acesso. Observe que, quando o `Dim` declaração especifica um nível de acesso, você não precisa incluir o `Dim` palavra-chave.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A configuração mais restritiva do nível de acesso de uma variável, menores as chances de que um código mal-intencionado pode fazer inadequado usá-lo.  
  
## <a name="see-also"></a>Consulte também

- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Público](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../../visual-basic/language-reference/modifiers/private.md)
