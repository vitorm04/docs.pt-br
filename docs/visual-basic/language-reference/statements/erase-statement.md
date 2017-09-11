---
title: "Instrução Erase (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
dev_langs:
- VB
helpviewer_keywords:
- Erase keyword
- Erase statement
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
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
ms.openlocfilehash: 015dc57f6df224fcb1f7f7a09f8aedc9404ea22b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="9c27d-102">Instrução Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c27d-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="9c27d-103">Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.</span><span class="sxs-lookup"><span data-stu-id="9c27d-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c27d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c27d-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="9c27d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9c27d-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="9c27d-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9c27d-106">Required.</span></span> <span data-ttu-id="9c27d-107">Lista de variáveis de matriz a ser apagada.</span><span class="sxs-lookup"><span data-stu-id="9c27d-107">List of array variables to be erased.</span></span> <span data-ttu-id="9c27d-108">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9c27d-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c27d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c27d-109">Remarks</span></span>  
 <span data-ttu-id="9c27d-110">O `Erase` declaração pode aparecer somente no nível de procedimento.</span><span class="sxs-lookup"><span data-stu-id="9c27d-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="9c27d-111">Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="9c27d-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="9c27d-112">O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="9c27d-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c27d-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c27d-113">Example</span></span>  
 <span data-ttu-id="9c27d-114">O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e liberar seu memória (elementos de armazenamento 1000 e 100, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="9c27d-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="9c27d-115">O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.</span><span class="sxs-lookup"><span data-stu-id="9c27d-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 <span data-ttu-id="9c27d-116">[!code-vb[19 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c27d-116">[!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c27d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c27d-117">See Also</span></span>  
 <span data-ttu-id="9c27d-118">[Nada](../../../visual-basic/language-reference/nothing.md) </span><span class="sxs-lookup"><span data-stu-id="9c27d-118">[Nothing](../../../visual-basic/language-reference/nothing.md) </span></span>  
<span data-ttu-id="9c27d-119"> [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9c27d-119"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)</span></span>
