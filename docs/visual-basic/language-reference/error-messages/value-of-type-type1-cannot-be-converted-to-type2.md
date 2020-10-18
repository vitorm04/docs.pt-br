---
title: Valor do tipo 'type1' não pode ser convertido em 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 107936aa969690d0cc9fd4a2605cfceea31eeca8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161407"
---
# <a name="bc31194-value-of-type-type1-cannot-be-converted-to-type2"></a><span data-ttu-id="65561-102">BC31194: o valor do tipo ' type1 ' não pode ser convertido em ' type2 '</span><span class="sxs-lookup"><span data-stu-id="65561-102">BC31194: Value of type 'type1' cannot be converted to 'type2'</span></span>

<span data-ttu-id="65561-103">O valor do tipo ' type1 ' não pode ser convertido em ' type2 '.</span><span class="sxs-lookup"><span data-stu-id="65561-103">Value of type 'type1' cannot be converted to 'type2'.</span></span> <span data-ttu-id="65561-104">Você pode usar a propriedade ' value ' para obter o valor da cadeia de caracteres do primeiro elemento de ' \<parentElement> '.</span><span class="sxs-lookup"><span data-stu-id="65561-104">You can use the 'Value' property to get the string value of the first element of '\<parentElement>'.</span></span>

 <span data-ttu-id="65561-105">Foi feita uma tentativa de converter implicitamente um literal XML para um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="65561-105">An attempt has been made to implicitly cast an XML literal to a specific type.</span></span> <span data-ttu-id="65561-106">O literal XML não pode ser convertido implicitamente no tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="65561-106">The XML literal cannot be implicitly cast to the specified type.</span></span>

 <span data-ttu-id="65561-107">**ID do erro:** BC31194</span><span class="sxs-lookup"><span data-stu-id="65561-107">**Error ID:** BC31194</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="65561-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="65561-108">To correct this error</span></span>

- <span data-ttu-id="65561-109">Use a `Value` Propriedade do literal XML para referenciar seu valor como um `String` .</span><span class="sxs-lookup"><span data-stu-id="65561-109">Use the `Value` property of the XML literal to reference its value as a `String`.</span></span> <span data-ttu-id="65561-110">Use a `CType` função, outra função de conversão de tipo ou a <xref:System.Convert> classe para converter o valor como o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="65561-110">Use the `CType` function, another type conversion function, or the <xref:System.Convert> class to cast the value as the specified type.</span></span>

## <a name="see-also"></a><span data-ttu-id="65561-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="65561-111">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="65561-112">Funções de conversão do tipo</span><span class="sxs-lookup"><span data-stu-id="65561-112">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="65561-113">Literais XML</span><span class="sxs-lookup"><span data-stu-id="65561-113">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="65561-114">XML</span><span class="sxs-lookup"><span data-stu-id="65561-114">XML</span></span>](../../programming-guide/language-features/xml/index.md)
