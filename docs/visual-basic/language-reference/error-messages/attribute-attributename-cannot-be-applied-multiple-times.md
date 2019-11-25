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
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="03262-102">O atributo '\<AttributeName > ' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="03262-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="03262-103">O atributo só pode ser aplicado uma vez.</span><span class="sxs-lookup"><span data-stu-id="03262-103">The attribute can only be applied once.</span></span> <span data-ttu-id="03262-104">O atributo `AttributeUsage` determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="03262-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="03262-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="03262-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03262-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="03262-106">To correct this error</span></span>  
  
1. <span data-ttu-id="03262-107">Verifique se o atributo é aplicado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="03262-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="03262-108">Se você estiver usando atributos personalizados que desenvolveu, considere alterar o atributo `AttributeUsage` para permitir o uso de vários atributos, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="03262-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03262-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03262-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="03262-110">Criando Atributos Personalizados</span><span class="sxs-lookup"><span data-stu-id="03262-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="03262-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="03262-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
