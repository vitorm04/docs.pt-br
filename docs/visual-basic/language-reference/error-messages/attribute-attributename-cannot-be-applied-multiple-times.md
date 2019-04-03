---
title: O atributo '<attributename>' não pode ser aplicado várias vezes
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: fe72e7a14723bcfa429ce80b15dbc22b256774aa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843585"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="9ef76-102">Atributo '\<attributename >' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="9ef76-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="9ef76-103">O atributo pode ser aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="9ef76-103">The attribute can only be applied once.</span></span> <span data-ttu-id="9ef76-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="9ef76-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="9ef76-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="9ef76-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9ef76-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9ef76-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9ef76-107">Verifique se que o atributo é aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="9ef76-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="9ef76-108">Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, assim como acontece com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9ef76-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ef76-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ef76-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="9ef76-110">Criando Atributos Personalizados</span><span class="sxs-lookup"><span data-stu-id="9ef76-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="9ef76-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="9ef76-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
