---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 4a0f3eb2b1603899e9acc1273c023ec5d0ed3132
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913330"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="cbeb2-102">Valor do tipo 'type1' não pode ser convertido em 'type2'</span><span class="sxs-lookup"><span data-stu-id="cbeb2-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="cbeb2-103">Valor do tipo 'type1' não pode ser convertido em 'type2'.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="cbeb2-104">Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de '\<parentElement >'.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="cbeb2-105">Tentativa de converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="cbeb2-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="cbeb2-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="cbeb2-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbeb2-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cbeb2-108">To correct this error</span></span>  
  
- <span data-ttu-id="cbeb2-109">Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="cbeb2-110">Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert> classe para converter o valor como o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbeb2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbeb2-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="cbeb2-112">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="cbeb2-112">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="cbeb2-113">Literais XML</span><span class="sxs-lookup"><span data-stu-id="cbeb2-113">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="cbeb2-114">XML</span><span class="sxs-lookup"><span data-stu-id="cbeb2-114">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
