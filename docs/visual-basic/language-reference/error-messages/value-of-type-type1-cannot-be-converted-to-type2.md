---
title: "Valor do tipo &quot;type1&quot; não pode ser convertido em &quot;type2&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
dev_langs:
- VB
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
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
ms.openlocfilehash: 683c7a457bdf8a95179867d058355dbec593a89e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="1b69d-102">Valor do tipo 'type1' não pode ser convertido em 'type2'</span><span class="sxs-lookup"><span data-stu-id="1b69d-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="1b69d-103">Valor do tipo 'type1' não pode ser convertido em 'type2'.</span><span class="sxs-lookup"><span data-stu-id="1b69d-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="1b69d-104">Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="1b69d-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="1b69d-105">Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="1b69d-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="1b69d-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="1b69d-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="1b69d-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="1b69d-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b69d-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1b69d-108">To correct this error</span></span>  
  
-   <span data-ttu-id="1b69d-109">Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`.</span><span class="sxs-lookup"><span data-stu-id="1b69d-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="1b69d-110">Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert>classe para converter o valor do tipo especificado.</xref:System.Convert></span><span class="sxs-lookup"><span data-stu-id="1b69d-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b69d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b69d-111">See Also</span></span>  
 <span data-ttu-id="1b69d-112"><xref:System.Convert></xref:System.Convert></span><span class="sxs-lookup"><span data-stu-id="1b69d-112"><xref:System.Convert></span></span>   
<span data-ttu-id="1b69d-113"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="1b69d-113"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="1b69d-114"> [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="1b69d-114"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="1b69d-115"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b69d-115"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
