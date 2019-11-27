---
title: Como controlar a disponibilidade de uma variável
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
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345387"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Como controlar a disponibilidade de uma variável (Visual Basic)
Você controla a disponibilidade de uma variável especificando seu *nível de acesso*. O nível de acesso determina qual código tem permissão para ler ou gravar na variável.  
  
- As *variáveis de membro* (definidas em nível de módulo e fora de qualquer procedimento) assumem o padrão de acesso público, o que significa que qualquer código que possa vê-las pode acessá-las. Você pode alterar isso especificando um modificador de acesso.  
  
- As *variáveis locais* (definidas dentro de um procedimento) nominalmente têm acesso público, embora apenas o código dentro de seu procedimento possa acessá-las. Você não pode alterar o nível de acesso de uma variável local, mas pode alterar o nível de acesso do procedimento que a contém.  
  
 Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Acesso público e privado  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Para tornar uma variável acessível somente de dentro de seu módulo, classe ou estrutura  
  
1. Coloque a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para a variável dentro do módulo, da classe ou da estrutura, mas fora de qualquer procedimento.  
  
2. Inclua a palavra-chave [Private](../../../../visual-basic/language-reference/modifiers/private.md) na instrução `Dim`.  
  
     Você pode ler ou gravar na variável de qualquer lugar dentro do módulo, da classe ou da estrutura, mas não de fora dela.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Para tornar uma variável acessível de qualquer código que possa vê-la  
  
1. Para uma variável de membro, coloque a instrução `Dim` para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2. Inclua a palavra-chave [Public](../../../../visual-basic/language-reference/modifiers/public.md) na instrução `Dim`.  
  
     Você pode ler ou gravar na variável de qualquer código que interopere com seu assembly.  
  
 - ou -  
  
1. Para uma variável local, coloque a instrução `Dim` para a variável dentro de um procedimento.  
  
2. Não inclua a palavra-chave `Public` na instrução `Dim`.  
  
     Você pode ler ou gravar na variável de qualquer lugar dentro do procedimento, mas não de fora dela.  
  
## <a name="protected-and-friend-access"></a>Acesso protegido e amigo  
 Você pode limitar o nível de acesso de uma variável à sua classe e a todas as classes derivadas ou a seu assembly. Você também pode especificar a União dessas limitações, que permite o acesso a partir do código em qualquer classe derivada ou em qualquer outro lugar no mesmo assembly. Você especifica essa União combinando as palavras-chave `Protected` e `Friend` na mesma declaração.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Para tornar uma variável acessível somente de dentro de sua classe e de quaisquer classes derivadas  
  
1. Coloque a instrução `Dim` para a variável dentro de uma classe, mas fora de qualquer procedimento.  
  
2. Inclua a palavra-chave [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) na instrução `Dim`.  
  
     Você pode ler ou gravar na variável de qualquer lugar dentro da classe, bem como de dentro de qualquer classe derivada dela, mas não de fora de nenhuma classe na cadeia de derivação.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Para tornar uma variável acessível somente de dentro do mesmo assembly  
  
1. Coloque a instrução `Dim` para a variável dentro de um módulo, classe ou estrutura, mas fora de qualquer procedimento.  
  
2. Inclua a palavra-chave [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) na instrução `Dim`.  
  
     Você pode ler ou gravar na variável de qualquer lugar dentro do módulo, da classe ou da estrutura, bem como de qualquer código no mesmo assembly, mas não de fora do assembly.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra declarações de variáveis com os níveis de acesso `Public`, `Protected`, `Friend`, `Protected Friend`e `Private`. Observe que, quando a instrução de `Dim` especifica um nível de acesso, não é necessário incluir a palavra-chave `Dim`.  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Quanto mais restritiva for o nível de acesso de uma variável, menor será a probabilidade de que o código mal-intencionado possa usar o uso impróprio.  
  
## <a name="see-also"></a>Consulte também

- [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Público](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../../visual-basic/language-reference/modifiers/private.md)
