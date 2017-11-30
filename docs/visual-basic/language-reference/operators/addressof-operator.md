---
title: Operador AddressOf (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="c20dc-102">Operador AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c20dc-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="c20dc-103">Cria uma instância de delegado de procedimento que referencia o procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="c20dc-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c20dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c20dc-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="c20dc-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c20dc-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="c20dc-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c20dc-106">Required.</span></span> <span data-ttu-id="c20dc-107">Especifica o procedimento a ser referenciado pelo delegado de procedimento recém-criado.</span><span class="sxs-lookup"><span data-stu-id="c20dc-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c20dc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c20dc-108">Remarks</span></span>  
 <span data-ttu-id="c20dc-109">O `AddressOf` operador cria um delegado de função que aponta para a função especificada por `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="c20dc-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="c20dc-110">Quando o procedimento especificado é que um método de instância, em seguida, o delegado de função refere-se a instância e o método.</span><span class="sxs-lookup"><span data-stu-id="c20dc-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="c20dc-111">Em seguida, quando o delegado de função é chamado o método especificado da instância especificada é chamado.</span><span class="sxs-lookup"><span data-stu-id="c20dc-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="c20dc-112">O `AddressOf` operador pode ser usado como o operando de um construtor delegado, ou ele pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="c20dc-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c20dc-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c20dc-113">Example</span></span>  
 <span data-ttu-id="c20dc-114">Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.</span><span class="sxs-lookup"><span data-stu-id="c20dc-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c20dc-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c20dc-115">Example</span></span>  
 <span data-ttu-id="c20dc-116">O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.</span><span class="sxs-lookup"><span data-stu-id="c20dc-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c20dc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c20dc-117">See Also</span></span>  
 [<span data-ttu-id="c20dc-118">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="c20dc-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="c20dc-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="c20dc-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="c20dc-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="c20dc-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="c20dc-121">Delegados</span><span class="sxs-lookup"><span data-stu-id="c20dc-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
