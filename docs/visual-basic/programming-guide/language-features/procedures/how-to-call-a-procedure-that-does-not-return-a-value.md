---
title: Como chamar um procedimento que não retorne um valor (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649042"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="11d64-102">Como chamar um procedimento que não retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11d64-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="11d64-103">Um `Sub` procedimento não retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="11d64-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="11d64-104">Você chamá-lo explicitamente com uma instrução de chamada autônoma.</span><span class="sxs-lookup"><span data-stu-id="11d64-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="11d64-105">Você não pode chamá-lo simplesmente usando seu nome dentro de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="11d64-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="11d64-106">Para chamar um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="11d64-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="11d64-107">Especifique o nome do `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="11d64-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="11d64-108">Siga o nome do procedimento com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="11d64-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="11d64-109">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="11d64-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="11d64-110">No entanto, usar os parênteses faz seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="11d64-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="11d64-111">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="11d64-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="11d64-112">Certifique-se de fornecer os argumentos na mesma ordem que a `Sub` procedimento define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="11d64-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="11d64-113">O exemplo a seguir chama o Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> função para ativar uma janela de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d64-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="11d64-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> usa o título da janela como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="11d64-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="11d64-115">Ele não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="11d64-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="11d64-116">Se um processo do bloco de notas não está em execução, o exemplo gera um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="11d64-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="11d64-117">O `Shell` procedimento pressupõe que os aplicativos estão nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="11d64-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="11d64-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11d64-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="11d64-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="11d64-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="11d64-120">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="11d64-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="11d64-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="11d64-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="11d64-122">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="11d64-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="11d64-123">Como criar um procedimento</span><span class="sxs-lookup"><span data-stu-id="11d64-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="11d64-124">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="11d64-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="11d64-125">Como: chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11d64-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
