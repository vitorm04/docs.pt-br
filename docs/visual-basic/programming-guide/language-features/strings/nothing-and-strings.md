---
title: Nothing e cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344302"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="bd9db-102">Nada e cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd9db-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="bd9db-103">O tempo de execução de Visual Basic e o .NET Framework avaliam `Nothing` de maneira diferente quando se trata de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bd9db-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="bd9db-104">Tempo de execução de Visual Basic e o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bd9db-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="bd9db-105">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bd9db-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="bd9db-106">O tempo de execução de Visual Basic geralmente avalia `Nothing` como uma cadeia de caracteres vazia ("").</span><span class="sxs-lookup"><span data-stu-id="bd9db-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="bd9db-107">O .NET Framework não, no entanto, e gera uma exceção sempre que é feita uma tentativa de executar uma operação de cadeia de caracteres em `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="bd9db-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9db-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd9db-108">See also</span></span>

- [<span data-ttu-id="bd9db-109">Introdução às cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd9db-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
