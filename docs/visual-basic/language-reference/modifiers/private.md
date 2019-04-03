---
title: Particular (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819470"
---
# <a name="private-visual-basic"></a>Particular (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, inclusive em todos os tipos contidos.  
  
## <a name="remarks"></a>Comentários  
 Se um elemento de programação representa a funcionalidade proprietária ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele tão restrito quanto possível. Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que define-o para acessá-lo. Para limitar o acesso a um elemento dessa forma, você pode declará-la com `Private`.  

> [!NOTE]
> Você também pode usar o [Private Protected](private-protected.md) modificador de acesso, o que torna um membro acessível de dentro dessa classe e de classes derivadas localizadas no seu assembly recipiente.

## <a name="rules"></a>Regras  

-   **Contexto da declaração.** Você pode usar `Private` apenas no nível de módulo. Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todo o código em um contexto de declaração pode acessar seus `Private` elementos. Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração. Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.  
  
-   **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Private` modificador pode ser usado nestes contextos:  
  
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
- [Protected Friend](./protected-friend.md)[acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
