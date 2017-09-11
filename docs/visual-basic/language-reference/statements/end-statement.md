---
title: "Fim de instrução | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.End
- End
dev_langs:
- VB
helpviewer_keywords:
- execution, ending
- files, closing
- End keyword, End statements
- programs, quitting
- code, exiting
- program termination
- End statement
- execution, stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93907108fe5a0905b7b2698a354229fce810a2da
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="end-statement"></a><span data-ttu-id="321d5-102">Instrução End</span><span class="sxs-lookup"><span data-stu-id="321d5-102">End Statement</span></span>
<span data-ttu-id="321d5-103">Finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="321d5-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="321d5-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="321d5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="321d5-105">Remarks</span></span>  
 <span data-ttu-id="321d5-106">Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para parar a execução.</span><span class="sxs-lookup"><span data-stu-id="321d5-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="321d5-107">`End`Fecha todos os arquivos abertos com uma `Open` instrução e limpa todas as variáveis do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="321d5-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="321d5-108">O aplicativo fecha assim que há outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="321d5-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="321d5-109">O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="321d5-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="321d5-110">Referências a objetos mantidas por outros programas são invalidadas.</span><span class="sxs-lookup"><span data-stu-id="321d5-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="321d5-111">Se um `End` declaração for encontrada dentro de uma `Try` ou `Catch` bloco de controle não passa para o correspondente `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="321d5-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="321d5-112">O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).</span><span class="sxs-lookup"><span data-stu-id="321d5-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="321d5-113">Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="321d5-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="321d5-114">Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atinge o `End` instrução.</span><span class="sxs-lookup"><span data-stu-id="321d5-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="321d5-115">Você deve usar `End` com parcimônia e somente quando você precisa parar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="321d5-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="321d5-116">As maneiras normais para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente.</span><span class="sxs-lookup"><span data-stu-id="321d5-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="321d5-117">Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="321d5-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="321d5-118">O `End` instrução chama o <xref:System.Environment.Exit%2A>método do <xref:System.Environment>classe o <xref:System>namespace.</xref:System> </xref:System.Environment> </xref:System.Environment.Exit%2A></span><span class="sxs-lookup"><span data-stu-id="321d5-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="321d5-119"><xref:System.Environment.Exit%2A>requer que você tenha `UnmanagedCode` permissão.</xref:System.Environment.Exit%2A></span><span class="sxs-lookup"><span data-stu-id="321d5-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="321d5-120">Se não, uma <xref:System.Security.SecurityException>ocorre erro.</xref:System.Security.SecurityException></span><span class="sxs-lookup"><span data-stu-id="321d5-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="321d5-121">Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco.</span><span class="sxs-lookup"><span data-stu-id="321d5-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="321d5-122">Por exemplo, `End Function` finaliza a definição de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="321d5-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="321d5-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="321d5-123">Example</span></span>  
 <span data-ttu-id="321d5-124">O exemplo a seguir usa o `End` instrução para encerrar a execução de código se o usuário solicitar.</span><span class="sxs-lookup"><span data-stu-id="321d5-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 <span data-ttu-id="321d5-125">[!code-vb[VbVersHelp60Controls&#64;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="321d5-125">[!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="321d5-126">Anotações de desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="321d5-126">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="321d5-127">Não há suporte para essa instrução.</span><span class="sxs-lookup"><span data-stu-id="321d5-127">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321d5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="321d5-128">See Also</span></span>  
 <span data-ttu-id="321d5-129"><xref:System.Security.Permissions.SecurityPermissionFlag></xref:System.Security.Permissions.SecurityPermissionFlag></span><span class="sxs-lookup"><span data-stu-id="321d5-129"><xref:System.Security.Permissions.SecurityPermissionFlag></span></span>   
<span data-ttu-id="321d5-130"> [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md) </span><span class="sxs-lookup"><span data-stu-id="321d5-130"> [Stop Statement](../../../visual-basic/language-reference/statements/stop-statement.md) </span></span>  
<span data-ttu-id="321d5-131"> [End \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md)</span><span class="sxs-lookup"><span data-stu-id="321d5-131"> [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)</span></span>
