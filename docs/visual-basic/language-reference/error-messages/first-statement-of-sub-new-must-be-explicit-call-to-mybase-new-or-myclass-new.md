---
title: "A primeira instrução deste &quot;Sub New&quot; deve ser uma chamada explícita para &quot;MyBase. New&quot; ou &quot;MyClass. New&quot; porque o &quot;&lt;constructorname&gt;&quot;na classe base&quot;&lt;baseclassname&gt;&quot;de&quot;&lt;derivedclassname&gt;&quot; está marcado como obsoleto: &quot;&lt;errormessage&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30920
- bc30920
dev_langs:
- VB
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
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
ms.openlocfilehash: feb04d426b7e050b7ad05cdfd4d481172dda3a49
ms.lasthandoff: 03/13/2017

---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a>A primeira instrução deste 'Sub New' deve ser uma chamada explícita para 'MyBase. New' ou 'MyClass. New' porque o '&lt;constructorname&gt;'na classe base'&lt;baseclassname&gt;'de'&lt;derivedclassname&gt;' está marcado como obsoleto: '&lt;errormessage&gt;'
Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute>atributo e com a diretriz para tratá-lo como um erro.</xref:System.ObsoleteAttribute>  
  
 Quando um construtor de classe derivada não chama um construtor de classe base, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tenta gerar uma chamada implícita para um construtor de classe base sem parâmetros. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível gerar uma chamada implícita. Nesse caso, o construtor exigido é marcado com o <xref:System.ObsoleteAttribute>atributo, isso [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível chamar proprietário.</xref:System.ObsoleteAttribute>  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando-se <xref:System.ObsoleteAttribute>ao proprietário.</xref:System.ObsoleteAttribute> Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A>propriedade como `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A> Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo como `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30920  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução do `Sub New` na classe derivada.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
