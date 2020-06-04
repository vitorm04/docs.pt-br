---
title: Instrução Erase
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404713"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="bf92f-102">Instrução Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf92f-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="bf92f-103">Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.</span><span class="sxs-lookup"><span data-stu-id="bf92f-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf92f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf92f-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="bf92f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="bf92f-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="bf92f-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="bf92f-106">Required.</span></span> <span data-ttu-id="bf92f-107">Lista de variáveis de matriz a serem apagadas.</span><span class="sxs-lookup"><span data-stu-id="bf92f-107">List of array variables to be erased.</span></span> <span data-ttu-id="bf92f-108">Várias variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="bf92f-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf92f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf92f-109">Remarks</span></span>  
 <span data-ttu-id="bf92f-110">A `Erase` instrução pode aparecer somente no nível do procedimento.</span><span class="sxs-lookup"><span data-stu-id="bf92f-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="bf92f-111">Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou de módulo.</span><span class="sxs-lookup"><span data-stu-id="bf92f-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="bf92f-112">A `Erase` instrução é equivalente a atribuir `Nothing` a cada variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="bf92f-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf92f-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf92f-113">Example</span></span>  
 <span data-ttu-id="bf92f-114">O exemplo a seguir usa a `Erase` instrução para limpar duas matrizes e liberar sua memória (1000 e 100 elementos de armazenamento, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="bf92f-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="bf92f-115">`ReDim`Em seguida, a instrução atribui uma nova instância de matriz à matriz tridimensional.</span><span class="sxs-lookup"><span data-stu-id="bf92f-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="bf92f-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf92f-116">See also</span></span>

- [<span data-ttu-id="bf92f-117">Nada</span><span class="sxs-lookup"><span data-stu-id="bf92f-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="bf92f-118">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="bf92f-118">ReDim Statement</span></span>](redim-statement.md)
