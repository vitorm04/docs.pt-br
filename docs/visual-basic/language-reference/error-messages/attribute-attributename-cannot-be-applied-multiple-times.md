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
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="28d07-102">BC30663: o atributo ' \<attributename> ' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="28d07-102">BC30663: Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="28d07-103">O atributo só pode ser aplicado uma vez.</span><span class="sxs-lookup"><span data-stu-id="28d07-103">The attribute can only be applied once.</span></span> <span data-ttu-id="28d07-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="28d07-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>

 <span data-ttu-id="28d07-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="28d07-105">**Error ID:** BC30663</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="28d07-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="28d07-106">To correct this error</span></span>

1. <span data-ttu-id="28d07-107">Verifique se o atributo é aplicado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="28d07-107">Make sure the attribute is only applied once.</span></span>

2. <span data-ttu-id="28d07-108">Se você estiver usando atributos personalizados que desenvolveu, considere alterar seu `AttributeUsage` atributo para permitir o uso de vários atributos, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="28d07-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a><span data-ttu-id="28d07-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="28d07-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="28d07-110">Criando atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="28d07-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="28d07-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="28d07-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
