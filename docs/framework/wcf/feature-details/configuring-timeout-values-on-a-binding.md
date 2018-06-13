---
title: Configurando valores de tempo limite em uma associação
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 21d99ad2ce092db738469f93e80c39380acabd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489603"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="34d27-102">Configurando valores de tempo limite em uma associação</span><span class="sxs-lookup"><span data-stu-id="34d27-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="34d27-103">Há um número de configurações de tempo limite em associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="34d27-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="34d27-104">Definir esses tempo limite configurações corretamente podem melhorar não apenas o serviço desempenho, mas também executar uma função na usabilidade e segurança de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="34d27-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="34d27-105">Limite a seguir estão disponíveis em associações do WCF:</span><span class="sxs-lookup"><span data-stu-id="34d27-105">The following timeouts are available on WCF bindings:</span></span>  
  
1.  <span data-ttu-id="34d27-106">openTimeout</span><span class="sxs-lookup"><span data-stu-id="34d27-106">OpenTimeout</span></span>  
  
2.  <span data-ttu-id="34d27-107">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="34d27-107">CloseTimeout</span></span>  
  
3.  <span data-ttu-id="34d27-108">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="34d27-108">SendTimeout</span></span>  
  
4.  <span data-ttu-id="34d27-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="34d27-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="34d27-110">Tempos limite de ligação do WCF</span><span class="sxs-lookup"><span data-stu-id="34d27-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="34d27-111">Cada uma das configurações abordadas neste tópico são feitas na associação, na configuração ou código.</span><span class="sxs-lookup"><span data-stu-id="34d27-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="34d27-112">O código a seguir mostra como definir o tempo limite em uma associação WCF no contexto de um serviço auto-hospedado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="34d27-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="34d27-113">O exemplo a seguir mostra como configurar o tempo limite em uma associação em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="34d27-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="34d27-114">Para obter mais informações sobre essas configurações podem ser encontradas na documentação para o <xref:System.ServiceModel.Channels.Binding> classe.</span><span class="sxs-lookup"><span data-stu-id="34d27-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="34d27-115">Tempos limite do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="34d27-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="34d27-116">No lado do cliente:</span><span class="sxs-lookup"><span data-stu-id="34d27-116">On the client side:</span></span>  
  
1.  <span data-ttu-id="34d27-117">SendTimeout – usado para inicializar o OperationTimeout, que controla todo o processo de enviar uma mensagem, incluindo recebendo uma mensagem de resposta para uma operação de serviço de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="34d27-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="34d27-118">Esse tempo limite também se aplica ao enviar mensagens de resposta de um método de contrato de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="34d27-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2.  <span data-ttu-id="34d27-119">OpenTimeout – usada ao abrir canais quando nenhum valor de tempo limite explícito for especificado.</span><span class="sxs-lookup"><span data-stu-id="34d27-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3.  <span data-ttu-id="34d27-120">CloseTimeout – usado ao fechar canais quando nenhum valor de tempo limite explícito for especificado.</span><span class="sxs-lookup"><span data-stu-id="34d27-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4.  <span data-ttu-id="34d27-121">ReceiveTimeout – não é usado.</span><span class="sxs-lookup"><span data-stu-id="34d27-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="34d27-122">Tempos limite do lado do serviço</span><span class="sxs-lookup"><span data-stu-id="34d27-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="34d27-123">No lado do serviço:</span><span class="sxs-lookup"><span data-stu-id="34d27-123">On the service side:</span></span>  
  
1.  <span data-ttu-id="34d27-124">SendTimeout, OpenTimeout, CloseTimeout são os mesmos que no cliente.</span><span class="sxs-lookup"><span data-stu-id="34d27-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2.  <span data-ttu-id="34d27-125">ReceiveTimeout – usado pela camada de estrutura de serviço para inicializar o tempo limite de ociosidade de sessão, que controla quanto tempo uma sessão pode ficar ociosa antes do tempo limite.</span><span class="sxs-lookup"><span data-stu-id="34d27-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
