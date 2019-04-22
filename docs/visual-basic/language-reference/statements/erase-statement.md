---
title: Instrução Erase (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840400"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="d33ca-102">Instrução Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33ca-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="d33ca-103">Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.</span><span class="sxs-lookup"><span data-stu-id="d33ca-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d33ca-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="d33ca-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d33ca-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="d33ca-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d33ca-106">Required.</span></span> <span data-ttu-id="d33ca-107">Lista de variáveis de matriz a ser apagado.</span><span class="sxs-lookup"><span data-stu-id="d33ca-107">List of array variables to be erased.</span></span> <span data-ttu-id="d33ca-108">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d33ca-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d33ca-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d33ca-109">Remarks</span></span>  
 <span data-ttu-id="d33ca-110">O `Erase` declaração pode aparecer somente no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="d33ca-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="d33ca-111">Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="d33ca-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="d33ca-112">O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="d33ca-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d33ca-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d33ca-113">Example</span></span>  
 <span data-ttu-id="d33ca-114">O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e sua memória livre (1000 e 100 elementos de armazenamento, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="d33ca-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="d33ca-115">O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.</span><span class="sxs-lookup"><span data-stu-id="d33ca-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="d33ca-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d33ca-116">See also</span></span>

- [<span data-ttu-id="d33ca-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="d33ca-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="d33ca-118">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="d33ca-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
