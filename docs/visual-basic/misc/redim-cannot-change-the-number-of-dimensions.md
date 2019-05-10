---
title: "'ReDim' não é possível alterar o número de dimensões"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 1e9695bbc7f104aa741de232f1f6d3c76df2cebf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591739"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="ada7f-102">'ReDim' não é possível alterar o número de dimensões</span><span class="sxs-lookup"><span data-stu-id="ada7f-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="ada7f-103">Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ada7f-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="ada7f-104">`ReDim` pode alterar o tamanho de uma ou mais dimensões de uma matriz que já foi formalmente declarado, mas ele não é possível alterar a classificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="ada7f-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ada7f-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ada7f-105">To correct this error</span></span>  
  
- <span data-ttu-id="ada7f-106">Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos das suas dimensões e, se possível, use `Dim` para declarar uma nova matriz com a classificação desejada.</span><span class="sxs-lookup"><span data-stu-id="ada7f-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada7f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ada7f-107">See also</span></span>

- [<span data-ttu-id="ada7f-108">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ada7f-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="ada7f-109">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ada7f-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="ada7f-110">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="ada7f-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="ada7f-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="ada7f-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
