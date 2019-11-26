---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968235"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>O atributo '\<AttributeName > ' não pode ser aplicado várias vezes

O atributo só pode ser aplicado uma vez. O atributo `AttributeUsage` determina se um atributo pode ser aplicado mais de uma vez.  
  
 **ID do erro:** BC30663  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se o atributo é aplicado apenas uma vez.  
  
2. Se você estiver usando atributos personalizados que desenvolveu, considere alterar o atributo `AttributeUsage` para permitir o uso de vários atributos, como no exemplo a seguir.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AttributeUsageAttribute>
- [Criando Atributos Personalizados](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
