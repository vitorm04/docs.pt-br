---
title: Nome &#39; &lt;nome&gt; &#39; não é declarada
ms.date: 07/20/2015
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: e17017e84720a2581abc5115338352aacc02d473
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Nome &#39; &lt;nome&gt; &#39; não é declarada
Uma instrução faz referência a um elemento de programação, mas o compilador não pode localizar um elemento com esse nome exato.  
  
 **ID do erro:** BC30451  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a ortografia do nome na declaração de referência. Visual Basic diferencia maiusculas de minúsculas, mas qualquer outra variação de grafia é considerada como um nome completamente diferente. Observe que o caractere de sublinhado (`_`) é parte do nome e, portanto, parte da ortografia.  
  
2.  Verifique se você tem o operador de acesso de membro (`.`) entre um objeto e seus membros. Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle chamado `TextBox1`, para acessar seu <xref:System.Windows.Forms.TextBoxBase.Text%2A> propriedade, você deve digitar `TextBox1.Text`. Se, em vez disso, você digita `TextBox1Text`, você criou um nome diferente.  
  
3.  Se a ortografia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se que o elemento foi declarado. Para obter mais informações, consulte [elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Se o elemento de programação tiver sido declarado, verifique se ele está no escopo. Se a referência está fora da região que declara o elemento de programação, talvez seja necessário qualificar o nome do elemento. Para obter mais informações, consulte [escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Consulte também  
 [Resumo de Declarações e Constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Nomes de Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
