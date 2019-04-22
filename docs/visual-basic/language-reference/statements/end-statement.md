---
title: Instrução End (Visual Basic)
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
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832015"
---
# <a name="end-statement"></a><span data-ttu-id="8b7be-102">Instrução End</span><span class="sxs-lookup"><span data-stu-id="8b7be-102">End Statement</span></span>
<span data-ttu-id="8b7be-103">Finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8b7be-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b7be-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="8b7be-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b7be-105">Remarks</span></span>  
 <span data-ttu-id="8b7be-106">Você pode colocar o `End` instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro para parar a execução.</span><span class="sxs-lookup"><span data-stu-id="8b7be-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="8b7be-107">`End` Fecha todos os arquivos abertos com uma `Open` instrução e limpa todas as variáveis do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b7be-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="8b7be-108">O aplicativo é fechado assim que há outros programas que contenham referências a seus objetos e nenhum dos seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="8b7be-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b7be-109">O `End` instrução interrompe a execução de código abruptamente e não chama o `Dispose` ou `Finalize` método ou qualquer outro código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b7be-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="8b7be-110">Referências a objetos mantidas por outros programas serão invalidadas.</span><span class="sxs-lookup"><span data-stu-id="8b7be-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="8b7be-111">Se um `End` instrução é encontrada dentro de uma `Try` ou `Catch` bloco, o controle não passa para os respectivos `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="8b7be-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="8b7be-112">O `Stop` instrução suspende a execução, mas ao contrário `End`, não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).</span><span class="sxs-lookup"><span data-stu-id="8b7be-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="8b7be-113">Porque `End` encerra o aplicativo sem participação a qualquer recurso que pode ser aberto, você deve tentar encerrar corretamente antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="8b7be-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="8b7be-114">Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deve fechá-los antes de controle atinge a `End` instrução.</span><span class="sxs-lookup"><span data-stu-id="8b7be-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="8b7be-115">Você deve usar `End` com parcimônia e somente quando precisar parar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8b7be-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="8b7be-116">As maneiras normais usadas para encerrar um procedimento ([instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) e [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas o fecham, mas também fornecem o código de chamada a oportunidade de corretamente.</span><span class="sxs-lookup"><span data-stu-id="8b7be-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="8b7be-117">Um aplicativo de console, por exemplo, pode simplesmente `Return` do `Main` procedimento.</span><span class="sxs-lookup"><span data-stu-id="8b7be-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8b7be-118">O `End` instrução chama o <xref:System.Environment.Exit%2A> método da <xref:System.Environment> classe no <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="8b7be-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="8b7be-119"><xref:System.Environment.Exit%2A> exige que você tenha `UnmanagedCode` permissão.</span><span class="sxs-lookup"><span data-stu-id="8b7be-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="8b7be-120">Se você não fizer isso, um <xref:System.Security.SecurityException> erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="8b7be-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="8b7be-121">Quando seguido por uma palavra-chave adicional, [final \<palavra-chave > demonstrativo](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento apropriado ou bloco.</span><span class="sxs-lookup"><span data-stu-id="8b7be-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="8b7be-122">Por exemplo, `End Function` finaliza a definição de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="8b7be-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b7be-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b7be-123">Example</span></span>  
 <span data-ttu-id="8b7be-124">O exemplo a seguir usa o `End` instrução para finalizar a execução de código se o usuário solicitar.</span><span class="sxs-lookup"><span data-stu-id="8b7be-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="8b7be-125">Notas do desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="8b7be-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="8b7be-126">Não há suporte para essa instrução.</span><span class="sxs-lookup"><span data-stu-id="8b7be-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7be-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b7be-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="8b7be-128">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="8b7be-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="8b7be-129">End \<palavra-chave > demonstrativo</span><span class="sxs-lookup"><span data-stu-id="8b7be-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
