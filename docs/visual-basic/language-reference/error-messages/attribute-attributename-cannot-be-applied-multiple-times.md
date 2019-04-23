---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: da4a766e2617308cb33b9673a88db9e7a954152a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304292"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="e3d29-102">Atributo '\<attributename >' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="e3d29-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="e3d29-103">O atributo pode ser aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="e3d29-103">The attribute can only be applied once.</span></span> <span data-ttu-id="e3d29-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="e3d29-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="e3d29-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="e3d29-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3d29-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e3d29-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e3d29-107">Verifique se que o atributo é aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="e3d29-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="e3d29-108">Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, assim como acontece com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3d29-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3d29-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3d29-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="e3d29-110">Criando Atributos Personalizados</span><span class="sxs-lookup"><span data-stu-id="e3d29-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="e3d29-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="e3d29-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
