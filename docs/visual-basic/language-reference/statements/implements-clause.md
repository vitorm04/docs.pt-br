---
title: Cláusula Implements (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 1e34245ac528e9e2463afbfd07dff91bf693830b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603399"
---
# <a name="implements-clause-visual-basic"></a>Cláusula Implements (Visual Basic)
Indica que um membro de classe ou estrutura está fornecendo a implementação de um membro definido em uma interface.  
  
## <a name="remarks"></a>Comentários  
O `Implements` palavra-chave não é igual a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Você usa o `Implements` instrução para especificar que uma classe ou estrutura implementa uma ou mais interfaces, e, em seguida, para cada membro que você usar o `Implements` palavra-chave para especificar qual interface e qual membro ele implementa.

Se uma classe ou estrutura implementa uma interface, ele deve incluir o `Implements` instrução imediatamente após o [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) ou [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md), e ela deve implementar todos os membros definidos pela interface.

## <a name="reimplementation"></a>Reimplementação  
Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado. Isso é diferente de substituir o membro de classe base nos seguintes aspectos:

- O membro de classe base não precisa ser [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.
- Você pode reimplementar o membro com um nome diferente.

O `Implements` palavra-chave pode ser usada nos seguintes contextos:
- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
