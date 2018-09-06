---
title: Cliente e serviço sem segurança na Intranet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e44b7af6581e6c5abdcb2f82b02d152dd22d0b3b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878792"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="31112-102">Cliente e serviço sem segurança na Intranet</span><span class="sxs-lookup"><span data-stu-id="31112-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="31112-103">A ilustração a seguir mostra um serviço Windows Communication Foundation (WCF) simples desenvolvido para fornecer informações sobre uma rede privada segura para um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="31112-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="31112-104">Segurança não é necessária porque os dados são de importância baixa, a rede deve ser inerentemente seguro ou a segurança é fornecida por uma camada abaixo a infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="31112-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 <span data-ttu-id="31112-105">![Cenário de serviço e cliente desprotegido de intranet](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span><span class="sxs-lookup"><span data-stu-id="31112-105">![Intranet unsecured client and service scenario](../../../../docs/framework/wcf/feature-details/media/unsecuredwebservice.gif "UnsecuredWebService")</span></span>  
  
|<span data-ttu-id="31112-106">Característica</span><span class="sxs-lookup"><span data-stu-id="31112-106">Characteristic</span></span>|<span data-ttu-id="31112-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="31112-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="31112-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="31112-108">Security Mode</span></span>|<span data-ttu-id="31112-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="31112-109">None</span></span>|  
|<span data-ttu-id="31112-110">Transporte</span><span class="sxs-lookup"><span data-stu-id="31112-110">Transport</span></span>|<span data-ttu-id="31112-111">TCP</span><span class="sxs-lookup"><span data-stu-id="31112-111">TCP</span></span>|  
|<span data-ttu-id="31112-112">Associação</span><span class="sxs-lookup"><span data-stu-id="31112-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="31112-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="31112-113">Interoperability</span></span>|<span data-ttu-id="31112-114">Somente o WCF</span><span class="sxs-lookup"><span data-stu-id="31112-114">WCF only</span></span>|  
|<span data-ttu-id="31112-115">Autenticação</span><span class="sxs-lookup"><span data-stu-id="31112-115">Authentication</span></span>|<span data-ttu-id="31112-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="31112-116">None</span></span>|  
|<span data-ttu-id="31112-117">Integridade</span><span class="sxs-lookup"><span data-stu-id="31112-117">Integrity</span></span>|<span data-ttu-id="31112-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="31112-118">None</span></span>|  
|<span data-ttu-id="31112-119">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="31112-119">Confidentiality</span></span>|<span data-ttu-id="31112-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="31112-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="31112-121">Serviço</span><span class="sxs-lookup"><span data-stu-id="31112-121">Service</span></span>  
 <span data-ttu-id="31112-122">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="31112-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="31112-123">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="31112-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="31112-124">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="31112-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="31112-125">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="31112-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="31112-126">Código</span><span class="sxs-lookup"><span data-stu-id="31112-126">Code</span></span>  
 <span data-ttu-id="31112-127">O código a seguir mostra como criar um ponto de extremidade sem segurança:</span><span class="sxs-lookup"><span data-stu-id="31112-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="31112-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="31112-128">Configuration</span></span>  
 <span data-ttu-id="31112-129">O código a seguir define o mesmo ponto de extremidade usando a configuração:</span><span class="sxs-lookup"><span data-stu-id="31112-129">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""   
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"   
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="31112-130">Cliente</span><span class="sxs-lookup"><span data-stu-id="31112-130">Client</span></span>  
 <span data-ttu-id="31112-131">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="31112-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="31112-132">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="31112-132">Do one of the following:</span></span>  
  
-   <span data-ttu-id="31112-133">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="31112-133">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="31112-134">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="31112-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="31112-135">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="31112-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="31112-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="31112-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="31112-137">Código</span><span class="sxs-lookup"><span data-stu-id="31112-137">Code</span></span>  
 <span data-ttu-id="31112-138">O código a seguir mostra um cliente WCF básico que acessa um ponto de extremidade não seguro usando o protocolo TCP.</span><span class="sxs-lookup"><span data-stu-id="31112-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="31112-139">Configuração</span><span class="sxs-lookup"><span data-stu-id="31112-139">Configuration</span></span>  
 <span data-ttu-id="31112-140">O código de configuração a seguir aplica-se para o cliente:</span><span class="sxs-lookup"><span data-stu-id="31112-140">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"   
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"   
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="31112-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31112-141">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 [<span data-ttu-id="31112-142">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="31112-142">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="31112-143">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="31112-143">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
