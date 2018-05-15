---
title: Como registrar informações em log sobre serviços
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
manager: douge
ms.openlocfilehash: a046c62de8789cbe438dcc849ffc23991a803ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="e2b7b-102">Como registrar informações em log sobre serviços</span><span class="sxs-lookup"><span data-stu-id="e2b7b-102">How to: Log Information About Services</span></span>
<span data-ttu-id="e2b7b-103">Por padrão, todos os projetos de serviço do Windows têm a capacidade de interagir com o log de eventos do aplicativo e gravar informações e exceções.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="e2b7b-104">Você usa o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para indicar se deseja que essa funcionalidade em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="e2b7b-105">Por padrão, o log está ativado para qualquer serviço que você criar com o modelo de projeto de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="e2b7b-106">Você pode usar uma forma estática do <xref:System.Diagnostics.EventLog> classe para gravar informações de serviço em um log sem a necessidade de criar uma instância de um <xref:System.Diagnostics.EventLog> componente ou registrar manualmente uma fonte.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="e2b7b-107">O instalador para o serviço registra automaticamente cada serviço em seu projeto como uma origem válida de eventos com o log de aplicativo no computador onde o serviço é instalado, quando o log está ativado.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="e2b7b-108">O serviço registra informações cada vez que o serviço é iniciado, interrompido, pausado, reiniciado, instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="e2b7b-109">Também registra erros que ocorrem.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-109">It also logs any failures that occur.</span></span> <span data-ttu-id="e2b7b-110">Você não precisa escrever nenhum código para gravar entradas de log ao usar o comportamento padrão; o serviço trata isso para você automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="e2b7b-111">Se você quiser gravar um log de eventos que não sejam o log do aplicativo, você deve definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade `false`, crie seu próprio log de eventos personalizado em seu código de serviços e registrar seu serviço como uma fonte válida de entradas de log.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="e2b7b-112">Você deve escrever código para registrar entradas de log sempre que uma ação que você está interessado ocorre.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2b7b-113">Se você usar um log de eventos personalizado e configura seu aplicativo de serviço para gravar nele, você não deve tentar acessar o log de eventos antes de configurar o serviço <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriedade em seu código.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="e2b7b-114">O log de eventos precisa o valor dessa propriedade para registrar seu serviço como uma origem válida de eventos.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="e2b7b-115">Para habilitar o log de eventos padrão para o serviço</span><span class="sxs-lookup"><span data-stu-id="e2b7b-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="e2b7b-116">Definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para seu componente para `true`.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2b7b-117">Por padrão, essa propriedade é definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="e2b7b-118">Você não precisa definir isso explicitamente, a menos que você está criando o processamento mais complexo, como avaliar uma condição e, em seguida, definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade com base no resultado da condição.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="e2b7b-119">Para desabilitar o log de eventos para o serviço</span><span class="sxs-lookup"><span data-stu-id="e2b7b-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="e2b7b-120">Definir o <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> propriedade para seu componente para `false`.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="e2b7b-121">Para configurar o registro em um log personalizado</span><span class="sxs-lookup"><span data-stu-id="e2b7b-121">To set up logging to a custom log</span></span>  
  
1.  <span data-ttu-id="e2b7b-122">Defina a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como `false`.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2b7b-123">Você deve definir <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como falso para usar um log personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2.  <span data-ttu-id="e2b7b-124">Configurar uma instância de um <xref:System.Diagnostics.EventLog> em seu aplicativo de serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3.  <span data-ttu-id="e2b7b-125">Criar um log personalizado chamando o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método e especificando a cadeia de caracteres de origem e o nome do log de arquivo que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4.  <span data-ttu-id="e2b7b-126">Definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade o <xref:System.Diagnostics.EventLog> instância do componente para a cadeia de caracteres de origem que você criou na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5.  <span data-ttu-id="e2b7b-127">Gravar as entradas, acessando o <xref:System.Diagnostics.EventLog.WriteEntry%2A> método sobre o <xref:System.Diagnostics.EventLog> instância do componente.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="e2b7b-128">O código a seguir mostra como configurar o log para um log personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e2b7b-129">Neste exemplo de código, uma instância de um <xref:System.Diagnostics.EventLog> componente é chamado `eventLog1` (`EventLog1` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e2b7b-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="e2b7b-130">Se você criou uma instância com outro nome na etapa 2, altere o código adequadamente.</span><span class="sxs-lookup"><span data-stu-id="e2b7b-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="e2b7b-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2b7b-131">See Also</span></span>  
 [<span data-ttu-id="e2b7b-132">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="e2b7b-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
