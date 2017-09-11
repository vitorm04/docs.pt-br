---
title: Tipos de erros (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
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
ms.openlocfilehash: 51cf5820e79ff9467357619d4f5b067bc4168bfb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="error-types-visual-basic"></a><span data-ttu-id="dd757-102">Tipos de erro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd757-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="dd757-103">Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], erros (também chamado de *exceções*) se enquadram em uma das três categorias: erros de sintaxe, erros de tempo de execução e erros lógicos.</span><span class="sxs-lookup"><span data-stu-id="dd757-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="dd757-104">Erros de sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd757-104">Syntax Errors</span></span>  
 <span data-ttu-id="dd757-105">*Erros de sintaxe* são aqueles que aparecem enquanto você escreve código.</span><span class="sxs-lookup"><span data-stu-id="dd757-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="dd757-106">verifica seu código conforme você digita no **Editor de códigos** janela e avisará se cometer um erro, como digitar incorretamente uma palavra ou usar um elemento de linguagem incorretamente.</span><span class="sxs-lookup"><span data-stu-id="dd757-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="dd757-107">Erros de sintaxe são o tipo mais comum de erros.</span><span class="sxs-lookup"><span data-stu-id="dd757-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="dd757-108">Você pode corrigi-los facilmente no ambiente de codificação assim que eles ocorrem.</span><span class="sxs-lookup"><span data-stu-id="dd757-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd757-109">O `Option Explicit` instrução é um meio de evitar erros de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="dd757-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="dd757-110">Força a declare, com antecedência, todas as variáveis a ser usado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dd757-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="dd757-111">Portanto, quando essas variáveis são usadas no código, qualquer erro tipográfico é detectado imediatamente e pode ser corrigido.</span><span class="sxs-lookup"><span data-stu-id="dd757-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="dd757-112">Erros de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dd757-112">Run-Time Errors</span></span>  
 <span data-ttu-id="dd757-113">*Erros de tempo de execução* são aqueles que aparecem somente após você compilar e executar seu código.</span><span class="sxs-lookup"><span data-stu-id="dd757-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="dd757-114">Essas técnicas envolvem código que pode parecer estar correta, pois ela tem nenhum erro de sintaxe, mas que não será executado.</span><span class="sxs-lookup"><span data-stu-id="dd757-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="dd757-115">Por exemplo, você pode escrever corretamente uma linha de código para abrir um arquivo.</span><span class="sxs-lookup"><span data-stu-id="dd757-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="dd757-116">Mas se o arquivo estiver corrompido, o aplicativo não pode executar o `Open` função e ele deixará de ser executado.</span><span class="sxs-lookup"><span data-stu-id="dd757-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="dd757-117">Você pode corrigir a maioria dos erros de tempo de execução por reescrever o código defeituoso, recompilar e executá-lo novamente.</span><span class="sxs-lookup"><span data-stu-id="dd757-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="dd757-118">Erros de lógica</span><span class="sxs-lookup"><span data-stu-id="dd757-118">Logic Errors</span></span>  
 <span data-ttu-id="dd757-119">*Erros de lógica* são aqueles que aparecem depois que o aplicativo estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="dd757-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="dd757-120">Eles são mais resultados geralmente não desejados ou inesperados em resposta às ações do usuário.</span><span class="sxs-lookup"><span data-stu-id="dd757-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="dd757-121">Por exemplo, uma chave digitada incorretamente ou outra fora da influência pode fazer com que seu aplicativo pare de funcionar dentro dos parâmetros esperados, ou completamente.</span><span class="sxs-lookup"><span data-stu-id="dd757-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="dd757-122">Erros lógicos são geralmente o tipo mais difícil para corrigir, pois não é sempre claro onde eles se originam.</span><span class="sxs-lookup"><span data-stu-id="dd757-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd757-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd757-123">See Also</span></span>  
 <span data-ttu-id="dd757-124">[Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dd757-124">[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="dd757-125"> [Noções básicas do depurador](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span><span class="sxs-lookup"><span data-stu-id="dd757-125"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)</span></span>
