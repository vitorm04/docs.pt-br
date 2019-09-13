---
title: Protegido (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929464"
---
# <a name="protected-visual-basic"></a>Protegido (Visual Basic)
Um modificador de acesso de membro que especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de sua própria classe ou de uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito e você deseja limitar o acesso ao elemento. No entanto, se a classe for herdável e você esperar uma hierarquia de classes derivadas, talvez seja necessário que essas classes derivadas acessem os dados ou o código. Nesse caso, você deseja que o elemento seja acessível tanto da classe base quanto de todas as classes derivadas. Para limitar o acesso a um elemento dessa maneira, você pode declará-lo `Protected`com.  

> [!NOTE]
> O `Protected` modificador de acesso pode ser combinado com dois outros modificadores:
>
> - O modificador [Friend protegido](protected-friend.md) torna um membro de classe acessível de dentro dessa classe, de classes derivadas e do mesmo assembly no qual a classe é definida. 
> - O modificador [particular protegido](private-protected.md) torna um membro de classe acessível por tipos derivados, mas somente dentro de seu assembly de contenção.
  
## <a name="rules"></a>Regras  
  
- **Contexto de declaração.** Você pode usar `Protected` somente no nível de classe. Isso significa que o contexto de Declaração `Protected` para um elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.  

## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Todo o código em uma classe pode acessar seus elementos. O código em qualquer classe derivada de uma classe base pode acessar todos os `Protected` elementos da classe base. Isso é verdadeiro para todas as gerações de derivação. Isso significa que uma classe pode acessar `Protected` elementos da classe base da classe base e assim por diante.  
  
     O acesso protegido não é um superconjunto ou subconjunto de acesso Friend.  
  
- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*. Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Protected` modificador pode ser usado nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Público](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Particular Protegido](private-protected.md)
- [Amigo Protegido](protected-friend.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
