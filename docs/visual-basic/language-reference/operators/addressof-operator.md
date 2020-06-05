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
ms.openlocfilehash: 3e7db8e7329ce8d21b6e07863e6f1673a6389608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372058"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="752d2-102">Operador AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752d2-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="752d2-103">Cria uma instância delegada que faz referência ao procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="752d2-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="752d2-104">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="752d2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="752d2-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="752d2-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="752d2-106">Required.</span></span> <span data-ttu-id="752d2-107">Especifica o procedimento a ser referenciado pelo delegado recém-criado.</span><span class="sxs-lookup"><span data-stu-id="752d2-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="752d2-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="752d2-108">Remarks</span></span>  
 <span data-ttu-id="752d2-109">O `AddressOf` operador cria um delegado que aponta para a sub-rotina ou função especificada por `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="752d2-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="752d2-110">Quando o procedimento especificado é um método de instância, o delegado se refere à instância e ao método.</span><span class="sxs-lookup"><span data-stu-id="752d2-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="752d2-111">Em seguida, quando o delegado é invocado, o método especificado da instância especificada é chamado.</span><span class="sxs-lookup"><span data-stu-id="752d2-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="752d2-112">O `AddressOf` operador pode ser usado como o operando de um construtor delegado ou pode ser usado em um contexto no qual o tipo do delegado possa ser determinado pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="752d2-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="752d2-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="752d2-113">Example</span></span>  
 <span data-ttu-id="752d2-114">Este exemplo usa o `AddressOf` operador para designar um delegado para manipular o `Click` evento de um botão.</span><span class="sxs-lookup"><span data-stu-id="752d2-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="752d2-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="752d2-115">Example</span></span>  
 <span data-ttu-id="752d2-116">O exemplo a seguir usa o `AddressOf` operador para designar a função de inicialização para um thread.</span><span class="sxs-lookup"><span data-stu-id="752d2-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="752d2-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="752d2-117">See also</span></span>

- [<span data-ttu-id="752d2-118">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="752d2-118">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="752d2-119">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="752d2-119">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="752d2-120">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="752d2-120">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="752d2-121">Delegados</span><span class="sxs-lookup"><span data-stu-id="752d2-121">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
