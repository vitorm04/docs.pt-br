---
title: Private (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
dev_langs:
- VB
helpviewer_keywords:
- Private keyword
- Private keyword, syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: b962956ad8fced61aad949e2c8c1c92add34cd03
ms.lasthandoff: 03/13/2017

---
# <a name="private-visual-basic"></a>Particular (Visual Basic)
Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seus contextos de declaração, inclusive em todos os tipos contidos.  
  
## <a name="remarks"></a>Comentários  
 Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele estritamente possível. Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que o define para acessá-lo. Para limitar o acesso a um elemento dessa maneira, você pode declará-lo com `Private`.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Private` somente no nível de módulo. Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo fonte, namespace, interface ou procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todo código em um contexto de declaração pode acessar seus `Private` elementos. Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração. Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.  
  
-   **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para uma comparação entre os modificadores de acesso, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Private` modificador pode ser usado nesses contextos:  
  
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
 [Público](../../../visual-basic/language-reference/modifiers/public.md)   
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
