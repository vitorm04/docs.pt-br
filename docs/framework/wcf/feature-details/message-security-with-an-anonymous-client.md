---
title: "Mensagem de segurança com um cliente anônimo"
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
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: edf1dd36fe8c0f3e6c1ae8087d1bacbc00cf307a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="35af8-102">Mensagem de segurança com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="35af8-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="35af8-103">O cenário a seguir mostra um cliente e o serviço protegido pelo [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="35af8-103">The following scenario shows a client and service secured by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] message security.</span></span> <span data-ttu-id="35af8-104">Uma meta de design é usar segurança de mensagem em vez de segurança de transporte, para que no futuro, ela pode suportar um modelo mais avançado baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="35af8-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="35af8-105">usando declarações avançada para autorização, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="35af8-105"> using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="35af8-106">Para um aplicativo de exemplo, consulte [mensagem segurança anônima](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="35af8-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="35af8-107">![Segurança com um cliente anônimo](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="35af8-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="35af8-108">Característica</span><span class="sxs-lookup"><span data-stu-id="35af8-108">Characteristic</span></span>|<span data-ttu-id="35af8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="35af8-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="35af8-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="35af8-110">Security Mode</span></span>|<span data-ttu-id="35af8-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="35af8-111">Message</span></span>|  
|<span data-ttu-id="35af8-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="35af8-112">Interoperability</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="35af8-113">somente</span><span class="sxs-lookup"><span data-stu-id="35af8-113"> only</span></span>|  
|<span data-ttu-id="35af8-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="35af8-114">Authentication (Server)</span></span>|<span data-ttu-id="35af8-115">Negociação inicial requer autenticação de servidor, mas não a autenticação do cliente</span><span class="sxs-lookup"><span data-stu-id="35af8-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="35af8-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="35af8-116">Authentication (Client)</span></span>|<span data-ttu-id="35af8-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="35af8-117">None</span></span>|  
|<span data-ttu-id="35af8-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="35af8-118">Integrity</span></span>|<span data-ttu-id="35af8-119">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="35af8-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="35af8-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="35af8-120">Confidentiality</span></span>|<span data-ttu-id="35af8-121">Sim, usando o contexto de segurança compartilhada</span><span class="sxs-lookup"><span data-stu-id="35af8-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="35af8-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="35af8-122">Transport</span></span>|<span data-ttu-id="35af8-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="35af8-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="35af8-124">Serviço</span><span class="sxs-lookup"><span data-stu-id="35af8-124">Service</span></span>  
 <span data-ttu-id="35af8-125">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="35af8-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="35af8-126">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="35af8-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="35af8-127">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="35af8-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="35af8-128">Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="35af8-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="35af8-129">Código</span><span class="sxs-lookup"><span data-stu-id="35af8-129">Code</span></span>  
 <span data-ttu-id="35af8-130">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="35af8-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="35af8-131">Configuração</span><span class="sxs-lookup"><span data-stu-id="35af8-131">Configuration</span></span>  
 <span data-ttu-id="35af8-132">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="35af8-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="35af8-133">O elemento de comportamento de serviço é usado para especificar um certificado que é usado para autenticar o serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="35af8-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="35af8-134">O elemento de serviço deve especificar o comportamento usando o `behaviorConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="35af8-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="35af8-135">O elemento de associação Especifica que o tipo de credencial de cliente `None`, permitindo que clientes anônimos usar o serviço.</span><span class="sxs-lookup"><span data-stu-id="35af8-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="35af8-136">Cliente</span><span class="sxs-lookup"><span data-stu-id="35af8-136">Client</span></span>  
 <span data-ttu-id="35af8-137">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="35af8-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="35af8-138">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="35af8-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="35af8-139">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="35af8-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="35af8-140">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="35af8-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="35af8-141">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="35af8-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="35af8-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="35af8-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="35af8-143">Código</span><span class="sxs-lookup"><span data-stu-id="35af8-143">Code</span></span>  
 <span data-ttu-id="35af8-144">O código a seguir cria uma instância do cliente.</span><span class="sxs-lookup"><span data-stu-id="35af8-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="35af8-145">A associação usa segurança de modo de mensagem e o tipo de credencial de cliente está definido como none.</span><span class="sxs-lookup"><span data-stu-id="35af8-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="35af8-146">Configuração</span><span class="sxs-lookup"><span data-stu-id="35af8-146">Configuration</span></span>  
 <span data-ttu-id="35af8-147">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="35af8-147">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35af8-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35af8-148">See Also</span></span>  
 [<span data-ttu-id="35af8-149">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="35af8-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="35af8-150">Segurança de aplicativos distribuídos</span><span class="sxs-lookup"><span data-stu-id="35af8-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="35af8-151">Segurança de mensagem anônima</span><span class="sxs-lookup"><span data-stu-id="35af8-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="35af8-152">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="35af8-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="35af8-153">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="35af8-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
