---
title: "Constantes devem ser do tipo intrínseco ou enumerado, não uma classe, estrutura, parâmetro de tipo ou tipo de matriz | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
dev_langs:
- VB
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
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
ms.openlocfilehash: a4951d8ab8a11257ca3da4724ae11a4f7d02fbf4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="b3e6c-102">As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz</span><span class="sxs-lookup"><span data-stu-id="b3e6c-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="b3e6c-103">Você tentou declarar uma constante como uma classe, estrutura ou tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="b3e6c-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="b3e6c-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span><span class="sxs-lookup"><span data-stu-id="b3e6c-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="b3e6c-105">**ID do erro:** BC30424</span><span class="sxs-lookup"><span data-stu-id="b3e6c-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3e6c-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b3e6c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b3e6c-107">Declare a constante como um intrínseco ou `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="b3e6c-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="b3e6c-108">Uma constante pode também ser um valor especial como `True`, `False`, ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b3e6c-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="b3e6c-109">O compilador considera esses valores predefinidos como do tipo intrínseco apropriado.</span><span class="sxs-lookup"><span data-stu-id="b3e6c-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e6c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3e6c-110">See Also</span></span>  
 <span data-ttu-id="b3e6c-111">[Constantes e enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="b3e6c-111">[Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="b3e6c-112"> [Tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="b3e6c-112"> [Data Types](../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="b3e6c-113"> [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="b3e6c-113"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
