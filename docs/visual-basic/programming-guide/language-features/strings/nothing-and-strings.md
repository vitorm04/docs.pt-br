---
title: Nada e cadeias de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591350"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="ae2a0-102">Nada e cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae2a0-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="ae2a0-103">Avaliam o tempo de execução do Visual Basic e o .NET Framework `Nothing` diferente quando se trata de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ae2a0-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="ae2a0-104">Tempo de execução do Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae2a0-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="ae2a0-105">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ae2a0-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="ae2a0-106">O tempo de execução do Visual Basic geralmente avalia `Nothing` como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="ae2a0-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="ae2a0-107">O .NET Framework não e gera uma exceção sempre que for feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ae2a0-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2a0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae2a0-108">See also</span></span>

- [<span data-ttu-id="ae2a0-109">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae2a0-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
