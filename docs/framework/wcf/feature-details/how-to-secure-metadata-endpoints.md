---
title: 'Como: proteger pontos de extremidade de metadados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c6439187560e15ec10f1eea4e1731421904e8643
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045291"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="e244e-102">Como: proteger pontos de extremidade de metadados</span><span class="sxs-lookup"><span data-stu-id="e244e-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="e244e-103">Os metadados de um serviço podem conter informações confidenciais sobre o aplicativo que um usuário mal-intencionado pode aproveitar.</span><span class="sxs-lookup"><span data-stu-id="e244e-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="e244e-104">Os consumidores do seu serviço também podem exigir um mecanismo seguro para obter metadados sobre seu serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="e244e-105">Portanto, às vezes é necessário publicar seus metadados usando um ponto de extremidade seguro.</span><span class="sxs-lookup"><span data-stu-id="e244e-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="e244e-106">Os pontos de extremidade de metadados são geralmente protegidos usando os mecanismos de segurança padrão definidos no Windows Communication Foundation (WCF) para proteger os pontos de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e244e-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="e244e-107">(Para obter mais informações, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="e244e-107">(For more information, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>

<span data-ttu-id="e244e-108">Este tópico percorre as etapas para criar um ponto de extremidade protegido por um certificado protocolo SSL (SSL) ou, em outras palavras, um ponto de extremidade HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e244e-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="e244e-109">Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro no código</span><span class="sxs-lookup"><span data-stu-id="e244e-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="e244e-110">Configure uma porta com um certificado X. 509 apropriado.</span><span class="sxs-lookup"><span data-stu-id="e244e-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="e244e-111">O certificado deve vir de uma autoridade confiável e deve ter um uso pretendido de "autorização de serviço".</span><span class="sxs-lookup"><span data-stu-id="e244e-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="e244e-112">Você deve usar a ferramenta HttpCfg. exe para anexar o certificado à porta.</span><span class="sxs-lookup"><span data-stu-id="e244e-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="e244e-113">Confira [Como Configure uma porta com um certificado](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)SSL.</span><span class="sxs-lookup"><span data-stu-id="e244e-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e244e-114">O assunto do certificado ou seu DNS (sistema de nomes de domínio) deve corresponder ao nome do computador.</span><span class="sxs-lookup"><span data-stu-id="e244e-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="e244e-115">Isso é essencial porque uma das primeiras etapas que o mecanismo HTTPS executa é verificar se o certificado é emitido para o mesmo Uniform Resource Identifier (URI) que o endereço no qual ele é invocado.</span><span class="sxs-lookup"><span data-stu-id="e244e-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="e244e-116">Criar uma nova instância da classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e244e-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="e244e-117">Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da classe como `true`.</span><span class="sxs-lookup"><span data-stu-id="e244e-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="e244e-118">Defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Propriedade como uma URL apropriada.</span><span class="sxs-lookup"><span data-stu-id="e244e-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="e244e-119">Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="e244e-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="e244e-120">Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="e244e-121">Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="e244e-122">Adicione a instância à coleção <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> de comportamentos que a propriedade da classe retorna, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e244e-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="e244e-123">Para criar um ponto de extremidade de obtenção de metadados de HTTPS seguro na configuração</span><span class="sxs-lookup"><span data-stu-id="e244e-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="e244e-124">Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento de > de comportamentos ao [ \<elemento System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) do arquivo de configuração para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="e244e-125">Adicione um elemento de [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) de portais ao [ \<elemento comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="e244e-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="e244e-126">Adicione um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elemento de > de comportamento `<serviceBehaviors>` ao elemento.</span><span class="sxs-lookup"><span data-stu-id="e244e-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="e244e-127">Defina o `name` atributo `<behavior>` do elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e244e-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="e244e-128">O atributo `name` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e244e-128">The `name` attribute is required.</span></span> <span data-ttu-id="e244e-129">O exemplo a seguir usa o `mySvcBehavior`valor.</span><span class="sxs-lookup"><span data-stu-id="e244e-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="e244e-130">Adicione [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) um`<behavior>` > de metadados ao elemento.</span><span class="sxs-lookup"><span data-stu-id="e244e-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="e244e-131">Defina o atributo `httpsGetEnabled` do elemento `<serviceMetadata>` como `true`.</span><span class="sxs-lookup"><span data-stu-id="e244e-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="e244e-132">Defina o `httpsGetUrl` atributo `<serviceMetadata>` do elemento para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e244e-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="e244e-133">Observe que, se você especificar um endereço absoluto, a URL deverá começar com o esquema "https://".</span><span class="sxs-lookup"><span data-stu-id="e244e-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="e244e-134">Se você especificar um endereço relativo, deverá fornecer um endereço base HTTPS para seu host de serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="e244e-135">Se essa propriedade não for definida, o endereço padrão será "", ou diretamente no endereço base HTTPS para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e244e-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="e244e-136">Para usar o comportamento com um serviço, defina o `behaviorConfiguration` atributo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) do elemento > do serviço como o valor do atributo Name do elemento Behavior.</span><span class="sxs-lookup"><span data-stu-id="e244e-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="e244e-137">O código de configuração a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="e244e-137">The following configuration code shows a complete example.</span></span>

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

## <a name="example"></a><span data-ttu-id="e244e-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e244e-138">Example</span></span>

<span data-ttu-id="e244e-139">O exemplo a seguir cria uma instância de <xref:System.ServiceModel.ServiceHost> uma classe e adiciona um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e244e-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="e244e-140">Em seguida, o código cria uma instância <xref:System.ServiceModel.Description.ServiceMetadataBehavior> da classe e define as propriedades para criar um ponto de troca de metadados seguro.</span><span class="sxs-lookup"><span data-stu-id="e244e-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="e244e-141">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e244e-141">Compiling the Code</span></span>

<span data-ttu-id="e244e-142">O exemplo de código usa os seguintes namespaces:</span><span class="sxs-lookup"><span data-stu-id="e244e-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="e244e-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e244e-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="e244e-144">Como: Configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="e244e-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="e244e-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="e244e-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e244e-146">Considerações de segurança com metadados</span><span class="sxs-lookup"><span data-stu-id="e244e-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="e244e-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e244e-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
