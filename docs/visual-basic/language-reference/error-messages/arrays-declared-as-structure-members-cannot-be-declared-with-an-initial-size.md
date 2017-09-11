---
title: "Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
dev_langs:
- VB
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
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
ms.openlocfilehash: b8ffa5a8c0e57aaabe3bb24a9614ca7188686692
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="12340-102">Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="12340-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="12340-103">Uma matriz em uma estrutura é declarada com um tamanho inicial.</span><span class="sxs-lookup"><span data-stu-id="12340-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="12340-104">Você não pode inicializar qualquer elemento de estrutura, e declarar o tamanho de uma matriz é uma forma de inicialização.</span><span class="sxs-lookup"><span data-stu-id="12340-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="12340-105">**ID do erro:** BC31043</span><span class="sxs-lookup"><span data-stu-id="12340-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12340-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="12340-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="12340-107">Defina a matriz na sua estrutura como dinâmica (sem tamanho inicial).</span><span class="sxs-lookup"><span data-stu-id="12340-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="12340-108">Se você precisar de um certo tamanho de matriz, você pode redimensionar uma matriz dinâmica com uma [instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="12340-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="12340-109">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="12340-109">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12340-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12340-110">See Also</span></span>  
 <span data-ttu-id="12340-111">[Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="12340-111">[Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="12340-112"> [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)</span><span class="sxs-lookup"><span data-stu-id="12340-112"> [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)</span></span>
