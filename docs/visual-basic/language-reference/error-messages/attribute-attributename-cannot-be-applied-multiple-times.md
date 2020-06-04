---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409953"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="d3f63-102">O atributo '\<attributename>' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="d3f63-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="d3f63-103">O atributo só pode ser aplicado uma vez.</span><span class="sxs-lookup"><span data-stu-id="d3f63-103">The attribute can only be applied once.</span></span> <span data-ttu-id="d3f63-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="d3f63-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="d3f63-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="d3f63-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d3f63-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d3f63-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d3f63-107">Verifique se o atributo é aplicado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d3f63-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="d3f63-108">Se você estiver usando atributos personalizados que desenvolveu, considere alterar seu `AttributeUsage` atributo para permitir o uso de vários atributos, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3f63-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3f63-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3f63-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="d3f63-110">Criando atributos personalizados</span><span class="sxs-lookup"><span data-stu-id="d3f63-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="d3f63-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="d3f63-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
