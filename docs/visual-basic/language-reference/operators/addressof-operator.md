---
title: Operador AddressOf
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350277"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="58f49-102">Operador AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58f49-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="58f49-103">Creates a delegate instance that references the specific procedure.</span><span class="sxs-lookup"><span data-stu-id="58f49-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58f49-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="58f49-105">Partes</span><span class="sxs-lookup"><span data-stu-id="58f49-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="58f49-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="58f49-106">Required.</span></span> <span data-ttu-id="58f49-107">Specifies the procedure to be referenced by the newly created delegate.</span><span class="sxs-lookup"><span data-stu-id="58f49-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58f49-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="58f49-108">Remarks</span></span>  
 <span data-ttu-id="58f49-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="58f49-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="58f49-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span><span class="sxs-lookup"><span data-stu-id="58f49-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="58f49-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span><span class="sxs-lookup"><span data-stu-id="58f49-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="58f49-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span><span class="sxs-lookup"><span data-stu-id="58f49-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f49-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58f49-113">Example</span></span>  
 <span data-ttu-id="58f49-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span><span class="sxs-lookup"><span data-stu-id="58f49-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="58f49-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58f49-115">Example</span></span>  
 <span data-ttu-id="58f49-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span><span class="sxs-lookup"><span data-stu-id="58f49-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="58f49-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58f49-117">See also</span></span>

- [<span data-ttu-id="58f49-118">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="58f49-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="58f49-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="58f49-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="58f49-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="58f49-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="58f49-121">Delegados</span><span class="sxs-lookup"><span data-stu-id="58f49-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
