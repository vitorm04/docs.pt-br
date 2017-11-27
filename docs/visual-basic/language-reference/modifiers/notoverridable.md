---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Especifica que uma propriedade ou procedimento não pode ser substituído em uma classe derivada.  
  
## <a name="remarks"></a>Comentários  
 O `NotOverridable` modificador impede que uma propriedade ou método que está sendo substituído em uma classe derivada.  O [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modificador permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada. Para obter mais informações, consulte [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Se o `Overridable` ou `NotOverridable` modificador não for especificado, a configuração padrão depende se a propriedade ou método substitui um método ou propriedade de classe base. Se a propriedade ou método substitui um método ou propriedade de classe base, a configuração padrão é `Overridable`; caso contrário, ele é `NotOverridable`.  
  
 Um elemento que não pode ser substituído às vezes é chamado um *lacrado* elemento.  
  
 Você pode usar `NotOverridable` somente na declaração de uma propriedade ou procedimento. Você pode especificar `NotOverridable` somente em uma propriedade ou procedimento que substitui outra propriedade ou procedimento, ou seja, somente em combinação com `Overrides`.  
  
## <a name="combined-modifiers"></a>Modificadores combinados  
 Não é possível especificar `Overridable` ou `NotOverridable` para um `Private` método.  
  
 Não é possível especificar `NotOverridable` junto com `MustOverride`, `Overridable`, ou `Shared` na mesma declaração.  
  
## <a name="usage"></a>Uso  
 O `NotOverridable` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Modificadores](../../../visual-basic/language-reference/modifiers/index.md)  
 [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)  
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
