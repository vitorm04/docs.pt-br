---
title: Segurança de mensagem com certificados mútuos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ad5862064966ccae4c313e7fa3d982ec9abbbcd2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399798"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="8b915-102">Segurança de mensagem com certificados mútuos</span><span class="sxs-lookup"><span data-stu-id="8b915-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="8b915-103">O cenário a seguir mostra um serviço Windows Communication Foundation (WCF) e o cliente protegido usando o modo de segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8b915-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="8b915-104">O cliente e o serviço são autenticados com certificados.</span><span class="sxs-lookup"><span data-stu-id="8b915-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="8b915-105">Esse cenário é interoperável, porque ele usa o WS-Security com o perfil de token X.509 do certificado.</span><span class="sxs-lookup"><span data-stu-id="8b915-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b915-106">Esse cenário não realiza a negociação do certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="8b915-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="8b915-107">O certificado de serviço deve ser fornecido ao cliente com antecedência sobre qualquer comunicação.</span><span class="sxs-lookup"><span data-stu-id="8b915-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="8b915-108">O certificado do servidor pode ser distribuído com o aplicativo ou fornecido em uma comunicação fora da banda.</span><span class="sxs-lookup"><span data-stu-id="8b915-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="8b915-109">![Mensagem de segurança com certificados mútuos](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="8b915-109">![Message security with mutual certificates](../../../../docs/framework/wcf/feature-details/media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="8b915-110">Característica</span><span class="sxs-lookup"><span data-stu-id="8b915-110">Characteristic</span></span>|<span data-ttu-id="8b915-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b915-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8b915-112">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="8b915-112">Security Mode</span></span>|<span data-ttu-id="8b915-113">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8b915-113">Message</span></span>|  
|<span data-ttu-id="8b915-114">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8b915-114">Interoperability</span></span>|<span data-ttu-id="8b915-115">Sim, com serviços e clientes compatíveis do perfil de token de certificado X.509 e WS-Security.</span><span class="sxs-lookup"><span data-stu-id="8b915-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="8b915-116">Autenticação</span><span class="sxs-lookup"><span data-stu-id="8b915-116">Authentication</span></span>|<span data-ttu-id="8b915-117">Autenticação mútua do servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="8b915-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="8b915-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="8b915-118">Integrity</span></span>|<span data-ttu-id="8b915-119">Sim</span><span class="sxs-lookup"><span data-stu-id="8b915-119">Yes</span></span>|  
|<span data-ttu-id="8b915-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="8b915-120">Confidentiality</span></span>|<span data-ttu-id="8b915-121">Sim</span><span class="sxs-lookup"><span data-stu-id="8b915-121">Yes</span></span>|  
|<span data-ttu-id="8b915-122">Transporte</span><span class="sxs-lookup"><span data-stu-id="8b915-122">Transport</span></span>|<span data-ttu-id="8b915-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="8b915-123">HTTP</span></span>|  
|<span data-ttu-id="8b915-124">Associação</span><span class="sxs-lookup"><span data-stu-id="8b915-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="8b915-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="8b915-125">Service</span></span>  
 <span data-ttu-id="8b915-126">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="8b915-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b915-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="8b915-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8b915-128">Crie um serviço autônomo usando o código sem nenhuma configuração.</span><span class="sxs-lookup"><span data-stu-id="8b915-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="8b915-129">Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8b915-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8b915-130">Código</span><span class="sxs-lookup"><span data-stu-id="8b915-130">Code</span></span>  
 <span data-ttu-id="8b915-131">Mostra o código a seguir cria um ponto de extremidade de serviço que usa segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8b915-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="8b915-132">O serviço requer um certificado para se autenticar.</span><span class="sxs-lookup"><span data-stu-id="8b915-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="8b915-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="8b915-133">Configuration</span></span>  
 <span data-ttu-id="8b915-134">A configuração a seguir pode ser usada em vez do código para criar o mesmo serviço.</span><span class="sxs-lookup"><span data-stu-id="8b915-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"   
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="8b915-135">Cliente</span><span class="sxs-lookup"><span data-stu-id="8b915-135">Client</span></span>  
 <span data-ttu-id="8b915-136">O código e a configuração a seguir destinam-se para executar de forma independente.</span><span class="sxs-lookup"><span data-stu-id="8b915-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8b915-137">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="8b915-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="8b915-138">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="8b915-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="8b915-139">Crie um cliente que não define os endereços de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8b915-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8b915-140">Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="8b915-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8b915-141">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8b915-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8b915-142">Código</span><span class="sxs-lookup"><span data-stu-id="8b915-142">Code</span></span>  
 <span data-ttu-id="8b915-143">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="8b915-143">The following code creates the client.</span></span> <span data-ttu-id="8b915-144">O modo de segurança é definido como mensagem e o tipo de credencial de cliente está definido como Certificate.</span><span class="sxs-lookup"><span data-stu-id="8b915-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="8b915-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="8b915-145">Configuration</span></span>  
 <span data-ttu-id="8b915-146">O exemplo a seguir configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="8b915-146">The following configures the client.</span></span> <span data-ttu-id="8b915-147">Um certificado de cliente deve ser especificado usando o [ \<clientCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="8b915-147">A client certificate must be specified using the [\<clientCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="8b915-148">Além disso, o certificado de serviço é especificado usando o [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="8b915-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"   
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b915-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b915-149">See Also</span></span>  
 [<span data-ttu-id="8b915-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="8b915-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="8b915-151">Modelo de segurança do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="8b915-151">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)  
 [<span data-ttu-id="8b915-152">Como: criar e instalar certificados temporários no WCF para segurança de transporte durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="8b915-152">How to: Create and Install Temporary Certificates in WCF for Transport Security During Development</span></span>](https://go.microsoft.com/fwlink/?LinkId=244264)
