---
title: Configurando valores de tempo limite em uma associação
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185285"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="08182-102">Configurando valores de tempo limite em uma associação</span><span class="sxs-lookup"><span data-stu-id="08182-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="08182-103">Há uma série de configurações de tempo total disponíveis nas ligações WCF.</span><span class="sxs-lookup"><span data-stu-id="08182-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="08182-104">Definir corretamente essas configurações de tempo limitado pode melhorar não apenas o desempenho do seu serviço, mas também desempenhar um papel na usabilidade e segurança do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="08182-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="08182-105">Os seguintes intervalos estão disponíveis nas ligações WCF:</span><span class="sxs-lookup"><span data-stu-id="08182-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="08182-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="08182-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="08182-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="08182-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="08182-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="08182-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="08182-109">Receivetimeout</span><span class="sxs-lookup"><span data-stu-id="08182-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="08182-110">Tempos de ligação WCF</span><span class="sxs-lookup"><span data-stu-id="08182-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="08182-111">Cada uma das configurações discutidas neste tópico são feitas na própria vinculação, seja em código ou configuração.</span><span class="sxs-lookup"><span data-stu-id="08182-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="08182-112">O código a seguir mostra como definir programáticamente tempos outs em uma vinculação WCF no contexto de um serviço auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="08182-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="08182-113">O exemplo a seguir mostra como configurar tempos outs em uma vinculação em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="08182-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="08182-114">Mais informações sobre essas configurações podem ser <xref:System.ServiceModel.Channels.Binding> encontradas na documentação da classe.</span><span class="sxs-lookup"><span data-stu-id="08182-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="08182-115">Tempos fora do cliente</span><span class="sxs-lookup"><span data-stu-id="08182-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="08182-116">No lado do cliente:</span><span class="sxs-lookup"><span data-stu-id="08182-116">On the client side:</span></span>  
  
1. <span data-ttu-id="08182-117">SendTimeout – usado para inicializar o OperationTimeout, que rege todo o processo de envio de uma mensagem, incluindo o recebimento de uma mensagem de resposta para uma operação de serviço de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="08182-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="08182-118">Esse tempo não é válido também ao enviar mensagens de resposta de um método de contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="08182-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="08182-119">OpenTimeout – usado ao abrir canais quando nenhum valor de tempo livre explícito é especificado.</span><span class="sxs-lookup"><span data-stu-id="08182-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="08182-120">CloseTimeout – usado quando os canais de fechamento não são especificados.</span><span class="sxs-lookup"><span data-stu-id="08182-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="08182-121">ReceiveTimeout – não é usado.</span><span class="sxs-lookup"><span data-stu-id="08182-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="08182-122">Tempos fora do serviço</span><span class="sxs-lookup"><span data-stu-id="08182-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="08182-123">No lado do serviço:</span><span class="sxs-lookup"><span data-stu-id="08182-123">On the service side:</span></span>  
  
1. <span data-ttu-id="08182-124">SendTimeout, OpenTimeout, CloseTimeout são os mesmos do cliente.</span><span class="sxs-lookup"><span data-stu-id="08182-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="08182-125">ReceiveTimeout – usado pela Camada de Estrutura de Serviço para inicializar o tempo de espera de sessão que controla quanto tempo uma sessão pode ficar ociosa antes de cronometrar.</span><span class="sxs-lookup"><span data-stu-id="08182-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
