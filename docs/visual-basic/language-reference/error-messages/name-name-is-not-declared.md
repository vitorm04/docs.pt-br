---
title: "O nome &#39;&lt;name&gt;&#39; n&#227;o &#233; declarado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30451"
  - "vbc30451"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30451"
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O nome &#39;&lt;name&gt;&#39; n&#227;o &#233; declarado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração refere\-se a um elemento de programação, mas o compilador não pode encontrar um elemento com este exato nome.  
  
 **Identificação do erro:**  BC30451  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia do nome na instrução faz referência.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]maiúsculas e minúsculas, mas qualquer outra variação na ortografia é considerada como um nome totalmente diferente.  Observe que a barra baixa \(`_`\) é parte do nome e é, por isso, parte da grafia.  
  
2.  Verifique se você possui o operador de acesso de membro \(`.`\) entre um objeto e seu membro.  Por exemplo, se você possui um controle <xref:System.Windows.Forms.TextBox> denominado `TextBox1`, para acessar sua propriedade <xref:System.Windows.Forms.TextBoxBase.Text%2A> você deve digitar `TextBox1.Text`.  Se ao invés disso você digitar `TextBox1Text`, você criou um nome diferente.  
  
3.  Se a grafia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se o elemento foi declarado.  Para obter mais informações, consulte [Elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Se o elemento de programação foideclarado, cheque se ele está no escopo.  Se o elemento de referência está fora da região que declara o elemento de programação, você pode precisar habilitar o nome do elemento.  Para obter mais informações, consulte [Escopo no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## Consulte também  
 [Resumo de declarações e constantes](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)