---
title: "Instrução Stop (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Stop
dev_langs:
- VB
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements, syntax
- Stop statements
- execution, suspending
- processing, interrupting
- processes, interrupting
- execution, stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
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
ms.openlocfilehash: 823b8f1461b09b1a9a4eeda461705dedff54ffb9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="c9766-102">Instrução Stop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9766-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="c9766-103">Suspende a execução.</span><span class="sxs-lookup"><span data-stu-id="c9766-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9766-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9766-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="c9766-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9766-105">Remarks</span></span>  
 <span data-ttu-id="c9766-106">Você pode colocar `Stop` instruções em qualquer lugar nos procedimentos para suspender a execução.</span><span class="sxs-lookup"><span data-stu-id="c9766-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="c9766-107">Usando o `Stop` instrução é semelhante à configuração de um ponto de interrupção no código.</span><span class="sxs-lookup"><span data-stu-id="c9766-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="c9766-108">O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).</span><span class="sxs-lookup"><span data-stu-id="c9766-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9766-109">Se o `Stop` declaração é encontrada no código que está em execução fora do ambiente de desenvolvimento integrado (IDE), o depurador é invocado.</span><span class="sxs-lookup"><span data-stu-id="c9766-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="c9766-110">Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.</span><span class="sxs-lookup"><span data-stu-id="c9766-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9766-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9766-111">Example</span></span>  
 <span data-ttu-id="c9766-112">Este exemplo usa o `Stop` instrução para suspender a execução de cada iteração por meio de `For...Next` loop.</span><span class="sxs-lookup"><span data-stu-id="c9766-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 <span data-ttu-id="c9766-113">[!code-vb[56 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c9766-113">[!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9766-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9766-114">See Also</span></span>  
 [<span data-ttu-id="c9766-115">Instrução End</span><span class="sxs-lookup"><span data-stu-id="c9766-115">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
