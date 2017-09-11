---
title: Mensagens de erro (Visual Basic)
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cbeca9d1b6971f8b3de112eb6a199b8bacbc1670
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="af043-102">Mensagens de erro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af043-102">Error Messages (Visual Basic)</span></span>
<span data-ttu-id="af043-103">Quando você escreve, compila ou executa um aplicativo do Visual Basic, os seguintes tipos de erros podem ocorrer:</span><span class="sxs-lookup"><span data-stu-id="af043-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1.  <span data-ttu-id="af043-104">Erros de tempo de design, que ocorrem quando você escreve um aplicativo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af043-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="af043-105">Erros em tempo de compilação, que ocorrem quando você compila um aplicativo no Visual Studio ou no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="af043-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3.  <span data-ttu-id="af043-106">Erros em tempo de execução, que ocorrem quando você executa um aplicativo no Visual Studio ou como um arquivo executável autônomo.</span><span class="sxs-lookup"><span data-stu-id="af043-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="af043-107">Para obter informações sobre como solucionar um erro específico, consulte [Recursos adicionais para programadores do Visual Basic](../../../visual-basic/getting-started/additional-resources.md).</span><span class="sxs-lookup"><span data-stu-id="af043-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="af043-108">Erros em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="af043-108">Run Time Errors</span></span>  
 <span data-ttu-id="af043-109">Se um aplicativo do Visual Basic tenta executar uma ação que o sistema não pode executar, ocorrerá um erro em tempo de execução, e [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] lançará um objeto `Exception`.</span><span class="sxs-lookup"><span data-stu-id="af043-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an `Exception` object.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="af043-110"> pode gerar erros personalizados de qualquer tipo de dados, incluindo objetos `Exception` usando a instrução `Throw`.</span><span class="sxs-lookup"><span data-stu-id="af043-110"> can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="af043-111">Um aplicativo pode identificar o erro exibindo o número do erro e a mensagem de uma exceção capturada.</span><span class="sxs-lookup"><span data-stu-id="af043-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="af043-112">Se não for detectado um erro, o aplicativo será encerrado.</span><span class="sxs-lookup"><span data-stu-id="af043-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="af043-113">O código pode interceptar e examine os erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af043-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="af043-114">Se você colocar o código que produz o erro em um bloco `Try`, você poderá capturar qualquer erro gerado em um bloco `Catch` correspondente.</span><span class="sxs-lookup"><span data-stu-id="af043-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="af043-115">Para obter informações sobre como interceptar erros em tempo de execução e responder a eles em seu código, consulte [Instrução Try... Catch... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="af043-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="af043-116">Erros no tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="af043-116">Compile Time Errors</span></span>  
 <span data-ttu-id="af043-117">Se o compilador do Visual Basic encontrar um problema no código, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="af043-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="af043-118">No Editor de Código, você pode identificar facilmente qual linha de código causou o erro, pois uma linha ondulada aparece sob essa linha de código.</span><span class="sxs-lookup"><span data-stu-id="af043-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="af043-119">A mensagem de erro será exibida se você apontar para a linha ondulada ou abrir a **Lista de Erros**, que também mostra outras mensagens.</span><span class="sxs-lookup"><span data-stu-id="af043-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="af043-120">Se um identificador tiver uma linha ondulada e um sublinhado curto exibidos abaixo do caractere mais à direita, você poderá gerar um stub para a classe, construtor, método, propriedade, campo ou enum.</span><span class="sxs-lookup"><span data-stu-id="af043-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="af043-121">Para obter mais informações, consulte [Gerar do uso](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span><span class="sxs-lookup"><span data-stu-id="af043-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="af043-122">Ao resolver os avisos do compilador do Visual Basic, você poderá escrever um código que é executado mais rápido e com menos erros.</span><span class="sxs-lookup"><span data-stu-id="af043-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="af043-123">Esses avisos identificam códigos que podem causar erros quando o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="af043-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="af043-124">Por exemplo, o compilador avisará se você tentar invocar um membro de uma variável de objeto não atribuída, retornar de uma função sem definir o valor retornado ou executar um bloco `Try` com erros na lógica para capturar exceções.</span><span class="sxs-lookup"><span data-stu-id="af043-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="af043-125">Para obter mais informações sobre avisos, incluindo como ativar e desativar, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="af043-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

