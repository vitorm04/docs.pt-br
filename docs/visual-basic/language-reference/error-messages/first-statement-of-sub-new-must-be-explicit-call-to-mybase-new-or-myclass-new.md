---
title: 'A primeira instrução isso &#39; Sub novo &#39; deve ser uma chamada explícita para &#39; MyBase. New &#39; ou &#39; MyClass. New &#39; porque o &#39; &lt;constructorname&gt;&#39; na classe base &#39;&lt; baseclassname&gt;&#39; do &#39;&lt; derivedclassname&gt;&#39; está marcado como obsoleto: &#39;&lt; ErrorMessage&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8882acd947251d85804fbefd54267ce078e31b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>A primeira instrução isso &#39; Sub novo &#39; deve ser uma chamada explícita para &#39; MyBase. New &#39; ou &#39; MyClass. New &#39; porque o &#39; &lt;constructorname&gt;&#39; na classe base &#39;&lt; baseclassname&gt;&#39; do &#39;&lt; derivedclassname&gt;&#39; está marcado como obsoleto: &#39;&lt; ErrorMessage&gt;&#39;
Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute> atributo e a diretiva para tratá-lo como um erro.  
  
 Quando um construtor de classe derivada não chama um construtor de classe base [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tenta gerar uma chamada implícita para um construtor sem parâmetros de classe base. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é possível gerar uma chamada implícita. Nesse caso, o construtor necessário está marcado com o <xref:System.ObsoleteAttribute> de atributo, isso [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] não é possível chamá-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini-lo `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30920  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução de `Sub New` na classe derivada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
