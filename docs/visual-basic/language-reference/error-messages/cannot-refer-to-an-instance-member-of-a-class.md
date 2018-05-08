---
title: Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe
Você tentou fazer referência a um membro não compartilhado de uma classe de dentro de um procedimento compartilhado. O exemplo a seguir demonstra essa situação.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 No exemplo anterior, a instrução de atribuição `x = 10` gera essa mensagem de erro. Isso ocorre porque um procedimento compartilhado está tentando acessar uma variável de instância.  
  
 A variável `x` é um membro de instância porque ele não está declarado como [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md). Cada instância da classe `sample` contém sua própria variável individual `x`. Quando uma instância define ou altera o valor de `x`, ele não afeta o valor de `x` em qualquer outra instância.  
  
 No entanto, o procedimento `setX` é `Shared` entre todas as instâncias da classe `sample`. Isso significa que ele não está associado a qualquer instância da classe, mas em vez disso, opera independentemente das instâncias individuais. Porque ele tem nenhuma conexão com uma determinada instância, `setX` não é possível acessar uma variável de instância. Ele deve operar somente em `Shared` variáveis. Quando `setX` define ou altera o valor de uma variável compartilhada, que o novo valor está disponível para todas as instâncias da classe.  
  
 **ID do erro:** BC30369  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Decida se deseja que o membro a ser compartilhado entre todas as instâncias da classe, ou mantido individual para cada instância.  
  
2.  Se desejar que uma única cópia do membro a ser compartilhado entre todas as instâncias, adicione a `Shared` palavra-chave para a declaração de membro. Manter o `Shared` palavra-chave na declaração do procedimento.  
  
3.  Se você quiser que cada instância tenha sua própria cópia individual do membro, não especifique `Shared` na declaração de membro. Remover o `Shared` palavra-chave da declaração de procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
