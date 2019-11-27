---
title: Público
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351288"
---
# <a name="public-visual-basic"></a>Público (Visual Basic)
Especifica que um ou mais elementos de programação declarados não têm restrições de acesso.  
  
## <a name="remarks"></a>Comentários  
 Se você estiver publicando um componente ou conjunto de componentes, como uma biblioteca de classes, geralmente você desejará que os elementos de programação sejam acessíveis por qualquer código que interopere com seu assembly. Para confere tal acesso ilimitado em um elemento, você pode declará-lo com `Public`.  
  
 Acesso público é o nível normal de um elemento de programação quando você não precisa limitar o acesso a ele. Observe que o nível de acesso de um elemento declarado em uma interface, módulo, classe ou estrutura usa como padrão a `Public` se você não declará-lo caso contrário.  
  
## <a name="rules"></a>Regras  
  
- **Contexto de declaração.** Você pode usar `Public` somente no nível do módulo, da interface ou do namespace. Isso significa que o contexto de declaração para um elemento de `Public` deve ser um arquivo de origem, namespace, interface, módulo, classe ou estrutura, e não pode ser um procedimento.  
  
## <a name="behavior"></a>Comportamento  
  
- **Nível de acesso.** Todo o código que pode acessar um módulo, uma classe ou uma estrutura pode acessar seus elementos de `Public`.  
  
- **Acesso padrão.** Variáveis locais dentro de um procedimento assumem o acesso público como padrão, e você não pode usar nenhum modificador de acesso neles.  
  
- **Modificadores de acesso.** As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*. Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O modificador de `Public` pode ser usado nesses contextos:  
  
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

- [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Particular Protegido](private-protected.md)
- [Amigo Protegido](protected-friend.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
