---
title: Como chamar um procedimento que não retorne um valor
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 3a5de98c6edf795a11bd9f0465aa6919f09eebfa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340955"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="10efc-102">Como chamar um procedimento que não retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10efc-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="10efc-103">Um procedimento de `Sub` não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="10efc-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="10efc-104">Você o chama explicitamente com uma instrução de chamada autônoma.</span><span class="sxs-lookup"><span data-stu-id="10efc-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="10efc-105">Você não pode chamá-lo simplesmente usando seu nome dentro de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="10efc-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="10efc-106">Para chamar um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="10efc-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="10efc-107">Especifique o nome do procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="10efc-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="10efc-108">Siga o nome do procedimento com parênteses para colocar a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="10efc-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="10efc-109">Se não houver argumentos, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="10efc-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="10efc-110">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="10efc-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="10efc-111">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="10efc-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="10efc-112">Certifique-se de fornecer os argumentos na mesma ordem em que o procedimento de `Sub` define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="10efc-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="10efc-113">O exemplo a seguir chama a função Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> para ativar uma janela do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="10efc-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="10efc-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> usa o título da janela como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="10efc-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="10efc-115">Ele não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="10efc-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="10efc-116">Se um processo do bloco de notas não estiver em execução, o exemplo lançará um <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="10efc-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="10efc-117">O procedimento `Shell` pressupõe que os aplicativos estão nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="10efc-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="10efc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10efc-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="10efc-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="10efc-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="10efc-120">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="10efc-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="10efc-121">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="10efc-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="10efc-122">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="10efc-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="10efc-123">Como criar um procedimento</span><span class="sxs-lookup"><span data-stu-id="10efc-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="10efc-124">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="10efc-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="10efc-125">Como: chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10efc-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
