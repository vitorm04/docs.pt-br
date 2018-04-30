---
title: Como especificar valores de credenciais de cliente
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856d33f88b55c35927998b15acc7bbf8ff1e9fe2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="16756-102">Como especificar valores de credenciais de cliente</span><span class="sxs-lookup"><span data-stu-id="16756-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="16756-103">Usando [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], o serviço pode especificar como um cliente é autenticado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16756-103">Using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="16756-104">Por exemplo, um serviço pode estipular que o cliente seja autenticado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="16756-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="16756-105">Para determinar o tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="16756-105">To determine the client credential type</span></span>  
  
1.  <span data-ttu-id="16756-106">Recupere metadados do ponto de extremidade de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="16756-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="16756-107">Os metadados normalmente consistem em dois arquivos: o código do cliente na linguagem de programação de sua escolha (o padrão é o Visual C#) e um arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="16756-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="16756-108">Uma maneira de recuperar metadados é usar a ferramenta Svcutil.exe para retornar o código do cliente e a configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="16756-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="16756-109">Para obter mais informações, consulte [recuperar metadados](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) e [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="16756-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2.  <span data-ttu-id="16756-110">Abra o arquivo de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="16756-110">Open the XML configuration file.</span></span> <span data-ttu-id="16756-111">Se você usar a ferramenta Svcutil.exe, o nome padrão do arquivo é Output.</span><span class="sxs-lookup"><span data-stu-id="16756-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3.  <span data-ttu-id="16756-112">Localizar o  **\<segurança >** elemento com o **modo** atributo (**< modo de segurança =** `MessageOrTransport` **>** onde `MessageOrTransport` é definido como um dos modos de segurança.</span><span class="sxs-lookup"><span data-stu-id="16756-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4.  <span data-ttu-id="16756-113">Localize o elemento filho que corresponde ao valor do modo.</span><span class="sxs-lookup"><span data-stu-id="16756-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="16756-114">Por exemplo, se o modo é definido como **mensagem**, localize o  **\<mensagem >** elemento contido no  **\<segurança >** elemento.</span><span class="sxs-lookup"><span data-stu-id="16756-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5.  <span data-ttu-id="16756-115">Observe o valor atribuído a **clientCredentialType** atributo.</span><span class="sxs-lookup"><span data-stu-id="16756-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="16756-116">O valor real depende de qual modo for usado, transporte ou mensagem.</span><span class="sxs-lookup"><span data-stu-id="16756-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="16756-117">O código XML a seguir mostra a configuração de um cliente usando a segurança de mensagem e que exigem um certificado autenticar o cliente.</span><span class="sxs-lookup"><span data-stu-id="16756-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="16756-118">Exemplo: O modo de transporte TCP com certificado como credenciais de cliente</span><span class="sxs-lookup"><span data-stu-id="16756-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="16756-119">Este exemplo define o modo de segurança para o modo de transporte e define o valor de credencial de cliente a um certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="16756-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="16756-120">Os procedimentos a seguir demonstram como definir o valor de credencial de cliente no código e configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="16756-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="16756-121">Isso pressupõe que você usou o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para retornar os metadados (código e configuração) do serviço.</span><span class="sxs-lookup"><span data-stu-id="16756-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="16756-122">Para obter mais informações, consulte [como: criar um cliente](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="16756-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="16756-123">Para especificar o valor de credencial de cliente no código do cliente</span><span class="sxs-lookup"><span data-stu-id="16756-123">To specify the client credential value on the client in code</span></span>  
  
1.  <span data-ttu-id="16756-124">Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o código e configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="16756-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2.  <span data-ttu-id="16756-125">Criar uma instância do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente usando o código gerado.</span><span class="sxs-lookup"><span data-stu-id="16756-125">Create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client using the generated code.</span></span>  
  
3.  <span data-ttu-id="16756-126">Na classe de cliente, defina o <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade o <xref:System.ServiceModel.ClientBase%601> classe para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="16756-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="16756-127">Este exemplo define a propriedade como um certificado x. 509 usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.</span><span class="sxs-lookup"><span data-stu-id="16756-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="16756-128">Você pode usar qualquer uma das enumerações do <xref:System.Security.Cryptography.X509Certificates.X509FindType> classe.</span><span class="sxs-lookup"><span data-stu-id="16756-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="16756-129">O nome da entidade é usado aqui, caso o certificado é alterado (devido a uma data de expiração).</span><span class="sxs-lookup"><span data-stu-id="16756-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="16756-130">Usando o nome de entidade permite que a infraestrutura para encontrar o certificado novamente.</span><span class="sxs-lookup"><span data-stu-id="16756-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="16756-131">Para especificar o valor de credencial de cliente no cliente de configuração</span><span class="sxs-lookup"><span data-stu-id="16756-131">To specify the client credential value on the client in configuration</span></span>  
  
1.  <span data-ttu-id="16756-132">Adicionar um [ \<comportamento >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="16756-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2.  <span data-ttu-id="16756-133">Adicionar um [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento para o [ \<comportamentos >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="16756-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="16756-134">Certifique-se de definir necessários `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="16756-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="16756-135">Adicionar um [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elemento para o [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="16756-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4.  <span data-ttu-id="16756-136">Defina os seguintes atributos com valores apropriados: `storeLocation`, `storeName`, `x509FindType`, e `findValue`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="16756-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="16756-137">Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).</span><span class="sxs-lookup"><span data-stu-id="16756-137">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
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
  
5.  <span data-ttu-id="16756-138">Ao configurar o cliente, especifique o comportamento definindo o `behaviorConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="16756-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="16756-139">O elemento de ponto de extremidade é um filho de [ \<cliente >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="16756-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="16756-140">Além disso, especifique o nome da configuração de associação, definindo o `bindingConfiguration` de atributo para a associação para o cliente.</span><span class="sxs-lookup"><span data-stu-id="16756-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="16756-141">Se você estiver usando um arquivo de configuração gerado, o nome da associação é gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="16756-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="16756-142">Neste exemplo, o nome é `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="16756-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="16756-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16756-143">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="16756-144">Programação de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="16756-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="16756-145">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="16756-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="16756-146">Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="16756-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="16756-147">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="16756-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="16756-148">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="16756-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="16756-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="16756-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [<span data-ttu-id="16756-150">\<security></span><span class="sxs-lookup"><span data-stu-id="16756-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [<span data-ttu-id="16756-151">\<message></span><span class="sxs-lookup"><span data-stu-id="16756-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [<span data-ttu-id="16756-152">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="16756-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [<span data-ttu-id="16756-153">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="16756-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [<span data-ttu-id="16756-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="16756-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [<span data-ttu-id="16756-155">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="16756-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
