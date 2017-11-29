---
title: "Instrução Erase (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="9aa9a-102">Instrução Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aa9a-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="9aa9a-103">Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9aa9a-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="9aa9a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9aa9a-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="9aa9a-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-106">Required.</span></span> <span data-ttu-id="9aa9a-107">Lista de variáveis de matriz a ser apagada.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-107">List of array variables to be erased.</span></span> <span data-ttu-id="9aa9a-108">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aa9a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9aa9a-109">Remarks</span></span>  
 <span data-ttu-id="9aa9a-110">O `Erase` instrução pode aparecer somente no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="9aa9a-111">Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="9aa9a-112">O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9aa9a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9aa9a-113">Example</span></span>  
 <span data-ttu-id="9aa9a-114">O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e liberar a memória (elementos de armazenamento 1000 e 100, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="9aa9a-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="9aa9a-115">O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.</span><span class="sxs-lookup"><span data-stu-id="9aa9a-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9aa9a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aa9a-116">See Also</span></span>  
 [<span data-ttu-id="9aa9a-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="9aa9a-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="9aa9a-118">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="9aa9a-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
