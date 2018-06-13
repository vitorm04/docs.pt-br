---
title: Substituível (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 4844bf7f3ecf23335715b950a96be15e54ebc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603763"
---
# <a name="overridable-visual-basic"></a>Substituível (Visual Basic)
Especifica que uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou procedimento em uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 O `Overridable` modificador permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada. O [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.  Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base. Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.  
  
 Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Um elemento que pode ser substituído às vezes é conhecido como um *virtual* elemento. Se ele pode ser substituído, mas não precisa ser, ele também é chamado um *concreta* elemento.  
  
 Você pode usar `Overridable` somente na declaração de uma propriedade ou procedimento.  
  
## <a name="combined-modifiers"></a>Modificadores combinados  
 Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.  
  
 Não é possível especificar `Overridable` junto com `MustOverride`, `NotOverridable`, ou `Shared` na mesma declaração.  
  
 Como um elemento de substituição é implicitamente substituível, você não pode combinar `Overridable` com `Overrides`.  
  
## <a name="usage"></a>Uso  
 O `Overridable` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
