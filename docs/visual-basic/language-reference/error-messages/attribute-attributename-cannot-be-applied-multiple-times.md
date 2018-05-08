---
title: Atributo &#39; &lt;attributename&gt; &#39; não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atributo &#39; &lt;attributename&gt; &#39; não pode ser aplicado várias vezes
O atributo só pode ser aplicado uma vez. O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.  
  
 **ID do erro:** BC30663  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se que o atributo é aplicado somente uma vez.  
  
2.  Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, como ocorre com o exemplo a seguir.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.AttributeUsageAttribute>  
 [Criando Atributos Personalizados](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
