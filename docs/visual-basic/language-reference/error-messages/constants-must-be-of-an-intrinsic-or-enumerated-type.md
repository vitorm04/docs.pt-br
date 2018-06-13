---
title: As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 9039376fc4d1f67ca9b526e46eaf28a0b1a3943c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587476"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="09103-102">As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz</span><span class="sxs-lookup"><span data-stu-id="09103-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="09103-103">Você tentou declarar uma constante como uma classe, estrutura ou o tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="09103-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="09103-104">Constantes devem ser de um tipo intrínseco (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ou `UShort`), ou um `Enum` tipo com base em um dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="09103-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="09103-105">**ID do erro:** BC30424</span><span class="sxs-lookup"><span data-stu-id="09103-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09103-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="09103-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="09103-107">Declare a constante como um intrínseco ou `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="09103-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="09103-108">Uma constante pode também ser um valor especial como `True`, `False`, ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="09103-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="09103-109">O compilador considera esses valores predefinidos para ser do tipo intrínseco apropriado.</span><span class="sxs-lookup"><span data-stu-id="09103-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09103-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09103-110">See Also</span></span>  
 [<span data-ttu-id="09103-111">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="09103-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="09103-112">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="09103-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="09103-113">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="09103-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
