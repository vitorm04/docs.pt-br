---
title: Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 06e5e36f3e0522e0449c0ef9698f3a1b01b9cb5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549061"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="f4c51-102">Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="f4c51-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="f4c51-103">Uma matriz em uma estrutura é declarada com um tamanho inicial.</span><span class="sxs-lookup"><span data-stu-id="f4c51-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="f4c51-104">Você não pode inicializar qualquer elemento de estrutura e a declaração de um tamanho da matriz é uma forma de inicialização.</span><span class="sxs-lookup"><span data-stu-id="f4c51-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="f4c51-105">**ID do erro:** BC31043</span><span class="sxs-lookup"><span data-stu-id="f4c51-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4c51-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f4c51-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f4c51-107">Defina a matriz na sua estrutura como dinâmica (sem tamanho inicial).</span><span class="sxs-lookup"><span data-stu-id="f4c51-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="f4c51-108">Se você precisar de um determinado tamanho de matriz, você pode redimensionar uma matriz dinâmica com um [instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="f4c51-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="f4c51-109">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="f4c51-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f4c51-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4c51-110">See also</span></span>
- [<span data-ttu-id="f4c51-111">Matrizes</span><span class="sxs-lookup"><span data-stu-id="f4c51-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f4c51-112">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="f4c51-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
