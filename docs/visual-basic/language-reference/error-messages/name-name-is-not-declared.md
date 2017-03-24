---
title: "Nome &quot;&lt;nome&gt;&quot; não está declarado como | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 81b6862a7f8ceb7998b2ea53336ed3af46b1db5f
ms.lasthandoff: 03/13/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nome '&lt;nome&gt;' não está declarado
Uma instrução refere-se a um elemento de programação, mas o compilador não pode localizar um elemento com esse nome exato.  
  
 **ID do erro:** BC30451  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a ortografia do nome na declaração de referência. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]diferencia maiusculas de minúsculas, mas qualquer outra variação de grafia é considerada como um nome completamente diferente. Observe que o caractere de sublinhado (`_`) é parte do nome e, portanto, parte da grafia.  
  
2.  Verifique se você tem o operador de acesso de membro (`.`) entre um objeto e seu membro. Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox>controle chamado `TextBox1`, para acessar seu <xref:System.Windows.Forms.TextBoxBase.Text%2A>propriedade, você deve digitar `TextBox1.Text`.</xref:System.Windows.Forms.TextBoxBase.Text%2A> </xref:System.Windows.Forms.TextBox> Se em vez disso você digitar `TextBox1Text`, você criou um nome diferente.  
  
3.  Se a ortografia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se que o elemento foi declarado. Para obter mais informações, consulte [elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Se o elemento de programação tiver sido declarado, verifique se ele está no escopo. Se a referência está fora da região que declara o elemento de programação, talvez seja necessário qualificar o nome do elemento. Para obter mais informações, consulte [escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Consulte também  
 [Resumo de declarações e constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
