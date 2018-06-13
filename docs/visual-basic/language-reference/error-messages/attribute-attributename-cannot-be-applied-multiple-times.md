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
ms.locfileid: "33584853"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="46939-102">Atributo &#39; &lt;attributename&gt; &#39; não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="46939-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="46939-103">O atributo só pode ser aplicado uma vez.</span><span class="sxs-lookup"><span data-stu-id="46939-103">The attribute can only be applied once.</span></span> <span data-ttu-id="46939-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="46939-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="46939-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="46939-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46939-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="46939-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="46939-107">Verifique se que o atributo é aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="46939-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="46939-108">Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, como ocorre com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="46939-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46939-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46939-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="46939-110">Criando Atributos Personalizados</span><span class="sxs-lookup"><span data-stu-id="46939-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="46939-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="46939-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
