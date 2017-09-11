---
title: "Registrando informações em log a partir do aplicativo (Visual Basic)"
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
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
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
ms.openlocfilehash: 58f21df20425b0164586143ad5af6f363a90c3ef
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="d2ebc-102">Registrando informações em log a partir do aplicativo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2ebc-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="d2ebc-103">Esta seção contém tópicos que abordam como registrar informações em log do aplicativo usando os objetos `My.Application.Log` ou `My.Log` e como estender os recursos de registro em log do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="d2ebc-104">O objeto `Log` fornece métodos para gravar informações nos ouvintes de log do aplicativo e a propriedade avançada `TraceSource` do objeto `Log` fornece informações detalhadas de configuração.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="d2ebc-105">O objeto `Log` será configurado pelo arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="d2ebc-106">O objeto `My.Log` está disponível somente para aplicativos do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="d2ebc-107">Para aplicativos cliente, use `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="d2ebc-108">Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d2ebc-109">Tarefas</span><span class="sxs-lookup"><span data-stu-id="d2ebc-109">Tasks</span></span>  
  
|<span data-ttu-id="d2ebc-110">Para</span><span class="sxs-lookup"><span data-stu-id="d2ebc-110">To</span></span>|<span data-ttu-id="d2ebc-111">Consulte</span><span class="sxs-lookup"><span data-stu-id="d2ebc-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="d2ebc-112">Gravar informações de evento em logs do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="d2ebc-113">Como gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="d2ebc-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="d2ebc-114">Gravar informações de exceção em logs do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="d2ebc-115">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="d2ebc-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="d2ebc-116">Gravar informações de rastreamento em logs do aplicativo quando o aplicativo for inicializado e desligado.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="d2ebc-117">Como registrar mensagens em log quando o aplicativo é iniciado ou encerrado</span><span class="sxs-lookup"><span data-stu-id="d2ebc-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="d2ebc-118">Configure `My.Application.Log` para gravar informações em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="d2ebc-119">Como gravar informações de evento em um arquivo de texto</span><span class="sxs-lookup"><span data-stu-id="d2ebc-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="d2ebc-120">Configure `My.Application.Log` para gravar informações em um log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="d2ebc-121">Como gravar em um log de eventos do aplicativo</span><span class="sxs-lookup"><span data-stu-id="d2ebc-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="d2ebc-122">Altere o local em que `My.Application.Log` grava as informações.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="d2ebc-123">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="d2ebc-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="d2ebc-124">Determine o local em que `My.Application.Log` grava as informações.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="d2ebc-125">Instruções passo a passo: determinando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="d2ebc-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="d2ebc-126">Crie um ouvinte de log personalizado para `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="d2ebc-127">Instruções passo a passo: criando ouvintes de log personalizados</span><span class="sxs-lookup"><span data-stu-id="d2ebc-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="d2ebc-128">Filtre a saída dos logs `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="d2ebc-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="d2ebc-129">Instruções passo a passo: filtrando a saída de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="d2ebc-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="d2ebc-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2ebc-130">See Also</span></span>  
 <span data-ttu-id="d2ebc-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d2ebc-131"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="d2ebc-132">[Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="d2ebc-132">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 [<span data-ttu-id="d2ebc-133">Solução de problemas: ouvintes de Log</span><span class="sxs-lookup"><span data-stu-id="d2ebc-133">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

