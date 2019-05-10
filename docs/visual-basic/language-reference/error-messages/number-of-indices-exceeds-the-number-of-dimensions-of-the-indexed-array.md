---
title: O número de índices excede o número de dimensões da matriz indexada
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665686"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="1264b-102">O número de índices excede o número de dimensões da matriz indexada</span><span class="sxs-lookup"><span data-stu-id="1264b-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="1264b-103">O número de índices usados para acessar um elemento de matriz deve ser exatamente o mesmo que a classificação da matriz, ou seja, o número de dimensões declarado para ele.</span><span class="sxs-lookup"><span data-stu-id="1264b-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="1264b-104">**ID do erro:** BC30106</span><span class="sxs-lookup"><span data-stu-id="1264b-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1264b-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1264b-105">To correct this error</span></span>  
  
- <span data-ttu-id="1264b-106">Remova subscritos da referência de matriz até que o número total de subscritos é igual a classificação da matriz.</span><span class="sxs-lookup"><span data-stu-id="1264b-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="1264b-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1264b-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1264b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1264b-108">See also</span></span>

- [<span data-ttu-id="1264b-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="1264b-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
