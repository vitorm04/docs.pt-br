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
ms.openlocfilehash: 66dba1df125a08b8ae05519a0c66edb6da15ceaa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583422"
---
# <a name="end-statement"></a><span data-ttu-id="2a658-102">Instrução End</span><span class="sxs-lookup"><span data-stu-id="2a658-102">End Statement</span></span>
<span data-ttu-id="2a658-103">Finaliza a execução imediatamente.</span><span class="sxs-lookup"><span data-stu-id="2a658-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a658-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a658-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a658-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a658-105">Remarks</span></span>  
 <span data-ttu-id="2a658-106">Você pode posicionar a instrução de `End` em qualquer lugar em um procedimento para forçar o aplicativo inteiro a parar de ser executado.</span><span class="sxs-lookup"><span data-stu-id="2a658-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="2a658-107">`End` fecha todos os arquivos abertos com uma instrução `Open` e limpa todas as variáveis do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2a658-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="2a658-108">O aplicativo é fechado assim que não há nenhum outro programa contendo referências a seus objetos e nenhum de seus códigos está em execução.</span><span class="sxs-lookup"><span data-stu-id="2a658-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a658-109">A instrução `End` interrompe a execução do código abruptamente e não invoca o `Dispose` ou o método `Finalize` ou qualquer outro código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a658-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="2a658-110">As referências de objeto mantidas por outros programas são invalidadas.</span><span class="sxs-lookup"><span data-stu-id="2a658-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="2a658-111">Se uma instrução `End` for encontrada em um bloco `Try` ou `Catch`, o controle não passará para o bloco de `Finally` correspondente.</span><span class="sxs-lookup"><span data-stu-id="2a658-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="2a658-112">A instrução `Stop` suspende a execução, mas ao contrário de `End`, ela não fecha nenhum arquivo ou limpa nenhuma variável, a menos que seja encontrada em um arquivo executável compilado (. exe).</span><span class="sxs-lookup"><span data-stu-id="2a658-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="2a658-113">Como `End` encerra seu aplicativo sem participar de recursos que possam estar abertos, você deve tentar fechar corretamente antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="2a658-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="2a658-114">Por exemplo, se seu aplicativo tiver qualquer formulário aberto, você deverá fechá-lo antes que o controle atinja a instrução de `End`.</span><span class="sxs-lookup"><span data-stu-id="2a658-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="2a658-115">Você deve usar `End` com moderação e somente quando precisar parar imediatamente.</span><span class="sxs-lookup"><span data-stu-id="2a658-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="2a658-116">As maneiras normais de encerrar um procedimento (instrução[Return](../../../visual-basic/language-reference/statements/return-statement.md) e [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) não apenas fecham o procedimento de forma limpa, mas também dão ao código de chamada a oportunidade de fechar corretamente.</span><span class="sxs-lookup"><span data-stu-id="2a658-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="2a658-117">Um aplicativo de console, por exemplo, pode simplesmente `Return` do procedimento `Main`.</span><span class="sxs-lookup"><span data-stu-id="2a658-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a658-118">A instrução `End` chama o método <xref:System.Environment.Exit%2A> da classe <xref:System.Environment> no namespace <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="2a658-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="2a658-119"><xref:System.Environment.Exit%2A> requer que você tenha a permissão `UnmanagedCode`.</span><span class="sxs-lookup"><span data-stu-id="2a658-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="2a658-120">Se você não fizer isso, ocorrerá um erro <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="2a658-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="2a658-121">Quando seguido por uma palavra-chave adicional, a [instrução End \<keyword >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineia o final da definição do procedimento ou bloco apropriado.</span><span class="sxs-lookup"><span data-stu-id="2a658-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="2a658-122">Por exemplo, `End Function` encerra a definição de um procedimento de `Function`.</span><span class="sxs-lookup"><span data-stu-id="2a658-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a658-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a658-123">Example</span></span>  
 <span data-ttu-id="2a658-124">O exemplo a seguir usa a instrução `End` para encerrar a execução de código se o usuário solicitá-la.</span><span class="sxs-lookup"><span data-stu-id="2a658-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="2a658-125">Notas para desenvolvedores de dispositivos inteligentes</span><span class="sxs-lookup"><span data-stu-id="2a658-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="2a658-126">Não há suporte para essa instrução.</span><span class="sxs-lookup"><span data-stu-id="2a658-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a658-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a658-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="2a658-128">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="2a658-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="2a658-129">Instrução End \<keyword ></span><span class="sxs-lookup"><span data-stu-id="2a658-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
