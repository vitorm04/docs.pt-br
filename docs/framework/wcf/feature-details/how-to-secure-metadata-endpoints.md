---
title: Como proteger pontos de extremidade de metadados
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
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6923703230d6792d8938de149f64c41a3bf95699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="9846c-102">Como proteger pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="9846c-102">How to: Secure Metadata Endpoints</span></span>
<span data-ttu-id="9846c-103">Metadados para um serviço podem conter informações confidenciais sobre seu aplicativo que um usuário mal-intencionado pode aproveitar.</span><span class="sxs-lookup"><span data-stu-id="9846c-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="9846c-104">Os consumidores de serviço também podem exigir um mecanismo seguro para obtenção de metadados sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="9846c-105">Portanto, às vezes, é necessário publicar seus metadados usando um ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="9846c-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>  
  
 <span data-ttu-id="9846c-106">Pontos de extremidade de metadados geralmente são protegidos por meio de mecanismos de segurança padrão definidos em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para proteger pontos de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9846c-106">Metadata endpoints are generally secured using the standard security mechanisms defined in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] for securing application endpoints.</span></span> <span data-ttu-id="9846c-107">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="9846c-107">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>  
  
 <span data-ttu-id="9846c-108">Este tópico explica as etapas para criar um ponto de extremidade protegido por um certificado Secure Sockets Layer (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9846c-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="9846c-109">Para criar uma empresa de metadados de obter HTTPS segura no código</span><span class="sxs-lookup"><span data-stu-id="9846c-109">To create a secure HTTPS GET metadata endpoint in code</span></span>  
  
1.  <span data-ttu-id="9846c-110">Configure uma porta com um certificado x. 509 apropriado.</span><span class="sxs-lookup"><span data-stu-id="9846c-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="9846c-111">O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido do "Serviço autorização".</span><span class="sxs-lookup"><span data-stu-id="9846c-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="9846c-112">Você deve usar a ferramenta HttpCfg.exe para anexar o certificado para a porta.</span><span class="sxs-lookup"><span data-stu-id="9846c-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="9846c-113">Consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="9846c-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9846c-114">O assunto do certificado ou seu sistema de nome de domínio (DNS) deve corresponder ao nome do computador.</span><span class="sxs-lookup"><span data-stu-id="9846c-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="9846c-115">Isso é essencial porque uma das primeiras etapas que executa o mecanismo HTTPS é verificar se o certificado é emitido para o mesmo URI Uniform Resource Identifier () como o endereço no qual ele é invocado.</span><span class="sxs-lookup"><span data-stu-id="9846c-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>  
  
2.  <span data-ttu-id="9846c-116">Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9846c-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>  
  
3.  <span data-ttu-id="9846c-117">Definir o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de classe para `true`.</span><span class="sxs-lookup"><span data-stu-id="9846c-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>  
  
4.  <span data-ttu-id="9846c-118">Definir o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> propriedade em uma URL apropriada.</span><span class="sxs-lookup"><span data-stu-id="9846c-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="9846c-119">Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="9846c-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="9846c-120">Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="9846c-121">Se essa propriedade não é definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
5.  <span data-ttu-id="9846c-122">Adicionar a instância para a coleção de comportamentos que o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade o <xref:System.ServiceModel.Description.ServiceDescription> classe retorna, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9846c-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="9846c-123">Para criar uma empresa de metadados de obter HTTPS segura na configuração</span><span class="sxs-lookup"><span data-stu-id="9846c-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>  
  
1.  <span data-ttu-id="9846c-124">Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento do arquivo de configuração para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>  
  
2.  <span data-ttu-id="9846c-125">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9846c-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="9846c-126">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento para o `<serviceBehaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9846c-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>  
  
4.  <span data-ttu-id="9846c-127">Definir o `name` atributo do `<behavior>` elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="9846c-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="9846c-128">O atributo `name` é necessário.</span><span class="sxs-lookup"><span data-stu-id="9846c-128">The `name` attribute is required.</span></span> <span data-ttu-id="9846c-129">O exemplo a seguir usa o valor `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="9846c-129">The example below uses the value `mySvcBehavior`.</span></span>  
  
5.  <span data-ttu-id="9846c-130">Adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) para o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9846c-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>  
  
6.  <span data-ttu-id="9846c-131">Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.</span><span class="sxs-lookup"><span data-stu-id="9846c-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>  
  
7.  <span data-ttu-id="9846c-132">Definir o `httpsGetUrl` atributo do `<serviceMetadata>` elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="9846c-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="9846c-133">Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="9846c-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="9846c-134">Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="9846c-135">Se essa propriedade não é definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9846c-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
8.  <span data-ttu-id="9846c-136">Para usar o comportamento com um serviço, defina o `behaviorConfiguration` atributo do [ \<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento para o valor do atributo name do elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="9846c-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="9846c-137">O código de configuração a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="9846c-137">The following configuration code shows a complete example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="mySvcBehavior">  
         <serviceMetadata httpsGetEnabled="true"   
              httpsGetUrl="https://localhost:8036/calcMetadata" />  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
     <services>  
      <service behaviorConfiguration="mySvcBehavior"   
            name="Microsoft.Security.Samples.Calculator">  
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"  
       binding="wsHttpBinding" bindingConfiguration=""     
       contract="Microsoft.Security.Samples.ICalculator" />  
      </service>  
     </services>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="9846c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9846c-138">Example</span></span>  
 <span data-ttu-id="9846c-139">O exemplo a seguir cria uma instância de um <xref:System.ServiceModel.ServiceHost> classe e adiciona um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9846c-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="9846c-140">O código, em seguida, cria uma instância do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> classe e define as propriedades para criar um ponto de troca de metadados seguros.</span><span class="sxs-lookup"><span data-stu-id="9846c-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9846c-141">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9846c-141">Compiling the Code</span></span>  
 <span data-ttu-id="9846c-142">O exemplo de código usa os namespaces a seguir:</span><span class="sxs-lookup"><span data-stu-id="9846c-142">The code example uses the following namespaces:</span></span>  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="9846c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9846c-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="9846c-144">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="9846c-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="9846c-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="9846c-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="9846c-146">Considerações de segurança com metadados</span><span class="sxs-lookup"><span data-stu-id="9846c-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [<span data-ttu-id="9846c-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9846c-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
