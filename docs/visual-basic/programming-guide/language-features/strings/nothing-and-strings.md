---
title: Nothing e cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360560"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="f6e42-102">Nada e cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6e42-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="f6e42-103">O tempo de execução Visual Basic e o .NET Framework são avaliados de `Nothing` maneira diferente quando se trata de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f6e42-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="f6e42-104">Tempo de execução de Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6e42-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="f6e42-105">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f6e42-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="f6e42-106">O tempo de execução de Visual Basic geralmente é avaliado `Nothing` como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="f6e42-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="f6e42-107">O .NET Framework não, no entanto, e gera uma exceção sempre que é feita uma tentativa de executar uma operação de cadeia de caracteres no `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="f6e42-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e42-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="f6e42-108">See also</span></span>

- [<span data-ttu-id="f6e42-109">Introdução a cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6e42-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
