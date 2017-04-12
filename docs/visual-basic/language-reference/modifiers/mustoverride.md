---
title: MustOverride (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MustOverride
- MustOverride
dev_langs:
- VB
helpviewer_keywords:
- virtual elements, pure
- elements, pure virtual
- properties [Visual Basic], redefining
- procedures, overriding
- overriding, MustOverride keyword
- procedures, redefining
- pure virtual elements
- MustOverride keyword
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
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
ms.openlocfilehash: 96f7cf150604f6c248b7a8659437759bf0e8166c
ms.lasthandoff: 03/13/2017

---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Especifica que uma propriedade ou um procedimento não é implementado dessa classe e deve ser substituído em uma classe derivada antes de ser usada.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar `MustOverride` somente na declaração de uma propriedade ou um procedimento. A propriedade ou procedimento que especifica `MustOverride` deve ser um membro de uma classe, e a classe deve ser marcada como [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Regras  
  
-   **Declaração incompleta.** Quando você especifica `MustOverride`, você não fornecer quaisquer linhas adicionais de código para a propriedade ou procedimento, não até o `End Function`, `End Property`, ou `End Sub` instrução.  
  
-   **Modificadores combinados.** Não é possível especificar `MustOverride` junto com `NotOverridable`, `Overridable`, ou `Shared` na mesma declaração.  
  
-   **Sombreamento e sobreposição.** Tanto o sombreamento e sobreposição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens. Para obter mais informações, consulte [sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Termos alternativos.** Um elemento que não pode ser usado, exceto em uma substituição às vezes é chamado um *puro virtual* elemento.  
  
 O `MustOverride` modificador pode ser usado nesses contextos:  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Sombreamento no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
