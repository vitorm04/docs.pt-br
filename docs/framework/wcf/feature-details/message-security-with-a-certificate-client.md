---
title: Segurança da mensagens com um cliente de certificado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 570c7763da912de4e0d2729e7579a200f35c4941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494687"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="66d41-102">Segurança da mensagens com um cliente de certificado</span><span class="sxs-lookup"><span data-stu-id="66d41-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="66d41-103">O cenário a seguir mostra um serviço protegido usando o modo de segurança de mensagem e o cliente do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="66d41-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="66d41-104">O cliente e o serviço são autenticadas com certificados.</span><span class="sxs-lookup"><span data-stu-id="66d41-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="66d41-105">Para obter mais informações, consulte [segurança de aplicativo distribuído](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="66d41-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>  
  
 <span data-ttu-id="66d41-106">Para um aplicativo de exemplo, consulte [certificado de segurança de mensagem](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="66d41-106">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  
  
 <span data-ttu-id="66d41-107">![Cliente com certificado](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span><span class="sxs-lookup"><span data-stu-id="66d41-107">![Client with certificate](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")</span></span>  
  
|<span data-ttu-id="66d41-108">Característica</span><span class="sxs-lookup"><span data-stu-id="66d41-108">Characteristic</span></span>|<span data-ttu-id="66d41-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="66d41-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="66d41-110">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="66d41-110">Security Mode</span></span>|<span data-ttu-id="66d41-111">Mensagem</span><span class="sxs-lookup"><span data-stu-id="66d41-111">Message</span></span>|  
|<span data-ttu-id="66d41-112">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="66d41-112">Interoperability</span></span>|<span data-ttu-id="66d41-113">Somente o WCF</span><span class="sxs-lookup"><span data-stu-id="66d41-113">WCF only</span></span>|  
|<span data-ttu-id="66d41-114">Autenticação (servidor)</span><span class="sxs-lookup"><span data-stu-id="66d41-114">Authentication (Server)</span></span>|<span data-ttu-id="66d41-115">Usando o certificado de serviço</span><span class="sxs-lookup"><span data-stu-id="66d41-115">Using service certificate</span></span>|  
|<span data-ttu-id="66d41-116">Autenticação (cliente)</span><span class="sxs-lookup"><span data-stu-id="66d41-116">Authentication (Client)</span></span>|<span data-ttu-id="66d41-117">Usando o certificado de cliente</span><span class="sxs-lookup"><span data-stu-id="66d41-117">Using client certificate</span></span>|  
|<span data-ttu-id="66d41-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="66d41-118">Integrity</span></span>|<span data-ttu-id="66d41-119">Sim</span><span class="sxs-lookup"><span data-stu-id="66d41-119">Yes</span></span>|  
|<span data-ttu-id="66d41-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="66d41-120">Confidentiality</span></span>|<span data-ttu-id="66d41-121">Sim</span><span class="sxs-lookup"><span data-stu-id="66d41-121">Yes</span></span>|  
|<span data-ttu-id="66d41-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="66d41-122">Transport</span></span>|<span data-ttu-id="66d41-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="66d41-123">HTTP</span></span>|  
|<span data-ttu-id="66d41-124">Associação</span><span class="sxs-lookup"><span data-stu-id="66d41-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="66d41-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="66d41-125">Service</span></span>  
 <span data-ttu-id="66d41-126">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="66d41-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="66d41-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="66d41-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="66d41-128">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="66d41-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="66d41-129">Criar um serviço usando a configuração fornecida, mas não pode definir pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="66d41-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="66d41-130">Código</span><span class="sxs-lookup"><span data-stu-id="66d41-130">Code</span></span>  
 <span data-ttu-id="66d41-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem para estabelecer um contexto de seguro.</span><span class="sxs-lookup"><span data-stu-id="66d41-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="66d41-132">Configuração</span><span class="sxs-lookup"><span data-stu-id="66d41-132">Configuration</span></span>  
 <span data-ttu-id="66d41-133">A configuração a seguir pode ser usada em vez do código.</span><span class="sxs-lookup"><span data-stu-id="66d41-133">The following configuration can be used instead of the code.</span></span>  
  
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
                  bindingConfiguration="MessageAndCerficiateClient"   
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
  
## <a name="client"></a><span data-ttu-id="66d41-134">Cliente</span><span class="sxs-lookup"><span data-stu-id="66d41-134">Client</span></span>  
 <span data-ttu-id="66d41-135">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="66d41-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="66d41-136">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="66d41-136">Do one of the following:</span></span>  
  
-   <span data-ttu-id="66d41-137">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="66d41-137">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="66d41-138">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="66d41-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="66d41-139">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="66d41-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="66d41-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="66d41-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="66d41-141">Código</span><span class="sxs-lookup"><span data-stu-id="66d41-141">Code</span></span>  
 <span data-ttu-id="66d41-142">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="66d41-142">The following code creates the client.</span></span> <span data-ttu-id="66d41-143">A associação é a segurança de modo de mensagem e o tipo de credencial de cliente é definido como `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="66d41-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="66d41-144">Configuração</span><span class="sxs-lookup"><span data-stu-id="66d41-144">Configuration</span></span>  
 <span data-ttu-id="66d41-145">A configuração a seguir especifica o certificado de cliente usando o comportamento de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="66d41-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="66d41-146">Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="66d41-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="66d41-147">O código também usa um <`identity`> elemento para especificar um domínio nome DNS (sistema) da identidade de servidor esperadas.</span><span class="sxs-lookup"><span data-stu-id="66d41-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="66d41-148">Para obter mais informações sobre a identidade, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="66d41-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66d41-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66d41-149">See Also</span></span>  
 [<span data-ttu-id="66d41-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="66d41-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="66d41-151">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="66d41-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="66d41-152">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="66d41-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="66d41-153">Modelo de segurança para o Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="66d41-153">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
