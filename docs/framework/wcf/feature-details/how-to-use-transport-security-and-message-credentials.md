---
title: Como utilizar credenciais de mensagem e segurança de transporte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f49c0eb46141081b91100a5ae1869cbcf556e353
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579378"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="e6ac6-102">Como utilizar credenciais de mensagem e segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e6ac6-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="e6ac6-103">A proteção de um serviço com as credenciais de transporte e de mensagem usa o melhor dos modos de segurança de transporte e de mensagem no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e6ac6-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e6ac6-104">Em Sum, a segurança da camada de transporte fornece integridade e confidencialidade, enquanto a segurança da camada de mensagens fornece uma variedade de credenciais que não são possíveis com mecanismos de segurança de transporte estritos.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="e6ac6-105">Este tópico mostra as etapas básicas para implementar o transporte com credenciais de mensagem usando as <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> associações e.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="e6ac6-106">Para obter mais informações sobre como definir o modo de segurança, consulte [como: definir o modo de segurança](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="e6ac6-106">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="e6ac6-107">Ao definir o modo de segurança como `TransportWithMessageCredential` , o transporte determina o mecanismo real que fornece a segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="e6ac6-108">Para HTTP, o mecanismo é protocolo SSL (SSL) via HTTP (HTTPS); para TCP, é SSL sobre TCP ou Windows.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="e6ac6-109">Se o transporte for HTTP (usando o <xref:System.ServiceModel.WSHttpBinding> ), o SSL sobre http fornecerá a segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="e6ac6-110">Nesse caso, você deve configurar o computador que hospeda o serviço com um certificado SSL associado a uma porta, conforme mostrado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="e6ac6-111">Se o transporte for TCP (usando o <xref:System.ServiceModel.NetTcpBinding> ), por padrão, a segurança no nível de transporte fornecida é a segurança do Windows ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="e6ac6-112">Ao usar SSL sobre TCP, você deve especificar o certificado usando o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método, conforme mostrado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="e6ac6-113">Para usar o WSHttpBinding com um certificado para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e6ac6-114">Use a ferramenta HttpCfg. exe para associar um certificado SSL a uma porta no computador.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="e6ac6-115">Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e6ac6-115">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="e6ac6-116">Crie uma instância da <xref:System.ServiceModel.WSHttpBinding> classe e defina a <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="e6ac6-117">Defina a propriedade <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="e6ac6-118">(Para obter mais informações, consulte [selecionando um tipo de credencial](selecting-a-credential-type.md).) O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-118">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="e6ac6-119">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e6ac6-120">Observe que o endereço deve usar o esquema "HTTPS" e deve conter o nome real do computador e o número da porta ao qual o certificado SSL está associado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="e6ac6-121">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="e6ac6-122">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="e6ac6-123">Crie a instância do <xref:System.ServiceModel.ServiceHost> e chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="e6ac6-124">Para usar o NetTcpbinding com um certificado para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e6ac6-125">Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="e6ac6-126">Defina <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="e6ac6-127">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="e6ac6-128">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e6ac6-129">Observe que o endereço deve usar o esquema "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="e6ac6-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="e6ac6-130">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="e6ac6-131">Crie a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="e6ac6-132">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X. 509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="e6ac6-133">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="e6ac6-134">Chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="e6ac6-135">Para usar o NetTcpbinding com o Windows para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e6ac6-136">Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="e6ac6-137">Defina a segurança de transporte para usar o Windows definindo o <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> para <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="e6ac6-138">(Observe que esse é o padrão.)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-138">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="e6ac6-139">Defina <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="e6ac6-140">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="e6ac6-141">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e6ac6-142">Observe que o endereço deve usar o esquema "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="e6ac6-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="e6ac6-143">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e6ac6-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="e6ac6-144">Crie a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="e6ac6-145">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X. 509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="e6ac6-146">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="e6ac6-147">Chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="e6ac6-148">Usando a configuração</span><span class="sxs-lookup"><span data-stu-id="e6ac6-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="e6ac6-149">Para usar o WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e6ac6-149">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="e6ac6-150">Configure o computador com um certificado SSL associado a uma porta.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="e6ac6-151">(Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="e6ac6-151">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="e6ac6-152">Você não precisa definir um <`transport`> valor do elemento com essa configuração.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="e6ac6-153">Especifique o tipo de credencial do cliente para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="e6ac6-154">O exemplo a seguir define o `clientCredentialType` atributo do `message` elemento <> como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="e6ac6-155">Para usar o NetTcpbinding com um certificado para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e6ac6-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="e6ac6-156">Para SSL sobre TCP, você deve especificar explicitamente o certificado no `<behaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="e6ac6-157">O exemplo a seguir especifica um certificado por seu emissor no local de armazenamento padrão (computador local e repositórios pessoais).</span><span class="sxs-lookup"><span data-stu-id="e6ac6-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="e6ac6-158">Adicionar um [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações</span><span class="sxs-lookup"><span data-stu-id="e6ac6-158">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="e6ac6-159">Adicione um elemento Binding e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="e6ac6-160">Adicione um <`security` elemento> e defina o `mode` atributo como `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="e6ac6-161">Adicione um `message>` elemento <e defina o `clientCredentialType` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="e6ac6-162">Para usar o NetTcpbinding com o Windows para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e6ac6-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="e6ac6-163">Adicionar um [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações,</span><span class="sxs-lookup"><span data-stu-id="e6ac6-163">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="e6ac6-164">Adicione um `binding` elemento <> e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="e6ac6-165">Adicione um <`security` elemento> e defina o `mode` atributo como `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="e6ac6-166">Adicione um `transport` elemento <> e defina o `clientCredentialType` atributo como `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e6ac6-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="e6ac6-167">Adicione um `message` elemento <> e defina o `clientCredentialType` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="e6ac6-168">O código a seguir define o valor para um certificado.</span><span class="sxs-lookup"><span data-stu-id="e6ac6-168">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6ac6-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6ac6-169">See also</span></span>

- [<span data-ttu-id="e6ac6-170">Como definir o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="e6ac6-170">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="e6ac6-171">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="e6ac6-171">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="e6ac6-172">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e6ac6-172">Securing Services and Clients</span></span>](securing-services-and-clients.md)
