---
title: Particular
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351325"
---
# <a name="private-visual-basic"></a>Particular (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, incluindo de dentro de qualquer tipo contido.  
  
## <a name="remarks"></a>Comentários  
 Se um elemento de programação representar a funcionalidade proprietária ou contiver dados confidenciais, você geralmente desejará limitar o acesso a ele o mais estritamente possível. Você Obtém a limitação máxima permitindo apenas o módulo, a classe ou a estrutura que a define para acessá-lo. Para limitar o acesso a um elemento dessa forma, você pode declará-lo com `Private`.  

> [!NOTE]
> Você também pode usar o modificador de acesso [protegido privado](private-protected.md) , que torna um membro acessível de dentro dessa classe e de classes derivadas localizadas em seu assembly recipiente.

## <a name="rules"></a>Regras  

- **Contexto de declaração.** Você pode usar `Private` somente no nível do módulo. Isso significa que o contexto de declaração para um elemento de `Private` deve ser um módulo, uma classe ou uma estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Todo o código dentro de um contexto de declaração pode acessar seus elementos de `Private`. Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração. Nenhum código fora do contexto da declaração pode acessar seus elementos de `Private`.  
  
- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*. Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O modificador de `Private` pode ser usado nesses contextos:  
  
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
- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Particular Protegido](./private-protected.md)
- [Níveis de acesso [Friend protegidos](./protected-friend.md) no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
