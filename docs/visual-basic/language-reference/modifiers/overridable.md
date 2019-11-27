---
title: Substituível
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351397"
---
# <a name="overridable-visual-basic"></a>Substituível (Visual Basic)
Especifica que uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou um procedimento em uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 O modificador `Overridable` permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada. O modificador [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) impede que uma propriedade ou um método seja substituído em uma classe derivada.  Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o modificador `Overridable` ou `NotOverridable` não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base. Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable`; caso contrário, será `NotOverridable`.  
  
 Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Um elemento que pode ser substituído às vezes é chamado de elemento *virtual* . Se ele puder ser substituído, mas não precisar ser, às vezes ele também é chamado de elemento *concreto* .  
  
 Você pode usar `Overridable` apenas em uma instrução de declaração de propriedade ou de procedimento.  
  
## <a name="combined-modifiers"></a>Modificadores combinados  
 Você não pode especificar `Overridable` ou `NotOverridable` para um método de `Private`.  
  
 Não é possível especificar `Overridable` junto com `MustOverride`, `NotOverridable`ou `Shared` na mesma declaração.  
  
 Como um elemento de substituição é implicitamente substituível, não é possível combinar `Overridable` com `Overrides`.  
  
## <a name="usage"></a>Uso  
 O modificador de `Overridable` pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
