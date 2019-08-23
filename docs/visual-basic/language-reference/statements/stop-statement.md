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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957614"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="8cd3f-102">Instrução Stop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cd3f-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="8cd3f-103">Suspende a execução.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cd3f-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="8cd3f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cd3f-105">Remarks</span></span>  
 <span data-ttu-id="8cd3f-106">Você pode colocar `Stop` instruções em qualquer lugar em procedimentos para suspender a execução.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="8cd3f-107">O uso `Stop` da instrução é semelhante à definição de um ponto de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="8cd3f-108">A `Stop` instrução suspende a execução, mas, `End`ao contrário, não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrado em um arquivo executável compilado (. exe).</span><span class="sxs-lookup"><span data-stu-id="8cd3f-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8cd3f-109">Se a `Stop` instrução for encontrada no código que está sendo executado fora do IDE (ambiente de desenvolvimento integrado), o depurador será invocado.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="8cd3f-110">Isso é verdadeiro independentemente de o código ter sido compilado no modo de depuração ou de varejo.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cd3f-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cd3f-111">Example</span></span>  
 <span data-ttu-id="8cd3f-112">Este exemplo usa a `Stop` instrução para suspender a execução para cada iteração por meio do `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="8cd3f-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="8cd3f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cd3f-113">See also</span></span>

- [<span data-ttu-id="8cd3f-114">Instrução End</span><span class="sxs-lookup"><span data-stu-id="8cd3f-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
