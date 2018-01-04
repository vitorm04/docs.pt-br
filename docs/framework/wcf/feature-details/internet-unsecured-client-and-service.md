---
title: "Serviço e cliente de internet desprotegido"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b202c4d67b48a9559afe035dc6b7bc95f6cc7779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="5237b-102">Serviço e cliente de internet desprotegido</span><span class="sxs-lookup"><span data-stu-id="5237b-102">Internet Unsecured Client and Service</span></span>
<span data-ttu-id="5237b-103">A seguinte ilustração mostra um exemplo de um público, não segura [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="5237b-103">The following illustration shows an example of a public, unsecured [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span>  
  
 <span data-ttu-id="5237b-104">![Não seguro da Internet inseguro e cenário de serviço](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span><span class="sxs-lookup"><span data-stu-id="5237b-104">![Unsecured Internet cleint and service scenario](../../../../docs/framework/wcf/feature-details/media/publicunsecured.gif "publicUnsecured")</span></span>  
  
|<span data-ttu-id="5237b-105">Característica</span><span class="sxs-lookup"><span data-stu-id="5237b-105">Characteristic</span></span>|<span data-ttu-id="5237b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5237b-106">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5237b-107">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="5237b-107">Security Mode</span></span>|<span data-ttu-id="5237b-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5237b-108">None</span></span>|  
|<span data-ttu-id="5237b-109">Transporte</span><span class="sxs-lookup"><span data-stu-id="5237b-109">Transport</span></span>|<span data-ttu-id="5237b-110">HTTP</span><span class="sxs-lookup"><span data-stu-id="5237b-110">HTTP</span></span>|  
|<span data-ttu-id="5237b-111">Associação</span><span class="sxs-lookup"><span data-stu-id="5237b-111">Binding</span></span>|<span data-ttu-id="5237b-112"><xref:System.ServiceModel.BasicHttpBinding>no código, ou o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento na configuração.</span><span class="sxs-lookup"><span data-stu-id="5237b-112"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="5237b-113">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="5237b-113">Interoperability</span></span>|<span data-ttu-id="5237b-114">Com os serviços e clientes de serviço da Web existentes</span><span class="sxs-lookup"><span data-stu-id="5237b-114">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="5237b-115">Autenticação</span><span class="sxs-lookup"><span data-stu-id="5237b-115">Authentication</span></span>|<span data-ttu-id="5237b-116">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5237b-116">None</span></span>|  
|<span data-ttu-id="5237b-117">Integridade</span><span class="sxs-lookup"><span data-stu-id="5237b-117">Integrity</span></span>|<span data-ttu-id="5237b-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5237b-118">None</span></span>|  
|<span data-ttu-id="5237b-119">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="5237b-119">Confidentiality</span></span>|<span data-ttu-id="5237b-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5237b-120">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="5237b-121">Serviço</span><span class="sxs-lookup"><span data-stu-id="5237b-121">Service</span></span>  
 <span data-ttu-id="5237b-122">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5237b-122">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5237b-123">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5237b-123">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5237b-124">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="5237b-124">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5237b-125">Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5237b-125">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5237b-126">Código</span><span class="sxs-lookup"><span data-stu-id="5237b-126">Code</span></span>  
 <span data-ttu-id="5237b-127">O código a seguir mostra como criar um ponto de extremidade sem segurança.</span><span class="sxs-lookup"><span data-stu-id="5237b-127">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="5237b-128">Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> tem o modo de segurança definido como <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="5237b-128">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="5237b-129">Configuração de serviço</span><span class="sxs-lookup"><span data-stu-id="5237b-129">Service Configuration</span></span>  
 <span data-ttu-id="5237b-130">O código a seguir define o mesmo ponto de extremidade usando a configuração.</span><span class="sxs-lookup"><span data-stu-id="5237b-130">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="5237b-131">Cliente</span><span class="sxs-lookup"><span data-stu-id="5237b-131">Client</span></span>  
 <span data-ttu-id="5237b-132">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="5237b-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5237b-133">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="5237b-133">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5237b-134">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="5237b-134">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="5237b-135">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5237b-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="5237b-136">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="5237b-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="5237b-137">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5237b-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="5237b-138">Código</span><span class="sxs-lookup"><span data-stu-id="5237b-138">Code</span></span>  
 <span data-ttu-id="5237b-139">O código a seguir mostra um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que acessa um ponto de extremidade não seguro.</span><span class="sxs-lookup"><span data-stu-id="5237b-139">The following code shows a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="5237b-140">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="5237b-140">Client Configuration</span></span>  
 <span data-ttu-id="5237b-141">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="5237b-141">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5237b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5237b-142">See Also</span></span>  
 [<span data-ttu-id="5237b-143">Cenários comuns de segurança</span><span class="sxs-lookup"><span data-stu-id="5237b-143">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [<span data-ttu-id="5237b-144">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="5237b-144">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="5237b-145">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5237b-145">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
