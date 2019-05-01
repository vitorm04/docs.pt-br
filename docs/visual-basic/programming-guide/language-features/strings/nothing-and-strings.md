---
title: Nada e cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032273"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="1cce5-102">Nada e cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cce5-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="1cce5-103">O tempo de execução do Visual Basic e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] avaliar `Nothing` diferente quando se trata de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="1cce5-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="1cce5-104">Tempo de execução do Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1cce5-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="1cce5-105">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1cce5-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="1cce5-106">O tempo de execução do Visual Basic geralmente avalia `Nothing` como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="1cce5-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="1cce5-107">O [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] não e gera uma exceção sempre que for feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1cce5-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cce5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cce5-108">See also</span></span>

- [<span data-ttu-id="1cce5-109">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cce5-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
