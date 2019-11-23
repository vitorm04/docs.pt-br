---
title: Como gravar mensagens de log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352064"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="afc13-102">Como gravar mensagens de log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afc13-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="afc13-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="afc13-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="afc13-104">Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` para registrar em log informações de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="afc13-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="afc13-105">Para registrar informações de exceção em log, use o método `My.Application.Log.WriteException`; consulte [How to: Log Exceptions (Como registrar em log as exceções)](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="afc13-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="afc13-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afc13-106">Example</span></span>

<span data-ttu-id="afc13-107">Este exemplo usa o método `My.Application.Log.WriteEntry` para gravar as informações de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="afc13-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="afc13-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="afc13-108">.NET Framework Security</span></span>

<span data-ttu-id="afc13-109">Certifique-se de que os dados gravados no log não incluem informações confidenciais como senhas de usuário.</span><span class="sxs-lookup"><span data-stu-id="afc13-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="afc13-110">Para obter mais informações, consulte [Working with Application Logs (Trabalhando com logs de aplicativo)](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="afc13-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="afc13-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afc13-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="afc13-112">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="afc13-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="afc13-113">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="afc13-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="afc13-114">Instruções passo a passo: determinando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="afc13-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="afc13-115">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="afc13-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="afc13-116">Instruções passo a passo: filtrando a saída de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="afc13-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
