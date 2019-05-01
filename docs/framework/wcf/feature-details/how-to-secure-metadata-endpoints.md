---
title: 'Como: proteger pontos de extremidade de metadados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 8481048dd31652a69f9284a44145bd4abfed89bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047562"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="98490-102">Como: proteger pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="98490-102">How to: Secure Metadata Endpoints</span></span>
<span data-ttu-id="98490-103">Metadados para um serviço podem conter informações confidenciais sobre seu aplicativo que um usuário mal-intencionado pode aproveitar.</span><span class="sxs-lookup"><span data-stu-id="98490-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="98490-104">Os consumidores do seu serviço também podem exigir um mecanismo seguro para obtenção de metadados sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="98490-105">Portanto, às vezes, é necessário publicar seus metadados usando um ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="98490-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>  
  
 <span data-ttu-id="98490-106">Pontos de extremidade de metadados geralmente são protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger pontos de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98490-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="98490-107">(Para obter mais informações, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="98490-107">(For more information, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>  
  
 <span data-ttu-id="98490-108">Este tópico explica as etapas para criar um ponto de extremidade protegido por um certificado Secure Sockets Layer (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="98490-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="98490-109">Para criar uma empresa de metadados de HTTPS GET segura no código</span><span class="sxs-lookup"><span data-stu-id="98490-109">To create a secure HTTPS GET metadata endpoint in code</span></span>  
  
1. <span data-ttu-id="98490-110">Configure uma porta com um certificado x. 509 apropriado.</span><span class="sxs-lookup"><span data-stu-id="98490-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="98490-111">O certificado deve vir de uma autoridade confiável, e deve ter um uso pretendido do "Autorização de serviço".</span><span class="sxs-lookup"><span data-stu-id="98490-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="98490-112">Você deve usar a ferramenta HttpCfg.exe para anexar o certificado à porta.</span><span class="sxs-lookup"><span data-stu-id="98490-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="98490-113">Confira [Como Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="98490-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="98490-114">O assunto do certificado ou seu sistema de nome de domínio (DNS) deve corresponder ao nome do computador.</span><span class="sxs-lookup"><span data-stu-id="98490-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="98490-115">Isso é essencial porque uma das primeiras etapas que executa o mecanismo HTTPS é verificar se o certificado é emitido para o mesmo identificador de URI (Uniform Resource) como o endereço no qual ele é invocado.</span><span class="sxs-lookup"><span data-stu-id="98490-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>  
  
2. <span data-ttu-id="98490-116">Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="98490-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>  
  
3. <span data-ttu-id="98490-117">Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> classe para `true`.</span><span class="sxs-lookup"><span data-stu-id="98490-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>  
  
4. <span data-ttu-id="98490-118">Defina o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> propriedade para uma URL apropriada.</span><span class="sxs-lookup"><span data-stu-id="98490-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="98490-119">Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="98490-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="98490-120">Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="98490-121">Se essa propriedade não for definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
5. <span data-ttu-id="98490-122">Adicionar a instância à coleção de comportamentos que o <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade do <xref:System.ServiceModel.Description.ServiceDescription> classe retorna, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="98490-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="98490-123">Para criar uma empresa de metadados de HTTPS GET segura na configuração</span><span class="sxs-lookup"><span data-stu-id="98490-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>  
  
1. <span data-ttu-id="98490-124">Adicionar um [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento para o [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento do arquivo de configuração para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>  
  
2. <span data-ttu-id="98490-125">Adicionar um [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="98490-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
3. <span data-ttu-id="98490-126">Adicionar um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento para o `<serviceBehaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="98490-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>  
  
4. <span data-ttu-id="98490-127">Defina as `name` atributo do `<behavior>` elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="98490-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="98490-128">O atributo `name` é necessário.</span><span class="sxs-lookup"><span data-stu-id="98490-128">The `name` attribute is required.</span></span> <span data-ttu-id="98490-129">O exemplo a seguir usa o valor `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="98490-129">The example below uses the value `mySvcBehavior`.</span></span>  
  
5. <span data-ttu-id="98490-130">Adicionar um [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) para o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="98490-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>  
  
6. <span data-ttu-id="98490-131">Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.</span><span class="sxs-lookup"><span data-stu-id="98490-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>  
  
7. <span data-ttu-id="98490-132">Defina as `httpsGetUrl` atributo do `<serviceMetadata>` elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="98490-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="98490-133">Observe que, se você especificar um endereço absoluto, a URL deve começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="98490-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="98490-134">Se você especificar um endereço relativo, você deve fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="98490-135">Se essa propriedade não for definida, o endereço padrão é "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="98490-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
8. <span data-ttu-id="98490-136">Para usar o comportamento com um serviço, defina a `behaviorConfiguration` atributo o [ \<serviço >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elemento como o valor do atributo name do elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="98490-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="98490-137">O código de configuração a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="98490-137">The following configuration code shows a complete example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="98490-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98490-138">Example</span></span>  
 <span data-ttu-id="98490-139">O exemplo a seguir cria uma instância de um <xref:System.ServiceModel.ServiceHost> de classe e adiciona um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="98490-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="98490-140">O código então cria uma instância da <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de classe e define as propriedades para criar um ponto de troca de metadados seguros.</span><span class="sxs-lookup"><span data-stu-id="98490-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98490-141">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="98490-141">Compiling the Code</span></span>  
 <span data-ttu-id="98490-142">O exemplo de código usa os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="98490-142">The code example uses the following namespaces:</span></span>  
  
- <xref:System.ServiceModel?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="98490-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98490-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="98490-144">Como: Configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="98490-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="98490-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="98490-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="98490-146">Considerações de segurança com metadados</span><span class="sxs-lookup"><span data-stu-id="98490-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="98490-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="98490-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
