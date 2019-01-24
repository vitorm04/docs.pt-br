---
title: Instrução Stop (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624776"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="eb888-102">Instrução Stop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb888-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="eb888-103">Suspende a execução.</span><span class="sxs-lookup"><span data-stu-id="eb888-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb888-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb888-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb888-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb888-105">Remarks</span></span>  
 <span data-ttu-id="eb888-106">Você pode colocar `Stop` instruções em qualquer lugar nos procedimentos para suspender a execução.</span><span class="sxs-lookup"><span data-stu-id="eb888-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="eb888-107">Usando o `Stop` instrução é semelhante à configuração de um ponto de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="eb888-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="eb888-108">O `Stop` instrução suspende a execução, mas ao contrário `End`, não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).</span><span class="sxs-lookup"><span data-stu-id="eb888-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb888-109">Se o `Stop` instrução for encontrada no código que está em execução fora do ambiente de desenvolvimento integrado (IDE), o depurador é invocado.</span><span class="sxs-lookup"><span data-stu-id="eb888-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="eb888-110">Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.</span><span class="sxs-lookup"><span data-stu-id="eb888-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb888-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eb888-111">Example</span></span>  
 <span data-ttu-id="eb888-112">Este exemplo usa o `Stop` instrução para suspender a execução para cada iteração por meio de `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="eb888-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb888-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb888-113">See also</span></span>
- [<span data-ttu-id="eb888-114">Instrução End</span><span class="sxs-lookup"><span data-stu-id="eb888-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
