---
title: Instrução Throw (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821357"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="ea0d5-102">Instrução Throw (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea0d5-102">Throw Statement (Visual Basic)</span></span>
<span data-ttu-id="ea0d5-103">Gera uma exceção dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-103">Throws an exception within a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea0d5-104">Syntax</span></span>  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a><span data-ttu-id="ea0d5-105">Parte</span><span class="sxs-lookup"><span data-stu-id="ea0d5-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="ea0d5-106">Fornece informações sobre a exceção seja lançada.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="ea0d5-107">Opcional quando residente em um `Catch` instrução, caso contrário, é necessária.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea0d5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea0d5-108">Remarks</span></span>  
 <span data-ttu-id="ea0d5-109">O `Throw` instrução gera uma exceção que você pode manipular com código de tratamento de exceções estruturado (`Try`... `Catch`... `Finally`) ou código de manipulação de exceção não estruturado (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="ea0d5-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="ea0d5-110">Você pode usar o `Throw` instrução para interceptar erros em seu código, porque o Visual Basic move para cima a pilha de chamadas até encontrar o código de manipulação de exceção apropriado.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>  
  
 <span data-ttu-id="ea0d5-111">Um `Throw` instrução com nenhuma expressão somente pode ser usada em uma `Catch` instrução, em que a instrução case Relança a exceção atualmente sendo tratada pela `Catch` instrução.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>  
  
 <span data-ttu-id="ea0d5-112">O `Throw` instrução redefine a pilha de chamadas para o `expression` exceção.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="ea0d5-113">Se `expression` não for fornecido, a pilha de chamadas é deixada inalterada.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="ea0d5-114">Você pode acessar a pilha de chamadas para a exceção por meio de <xref:System.Exception.StackTrace%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ea0d5-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0d5-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea0d5-115">Example</span></span>  
 <span data-ttu-id="ea0d5-116">O código a seguir usa o `Throw` instrução para gerar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="ea0d5-116">The following code uses the `Throw` statement to throw an exception:</span></span>  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a><span data-ttu-id="ea0d5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea0d5-117">Requirements</span></span>  
 <span data-ttu-id="ea0d5-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ea0d5-118">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ea0d5-119">**Módulo:** `Interaction`</span><span class="sxs-lookup"><span data-stu-id="ea0d5-119">**Module:** `Interaction`</span></span>  
  
 <span data-ttu-id="ea0d5-120">**Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ea0d5-120">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0d5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea0d5-121">See also</span></span>

- [<span data-ttu-id="ea0d5-122">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="ea0d5-122">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ea0d5-123">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="ea0d5-123">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
