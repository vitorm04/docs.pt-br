---
title: "Essa matriz é fixa ou está temporariamente bloqueada (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID10
dev_langs:
- VB
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c30def1879ec5c44753eeda6a1449f1361f4210a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="c115f-102">Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c115f-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="c115f-103">Este erro possui as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="c115f-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="c115f-104">Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="c115f-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="c115f-105">Redimensioning uma matriz dinâmica de nível de módulo, na qual um elemento foi passado como um argumento para um procedimento.</span><span class="sxs-lookup"><span data-stu-id="c115f-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="c115f-106">Se um elemento for passado, a matriz é bloqueada para impedir desalocando memória para o parâmetro de referência dentro do procedimento.</span><span class="sxs-lookup"><span data-stu-id="c115f-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="c115f-107">Tentativa de atribuir um valor para um `Variant` variável que contém uma matriz, mas o `Variant` está bloqueado no momento.</span><span class="sxs-lookup"><span data-stu-id="c115f-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c115f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c115f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c115f-109">Verifique a matriz original dinâmico em vez de fixo por declará-la com `ReDim` (se a matriz declarada dentro de um procedimento), ou por declará-la sem especificar o número de elementos (se a matriz é declarada no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="c115f-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="c115f-110">Determine se você realmente precisa passar o elemento, já que é visível em todos os procedimentos no módulo.</span><span class="sxs-lookup"><span data-stu-id="c115f-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="c115f-111">Determinar o que está bloqueando o `Variant` e corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="c115f-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c115f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c115f-112">See Also</span></span>  
 [<span data-ttu-id="c115f-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c115f-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
