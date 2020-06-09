---
title: Cliente e serviço sem segurança na Intranet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: 591f7db0f6b4e928a991961d3bc7c404f41028bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579274"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="055c2-102">Cliente e serviço sem segurança na Intranet</span><span class="sxs-lookup"><span data-stu-id="055c2-102">Intranet Unsecured Client and Service</span></span>
<span data-ttu-id="055c2-103">A ilustração a seguir descreve um serviço de Windows Communication Foundation simples (WCF) desenvolvido para fornecer informações sobre uma rede privada segura para um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="055c2-103">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="055c2-104">A segurança não é necessária porque os dados são de baixa importância, a rede deve ser inerentemente segura ou a segurança é fornecida por uma camada abaixo da infraestrutura do WCF.</span><span class="sxs-lookup"><span data-stu-id="055c2-104">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Cenário de cliente e serviço desprotegido da intranet.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="055c2-106">Característica</span><span class="sxs-lookup"><span data-stu-id="055c2-106">Characteristic</span></span>|<span data-ttu-id="055c2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="055c2-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="055c2-108">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="055c2-108">Security Mode</span></span>|<span data-ttu-id="055c2-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="055c2-109">None</span></span>|  
|<span data-ttu-id="055c2-110">Transport</span><span class="sxs-lookup"><span data-stu-id="055c2-110">Transport</span></span>|<span data-ttu-id="055c2-111">TCP</span><span class="sxs-lookup"><span data-stu-id="055c2-111">TCP</span></span>|  
|<span data-ttu-id="055c2-112">Associação</span><span class="sxs-lookup"><span data-stu-id="055c2-112">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="055c2-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="055c2-113">Interoperability</span></span>|<span data-ttu-id="055c2-114">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="055c2-114">WCF only</span></span>|  
|<span data-ttu-id="055c2-115">Autenticação</span><span class="sxs-lookup"><span data-stu-id="055c2-115">Authentication</span></span>|<span data-ttu-id="055c2-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="055c2-116">None</span></span>|  
|<span data-ttu-id="055c2-117">Integridade</span><span class="sxs-lookup"><span data-stu-id="055c2-117">Integrity</span></span>|<span data-ttu-id="055c2-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="055c2-118">None</span></span>|  
|<span data-ttu-id="055c2-119">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="055c2-119">Confidentiality</span></span>|<span data-ttu-id="055c2-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="055c2-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="055c2-121">Serviço</span><span class="sxs-lookup"><span data-stu-id="055c2-121">Service</span></span>  
 <span data-ttu-id="055c2-122">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="055c2-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="055c2-123">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="055c2-123">Do one of the following:</span></span>  
  
- <span data-ttu-id="055c2-124">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="055c2-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="055c2-125">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="055c2-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="055c2-126">Código</span><span class="sxs-lookup"><span data-stu-id="055c2-126">Code</span></span>  
 <span data-ttu-id="055c2-127">O código a seguir mostra como criar um ponto de extremidade sem segurança:</span><span class="sxs-lookup"><span data-stu-id="055c2-127">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="055c2-128">Configuração</span><span class="sxs-lookup"><span data-stu-id="055c2-128">Configuration</span></span>  
 <span data-ttu-id="055c2-129">O código a seguir configura o mesmo ponto de extremidade usando a configuração:</span><span class="sxs-lookup"><span data-stu-id="055c2-129">The following code sets up the same endpoint using configuration:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="055c2-130">Cliente</span><span class="sxs-lookup"><span data-stu-id="055c2-130">Client</span></span>  
 <span data-ttu-id="055c2-131">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="055c2-131">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="055c2-132">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="055c2-132">Do one of the following:</span></span>  
  
- <span data-ttu-id="055c2-133">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="055c2-133">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="055c2-134">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="055c2-134">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="055c2-135">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="055c2-135">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="055c2-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="055c2-136">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="055c2-137">Código</span><span class="sxs-lookup"><span data-stu-id="055c2-137">Code</span></span>  
 <span data-ttu-id="055c2-138">O código a seguir mostra um cliente WCF básico que acessa um ponto de extremidade desprotegido usando o protocolo TCP.</span><span class="sxs-lookup"><span data-stu-id="055c2-138">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="055c2-139">Configuração</span><span class="sxs-lookup"><span data-stu-id="055c2-139">Configuration</span></span>  
 <span data-ttu-id="055c2-140">O código de configuração a seguir se aplica ao cliente:</span><span class="sxs-lookup"><span data-stu-id="055c2-140">The following configuration code applies to the client:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="055c2-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="055c2-141">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="055c2-142">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="055c2-142">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="055c2-143">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="055c2-143">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
