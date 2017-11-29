---
title: "Público (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a>Público (Visual Basic)
Especifica que um ou mais elementos de programação declarados não têm acesso restrições.  
  
## <a name="remarks"></a>Comentários  
 Se você estiver publicando um componente ou um conjunto de componentes, como uma biblioteca de classes, normalmente você deseja que os elementos de programação para ser acessado por qualquer código que interage com seu assembly. Para concede tal acesso ilimitado em um elemento, você pode declará-la com `Public`.  
  
 Acesso público é o nível normal para um elemento de programação quando não é necessário limitar o acesso a ele. Observe que o nível de acesso de um elemento declarado dentro de uma interface, módulo, classe ou estrutura padrão é `Public` se você não declarar o contrário.  
  
## <a name="rules"></a>Regras  
  
-   **Contexto de declaração.** Você pode usar `Public` apenas no nível de namespace ou módulo. Isso significa que o contexto da declaração para um `Public` elemento deve ser um arquivo de origem, namespace, interface, módulo, classe ou estrutura e não pode ser um procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Nível de acesso.** Todo código que pode acessar um módulo, classe ou estrutura pode acessar seus `Public` elementos.  
  
-   **Acesso padrão.** Variáveis locais dentro de um padrão de procedimento para acesso público e você não podem usar quaisquer modificadores de acesso neles.  
  
-   **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*. Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Public` modificador pode ser usado nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
