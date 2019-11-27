---
title: Cláusula Implements
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
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345869"
---
# <a name="implements-clause-visual-basic"></a>Cláusula Implements (Visual Basic)
Indica que um membro de classe ou estrutura está fornecendo a implementação para um membro definido em uma interface.  
  
## <a name="remarks"></a>Comentários  
A palavra-chave `Implements` não é a mesma que a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Use a instrução `Implements` para especificar que uma classe ou estrutura implementa uma ou mais interfaces e, em seguida, para cada membro, use a palavra-chave `Implements` para especificar qual interface e qual membro ele implementa.

Se uma classe ou estrutura implementa uma interface, ela deve incluir a instrução `Implements` imediatamente após a instrução de [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou a [instrução de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md), e deve implementar todos os membros definidos pela interface.

## <a name="reimplementation"></a>Reimplementação  
Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado. Isso é diferente de substituir o membro da classe base nos seguintes aspectos:

- O membro da classe base não precisa ser [substituível](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.
- Você pode reimplementar o membro com um nome diferente.

A palavra-chave `Implements` pode ser usada nos seguintes contextos:

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
