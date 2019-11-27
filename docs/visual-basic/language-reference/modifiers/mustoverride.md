---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351491"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Especifica que uma propriedade ou procedimento não está implementado nesta classe e deve ser substituído em uma classe derivada antes que possa ser usado.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `MustOverride` apenas em uma instrução de declaração de propriedade ou de procedimento. A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe e a classe deve ser marcada como [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Regras  
  
- **Declaração incompleta.** Ao especificar `MustOverride`, você não fornece nenhuma linha adicional de código para a propriedade ou procedimento, nem mesmo a instrução `End Function`, `End Property`ou `End Sub`.  
  
- **Modificadores combinados.** Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`ou `Shared` na mesma declaração.  
  
- **Sombreamento e substituição.** Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Termos alternativos.** Um elemento que não pode ser usado, exceto em uma substituição, às vezes é chamado de elemento *virtual puro* .  
  
 O modificador de `MustOverride` pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
- [Sombreamento em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
