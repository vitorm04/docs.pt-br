---
title: Segurança da mensagens com um cliente de certificado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 3660877194931c2be5b9b1c9aa54e2595701697f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184650"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="23709-102">Segurança da mensagens com um cliente de certificado</span><span class="sxs-lookup"><span data-stu-id="23709-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="23709-103">O cenário a seguir mostra um cliente e serviço da Windows Communication Foundation (WCF) protegidos usando o modo de segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="23709-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="23709-104">Tanto o cliente quanto o serviço são autenticados com certificados.</span><span class="sxs-lookup"><span data-stu-id="23709-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="23709-105">Para obter mais informações, consulte [Segurança distribuída de aplicativos](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="23709-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![Captura de tela que mostra um cliente com certificado.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="23709-107">Para obter um aplicativo de exemplo, consulte [Certificado de segurança de mensagens](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="23709-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="23709-108">Característica</span><span class="sxs-lookup"><span data-stu-id="23709-108">Characteristic</span></span>|<span data-ttu-id="23709-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="23709-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="23709-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="23709-110">Security Mode</span></span>|<span data-ttu-id="23709-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="23709-111">Message</span></span>|  
|<span data-ttu-id="23709-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="23709-112">Interoperability</span></span>|<span data-ttu-id="23709-113">Somente WCF</span><span class="sxs-lookup"><span data-stu-id="23709-113">WCF only</span></span>|  
|<span data-ttu-id="23709-114">Autenticação (Servidor)</span><span class="sxs-lookup"><span data-stu-id="23709-114">Authentication (Server)</span></span>|<span data-ttu-id="23709-115">Usando certificado de serviço</span><span class="sxs-lookup"><span data-stu-id="23709-115">Using service certificate</span></span>|  
|<span data-ttu-id="23709-116">Autenticação (Cliente)</span><span class="sxs-lookup"><span data-stu-id="23709-116">Authentication (Client)</span></span>|<span data-ttu-id="23709-117">Usando o certificado do cliente</span><span class="sxs-lookup"><span data-stu-id="23709-117">Using client certificate</span></span>|  
|<span data-ttu-id="23709-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="23709-118">Integrity</span></span>|<span data-ttu-id="23709-119">Sim</span><span class="sxs-lookup"><span data-stu-id="23709-119">Yes</span></span>|  
|<span data-ttu-id="23709-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="23709-120">Confidentiality</span></span>|<span data-ttu-id="23709-121">Sim</span><span class="sxs-lookup"><span data-stu-id="23709-121">Yes</span></span>|  
|<span data-ttu-id="23709-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="23709-122">Transport</span></span>|<span data-ttu-id="23709-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="23709-123">HTTP</span></span>|  
|<span data-ttu-id="23709-124">Associação</span><span class="sxs-lookup"><span data-stu-id="23709-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="23709-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="23709-125">Service</span></span>  
 <span data-ttu-id="23709-126">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="23709-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="23709-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="23709-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="23709-128">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="23709-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="23709-129">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.</span><span class="sxs-lookup"><span data-stu-id="23709-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="23709-130">Código</span><span class="sxs-lookup"><span data-stu-id="23709-130">Code</span></span>  
 <span data-ttu-id="23709-131">O código a seguir mostra como criar um ponto final de serviço que usa a segurança da mensagem para estabelecer um contexto seguro.</span><span class="sxs-lookup"><span data-stu-id="23709-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="23709-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="23709-132">Configuration</span></span>  
 <span data-ttu-id="23709-133">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="23709-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="23709-134">Cliente</span><span class="sxs-lookup"><span data-stu-id="23709-134">Client</span></span>  
 <span data-ttu-id="23709-135">O seguinte código e configuração devem ser executados independentemente.</span><span class="sxs-lookup"><span data-stu-id="23709-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="23709-136">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="23709-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="23709-137">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="23709-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="23709-138">Crie um cliente que não defina nenhum endereço de ponto final.</span><span class="sxs-lookup"><span data-stu-id="23709-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="23709-139">Em vez disso, use o construtor cliente que toma o nome da configuração como argumento.</span><span class="sxs-lookup"><span data-stu-id="23709-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="23709-140">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="23709-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="23709-141">Código</span><span class="sxs-lookup"><span data-stu-id="23709-141">Code</span></span>  
 <span data-ttu-id="23709-142">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="23709-142">The following code creates the client.</span></span> <span data-ttu-id="23709-143">A vinculação é para a segurança do modo de `Certificate`mensagem, e o tipo de credencial do cliente está definido como .</span><span class="sxs-lookup"><span data-stu-id="23709-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="23709-144">Configuração</span><span class="sxs-lookup"><span data-stu-id="23709-144">Configuration</span></span>  
 <span data-ttu-id="23709-145">A configuração a seguir especifica o certificado cliente usando um comportamento de ponto final.</span><span class="sxs-lookup"><span data-stu-id="23709-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="23709-146">Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="23709-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="23709-147">O código também `identity` usa um elemento> <para especificar um DNS (Domain Name System, sistema de nome de domínio) da identidade de servidor esperada.</span><span class="sxs-lookup"><span data-stu-id="23709-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="23709-148">Para obter mais informações sobre identidade, consulte [Identidade de Serviço e Autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="23709-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23709-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="23709-149">See also</span></span>

- [<span data-ttu-id="23709-150">Visão geral da segurança</span><span class="sxs-lookup"><span data-stu-id="23709-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="23709-151">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="23709-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="23709-152">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="23709-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- <span data-ttu-id="23709-153">[Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="23709-153">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
