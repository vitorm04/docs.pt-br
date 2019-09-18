---
title: 'Como: Registrar em log informações sobre serviços'
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
ms.openlocfilehash: 3c974d5a98f8056e45899b109878e5a28ab2938e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053616"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="842a6-102">Como: Registrar em log informações sobre serviços</span><span class="sxs-lookup"><span data-stu-id="842a6-102">How to: Log Information About Services</span></span>
<span data-ttu-id="842a6-103">Por padrão, todos os projetos de Serviço Windows têm a capacidade de interagir com o log de eventos do aplicativo e gravar informações e exceções.</span><span class="sxs-lookup"><span data-stu-id="842a6-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="842a6-104">A propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> é usada para indicar se você deseja essa funcionalidade em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="842a6-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="842a6-105">Por padrão, o registro em log é habilitado para qualquer serviço criado com o modelo de projeto de Serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="842a6-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="842a6-106">Você pode usar uma forma estática da classe <xref:System.Diagnostics.EventLog> para gravar informações de serviço em um log sem precisar criar uma instância de um componente <xref:System.Diagnostics.EventLog> nem registrar uma fonte manualmente.</span><span class="sxs-lookup"><span data-stu-id="842a6-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="842a6-107">O instalador do serviço registra automaticamente cada serviço no projeto como uma fonte de eventos válida no log do aplicativo no computador no qual o serviço está instalado, quando o registro em log está habilitado.</span><span class="sxs-lookup"><span data-stu-id="842a6-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="842a6-108">O serviço registra informações sempre que é iniciado, interrompido, colocado em pausa, retomado, instalado ou desinstalado.</span><span class="sxs-lookup"><span data-stu-id="842a6-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="842a6-109">Ele também registra as falhas que ocorrem.</span><span class="sxs-lookup"><span data-stu-id="842a6-109">It also logs any failures that occur.</span></span> <span data-ttu-id="842a6-110">Você não precisa escrever nenhum código para gravar entradas no log ao usar o comportamento padrão. O serviço faz isso automaticamente.</span><span class="sxs-lookup"><span data-stu-id="842a6-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="842a6-111">Se você quiser gravar em um log de eventos que não seja o log do aplicativo, será necessário definir a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como `false`, criar seu próprio log de eventos personalizado no código de serviços e registrar o serviço como uma fonte válida de entradas para esse log.</span><span class="sxs-lookup"><span data-stu-id="842a6-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="842a6-112">Em seguida, você precisará escrever o código para registrar entradas no log sempre que ocorrer uma ação do seu interesse.</span><span class="sxs-lookup"><span data-stu-id="842a6-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="842a6-113">Se você usar um log de eventos personalizado e configurar o aplicativo de serviço para gravar nele, não tente acessar o log de eventos antes de configurar a propriedade <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> do serviço no código.</span><span class="sxs-lookup"><span data-stu-id="842a6-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="842a6-114">O log de eventos precisa do valor dessa propriedade para registrar o serviço como uma origem válida de eventos.</span><span class="sxs-lookup"><span data-stu-id="842a6-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="842a6-115">Para habilitar o registro em log de eventos padrão para o serviço</span><span class="sxs-lookup"><span data-stu-id="842a6-115">To enable default event logging for your service</span></span>  
  
- <span data-ttu-id="842a6-116">Defina a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> do componente para `true`.</span><span class="sxs-lookup"><span data-stu-id="842a6-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="842a6-117">Por padrão, essa propriedade é definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="842a6-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="842a6-118">Você não precisa definir isso explicitamente, a menos que esteja criando um processamento mais complexo, como avaliar uma condição e, em seguida, definir a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> com base no resultado dessa condição.</span><span class="sxs-lookup"><span data-stu-id="842a6-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="842a6-119">Para desabilitar o registro em log de eventos para o serviço</span><span class="sxs-lookup"><span data-stu-id="842a6-119">To disable event logging for your service</span></span>  
  
- <span data-ttu-id="842a6-120">Defina a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> do componente para `false`.</span><span class="sxs-lookup"><span data-stu-id="842a6-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="842a6-121">Para configurar o registro em um log personalizado</span><span class="sxs-lookup"><span data-stu-id="842a6-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="842a6-122">Defina a propriedade <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como `false`.</span><span class="sxs-lookup"><span data-stu-id="842a6-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="842a6-123">Você precisa definir <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> como false para usar um log personalizado.</span><span class="sxs-lookup"><span data-stu-id="842a6-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="842a6-124">Configure uma instância de um componente <xref:System.Diagnostics.EventLog> no aplicativo de Serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="842a6-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="842a6-125">Crie um log personalizado chamando o método <xref:System.Diagnostics.EventLog.CreateEventSource%2A> e especificando a cadeia de caracteres de origem e o nome do arquivo de log que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="842a6-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="842a6-126">Defina a propriedade <xref:System.Diagnostics.EventLog.Source%2A> na instância do componente <xref:System.Diagnostics.EventLog> para a cadeia de caracteres de origem que você criou na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="842a6-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="842a6-127">Grave as entradas, acessando o método <xref:System.Diagnostics.EventLog.WriteEntry%2A> na instância do componente <xref:System.Diagnostics.EventLog>.</span><span class="sxs-lookup"><span data-stu-id="842a6-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="842a6-128">O código a seguir mostra como configurar o registro em um log personalizado.</span><span class="sxs-lookup"><span data-stu-id="842a6-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="842a6-129">Neste exemplo de código, uma instância de um componente <xref:System.Diagnostics.EventLog> é chamada de `eventLog1` (`EventLog1` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="842a6-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="842a6-130">Se você criar uma instância com outro nome na etapa 2, altere o código adequadamente.</span><span class="sxs-lookup"><span data-stu-id="842a6-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="842a6-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="842a6-131">See also</span></span>

- [<span data-ttu-id="842a6-132">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="842a6-132">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
