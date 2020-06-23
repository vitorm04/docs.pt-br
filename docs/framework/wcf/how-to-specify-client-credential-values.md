---
title: Como especificar valores de credenciais de cliente
description: Saiba como um serviço WCF pode especificar como um cliente é autenticado nesse serviço. Este exemplo especifica um certificado X. 509 e o modo de transporte.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244446"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="b21b3-104">Como especificar valores de credenciais de cliente</span><span class="sxs-lookup"><span data-stu-id="b21b3-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="b21b3-105">Usando o Windows Communication Foundation (WCF), o serviço pode especificar como um cliente é autenticado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b21b3-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="b21b3-106">Por exemplo, um serviço pode estipular que o cliente seja autenticado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="b21b3-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="b21b3-107">Para determinar o tipo de credencial do cliente</span><span class="sxs-lookup"><span data-stu-id="b21b3-107">To determine the client credential type</span></span>

1. <span data-ttu-id="b21b3-108">Recuperar metadados do ponto de extremidade de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="b21b3-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="b21b3-109">Os metadados geralmente consistem em dois arquivos: o código do cliente na linguagem de programação de sua escolha (o padrão é o Visual C#) e um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="b21b3-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="b21b3-110">Uma maneira de recuperar metadados é usar a ferramenta Svcutil.exe para retornar o código do cliente e a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="b21b3-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="b21b3-111">Para obter mais informações, consulte [Recuperando metadados](./feature-details/retrieving-metadata.md) e [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b21b3-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="b21b3-112">Abra o arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="b21b3-112">Open the XML configuration file.</span></span> <span data-ttu-id="b21b3-113">Se você usar a ferramenta Svcutil.exe, o nome padrão do arquivo será Output.config.</span><span class="sxs-lookup"><span data-stu-id="b21b3-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="b21b3-114">Localize o **\<security>** elemento com o atributo **Mode** ( **\<security mode =**`MessageOrTransport`**>** em que `MessageOrTransport` é definido como um dos modos de segurança.</span><span class="sxs-lookup"><span data-stu-id="b21b3-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="b21b3-115">Localize o elemento filho que corresponde ao valor de modo.</span><span class="sxs-lookup"><span data-stu-id="b21b3-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="b21b3-116">Por exemplo, se o modo for definido como **Message**, localize o **\<message>** elemento contido no **\<security>** elemento.</span><span class="sxs-lookup"><span data-stu-id="b21b3-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="b21b3-117">Observe o valor atribuído ao atributo **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="b21b3-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="b21b3-118">O valor real depende de qual modo é usado, transporte ou mensagem.</span><span class="sxs-lookup"><span data-stu-id="b21b3-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="b21b3-119">O código XML a seguir mostra a configuração de um cliente usando a segurança de mensagem e exigindo um certificado para autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="b21b3-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="b21b3-120">Exemplo: modo de transporte TCP com certificado como credencial do cliente</span><span class="sxs-lookup"><span data-stu-id="b21b3-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="b21b3-121">Este exemplo define o modo de segurança para o modo de transporte e define o valor de credencial do cliente para um certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b21b3-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="b21b3-122">Os procedimentos a seguir demonstram como definir o valor de credencial do cliente no cliente em código e configuração.</span><span class="sxs-lookup"><span data-stu-id="b21b3-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="b21b3-123">Isso pressupõe que você tenha usado a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para retornar os metadados (código e configuração) do serviço.</span><span class="sxs-lookup"><span data-stu-id="b21b3-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="b21b3-124">Para obter mais informações, consulte [como: criar um cliente](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="b21b3-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="b21b3-125">Para especificar o valor de credencial do cliente no código</span><span class="sxs-lookup"><span data-stu-id="b21b3-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="b21b3-126">Use a [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o código e a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="b21b3-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="b21b3-127">Crie uma instância do cliente WCF usando o código gerado.</span><span class="sxs-lookup"><span data-stu-id="b21b3-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="b21b3-128">Na classe cliente, defina a <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade da <xref:System.ServiceModel.ClientBase%601> classe como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="b21b3-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="b21b3-129">Este exemplo define a propriedade como um certificado X. 509 usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.</span><span class="sxs-lookup"><span data-stu-id="b21b3-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="b21b3-130">Você pode usar qualquer uma das enumerações da <xref:System.Security.Cryptography.X509Certificates.X509FindType> classe.</span><span class="sxs-lookup"><span data-stu-id="b21b3-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="b21b3-131">O nome da entidade é usado aqui no caso de o certificado ser alterado (devido a uma data de expiração).</span><span class="sxs-lookup"><span data-stu-id="b21b3-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="b21b3-132">O uso do nome da entidade permite que a infraestrutura localize o certificado novamente.</span><span class="sxs-lookup"><span data-stu-id="b21b3-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="b21b3-133">Para especificar o valor de credencial do cliente no cliente na configuração</span><span class="sxs-lookup"><span data-stu-id="b21b3-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="b21b3-134">Adicione um [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento ao [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b21b3-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="b21b3-135">Adicione um [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elemento ao [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b21b3-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="b21b3-136">Certifique-se de definir o `name` atributo necessário para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="b21b3-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="b21b3-137">Adicione um [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elemento ao [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b21b3-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="b21b3-138">Defina os seguintes atributos para os valores apropriados: `storeLocation` ,, `storeName` `x509FindType` e `findValue` , conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b21b3-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="b21b3-139">Para obter mais informações sobre certificados, consulte [Working with Certificates](./feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="b21b3-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. <span data-ttu-id="b21b3-140">Ao configurar o cliente, especifique o comportamento definindo o `behaviorConfiguration` atributo do `<endpoint>` elemento, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b21b3-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="b21b3-141">O elemento de ponto de extremidade é um filho do [\<client>](../configure-apps/file-schema/wcf/client.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="b21b3-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="b21b3-142">Além disso, especifique o nome da configuração de associação definindo o `bindingConfiguration` atributo como a associação para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b21b3-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="b21b3-143">Se você estiver usando um arquivo de configuração gerado, o nome da Associação será gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b21b3-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="b21b3-144">Neste exemplo, o nome é `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="b21b3-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="b21b3-145">Veja também</span><span class="sxs-lookup"><span data-stu-id="b21b3-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="b21b3-146">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="b21b3-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="b21b3-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="b21b3-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b21b3-148">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="b21b3-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="b21b3-149">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b21b3-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="b21b3-150">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="b21b3-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
