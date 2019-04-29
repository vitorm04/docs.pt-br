---
title: Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 5d58b531b670715716e849cd37227bc899195df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935363"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="476f1-102">Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="476f1-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="476f1-103">Uma matriz em uma estrutura é declarada com um tamanho inicial.</span><span class="sxs-lookup"><span data-stu-id="476f1-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="476f1-104">Você não pode inicializar qualquer elemento de estrutura e a declaração de um tamanho da matriz é uma forma de inicialização.</span><span class="sxs-lookup"><span data-stu-id="476f1-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="476f1-105">**ID do erro:** BC31043</span><span class="sxs-lookup"><span data-stu-id="476f1-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="476f1-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="476f1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="476f1-107">Defina a matriz na sua estrutura como dinâmica (sem tamanho inicial).</span><span class="sxs-lookup"><span data-stu-id="476f1-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="476f1-108">Se você precisar de um determinado tamanho de matriz, você pode redimensionar uma matriz dinâmica com um [instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="476f1-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="476f1-109">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="476f1-109">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="476f1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="476f1-110">See also</span></span>

- [<span data-ttu-id="476f1-111">Matrizes</span><span class="sxs-lookup"><span data-stu-id="476f1-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="476f1-112">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="476f1-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
