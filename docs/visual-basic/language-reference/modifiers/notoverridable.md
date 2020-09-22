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
ms.openlocfilehash: 8eec54a12c7fb748df46e8c48a8b07eab983cc72
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867868"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)

Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.  
  
## <a name="remarks"></a>Comentários  

 O `NotOverridable` modificador impede que uma propriedade ou um método seja substituído em uma classe derivada.  O modificador [Overridable](overridable.md) permite que uma propriedade ou método em uma classe seja substituído em uma classe derivada. Para obter mais informações, consulte [Noções básicas de herança](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o `Overridable` `NotOverridable` modificador ou não for especificado, a configuração padrão dependerá se a propriedade ou o método substituirá uma propriedade ou método de classe base. Se a propriedade ou o método substituir uma propriedade ou método de classe base, a configuração padrão será `Overridable` ; caso contrário, será `NotOverridable` .  
  
 Um elemento que não pode ser substituído às vezes é chamado de elemento *lacrado* .  
  
 Você pode usar `NotOverridable` somente em uma instrução de declaração de propriedade ou de procedimento. Você pode especificar `NotOverridable` apenas em uma propriedade ou um procedimento que substitua outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides` .  
  
## <a name="combined-modifiers"></a>Modificadores combinados  

 Você não pode especificar `Overridable` ou `NotOverridable` para um `Private` método.  
  
 Você não pode especificar `NotOverridable` juntos com `MustOverride` , `Overridable` ou `Shared` na mesma declaração.  
  
## <a name="usage"></a>Uso  

 O `NotOverridable` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../statements/function-statement.md)  
  
 [Instrução Property](../statements/property-statement.md)  
  
 [Instrução Sub](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Confira também

- [Modificadores](index.md)
- [Noções básicas de herança](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [Substituível](overridable.md)
- [Substituições](overrides.md)
- [Palavras-chave](../keywords/index.md)
- [Sombreamento no Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
