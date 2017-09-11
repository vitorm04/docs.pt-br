---
title: "Como: chamar um procedimento que não retorna um valor (Visual Basic) | Documentos do Microsoft"
ms.custom: 
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 26120b763d2ecedb3aa43adb08e4c87c2b1e0be1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="9a8ae-102">Como chamar um procedimento que não retorne um valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a8ae-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="9a8ae-103">Um `Sub` procedimento não retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="9a8ae-104">Você chamá-lo explicitamente com uma instrução de chamada autônoma.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="9a8ae-105">Você não pode chamá-lo simplesmente usando seu nome dentro de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="9a8ae-106">Para chamar um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="9a8ae-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="9a8ae-107">Especifique o nome do `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="9a8ae-108">Siga o nome do procedimento com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="9a8ae-109">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="9a8ae-110">No entanto, usar os parênteses torna seu código mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="9a8ae-111">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="9a8ae-112">Certifique-se de fornecer os argumentos na mesma ordem que a `Sub` procedimento define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="9a8ae-113">A exemplo a seguir chama o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>função para ativar uma janela de aplicativo.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="9a8ae-113">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="9a8ae-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>leva o título da janela como seu único argumento.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="9a8ae-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="9a8ae-115">Ele não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="9a8ae-116">Se um processo do bloco de notas não estiver em execução, o exemplo gera um <xref:System.ArgumentException>.</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="9a8ae-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="9a8ae-117">O `Shell` procedimento pressupõe que os aplicativos estão nos caminhos especificados.</span><span class="sxs-lookup"><span data-stu-id="9a8ae-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     <span data-ttu-id="9a8ae-118">[!code-vb[VbVbalrCatRef n º&11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9a8ae-118">[!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8ae-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a8ae-119">See Also</span></span>  
 <span data-ttu-id="9a8ae-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A></span><span class="sxs-lookup"><span data-stu-id="9a8ae-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></span></span>   
 <span data-ttu-id="9a8ae-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="9a8ae-121"><xref:System.ArgumentException></span></span>   
<span data-ttu-id="9a8ae-122"> [Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-122"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="9a8ae-123"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-123"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="9a8ae-124"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-124"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9a8ae-125"> [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-125"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="9a8ae-126"> [Como: criar um procedimento](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-126"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="9a8ae-127"> [Como: chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="9a8ae-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="9a8ae-128"> [Como: chamar um manipulador de eventos no Visual Basic](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="9a8ae-128"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
