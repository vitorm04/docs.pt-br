---
title: Mensagem de segurança com um cliente anônimo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d3e8269fc05caf70f4329ce8f13a3633a8982c0b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676227"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="b65ee-102">Mensagem de segurança com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="b65ee-102">Message Security with an Anonymous Client</span></span>
<span data-ttu-id="b65ee-103">O cenário a seguir mostra um cliente e serviço protegidos pela segurança de mensagem do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b65ee-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="b65ee-104">Uma meta de design é usar segurança de mensagem em vez de segurança de transporte, para que no futuro ele pode dar suporte a um modelo mais avançado baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="b65ee-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="b65ee-105">Para obter mais informações sobre como usar rica de declarações para autorização, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="b65ee-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="b65ee-106">Para um aplicativo de exemplo, consulte [mensagem de segurança anônima](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="b65ee-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>  
  
 <span data-ttu-id="b65ee-107">![Segurança com um cliente anônimo da mensagem](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="b65ee-107">![Message security with an anynymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>  
  
|<span data-ttu-id="b65ee-108">Característica</span><span class="sxs-lookup"><span data-stu-id="b65ee-108">Characteristic</span></span>|<span data-ttu-id="b65ee-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b65ee-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b65ee-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="b65ee-110">Security Mode</span></span>|<span data-ttu-id="b65ee-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b65ee-111">Message</span></span>|  
|<span data-ttu-id="b65ee-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b65ee-112">Interoperability</span></span>|<span data-ttu-id="b65ee-113">Somente o WCF</span><span class="sxs-lookup"><span data-stu-id="b65ee-113">WCF only</span></span>|  
|<span data-ttu-id="b65ee-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="b65ee-114">Authentication (Server)</span></span>|<span data-ttu-id="b65ee-115">Negociação inicial exige a autenticação do servidor, mas não a autenticação do cliente</span><span class="sxs-lookup"><span data-stu-id="b65ee-115">Initial negotiation requires server authentication, but not client authentication</span></span>|  
|<span data-ttu-id="b65ee-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="b65ee-116">Authentication (Client)</span></span>|<span data-ttu-id="b65ee-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b65ee-117">None</span></span>|  
|<span data-ttu-id="b65ee-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="b65ee-118">Integrity</span></span>|<span data-ttu-id="b65ee-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="b65ee-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="b65ee-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="b65ee-120">Confidentiality</span></span>|<span data-ttu-id="b65ee-121">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="b65ee-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="b65ee-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="b65ee-122">Transport</span></span>|<span data-ttu-id="b65ee-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="b65ee-123">HTTP</span></span>|  
  
## <a name="service"></a><span data-ttu-id="b65ee-124">Serviço</span><span class="sxs-lookup"><span data-stu-id="b65ee-124">Service</span></span>  
 <span data-ttu-id="b65ee-125">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="b65ee-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b65ee-126">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b65ee-126">Do one of the following:</span></span>  
  
-   <span data-ttu-id="b65ee-127">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="b65ee-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="b65ee-128">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b65ee-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b65ee-129">Código</span><span class="sxs-lookup"><span data-stu-id="b65ee-129">Code</span></span>  
 <span data-ttu-id="b65ee-130">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b65ee-130">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a><span data-ttu-id="b65ee-131">Configuração</span><span class="sxs-lookup"><span data-stu-id="b65ee-131">Configuration</span></span>  
 <span data-ttu-id="b65ee-132">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="b65ee-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="b65ee-133">O elemento de comportamento de serviço é usado para especificar um certificado que é usado para autenticar o serviço ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b65ee-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="b65ee-134">O elemento de serviço deve especificar o comportamento usando o `behaviorConfiguration` atributo.</span><span class="sxs-lookup"><span data-stu-id="b65ee-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="b65ee-135">O elemento de associação Especifica que o tipo de credencial de cliente `None`, permitindo que os clientes anônimos usar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b65ee-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="b65ee-136">Cliente</span><span class="sxs-lookup"><span data-stu-id="b65ee-136">Client</span></span>  
 <span data-ttu-id="b65ee-137">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="b65ee-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b65ee-138">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b65ee-138">Do one of the following:</span></span>  
  
-   <span data-ttu-id="b65ee-139">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="b65ee-139">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="b65ee-140">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b65ee-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b65ee-141">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="b65ee-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b65ee-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b65ee-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b65ee-143">Código</span><span class="sxs-lookup"><span data-stu-id="b65ee-143">Code</span></span>  
 <span data-ttu-id="b65ee-144">O código a seguir cria uma instância do cliente.</span><span class="sxs-lookup"><span data-stu-id="b65ee-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="b65ee-145">A associação usa segurança de modo de mensagem e o tipo de credencial de cliente é definido como none.</span><span class="sxs-lookup"><span data-stu-id="b65ee-145">The binding uses message mode security, and the client credential type is set to none.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a><span data-ttu-id="b65ee-146">Configuração</span><span class="sxs-lookup"><span data-stu-id="b65ee-146">Configuration</span></span>  
 <span data-ttu-id="b65ee-147">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="b65ee-147">The following code configures the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b65ee-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b65ee-148">See Also</span></span>  
 [<span data-ttu-id="b65ee-149">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="b65ee-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="b65ee-150">Segurança de aplicativos distribuídos</span><span class="sxs-lookup"><span data-stu-id="b65ee-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [<span data-ttu-id="b65ee-151">Segurança de mensagem anônima</span><span class="sxs-lookup"><span data-stu-id="b65ee-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [<span data-ttu-id="b65ee-152">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="b65ee-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b65ee-153">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b65ee-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
