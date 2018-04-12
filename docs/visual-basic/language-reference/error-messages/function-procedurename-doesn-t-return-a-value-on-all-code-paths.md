---
title: Função &#39; &lt;procedurename&gt;&#39; &#39; t retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="4a9d6-102">Função &#39; &lt;procedurename&gt;&#39; &#39; t retorna um valor em todos os caminhos de código</span><span class="sxs-lookup"><span data-stu-id="4a9d6-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="4a9d6-103">Função '\<procedurename >' não retorna um valor em todos os caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="4a9d6-104">Uma instrução 'Return' está faltando?</span><span class="sxs-lookup"><span data-stu-id="4a9d6-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="4a9d6-105">Um `Function` procedimento tem pelo menos um caminho possível pelo seu código que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="4a9d6-106">Você pode retornar um valor de uma `Function` procedimento em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="4a9d6-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="4a9d6-107">Incluir o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4a9d6-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="4a9d6-108">Atribuir o valor para o `Function` procedimento nome e, em seguida, executar um `Exit Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="4a9d6-109">Atribuir o valor para o `Function` procedimento nome e, em seguida, executar o `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="4a9d6-110">Se o controle passará para `Exit Function` ou `End Function` e você não tiver atribuído qualquer valor para o nome do procedimento, o procedimento retorna o valor padrão do tipo de dados de retorno.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="4a9d6-111">Para obter mais informações, consulte "Comportamento" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4a9d6-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="4a9d6-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-112">By default, this message is a warning.</span></span> <span data-ttu-id="4a9d6-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4a9d6-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4a9d6-114">**ID do erro:** BC42105</span><span class="sxs-lookup"><span data-stu-id="4a9d6-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a9d6-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4a9d6-115">To correct this error</span></span>  
  
-   <span data-ttu-id="4a9d6-116">Verifique sua lógica de fluxo de controle e verifique se que você atribuir um valor antes de cada instrução que produz um retorno.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="4a9d6-117">É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar sempre o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="4a9d6-118">Se você fizer isso, a última instrução antes de `End Function` deve ser um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4a9d6-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9d6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a9d6-119">See Also</span></span>  
 [<span data-ttu-id="4a9d6-120">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="4a9d6-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="4a9d6-121">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="4a9d6-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="4a9d6-122">Página de Compilação, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a9d6-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
