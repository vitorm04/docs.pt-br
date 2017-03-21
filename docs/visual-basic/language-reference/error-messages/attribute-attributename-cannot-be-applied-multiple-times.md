---
title: "Atributo &quot;&lt;attributename&gt;&quot; não pode ser aplicado várias vezes | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
dev_langs:
- VB
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
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
ms.openlocfilehash: 42d854393af2eecd0a624c7937a00b6912c898ac
ms.lasthandoff: 03/13/2017

---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atributo '&lt;attributename&gt;' não pode ser aplicado várias vezes
O atributo só pode ser aplicado uma vez. O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.  
  
 **ID do erro:** BC30663  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que o atributo é aplicado somente uma vez.  
  
2.  Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, como ocorre com o exemplo a seguir.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AttributeUsageAttribute></xref:System.AttributeUsageAttribute>   
 [Criando atributos personalizados](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
