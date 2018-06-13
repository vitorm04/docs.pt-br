---
title: 'Solucionando problemas: ouvintes de log (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 54c3ed0f607edf992fa3c40a8e6214252740587c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589027"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="60189-102">Solucionando problemas: ouvintes de log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60189-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="60189-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60189-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="60189-104">Para determinar quais ouvintes de log recebem essas mensagens, consulte [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="60189-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="60189-105">O objeto `Log` pode usar filtragem de log para limitar a quantidade de informações que ele registra no log.</span><span class="sxs-lookup"><span data-stu-id="60189-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="60189-106">Se os filtros tiverem sido configurados incorretamente, os logs poderão conter informações incorretas.</span><span class="sxs-lookup"><span data-stu-id="60189-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="60189-107">Para obter informações sobre filtragem, consulte [Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="60189-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="60189-108">No entanto, se um log tiver sido configurado incorretamente, talvez seja necessário obter mais informações sobre sua configuração atual.</span><span class="sxs-lookup"><span data-stu-id="60189-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="60189-109">É possível obter essas informações por meio da propriedade `TraceSource` avançada do log.</span><span class="sxs-lookup"><span data-stu-id="60189-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="60189-110">Para determinar os ouvintes de log do objeto Log no código</span><span class="sxs-lookup"><span data-stu-id="60189-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="60189-111">Importe o namespace <xref:System.Diagnostics> no início do arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="60189-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="60189-112">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="60189-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="60189-113">Crie uma função que retorna uma cadeia de caracteres que consiste de informações para cada um dos ouvintes de log.</span><span class="sxs-lookup"><span data-stu-id="60189-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="60189-114">Passe a coleção dos ouvintes de rastreamento do log para a função `GetListeners` e exiba o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="60189-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="60189-115">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="60189-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60189-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60189-116">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="60189-117">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="60189-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="60189-118">Instruções passo a passo: determinando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="60189-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
