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
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944461"
---
# <a name="end-statement"></a><span data-ttu-id="9fa8f-102">Instrução End</span><span class="sxs-lookup"><span data-stu-id="9fa8f-102">End Statement</span></span>
<span data-ttu-id="9fa8f-103">Finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa8f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fa8f-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="9fa8f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fa8f-105">Remarks</span></span>  
 <span data-ttu-id="9fa8f-106">Você pode posicionar `End` a instrução em qualquer lugar em um procedimento para forçar o aplicativo inteiro a parar de ser executado.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="9fa8f-107">`End`Fecha todos os arquivos abertos com `Open` uma instrução e limpa todas as variáveis do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="9fa8f-108">O aplicativo é fechado assim que não há nenhum outro programa contendo referências a seus objetos e nenhum de seus códigos está em execução.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fa8f-109">A `End` instrução interrompe a execução do código abruptamente e não invoca o `Dispose` método `Finalize` ou ou qualquer outro código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="9fa8f-110">As referências de objeto mantidas por outros programas são invalidadas.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="9fa8f-111">Se uma `End` instrução for encontrada dentro de `Try` um `Catch` bloco ou, o controle não passará para `Finally` o bloco correspondente.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="9fa8f-112">A `Stop` instrução suspende a execução, mas, `End`ao contrário, não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrado em um arquivo executável compilado (. exe).</span><span class="sxs-lookup"><span data-stu-id="9fa8f-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="9fa8f-113">Como `End` o encerra o aplicativo sem participar de recursos que possam estar abertos, você deve tentar fechar corretamente antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="9fa8f-114">Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deverá fechá-lo antes que o `End` controle atinja a instrução.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="9fa8f-115">Você deve usar `End` com moderação e somente quando precisar parar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="9fa8f-116">As maneiras normais de encerrar um procedimento (instrução[Return](../../../visual-basic/language-reference/statements/return-statement.md) e [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas fecham o procedimento de forma limpa, mas também dão ao código de chamada a oportunidade de fechar corretamente.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="9fa8f-117">Um aplicativo de console, por exemplo, pode `Return` simplesmente `Main` do procedimento.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9fa8f-118">A `End` instrução chama o <xref:System.Environment.Exit%2A> <xref:System.Environment> método<xref:System> da classe no namespace.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="9fa8f-119"><xref:System.Environment.Exit%2A>exige que você tenha `UnmanagedCode` permissão.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="9fa8f-120">Se você não fizer isso, <xref:System.Security.SecurityException> ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="9fa8f-121">Quando seguido por uma palavra-chave adicional, a [instrução End \<keyword >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento ou bloco apropriado.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="9fa8f-122">Por exemplo, `End Function` encerra a definição de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fa8f-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fa8f-123">Example</span></span>  
 <span data-ttu-id="9fa8f-124">O exemplo a seguir usa `End` a instrução para encerrar a execução de código se o usuário solicitá-la.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="9fa8f-125">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="9fa8f-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="9fa8f-126">Não há suporte para essa instrução.</span><span class="sxs-lookup"><span data-stu-id="9fa8f-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa8f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa8f-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="9fa8f-128">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="9fa8f-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="9fa8f-129">Instrução \<de > de palavra-chave end</span><span class="sxs-lookup"><span data-stu-id="9fa8f-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
