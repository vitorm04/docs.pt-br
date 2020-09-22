---
title: As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874563"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="984cf-102">As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz</span><span class="sxs-lookup"><span data-stu-id="984cf-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="984cf-103">Você tentou declarar uma constante como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico recipiente.</span><span class="sxs-lookup"><span data-stu-id="984cf-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="984cf-104">Constantes devem ser de um tipo intrínseco (,,,,,,,, `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` , `Short` , `Single` ,,, `String` `UInteger` `ULong` , ou `UShort` ), ou um `Enum` tipo com base em um dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="984cf-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="984cf-105">**ID do erro:** BC30424</span><span class="sxs-lookup"><span data-stu-id="984cf-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="984cf-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="984cf-106">To correct this error</span></span>  
  
1. <span data-ttu-id="984cf-107">Declare a constante como um tipo intrínseco ou `Enum` .</span><span class="sxs-lookup"><span data-stu-id="984cf-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2. <span data-ttu-id="984cf-108">Uma constante também pode ser um valor especial, como `True` , `False` ou `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="984cf-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="984cf-109">O compilador considera esses valores predefinidos como sendo do tipo intrínseco apropriado.</span><span class="sxs-lookup"><span data-stu-id="984cf-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="984cf-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="984cf-110">See also</span></span>

- [<span data-ttu-id="984cf-111">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="984cf-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="984cf-112">Data Types</span><span class="sxs-lookup"><span data-stu-id="984cf-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="984cf-113">Data Types</span><span class="sxs-lookup"><span data-stu-id="984cf-113">Data Types</span></span>](../data-types/index.md)
