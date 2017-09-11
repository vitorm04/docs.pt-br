---
title: "Atributo &quot;&lt;attributename&gt;&quot; não pode ser aplicado várias vezes | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
dev_langs:
- VB
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 10e6bf6d8412a9f73138d5fce7b0e4735c5b6ddf
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="19418-102">Atributo '&lt;attributename&gt;' não pode ser aplicado várias vezes</span><span class="sxs-lookup"><span data-stu-id="19418-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="19418-103">O atributo só pode ser aplicado uma vez.</span><span class="sxs-lookup"><span data-stu-id="19418-103">The attribute can only be applied once.</span></span> <span data-ttu-id="19418-104">O `AttributeUsage` atributo determina se um atributo pode ser aplicado mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="19418-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="19418-105">**ID do erro:** BC30663</span><span class="sxs-lookup"><span data-stu-id="19418-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19418-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="19418-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="19418-107">Verifique se que o atributo é aplicado somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="19418-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="19418-108">Se você estiver usando atributos personalizados que você desenvolveu, considere alterar seus `AttributeUsage` atributo para permitir que vários usos de atributo, como ocorre com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="19418-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19418-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="19418-109">See Also</span></span>  
 <span data-ttu-id="19418-110"><xref:System.AttributeUsageAttribute></xref:System.AttributeUsageAttribute></span><span class="sxs-lookup"><span data-stu-id="19418-110"><xref:System.AttributeUsageAttribute></span></span>   
<span data-ttu-id="19418-111"> [Criando atributos personalizados](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="19418-111"> [Creating Custom Attributes](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="19418-112"> [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span><span class="sxs-lookup"><span data-stu-id="19418-112"> [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span></span>
