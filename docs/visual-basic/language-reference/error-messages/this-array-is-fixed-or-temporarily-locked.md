---
title: Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: f70b984fc493e79d7a83b33236615a3220405786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516987"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="08024-102">Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08024-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="08024-103">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="08024-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="08024-104">Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="08024-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="08024-105">Redimensioning uma matriz dinâmica de nível de módulo, no qual um elemento foi passado como um argumento para um procedimento.</span><span class="sxs-lookup"><span data-stu-id="08024-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="08024-106">Se um elemento for passado, a matriz é bloqueada para impedir desalocando memória para o parâmetro de referência dentro do procedimento.</span><span class="sxs-lookup"><span data-stu-id="08024-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="08024-107">Tentativa de atribuir um valor para um `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.</span><span class="sxs-lookup"><span data-stu-id="08024-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08024-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="08024-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="08024-109">Verifique a matriz original dinâmico e não fixados pelas declará-la com `ReDim` (se a matriz é declarada dentro de um procedimento), ou ao declará-la sem especificar o número de elementos (se a matriz é declarada no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="08024-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="08024-110">Determine se você realmente precisa passar o elemento, já que é visível em todos os procedimentos no módulo.</span><span class="sxs-lookup"><span data-stu-id="08024-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="08024-111">Determinar o que está bloqueando o `Variant` e corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="08024-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08024-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08024-112">See also</span></span>
- [<span data-ttu-id="08024-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="08024-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
