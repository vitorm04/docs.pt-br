---
title: "&#39; ReDim &#39; não é possível alterar o número de dimensões"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cf3713c72bd07803935065780e894c130911a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="1da89-102">&#39; ReDim &#39; não é possível alterar o número de dimensões</span><span class="sxs-lookup"><span data-stu-id="1da89-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="1da89-103">Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="1da89-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="1da89-104">`ReDim`pode alterar o tamanho de uma ou mais dimensões de uma matriz que já tenha sido formalmente declarado, mas ele não pode alterar a classificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="1da89-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1da89-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1da89-105">To correct this error</span></span>  
  
-   <span data-ttu-id="1da89-106">Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos das suas dimensões e, se possível, use `Dim` para declarar uma nova matriz com a classificação desejada.</span><span class="sxs-lookup"><span data-stu-id="1da89-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da89-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1da89-107">See Also</span></span>  
 [<span data-ttu-id="1da89-108">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1da89-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="1da89-109">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1da89-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="1da89-110">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="1da89-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="1da89-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="1da89-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
