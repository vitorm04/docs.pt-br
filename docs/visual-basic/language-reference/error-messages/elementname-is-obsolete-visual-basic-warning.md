---
title: "&quot;&lt;elementname&gt;&quot; é obsoleto (aviso do Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: ccec3b2659502c84dd4db9c9c4d796362958030b
ms.lasthandoff: 03/13/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a>'&lt;elementname&gt;' é obsoleto (aviso do Visual Basic)
Uma instrução tenta acessar um elemento de programação que foi marcado com o <xref:System.ObsoleteAttribute>atributo e com a diretriz para tratá-lo como um aviso.</xref:System.ObsoleteAttribute>  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando-se <xref:System.ObsoleteAttribute>ao proprietário.</xref:System.ObsoleteAttribute> Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A>propriedade como `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A> Se você defini-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini-lo como `False`, ou deixá-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A>propriedade <xref:System.ObsoleteAttribute>é `False`.</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A> Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que a referência do código-fonte é o nome do elemento digitado corretamente.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

