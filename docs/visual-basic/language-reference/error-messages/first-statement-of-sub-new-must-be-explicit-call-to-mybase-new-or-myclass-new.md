---
title: 'A primeira instrução &#39;Sub New&#39; deve ser uma chamada explícita para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; porque o &#39; &lt;constructorname&gt; &#39; na classe base &#39; &lt;baseclassname&gt; &#39; de &#39; &lt;derivedclassname&gt; &#39; está marcado como obsoleto: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: dbce2a9edcc38ff137cb7ec0c97e5c259c0a0979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589887"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>A primeira instrução &#39;Sub New&#39; deve ser uma chamada explícita para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; porque o &#39; &lt;constructorname&gt; &#39; na classe base &#39; &lt;baseclassname&gt; &#39; de &#39; &lt;derivedclassname&gt; &#39; está marcado como obsoleto: &#39; &lt;errormessage&gt;&#39;
Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.  
  
 Quando um construtor de classe derivada não chama um construtor de classe base, o Visual Basic tenta gerar uma chamada implícita para um construtor sem parâmetros de classe base. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, o Visual Basic não pode gerar uma chamada implícita. Nesse caso, o construtor necessário está marcado com o <xref:System.ObsoleteAttribute> de atributo, para o Visual Basic não é possível chamá-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini-lo `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30920  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução de `Sub New` na classe derivada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
