---
title: 'Como: Registrar mensagens em log quando o aplicativo é iniciado ou desligado (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 40236a1ab5daea0003fce0ad6e35e258a42cc405
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973919"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="9aea3-102">Como: Registrar mensagens em log quando o aplicativo é iniciado ou desligado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aea3-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="9aea3-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9aea3-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="9aea3-104">Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` com os eventos `Startup` e `Shutdown` para gravar informações de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9aea3-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="9aea3-105">Para acessar o código do manipulador de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9aea3-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="9aea3-106">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9aea3-107">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="9aea3-108">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="9aea3-109">Clique no botão **Exibir Eventos de Aplicativo** para abrir o Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="9aea3-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="9aea3-110">Isso abrirá o arquivo ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="9aea3-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="9aea3-111">Para registrar mensagens em log quando o aplicativo é iniciado</span><span class="sxs-lookup"><span data-stu-id="9aea3-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="9aea3-112">Abra o arquivo ApplicationEvents.vb no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="9aea3-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="9aea3-113">No menu **Geral**, escolha **Eventos MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="9aea3-114">No menu **Declarações**, escolha **Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="9aea3-115">A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> antes da execução do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="9aea3-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="9aea3-116">Adicione o método `My.Application.Log.WriteEntry` ao manipulador de eventos `Startup`.</span><span class="sxs-lookup"><span data-stu-id="9aea3-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="9aea3-117">Para registrar mensagens em log quando o aplicativo é desligado</span><span class="sxs-lookup"><span data-stu-id="9aea3-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="9aea3-118">Abra o arquivo ApplicationEvents.vb no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="9aea3-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="9aea3-119">No menu **Geral**, escolha **Eventos MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="9aea3-120">No menu **Declarações**, escolha **Desligamento**.</span><span class="sxs-lookup"><span data-stu-id="9aea3-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="9aea3-121">A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> após a execução do aplicativo principal, mas antes de desligar.</span><span class="sxs-lookup"><span data-stu-id="9aea3-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="9aea3-122">Adicione o método `My.Application.Log.WriteEntry` ao manipulador de eventos `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="9aea3-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="9aea3-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9aea3-123">Example</span></span>  
 <span data-ttu-id="9aea3-124">Você pode usar o **Designer de Projeto** para acessar os eventos do aplicativo no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="9aea3-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="9aea3-125">Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9aea3-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9aea3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aea3-126">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="9aea3-127">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aea3-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="9aea3-128">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="9aea3-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
