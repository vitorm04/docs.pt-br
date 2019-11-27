---
title: Esta matriz é fixa ou está temporariamente bloqueada
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350784"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="37a96-102">Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37a96-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="37a96-103">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="37a96-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="37a96-104">Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="37a96-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="37a96-105">Redimensionamento de uma matriz dinâmica em nível de módulo, na qual um elemento foi passado como um argumento para um procedimento.</span><span class="sxs-lookup"><span data-stu-id="37a96-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="37a96-106">Se um elemento for passado, a matriz será bloqueada para evitar a desalocação de memória para o parâmetro de referência no procedimento.</span><span class="sxs-lookup"><span data-stu-id="37a96-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="37a96-107">A tentativa de atribuir um valor a uma variável `Variant` que contém uma matriz, mas o `Variant` está bloqueado no momento.</span><span class="sxs-lookup"><span data-stu-id="37a96-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37a96-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="37a96-108">To correct this error</span></span>  
  
1. <span data-ttu-id="37a96-109">Torne a matriz original dinâmica, em vez de corrigida, declarando-a com `ReDim` (se a matriz for declarada dentro de um procedimento) ou declarando-a sem especificar o número de elementos (se a matriz for declarada no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="37a96-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="37a96-110">Determine se você realmente precisa passar o elemento, pois ele está visível em todos os procedimentos no módulo.</span><span class="sxs-lookup"><span data-stu-id="37a96-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="37a96-111">Determine o que está bloqueando o `Variant` e corrija-o.</span><span class="sxs-lookup"><span data-stu-id="37a96-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a96-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37a96-112">See also</span></span>

- [<span data-ttu-id="37a96-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="37a96-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
