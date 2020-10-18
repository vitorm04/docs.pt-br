---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162655"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a>BC30663: o atributo ' \<attributename> ' não pode ser aplicado várias vezes

O atributo só pode ser aplicado uma vez. O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.

 **ID do erro:** BC30663

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Verifique se o atributo é aplicado apenas uma vez.

2. Se você estiver usando atributos personalizados que desenvolveu, considere alterar seu `AttributeUsage` atributo para permitir o uso de vários atributos, como no exemplo a seguir.

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a>Veja também

- <xref:System.AttributeUsageAttribute>
- [Criando atributos personalizados](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
