---
title: Instrução End
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604415"
---
# <a name="end-statement"></a><span data-ttu-id="3b189-102">Instrução End</span><span class="sxs-lookup"><span data-stu-id="3b189-102">End Statement</span></span>
<span data-ttu-id="3b189-103">Finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="3b189-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b189-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b189-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b189-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b189-105">Remarks</span></span>  
 <span data-ttu-id="3b189-106">Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para interromper a execução.</span><span class="sxs-lookup"><span data-stu-id="3b189-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="3b189-107">`End` Fecha todos os arquivos abertos com um `Open` instrução e limpa todas as variáveis do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b189-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="3b189-108">O aplicativo fecha assim que existem em outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="3b189-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b189-109">O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b189-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="3b189-110">Referências a objetos mantidas por outros programas são invalidadas.</span><span class="sxs-lookup"><span data-stu-id="3b189-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="3b189-111">Se um `End` instrução for encontrada dentro de um `Try` ou `Catch` bloco, o controle passará para o correspondente `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="3b189-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="3b189-112">O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).</span><span class="sxs-lookup"><span data-stu-id="3b189-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="3b189-113">Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="3b189-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="3b189-114">Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atingir o `End` instrução.</span><span class="sxs-lookup"><span data-stu-id="3b189-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="3b189-115">Você deve usar `End` com moderação e somente quando você precisa parar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="3b189-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="3b189-116">As maneiras normais para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente.</span><span class="sxs-lookup"><span data-stu-id="3b189-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="3b189-117">Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3b189-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b189-118">O `End` chamadas de instrução o <xref:System.Environment.Exit%2A> método o <xref:System.Environment> classe no <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="3b189-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="3b189-119"><xref:System.Environment.Exit%2A> requer que você tenha `UnmanagedCode` permissão.</span><span class="sxs-lookup"><span data-stu-id="3b189-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="3b189-120">Se você não fizer isso, um <xref:System.Security.SecurityException> erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="3b189-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="3b189-121">Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco.</span><span class="sxs-lookup"><span data-stu-id="3b189-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="3b189-122">Por exemplo, `End Function` finaliza a definição de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3b189-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b189-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b189-123">Example</span></span>  
 <span data-ttu-id="3b189-124">O exemplo a seguir usa o `End` instrução para finalizar a execução de código se o usuário solicitar.</span><span class="sxs-lookup"><span data-stu-id="3b189-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="3b189-125">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="3b189-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="3b189-126">Não há suporte para essa instrução.</span><span class="sxs-lookup"><span data-stu-id="3b189-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b189-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b189-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="3b189-128">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="3b189-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="3b189-129">Final \<palavra-chave > instrução</span><span class="sxs-lookup"><span data-stu-id="3b189-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
