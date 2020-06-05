---
title: A função '<procedurename>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: edb2195f4e83c2315aa929936aff8af88ca8556c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374129"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="5c5aa-102">A função '\<procedurename>' não retorna um valor em todos os caminhos de código</span><span class="sxs-lookup"><span data-stu-id="5c5aa-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="5c5aa-103">A função ' \<procedurename> ' não retorna um valor em todos os caminhos de código.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="5c5aa-104">Você está perdendo uma instrução ' Return '?</span><span class="sxs-lookup"><span data-stu-id="5c5aa-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="5c5aa-105">Um `Function` procedimento tem pelo menos um caminho possível por meio de seu código que não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="5c5aa-106">Você pode retornar um valor de um `Function` procedimento de qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5c5aa-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="5c5aa-107">Inclua o valor em uma [instrução return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5c5aa-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="5c5aa-108">Atribua o valor ao `Function` nome do procedimento e, em seguida, execute uma `Exit Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="5c5aa-109">Atribua o valor ao `Function` nome do procedimento e, em seguida, execute a `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="5c5aa-110">Se o controle passar para `Exit Function` ou `End Function` e você não tiver atribuído nenhum valor ao nome do procedimento, o procedimento retornará o valor padrão do tipo de dados de retorno.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="5c5aa-111">Para obter mais informações, consulte "Behavior" na [instrução function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5c5aa-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="5c5aa-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-112">By default, this message is a warning.</span></span> <span data-ttu-id="5c5aa-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c5aa-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5c5aa-114">**ID do erro:** BC42105</span><span class="sxs-lookup"><span data-stu-id="5c5aa-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c5aa-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5c5aa-115">To correct this error</span></span>  
  
- <span data-ttu-id="5c5aa-116">Verifique sua lógica de fluxo de controle e certifique-se de atribuir um valor antes de cada instrução que causa um retorno.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="5c5aa-117">É mais fácil garantir que cada retorno do procedimento retorne um valor se você sempre usar a `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="5c5aa-118">Se você fizer isso, a última instrução antes `End Function` deve ser uma `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c5aa-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5aa-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c5aa-119">See also</span></span>

- [<span data-ttu-id="5c5aa-120">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="5c5aa-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="5c5aa-121">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="5c5aa-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="5c5aa-122">Página de Compilação, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c5aa-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
