---
title: Sombras (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: c314db90a1a0f89613e20897387bdec8ec534837
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834134"
---
# <a name="shadows-visual-basic"></a>Sombras (Visual Basic)
Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico, ou conjunto de elementos sobrecarregados, em uma classe base.  
  
## <a name="remarks"></a>Comentários  
 O objetivo principal do sombreamento (também conhecido como *ocultar pelo nome*) é preservar a definição de seus membros de classe. A classe base pode passar por uma alteração que cria um elemento com o mesmo nome que um que já definido. Se isso acontecer, o `Shadows` modificador obriga referências através da sua classe a ser resolvido para o membro que você definiu, em vez de para o novo elemento de classe base.  
  
 Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="rules"></a>Regras  
  
-   **Contexto da declaração.** Você pode usar `Shadows` apenas no nível de classe. Isso significa que o contexto da declaração para um `Shadows` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, estrutura, módulo ou procedimento.  
  
     Você pode declarar apenas um elemento de sombreamento em uma instrução única declaração.  
  
-   **Modificadores combinados.** Não é possível especificar `Shadows` junto com `Overloads`, `Overrides`, ou `Static` na mesma declaração.  
  
-   **Tipos de elemento.** Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo. Se você sombrear uma propriedade ou procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno é preciso coincide com a propriedade da classe base ou o procedimento.  
  
-   **Acessando.** O elemento sombreado na classe base está normalmente disponível de dentro da classe derivada que sombreia. No entanto, as seguintes considerações se aplicam.  
  
    -   Se o elemento de sombreamento não está acessível a partir do código que faz referência a ele, a referência será resolvida para o elemento sombreado. Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar o `Private` elemento acessa o elemento de classe base em vez disso.  
  
    -   Se você sombrear um elemento, você ainda pode acessar o elemento sombreado por meio de um objeto declarado com o tipo da classe base. Você também pode acessá-lo por meio de `MyBase`.  
  
 O `Shadows` modificador pode ser usado nestes contextos:  
  
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

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Estático](../../../visual-basic/language-reference/modifiers/static.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
