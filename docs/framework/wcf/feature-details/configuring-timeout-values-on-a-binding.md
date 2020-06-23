---
title: Configurando valores de tempo limite em uma associação
description: Saiba como gerenciar configurações de tempo limite para associações do WCF para melhorar o desempenho, a usabilidade e a segurança do seu serviço.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245109"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="993b8-103">Configurando valores de tempo limite em uma associação</span><span class="sxs-lookup"><span data-stu-id="993b8-103">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="993b8-104">Há várias configurações de tempo limite disponíveis nas associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="993b8-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="993b8-105">Definir essas configurações de tempo limite corretamente pode melhorar não apenas o desempenho do serviço, mas também desempenhar uma função na usabilidade e na segurança do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="993b8-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="993b8-106">Os seguintes tempos limite estão disponíveis em associações WCF:</span><span class="sxs-lookup"><span data-stu-id="993b8-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="993b8-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="993b8-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="993b8-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="993b8-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="993b8-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="993b8-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="993b8-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="993b8-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="993b8-111">Tempos limite de associação do WCF</span><span class="sxs-lookup"><span data-stu-id="993b8-111">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="993b8-112">Cada uma das configurações discutidas neste tópico é feita na própria associação, seja no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="993b8-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="993b8-113">O código a seguir mostra como definir os tempos limite de forma programática em uma associação do WCF no contexto de um serviço hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="993b8-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="993b8-114">O exemplo a seguir mostra como configurar tempos limite em uma associação em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="993b8-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="993b8-115">Mais informações sobre essas configurações podem ser encontradas na documentação da <xref:System.ServiceModel.Channels.Binding> classe.</span><span class="sxs-lookup"><span data-stu-id="993b8-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="993b8-116">Tempos limite do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="993b8-116">Client-side Timeouts</span></span>  
 <span data-ttu-id="993b8-117">No lado do cliente:</span><span class="sxs-lookup"><span data-stu-id="993b8-117">On the client side:</span></span>  
  
1. <span data-ttu-id="993b8-118">SendTimeout – usado para inicializar o OperationTimeout, que governa todo o processo de envio de uma mensagem, incluindo o recebimento de uma mensagem de resposta para uma operação de serviço de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="993b8-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="993b8-119">Esse tempo limite também se aplica ao enviar mensagens de resposta de um método de contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="993b8-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="993b8-120">OpenTimeout – usado ao abrir canais quando nenhum valor de tempo limite explícito é especificado.</span><span class="sxs-lookup"><span data-stu-id="993b8-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="993b8-121">CloseTimeout – usado ao fechar canais quando nenhum valor de tempo limite explícito é especificado.</span><span class="sxs-lookup"><span data-stu-id="993b8-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="993b8-122">ReceiveTimeout – não é usado.</span><span class="sxs-lookup"><span data-stu-id="993b8-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="993b8-123">Tempos limite do lado do serviço</span><span class="sxs-lookup"><span data-stu-id="993b8-123">Service-side Timeouts</span></span>  
 <span data-ttu-id="993b8-124">No lado do serviço:</span><span class="sxs-lookup"><span data-stu-id="993b8-124">On the service side:</span></span>  
  
1. <span data-ttu-id="993b8-125">SendTimeout, OpenTimeout, CloseTimeout são os mesmos que no cliente.</span><span class="sxs-lookup"><span data-stu-id="993b8-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="993b8-126">ReceiveTimeout – usado pela camada do Service Framework para inicializar o tempo limite de ociosidade da sessão que controla por quanto tempo uma sessão pode ficar ociosa antes de atingir o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="993b8-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
