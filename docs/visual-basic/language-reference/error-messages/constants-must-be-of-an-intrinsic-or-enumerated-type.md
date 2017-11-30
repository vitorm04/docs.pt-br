---
title: "As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords: BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 702472751810c2d2bd08ece944ef0ffafc2049b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="a689f-102">As constantes devem ser do tipo intrínseco ou enumerado, e não classe, estrutura, parâmetro de tipo ou tipo de matriz</span><span class="sxs-lookup"><span data-stu-id="a689f-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="a689f-103">Você tentou declarar uma constante como uma classe, estrutura ou o tipo de matriz, ou como um parâmetro de tipo definido por um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a689f-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="a689f-104">Constantes devem ser de um tipo intrínseco (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, ou `UShort`), ou um `Enum` tipo com base em um dos tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="a689f-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="a689f-105">**ID do erro:** BC30424</span><span class="sxs-lookup"><span data-stu-id="a689f-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a689f-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a689f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a689f-107">Declare a constante como um intrínseco ou `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="a689f-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="a689f-108">Uma constante pode também ser um valor especial como `True`, `False`, ou `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a689f-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="a689f-109">O compilador considera esses valores predefinidos para ser do tipo intrínseco apropriado.</span><span class="sxs-lookup"><span data-stu-id="a689f-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a689f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a689f-110">See Also</span></span>  
 [<span data-ttu-id="a689f-111">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="a689f-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="a689f-112">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a689f-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="a689f-113">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a689f-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)
