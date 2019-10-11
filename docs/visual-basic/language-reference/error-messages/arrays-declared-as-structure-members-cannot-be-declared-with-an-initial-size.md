---
title: Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250147"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="f0d59-102">Matrizes declaradas como membros de estrutura não podem ser declaradas com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="f0d59-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="f0d59-103">Uma matriz em uma estrutura é declarada com um tamanho inicial.</span><span class="sxs-lookup"><span data-stu-id="f0d59-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="f0d59-104">Você não pode inicializar nenhum elemento de estrutura e declarar um tamanho de matriz é uma forma de inicialização.</span><span class="sxs-lookup"><span data-stu-id="f0d59-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="f0d59-105">**ID do erro:** BC31043</span><span class="sxs-lookup"><span data-stu-id="f0d59-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="f0d59-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0d59-106">Example</span></span>

<span data-ttu-id="f0d59-107">O exemplo a seguir gera BC31043:</span><span class="sxs-lookup"><span data-stu-id="f0d59-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="f0d59-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f0d59-108">To correct this error</span></span>

1. <span data-ttu-id="f0d59-109">Defina a matriz em sua estrutura como dinâmica (sem tamanho inicial).</span><span class="sxs-lookup"><span data-stu-id="f0d59-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="f0d59-110">Se você precisar de um determinado tamanho de matriz, poderá redimensionar uma matriz dinâmica com uma [instrução ReDim](../statements/redim-statement.md) quando o código estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="f0d59-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="f0d59-111">O exemplo a seguir ilustra isto:</span><span class="sxs-lookup"><span data-stu-id="f0d59-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="f0d59-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0d59-112">See also</span></span>

- [<span data-ttu-id="f0d59-113">Matrizes</span><span class="sxs-lookup"><span data-stu-id="f0d59-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f0d59-114">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="f0d59-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
