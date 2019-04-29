---
title: Configurando valores de tempo limite em uma associação
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779321"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="c91a0-102">Configurando valores de tempo limite em uma associação</span><span class="sxs-lookup"><span data-stu-id="c91a0-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="c91a0-103">Há uma série de configurações de tempo limite em associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="c91a0-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="c91a0-104">Definir tempo limite dessas configurações corretamente podem melhorar não apenas seu serviço desempenho, mas também play uma função na usabilidade e a segurança do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="c91a0-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="c91a0-105">Limite a seguir estão disponíveis em associações do WCF:</span><span class="sxs-lookup"><span data-stu-id="c91a0-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="c91a0-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="c91a0-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="c91a0-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="c91a0-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="c91a0-108">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c91a0-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="c91a0-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c91a0-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="c91a0-110">Tempos limite de associação do WCF</span><span class="sxs-lookup"><span data-stu-id="c91a0-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="c91a0-111">Cada uma das configurações discutidas neste tópico são feitas na associação em si, no código ou na configuração.</span><span class="sxs-lookup"><span data-stu-id="c91a0-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="c91a0-112">O código a seguir mostra como definir o tempo limite programaticamente uma associação do WCF no contexto de um serviço auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="c91a0-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="c91a0-113">O exemplo a seguir mostra como configurar tempos limite em uma associação em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c91a0-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c91a0-114">Para obter mais informações sobre essas configurações podem ser encontradas na documentação para o <xref:System.ServiceModel.Channels.Binding> classe.</span><span class="sxs-lookup"><span data-stu-id="c91a0-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="c91a0-115">Tempos limite do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="c91a0-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="c91a0-116">No lado do cliente:</span><span class="sxs-lookup"><span data-stu-id="c91a0-116">On the client side:</span></span>  
  
1. <span data-ttu-id="c91a0-117">SendTimeout – usado para inicializar o OperationTimeout, que governa o todo o processo de envio de uma mensagem, incluindo recebendo uma mensagem de resposta para uma operação de serviço de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="c91a0-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="c91a0-118">Esse tempo limite também se aplica ao enviar mensagens de resposta de um método de contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="c91a0-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="c91a0-119">OpenTimeout – usado ao abrir canais quando nenhum valor de tempo limite explícito for especificado.</span><span class="sxs-lookup"><span data-stu-id="c91a0-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="c91a0-120">CloseTimeout – usado ao fechar canais quando nenhum valor de tempo limite explícito for especificado.</span><span class="sxs-lookup"><span data-stu-id="c91a0-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="c91a0-121">ReceiveTimeout – não é usado.</span><span class="sxs-lookup"><span data-stu-id="c91a0-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="c91a0-122">Tempos limite do lado do serviço</span><span class="sxs-lookup"><span data-stu-id="c91a0-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="c91a0-123">No lado do serviço:</span><span class="sxs-lookup"><span data-stu-id="c91a0-123">On the service side:</span></span>  
  
1. <span data-ttu-id="c91a0-124">SendTimeout, OpenTimeout, CloseTimeout são os mesmos como no cliente.</span><span class="sxs-lookup"><span data-stu-id="c91a0-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="c91a0-125">ReceiveTimeout – usada pela camada de serviço de estrutura para inicializar o tempo limite de ociosidade de sessão, que controla quanto tempo uma sessão pode ficar ociosa antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="c91a0-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
