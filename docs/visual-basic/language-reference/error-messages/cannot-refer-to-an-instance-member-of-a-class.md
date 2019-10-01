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
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701170"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Não é possível fazer referência a um membro da instância de uma classe de dentro de um método compartilhado ou inicializador de membro compartilhado sem uma instância explícita da classe
Você tentou fazer referência a um membro não compartilhado de uma classe de dentro de um procedimento compartilhado. O exemplo a seguir demonstra tal situação.  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 No exemplo anterior, a instrução de atribuição `x = 10` gera essa mensagem de erro. Isso ocorre porque um procedimento compartilhado está tentando acessar uma variável de instância.  
  
 A variável `x` é um membro de instância porque não está declarada como [compartilhada](../../../visual-basic/language-reference/modifiers/shared.md). Cada instância da classe `sample` contém sua própria variável individual `x`. Quando uma instância define ou altera o valor de `x`, ela não afeta o valor de `x` em nenhuma outra instância.  
  
 No entanto, o procedimento `setX` é `Shared` entre todas as instâncias da classe `sample`. Isso significa que ele não está associado a uma instância da classe, mas opera independentemente de instâncias individuais. Como não tem conexão com uma instância específica, `setX` não pode acessar uma variável de instância. Ele deve operar somente em variáveis `Shared`. Quando `setX` define ou altera o valor de uma variável compartilhada, esse novo valor está disponível para todas as instâncias da classe.  
  
 **ID do erro:** BC30369  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Decida se deseja que o membro seja compartilhado entre todas as instâncias da classe ou mantido separadamente para cada instância.  
  
2. Se você quiser que uma única cópia do membro seja compartilhada entre todas as instâncias, adicione a palavra-chave `Shared` à declaração de membro. Mantenha a palavra-chave `Shared` na declaração de procedimento.  
  
3. Se você quiser que cada instância tenha sua própria cópia individual do membro, não especifique `Shared` para a declaração de membro. Remova a palavra-chave `Shared` da declaração de procedimento.  
  
## <a name="see-also"></a>Consulte também

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
