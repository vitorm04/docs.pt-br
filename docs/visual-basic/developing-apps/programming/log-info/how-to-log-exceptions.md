---
title: "Como registrar em log as exceções no Visual Basic"
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
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: adf2dc683a139d21f24379efc779d4510a2057eb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="cc031-102">Como registrar em log as exceções no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc031-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="cc031-103">É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre exceções que ocorrem em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc031-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="cc031-104">Esses exemplos mostram como usar o método `My.Application.Log.WriteException` para registrar em log exceções capturadas explicitamente e exceções sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="cc031-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="cc031-105">Para registrar informações de rastreamento de registros em log, use o método `My.Application.Log.WriteEntry`.</span><span class="sxs-lookup"><span data-stu-id="cc031-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="cc031-106">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc031-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="cc031-107">Registrar em log uma exceção manipulada</span><span class="sxs-lookup"><span data-stu-id="cc031-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="cc031-108">Crie o método que gerará as informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="cc031-108">Create the method that will generate the exception information.</span></span>  
  
     <span data-ttu-id="cc031-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span></span>  
  
2.  <span data-ttu-id="cc031-110">Use um bloco `Try...Catch` para capturar a exceção.</span><span class="sxs-lookup"><span data-stu-id="cc031-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     <span data-ttu-id="cc031-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span></span>  
  
3.  <span data-ttu-id="cc031-112">Coloque o código que poderá gerar uma exceção no bloco `Try`.</span><span class="sxs-lookup"><span data-stu-id="cc031-112">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="cc031-113">Remova a marca de comentário das linhas `Dim` e `MsgBox` para lançar uma exceção <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="cc031-113">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     <span data-ttu-id="cc031-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span></span>  
  
4.  <span data-ttu-id="cc031-115">No bloco `Catch`, use o método `My.Application.Log.WriteException` para gravar as informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="cc031-115">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     <span data-ttu-id="cc031-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span></span>  
  
     <span data-ttu-id="cc031-117">O exemplo a seguir mostra o código completo para registrar em log uma exceção manipulada.</span><span class="sxs-lookup"><span data-stu-id="cc031-117">The following example shows the complete code for logging a handled exception.</span></span>  
  
     <span data-ttu-id="cc031-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span></span>  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="cc031-119">Registrar em log uma exceção sem tratamento</span><span class="sxs-lookup"><span data-stu-id="cc031-119">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="cc031-120">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="cc031-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cc031-121">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="cc031-121">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="cc031-122">Clique na guia **Aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="cc031-122">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="cc031-123">Clique no botão **Exibir Eventos de Aplicativo** para abrir o Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="cc031-123">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="cc031-124">Isso abrirá o arquivo ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="cc031-124">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="cc031-125">Abra o arquivo ApplicationEvents.vb no Editor de Códigos.</span><span class="sxs-lookup"><span data-stu-id="cc031-125">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="cc031-126">No menu **Geral**, escolha **Eventos MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="cc031-126">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="cc031-127">No menu **Declarações**, escolha **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="cc031-127">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="cc031-128">A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> antes da execução do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="cc031-128">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="cc031-129">Adicione o método `My.Application.Log.WriteException` ao manipulador de eventos `UnhandledException`.</span><span class="sxs-lookup"><span data-stu-id="cc031-129">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     <span data-ttu-id="cc031-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span></span>  
  
     <span data-ttu-id="cc031-131">O exemplo a seguir mostra o código completo para registrar em log uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="cc031-131">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     <span data-ttu-id="cc031-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc031-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc031-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc031-133">See Also</span></span>  
 <span data-ttu-id="cc031-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cc031-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="cc031-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="cc031-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="cc031-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="cc031-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="cc031-137">[Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="cc031-137">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="cc031-138">[Como Gravar Mensagens de Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="cc031-138">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="cc031-139">[Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="cc031-139">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="cc031-140">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="cc031-140">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

