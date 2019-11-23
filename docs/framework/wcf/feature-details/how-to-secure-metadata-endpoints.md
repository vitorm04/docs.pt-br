---
title: Como proteger pontos de extremidade de metadados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834685"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="a63b0-102">Como proteger pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="a63b0-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="a63b0-103">Os metadados de um serviço podem conter informações confidenciais sobre o aplicativo que um usuário mal-intencionado pode aproveitar.</span><span class="sxs-lookup"><span data-stu-id="a63b0-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="a63b0-104">Os consumidores do seu serviço também podem exigir um mecanismo seguro para obter metadados sobre seu serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="a63b0-105">Portanto, às vezes é necessário publicar seus metadados usando um ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="a63b0-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="a63b0-106">Os pontos de extremidade de metadados são geralmente protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger os pontos de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a63b0-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="a63b0-107">Para obter mais informações, consulte [visão geral de segurança](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a63b0-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="a63b0-108">Este tópico percorre as etapas para criar um ponto de extremidade protegido por um certificado protocolo SSL (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a63b0-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="a63b0-109">Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro no código</span><span class="sxs-lookup"><span data-stu-id="a63b0-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="a63b0-110">Configure uma porta com um certificado X. 509 apropriado.</span><span class="sxs-lookup"><span data-stu-id="a63b0-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="a63b0-111">O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido de "autorização de serviço".</span><span class="sxs-lookup"><span data-stu-id="a63b0-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="a63b0-112">Você deve usar a ferramenta HttpCfg. exe para anexar o certificado à porta.</span><span class="sxs-lookup"><span data-stu-id="a63b0-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="a63b0-113">Consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a63b0-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a63b0-114">O assunto do certificado ou seu DNS (sistema de nomes de domínio) deve corresponder ao nome do computador.</span><span class="sxs-lookup"><span data-stu-id="a63b0-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="a63b0-115">Isso é essencial porque uma das primeiras etapas que o mecanismo HTTPS executa é verificar se o certificado é emitido para o mesmo Uniform Resource Identifier (URI) que o endereço no qual ele é invocado.</span><span class="sxs-lookup"><span data-stu-id="a63b0-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="a63b0-116">Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a63b0-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="a63b0-117">Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> como `true`.</span><span class="sxs-lookup"><span data-stu-id="a63b0-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="a63b0-118">Defina a propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> como uma URL apropriada.</span><span class="sxs-lookup"><span data-stu-id="a63b0-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="a63b0-119">Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="a63b0-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="a63b0-120">Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="a63b0-121">Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="a63b0-122">Adicione a instância à coleção de comportamentos que a propriedade <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> da classe <xref:System.ServiceModel.Description.ServiceDescription> retorna, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a63b0-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="a63b0-123">Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro na configuração</span><span class="sxs-lookup"><span data-stu-id="a63b0-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="a63b0-124">Adicione um elemento [> Behaviors de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) ao elemento [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) do arquivo de configuração para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="a63b0-125">Adicione um elemento de [> de\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) de portais ao elemento [> comportamentos de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="a63b0-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="a63b0-126">Adicione um elemento de [comportamento de\<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) ao elemento `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="a63b0-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="a63b0-127">Defina o atributo `name` do elemento `<behavior>` como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="a63b0-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="a63b0-128">O atributo `name` é necessário.</span><span class="sxs-lookup"><span data-stu-id="a63b0-128">The `name` attribute is required.</span></span> <span data-ttu-id="a63b0-129">O exemplo a seguir usa o valor `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="a63b0-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="a63b0-130">Adicione um [> de\<de metadados](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ao elemento `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="a63b0-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="a63b0-131">Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.</span><span class="sxs-lookup"><span data-stu-id="a63b0-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="a63b0-132">Defina o atributo `httpsGetUrl` do elemento `<serviceMetadata>` como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="a63b0-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="a63b0-133">Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="a63b0-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="a63b0-134">Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="a63b0-135">Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a63b0-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="a63b0-136">Para usar o comportamento com um serviço, defina o atributo `behaviorConfiguration` do elemento [\<do serviço de >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) como o valor do atributo Name do elemento Behavior.</span><span class="sxs-lookup"><span data-stu-id="a63b0-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="a63b0-137">O código de configuração a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="a63b0-137">The following configuration code shows a complete example.</span></span>

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

## <a name="example"></a><span data-ttu-id="a63b0-138">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a63b0-138">Example</span></span>

<span data-ttu-id="a63b0-139">O exemplo a seguir cria uma instância de uma classe <xref:System.ServiceModel.ServiceHost> e adiciona um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a63b0-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="a63b0-140">Em seguida, o código cria uma instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e define as propriedades para criar um ponto de troca de metadados seguro.</span><span class="sxs-lookup"><span data-stu-id="a63b0-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="a63b0-141">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="a63b0-141">Compiling the Code</span></span>

<span data-ttu-id="a63b0-142">O exemplo de código usa os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="a63b0-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="a63b0-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a63b0-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="a63b0-144">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="a63b0-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="a63b0-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a63b0-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a63b0-146">Considerações de segurança com metadados</span><span class="sxs-lookup"><span data-stu-id="a63b0-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="a63b0-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a63b0-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
