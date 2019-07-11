---
title: Operador AddressOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760381"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="fb800-102">Operador AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb800-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="fb800-103">Cria uma instância de delegado que referencia o procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="fb800-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb800-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb800-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="fb800-105">Partes</span><span class="sxs-lookup"><span data-stu-id="fb800-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="fb800-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fb800-106">Required.</span></span> <span data-ttu-id="fb800-107">Especifica o procedimento a ser referenciado pelo delegado criado recentemente.</span><span class="sxs-lookup"><span data-stu-id="fb800-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb800-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb800-108">Remarks</span></span>  
 <span data-ttu-id="fb800-109">O `AddressOf` operador cria um delegado que aponta para o sub ou função especificada por `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="fb800-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="fb800-110">Quando o procedimento especificado é que um método de instância, em seguida, o delegado refere-se para a instância e o método.</span><span class="sxs-lookup"><span data-stu-id="fb800-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="fb800-111">Em seguida, quando o delegado é invocado é chamado o método especificado da instância especificada.</span><span class="sxs-lookup"><span data-stu-id="fb800-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="fb800-112">O `AddressOf` operador pode ser usado como o operando de um construtor delegate ou ele pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="fb800-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb800-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb800-113">Example</span></span>  
 <span data-ttu-id="fb800-114">Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.</span><span class="sxs-lookup"><span data-stu-id="fb800-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="fb800-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb800-115">Example</span></span>  
 <span data-ttu-id="fb800-116">O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.</span><span class="sxs-lookup"><span data-stu-id="fb800-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="fb800-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb800-117">See also</span></span>

- [<span data-ttu-id="fb800-118">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="fb800-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="fb800-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="fb800-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fb800-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="fb800-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fb800-121">Delegados</span><span class="sxs-lookup"><span data-stu-id="fb800-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
