---
title: Mensagem de segurança com um cliente anônimo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: fccdd021e392e6c37615a9091ce13f0e94167246
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212000"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="a8439-102">Mensagem de segurança com um cliente anônimo</span><span class="sxs-lookup"><span data-stu-id="a8439-102">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="a8439-103">O cenário a seguir mostra um cliente e um serviço protegido pela segurança de mensagem do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a8439-103">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="a8439-104">Uma meta de design é usar a segurança de mensagens em vez da segurança de transporte, para que, no futuro, ela possa dar suporte a um modelo mais rico baseado em declarações.</span><span class="sxs-lookup"><span data-stu-id="a8439-104">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="a8439-105">Para obter mais informações sobre como usar declarações avançadas para autorização, consulte [Gerenciando declarações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="a8439-105">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="a8439-106">Para um aplicativo de exemplo, consulte [segurança da mensagem anônimo](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span><span class="sxs-lookup"><span data-stu-id="a8439-106">For a sample application, see [Message Security Anonymous](../../../../docs/framework/wcf/samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="a8439-107">![Segurança de mensagem com um cliente anônimo](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="a8439-107">![Message security with an anonymous client](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="a8439-108">Característica</span><span class="sxs-lookup"><span data-stu-id="a8439-108">Characteristic</span></span>|<span data-ttu-id="a8439-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8439-109">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="a8439-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="a8439-110">Security Mode</span></span>|<span data-ttu-id="a8439-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a8439-111">Message</span></span>|
|<span data-ttu-id="a8439-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="a8439-112">Interoperability</span></span>|<span data-ttu-id="a8439-113">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="a8439-113">WCF only</span></span>|
|<span data-ttu-id="a8439-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="a8439-114">Authentication (Server)</span></span>|<span data-ttu-id="a8439-115">A negociação inicial requer autenticação de servidor, mas não autenticação de cliente</span><span class="sxs-lookup"><span data-stu-id="a8439-115">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="a8439-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="a8439-116">Authentication (Client)</span></span>|<span data-ttu-id="a8439-117">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a8439-117">None</span></span>|
|<span data-ttu-id="a8439-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="a8439-118">Integrity</span></span>|<span data-ttu-id="a8439-119">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="a8439-119">Yes, using shared security context</span></span>|
|<span data-ttu-id="a8439-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="a8439-120">Confidentiality</span></span>|<span data-ttu-id="a8439-121">Sim, usando o contexto de segurança compartilhado</span><span class="sxs-lookup"><span data-stu-id="a8439-121">Yes, using shared security context</span></span>|
|<span data-ttu-id="a8439-122">Transport</span><span class="sxs-lookup"><span data-stu-id="a8439-122">Transport</span></span>|<span data-ttu-id="a8439-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="a8439-123">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="a8439-124">Service</span><span class="sxs-lookup"><span data-stu-id="a8439-124">Service</span></span>

<span data-ttu-id="a8439-125">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="a8439-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a8439-126">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="a8439-126">Do one of the following:</span></span>

- <span data-ttu-id="a8439-127">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="a8439-127">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="a8439-128">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8439-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="a8439-129">Código</span><span class="sxs-lookup"><span data-stu-id="a8439-129">Code</span></span>

<span data-ttu-id="a8439-130">O código a seguir mostra como criar um ponto de extremidade de serviço que usa a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a8439-130">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="a8439-131">Configuração do</span><span class="sxs-lookup"><span data-stu-id="a8439-131">Configuration</span></span>

<span data-ttu-id="a8439-132">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="a8439-132">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="a8439-133">O elemento de comportamento do serviço é usado para especificar um certificado que é usado para autenticar o serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8439-133">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="a8439-134">O elemento de serviço deve especificar o comportamento usando o atributo `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a8439-134">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="a8439-135">O elemento Binding especifica que o tipo de credencial do cliente é `None`, permitindo que clientes anônimos usem o serviço.</span><span class="sxs-lookup"><span data-stu-id="a8439-135">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

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

## <a name="client"></a><span data-ttu-id="a8439-136">Cliente</span><span class="sxs-lookup"><span data-stu-id="a8439-136">Client</span></span>

<span data-ttu-id="a8439-137">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="a8439-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="a8439-138">Siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="a8439-138">Do one of the following:</span></span>

- <span data-ttu-id="a8439-139">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="a8439-139">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="a8439-140">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a8439-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="a8439-141">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="a8439-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="a8439-142">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a8439-142">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="a8439-143">Código</span><span class="sxs-lookup"><span data-stu-id="a8439-143">Code</span></span>

<span data-ttu-id="a8439-144">O código a seguir cria uma instância do cliente.</span><span class="sxs-lookup"><span data-stu-id="a8439-144">The following code creates an instance of the client.</span></span> <span data-ttu-id="a8439-145">A associação usa a segurança do modo de mensagem e o tipo de credencial do cliente é definido como nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8439-145">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="a8439-146">Configuração do</span><span class="sxs-lookup"><span data-stu-id="a8439-146">Configuration</span></span>

<span data-ttu-id="a8439-147">O código a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="a8439-147">The following code configures the client.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a8439-148">Veja também</span><span class="sxs-lookup"><span data-stu-id="a8439-148">See also</span></span>

- [<span data-ttu-id="a8439-149">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="a8439-149">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="a8439-150">Segurança de aplicativos distribuídos</span><span class="sxs-lookup"><span data-stu-id="a8439-150">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="a8439-151">Segurança de mensagem anônima</span><span class="sxs-lookup"><span data-stu-id="a8439-151">Message Security Anonymous</span></span>](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [<span data-ttu-id="a8439-152">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a8439-152">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- <span data-ttu-id="a8439-153">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a8439-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
