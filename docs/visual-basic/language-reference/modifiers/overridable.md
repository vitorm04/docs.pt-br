---
title: "Substituível (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Overridable
- vb.Overridable
dev_langs:
- VB
helpviewer_keywords:
- elements, concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements, virtual
- virtual elements
- procedures, overriding
- concrete elements
- procedures, redefining
- Overridable keyword
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: 17
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
ms.openlocfilehash: f4de9ed8ff6fb402eccb7ccbe0492f12694256a0
ms.lasthandoff: 03/13/2017

---
# <a name="overridable-visual-basic"></a>Substituível (Visual Basic)
Especifica se uma propriedade ou procedimento pode ser substituído por uma propriedade nomeada de forma idêntica ou procedimento derivado de uma classe base.  
  
## <a name="remarks"></a>Comentários  
 O `Overridable` modificador permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada. O [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.  Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade da classe base. Se a propriedade ou método substitui um método ou propriedade da classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.  
  
 Você pode sombrear ou substituir para redefinir um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Um elemento que pode ser substituído às vezes é conhecido como um *virtual* elemento. Se ele pode ser substituído, mas não precisa ser, ele também é chamado um *concreta* elemento.  
  
 Você pode usar `Overridable` somente na declaração de uma propriedade ou um procedimento.  
  
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
 [Noções básicas sobre herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
