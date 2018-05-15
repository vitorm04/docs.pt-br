---
title: O valor do tipo &#39;type1&#39; não pode ser convertido em &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a><span data-ttu-id="7c6d5-102">O valor do tipo &#39;type1&#39; não pode ser convertido em &#39;type2&#39;</span><span class="sxs-lookup"><span data-stu-id="7c6d5-102">Value of type &#39;type1&#39; cannot be converted to &#39;type2&#39;</span></span>
<span data-ttu-id="7c6d5-103">O valor do tipo 'type1' não pode ser convertido em 'type2'.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="7c6d5-104">Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="7c6d5-105">Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="7c6d5-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="7c6d5-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="7c6d5-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c6d5-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7c6d5-108">To correct this error</span></span>  
  
-   <span data-ttu-id="7c6d5-109">Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="7c6d5-110">Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert> classe para converter o valor como o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="7c6d5-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6d5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c6d5-111">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="7c6d5-112">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="7c6d5-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7c6d5-113">Literais XML</span><span class="sxs-lookup"><span data-stu-id="7c6d5-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="7c6d5-114">XML</span><span class="sxs-lookup"><span data-stu-id="7c6d5-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
