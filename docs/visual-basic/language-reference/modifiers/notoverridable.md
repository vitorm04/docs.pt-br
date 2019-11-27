---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351451"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 O modificador `NotOverridable` impede que uma propriedade ou um método seja substituído em uma classe derivada.  O modificador [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada. Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o modificador `Overridable` ou `NotOverridable` não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base. Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable`; caso contrário, será `NotOverridable`.  
  
 Um elemento que não pode ser substituído às vezes é chamado de elemento *lacrado* .  
  
 Você pode usar `NotOverridable` apenas em uma instrução de declaração de propriedade ou de procedimento. Você pode especificar `NotOverridable` apenas em uma propriedade ou procedimento que substitua outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides`.  
  
## <a name="combined-modifiers"></a>Modificadores combinados  
 Você não pode especificar `Overridable` ou `NotOverridable` para um método de `Private`.  
  
 Não é possível especificar `NotOverridable` junto com `MustOverride`, `Overridable`ou `Shared` na mesma declaração.  
  
## <a name="usage"></a>Uso  
 O modificador de `NotOverridable` pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)
- [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
