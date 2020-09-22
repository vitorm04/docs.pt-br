---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8c80429db618e1bcadce1a58a6514d625f0b3cf1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870228"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="bca6a-102">Valor do tipo 'type1' não pode ser convertido em 'type2'</span><span class="sxs-lookup"><span data-stu-id="bca6a-102">Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="bca6a-103">O valor do tipo ' type1 ' não pode ser convertido em ' type2 '.</span><span class="sxs-lookup"><span data-stu-id="bca6a-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="bca6a-104">Você pode usar a propriedade ' value ' para obter o valor da cadeia de caracteres do primeiro elemento de ' \<parentElement> '.</span><span class="sxs-lookup"><span data-stu-id="bca6a-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>  
  
 <span data-ttu-id="bca6a-105">Foi feita uma tentativa de converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="bca6a-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="bca6a-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="bca6a-106">The XML literal cannot be implicitly cast to the specified type.</span></span>  
  
 <span data-ttu-id="bca6a-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="bca6a-107">**Error ID:** BC31194</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bca6a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bca6a-108">To correct this error</span></span>  
  
- <span data-ttu-id="bca6a-109">Use a `Value` Propriedade do literal XML para referenciar seu valor como um `String` .</span><span class="sxs-lookup"><span data-stu-id="bca6a-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="bca6a-110">Use a `CType` função, outra função de conversão de tipo ou a <xref:System.Convert> classe para converter o valor como o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="bca6a-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca6a-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="bca6a-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="bca6a-112">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="bca6a-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="bca6a-113">Literais XML</span><span class="sxs-lookup"><span data-stu-id="bca6a-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="bca6a-114">XML</span><span class="sxs-lookup"><span data-stu-id="bca6a-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
