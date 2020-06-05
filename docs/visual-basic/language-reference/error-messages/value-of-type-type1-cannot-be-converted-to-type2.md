---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: f19f157bd4c76f481aa3232bc33c2a0c6ac21367
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400273"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="38368-102">Valor do tipo 'type1' não pode ser convertido em 'type2'</span><span class="sxs-lookup"><span data-stu-id="38368-102">Value of type 'type1' cannot be converted to 'type2'</span></span>
<span data-ttu-id="38368-103">O valor do tipo ' type1 ' não pode ser convertido em ' type2 '.</span><span class="sxs-lookup"><span data-stu-id="38368-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="38368-104">Você pode usar a propriedade ' value ' para obter o valor da cadeia de caracteres do primeiro elemento de ' \<parentElement> '.</span><span class="sxs-lookup"><span data-stu-id="38368-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="38368-105">Foi feita uma tentativa de converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="38368-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="38368-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="38368-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="38368-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="38368-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38368-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="38368-108">To correct this error</span></span>  
  
- <span data-ttu-id="38368-109">Use a `Value` Propriedade do literal XML para referenciar seu valor como um `String` .</span><span class="sxs-lookup"><span data-stu-id="38368-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="38368-110">Use a `CType` função, outra função de conversão de tipo ou a <xref:System.Convert> classe para converter o valor como o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="38368-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38368-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="38368-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="38368-112">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="38368-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="38368-113">Literais XML</span><span class="sxs-lookup"><span data-stu-id="38368-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="38368-114">XML</span><span class="sxs-lookup"><span data-stu-id="38368-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
