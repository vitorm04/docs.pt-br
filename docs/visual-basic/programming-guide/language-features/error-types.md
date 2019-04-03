---
title: Tipos de erro (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831560"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="c2e22-102">Tipos de erro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2e22-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="c2e22-103">No Visual Basic, erros (também chamado de *exceções*) se enquadram em uma das três categorias: erros de sintaxe, erros de tempo de execução e erros lógicos.</span><span class="sxs-lookup"><span data-stu-id="c2e22-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="c2e22-104">Erros de sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2e22-104">Syntax Errors</span></span>  
 <span data-ttu-id="c2e22-105">*Erros de sintaxe* são aqueles que aparecem enquanto você escreve código.</span><span class="sxs-lookup"><span data-stu-id="c2e22-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="c2e22-106">Visual Basic verifica seu código conforme você digita os **Editor de códigos** janela e o alerta se você cometer um erro, como digitar incorretamente uma palavra ou usar um elemento de linguagem incorretamente.</span><span class="sxs-lookup"><span data-stu-id="c2e22-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="c2e22-107">Erros de sintaxe são o tipo mais comum de erros.</span><span class="sxs-lookup"><span data-stu-id="c2e22-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="c2e22-108">Você pode corrigi-los facilmente no ambiente de codificação, assim que elas ocorrem.</span><span class="sxs-lookup"><span data-stu-id="c2e22-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2e22-109">O `Option Explicit` instrução é um meio de evitar erros de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="c2e22-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="c2e22-110">Isso força você a declara, com antecedência, todas as variáveis a ser usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2e22-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="c2e22-111">Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="c2e22-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="c2e22-112">Erros de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c2e22-112">Run-Time Errors</span></span>  
 <span data-ttu-id="c2e22-113">*Erros de tempo de execução* são aqueles que aparecem somente depois que você compilar e executar seu código.</span><span class="sxs-lookup"><span data-stu-id="c2e22-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="c2e22-114">Essas técnicas envolvem código que pode parecer estar correta, em que ela tem nenhum erro de sintaxe, mas que não será executado.</span><span class="sxs-lookup"><span data-stu-id="c2e22-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="c2e22-115">Por exemplo, você pode escrever uma linha de código para abrir um arquivo corretamente.</span><span class="sxs-lookup"><span data-stu-id="c2e22-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="c2e22-116">Mas se o arquivo estiver corrompido, o aplicativo não é possível executar o `Open` função e ele será interrompido.</span><span class="sxs-lookup"><span data-stu-id="c2e22-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="c2e22-117">Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código com defeito e, em seguida, recompilar e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="c2e22-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="c2e22-118">Erros de lógica</span><span class="sxs-lookup"><span data-stu-id="c2e22-118">Logic Errors</span></span>  
 <span data-ttu-id="c2e22-119">*Erros de lógica* são aqueles que aparecem depois que o aplicativo está em uso.</span><span class="sxs-lookup"><span data-stu-id="c2e22-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="c2e22-120">Eles são a maioria dos resultados de muitas vezes não desejados ou inesperados em resposta às ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="c2e22-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="c2e22-121">Por exemplo, uma chave digitada incorretamente ou outra fora da influência pode fazer com que seu aplicativo para parar de funcionar dentro dos parâmetros esperados, ou completamente.</span><span class="sxs-lookup"><span data-stu-id="c2e22-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="c2e22-122">Erros de lógica geralmente são o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.</span><span class="sxs-lookup"><span data-stu-id="c2e22-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e22-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2e22-123">See also</span></span>

- [<span data-ttu-id="c2e22-124">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="c2e22-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="c2e22-125">Noções básicas do depurador</span><span class="sxs-lookup"><span data-stu-id="c2e22-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
