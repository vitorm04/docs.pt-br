---
title: "Implementa a cláusula (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImplementsClause
dev_langs:
- VB
helpviewer_keywords:
- interface implementation, reimplementation
- interface members, reimplementation
- interface members, Implements keyword
- interface members
- members, reimplementation
- interface implementation, Implements keyword
- interface members, implementing
- Implements keyword
- Implements statement, about Implements
- members, implementing
- members, Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: 15
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
ms.openlocfilehash: 93d52759ecd4f46b9e7c403378d0531377f7986e
ms.lasthandoff: 03/13/2017

---
# <a name="implements-clause-visual-basic"></a>Cláusula Implements (Visual Basic)
Indica que um membro de classe ou estrutura está fornecendo a implementação para um membro definido em uma interface.  
  
## <a name="remarks"></a>Comentários  
 O `Implements` palavra-chave não é igual a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Você usa o `Implements` para especificar que uma classe ou estrutura implementa uma ou mais interfaces, e, em seguida, para cada membro que você usar o `Implements` palavra-chave para especificar qual interface e qual membro ele implementa.  
  
 Se uma classe ou estrutura implementa uma interface, ela deve incluir a `Implements` instrução imediatamente após o [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) ou [declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md), e ela deve implementar todos os membros definidos pela interface.  
  
## <a name="reimplementation"></a>Reimplementação  
 Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado. Isso é diferente de substituir o membro da classe base nos seguintes aspectos:  
  
-   O membro da classe base não precisa ser [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.  
  
-   Você pode reimplementar o membro com um nome diferente.  
  
 O `Implements` palavra-chave pode ser usada nesses contextos:  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
