---
title: Segurança de mensagem com certificados mútuos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 44d06762bf66950ea0cc06986c61ecd548ae2e0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576402"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="b354b-102">Segurança de mensagem com certificados mútuos</span><span class="sxs-lookup"><span data-stu-id="b354b-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="b354b-103">O cenário a seguir mostra um serviço de Windows Communication Foundation (WCF) e o cliente protegidos usando o modo de segurança da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b354b-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="b354b-104">O cliente e o serviço são autenticados com certificados.</span><span class="sxs-lookup"><span data-stu-id="b354b-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="b354b-105">Esse cenário é interoperável porque usa o WS-Security com o perfil de token de certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b354b-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b354b-106">Esse cenário não realiza a negociação do certificado de serviço.</span><span class="sxs-lookup"><span data-stu-id="b354b-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="b354b-107">O certificado de serviço deve ser fornecido ao cliente antes de qualquer comunicação.</span><span class="sxs-lookup"><span data-stu-id="b354b-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="b354b-108">O certificado do servidor pode ser distribuído com o aplicativo ou fornecido em uma comunicação fora de banda.</span><span class="sxs-lookup"><span data-stu-id="b354b-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="b354b-109">![Segurança de mensagem com certificados mútuos](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="b354b-109">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="b354b-110">Característica</span><span class="sxs-lookup"><span data-stu-id="b354b-110">Characteristic</span></span>|<span data-ttu-id="b354b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="b354b-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b354b-112">Modo de segurança</span><span class="sxs-lookup"><span data-stu-id="b354b-112">Security Mode</span></span>|<span data-ttu-id="b354b-113">Mensagem</span><span class="sxs-lookup"><span data-stu-id="b354b-113">Message</span></span>|  
|<span data-ttu-id="b354b-114">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b354b-114">Interoperability</span></span>|<span data-ttu-id="b354b-115">Sim, com serviços e clientes compatíveis com o perfil de token de certificado do WS-Security e X. 509.</span><span class="sxs-lookup"><span data-stu-id="b354b-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="b354b-116">Autenticação</span><span class="sxs-lookup"><span data-stu-id="b354b-116">Authentication</span></span>|<span data-ttu-id="b354b-117">Autenticação mútua do servidor e do cliente.</span><span class="sxs-lookup"><span data-stu-id="b354b-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="b354b-118">Integridade</span><span class="sxs-lookup"><span data-stu-id="b354b-118">Integrity</span></span>|<span data-ttu-id="b354b-119">Sim</span><span class="sxs-lookup"><span data-stu-id="b354b-119">Yes</span></span>|  
|<span data-ttu-id="b354b-120">Confidencialidade</span><span class="sxs-lookup"><span data-stu-id="b354b-120">Confidentiality</span></span>|<span data-ttu-id="b354b-121">Sim</span><span class="sxs-lookup"><span data-stu-id="b354b-121">Yes</span></span>|  
|<span data-ttu-id="b354b-122">Transport</span><span class="sxs-lookup"><span data-stu-id="b354b-122">Transport</span></span>|<span data-ttu-id="b354b-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="b354b-123">HTTP</span></span>|  
|<span data-ttu-id="b354b-124">Associação</span><span class="sxs-lookup"><span data-stu-id="b354b-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="b354b-125">Serviço</span><span class="sxs-lookup"><span data-stu-id="b354b-125">Service</span></span>  
 <span data-ttu-id="b354b-126">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="b354b-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b354b-127">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b354b-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="b354b-128">Crie um serviço autônomo usando o código sem configuração.</span><span class="sxs-lookup"><span data-stu-id="b354b-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="b354b-129">Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b354b-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b354b-130">Código</span><span class="sxs-lookup"><span data-stu-id="b354b-130">Code</span></span>  
 <span data-ttu-id="b354b-131">O código a seguir mostra como criar um ponto de extremidade de serviço que usa a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b354b-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="b354b-132">O serviço requer um certificado para se autenticar.</span><span class="sxs-lookup"><span data-stu-id="b354b-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="b354b-133">Configuração</span><span class="sxs-lookup"><span data-stu-id="b354b-133">Configuration</span></span>  
 <span data-ttu-id="b354b-134">A configuração a seguir pode ser usada em vez do código para criar o mesmo serviço.</span><span class="sxs-lookup"><span data-stu-id="b354b-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="b354b-135">Cliente</span><span class="sxs-lookup"><span data-stu-id="b354b-135">Client</span></span>  
 <span data-ttu-id="b354b-136">O código e a configuração a seguir devem ser executados de forma independente.</span><span class="sxs-lookup"><span data-stu-id="b354b-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="b354b-137">Realize um dos seguintes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="b354b-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="b354b-138">Crie um cliente autônomo usando o código (e o código do cliente).</span><span class="sxs-lookup"><span data-stu-id="b354b-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="b354b-139">Crie um cliente que não defina nenhum endereço de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b354b-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="b354b-140">Em vez disso, use o construtor do cliente que usa o nome da configuração como um argumento.</span><span class="sxs-lookup"><span data-stu-id="b354b-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="b354b-141">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b354b-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="b354b-142">Código</span><span class="sxs-lookup"><span data-stu-id="b354b-142">Code</span></span>  
 <span data-ttu-id="b354b-143">O código a seguir cria o cliente.</span><span class="sxs-lookup"><span data-stu-id="b354b-143">The following code creates the client.</span></span> <span data-ttu-id="b354b-144">O modo de segurança é definido como mensagem e o tipo de credencial do cliente é definido como certificado.</span><span class="sxs-lookup"><span data-stu-id="b354b-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="b354b-145">Configuração</span><span class="sxs-lookup"><span data-stu-id="b354b-145">Configuration</span></span>  
 <span data-ttu-id="b354b-146">O seguinte configura o cliente.</span><span class="sxs-lookup"><span data-stu-id="b354b-146">The following configures the client.</span></span> <span data-ttu-id="b354b-147">Um certificado de cliente deve ser especificado usando o [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b354b-147">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="b354b-148">Além disso, o certificado de serviço é especificado usando o [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b354b-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b354b-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b354b-149">See also</span></span>

- [<span data-ttu-id="b354b-150">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="b354b-150">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b354b-151">[Modelo de segurança para o Windows Server app Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b354b-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="b354b-152">[Como: criar e instalar certificados temporários no WCF para segurança de transporte durante o desenvolvimento](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="b354b-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
