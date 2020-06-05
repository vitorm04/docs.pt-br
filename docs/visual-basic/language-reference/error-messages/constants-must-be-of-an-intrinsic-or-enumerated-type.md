---
title: As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9e36b84252c3d8762308e95323b8e284977df8c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409758"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="623ae-102">As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz</span><span class="sxs-lookup"><span data-stu-id="623ae-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="623ae-103">Você tentou declarar uma constante como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico recipiente.</span><span class="sxs-lookup"><span data-stu-id="623ae-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="623ae-104">Constantes devem ser de um tipo intrínseco (,,,,,,,, `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` , `Short` , `Single` ,,, `String` `UInteger` `ULong` , ou `UShort` ), ou um `Enum` tipo com base em um dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="623ae-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="623ae-105">**ID do erro:** BC30424</span><span class="sxs-lookup"><span data-stu-id="623ae-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="623ae-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="623ae-106">To correct this error</span></span>  
  
1. <span data-ttu-id="623ae-107">Declare a constante como um tipo intrínseco ou `Enum` .</span><span class="sxs-lookup"><span data-stu-id="623ae-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2. <span data-ttu-id="623ae-108">Uma constante também pode ser um valor especial, como `True` , `False` ou `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="623ae-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="623ae-109">O compilador considera esses valores predefinidos como sendo do tipo intrínseco apropriado.</span><span class="sxs-lookup"><span data-stu-id="623ae-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623ae-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="623ae-110">See also</span></span>

- [<span data-ttu-id="623ae-111">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="623ae-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="623ae-112">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="623ae-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="623ae-113">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="623ae-113">Data Types</span></span>](../data-types/index.md)
