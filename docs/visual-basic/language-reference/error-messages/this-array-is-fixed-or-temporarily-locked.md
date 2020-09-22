---
title: Esta matriz é fixa ou está temporariamente bloqueada
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 05fb8e2ef788920fd200d79a75eec3d7c252b123
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873582"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="931b9-102">Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="931b9-102">This array is fixed or temporarily locked (Visual Basic)</span></span>

<span data-ttu-id="931b9-103">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="931b9-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="931b9-104">Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="931b9-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="931b9-105">Redimensionamento de uma matriz dinâmica em nível de módulo, na qual um elemento foi passado como um argumento para um procedimento.</span><span class="sxs-lookup"><span data-stu-id="931b9-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="931b9-106">Se um elemento for passado, a matriz será bloqueada para evitar a desalocação de memória para o parâmetro de referência no procedimento.</span><span class="sxs-lookup"><span data-stu-id="931b9-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="931b9-107">Tentativa de atribuir um valor a uma `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.</span><span class="sxs-lookup"><span data-stu-id="931b9-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="931b9-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="931b9-108">To correct this error</span></span>  
  
1. <span data-ttu-id="931b9-109">Torne a matriz original dinâmica, em vez de corrigida, declarando-a com `ReDim` (se a matriz for declarada dentro de um procedimento) ou declarando-a sem especificar o número de elementos (se a matriz for declarada no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="931b9-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="931b9-110">Determine se você realmente precisa passar o elemento, pois ele está visível em todos os procedimentos no módulo.</span><span class="sxs-lookup"><span data-stu-id="931b9-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="931b9-111">Determine o que está bloqueando o `Variant` e corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="931b9-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931b9-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="931b9-112">See also</span></span>

- [<span data-ttu-id="931b9-113">matrizes</span><span class="sxs-lookup"><span data-stu-id="931b9-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
