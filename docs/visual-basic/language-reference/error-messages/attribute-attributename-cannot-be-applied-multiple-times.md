---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 62e84d174e4e218472eda9b7c08ed677e0140438
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278701"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="be67c-102">Atributo '\<attributename >' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="be67c-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="be67c-103">O atributo pode ser aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="be67c-103">The attribute can only be applied once.</span></span> <span data-ttu-id="be67c-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="be67c-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="be67c-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="be67c-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be67c-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be67c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="be67c-107">Verifique se que o atributo é aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="be67c-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="be67c-108">Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, assim como acontece com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="be67c-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be67c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be67c-109">See also</span></span>
- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="be67c-110">Criando Atributos Personalizados</span><span class="sxs-lookup"><span data-stu-id="be67c-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="be67c-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="be67c-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
