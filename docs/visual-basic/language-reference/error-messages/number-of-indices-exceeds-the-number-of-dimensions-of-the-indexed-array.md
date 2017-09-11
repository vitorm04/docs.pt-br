---
title: "Número de índices excede o número de dimensões da matriz indexada | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30106
- vbc30106
dev_langs:
- VB
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: 10
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
ms.sourcegitcommit: f19bef65c85459e09479fd4ad6da39a4813fdce6
ms.openlocfilehash: de8488711ebb507ae3c0f3ea55c8400c9b4b1089
ms.contentlocale: pt-br
ms.lasthandoff: 05/16/2017

---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="c4602-102">O número de índices excede o número de dimensões da matriz indexada</span><span class="sxs-lookup"><span data-stu-id="c4602-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="c4602-103">O número de índices usado para acessar um elemento de matriz deve ser exatamente o mesmo que a classificação da matriz, ou seja, o número de dimensões declarada para ela.</span><span class="sxs-lookup"><span data-stu-id="c4602-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="c4602-104">**ID do erro:** BC30106</span><span class="sxs-lookup"><span data-stu-id="c4602-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4602-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c4602-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c4602-106">Remova subscrições da referência de matriz até que o número total de subscrições é igual a classificação da matriz.</span><span class="sxs-lookup"><span data-stu-id="c4602-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="c4602-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c4602-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4602-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4602-108">See Also</span></span>  
 [<span data-ttu-id="c4602-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c4602-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
