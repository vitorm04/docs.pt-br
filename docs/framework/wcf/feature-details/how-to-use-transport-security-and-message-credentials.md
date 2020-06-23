---
title: Como utilizar credenciais de mensagem e segurança de transporte
description: Saiba como implementar a segurança de transporte com credenciais de mensagem, que oferece o melhor dos modos de segurança de transporte e de mensagens no WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246643"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="e3332-103">Como utilizar credenciais de mensagem e segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e3332-103">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="e3332-104">A proteção de um serviço com as credenciais de transporte e de mensagem usa o melhor dos modos de segurança de transporte e de mensagem no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3332-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e3332-105">Em Sum, a segurança da camada de transporte fornece integridade e confidencialidade, enquanto a segurança da camada de mensagens fornece uma variedade de credenciais que não são possíveis com mecanismos de segurança de transporte estritos.</span><span class="sxs-lookup"><span data-stu-id="e3332-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="e3332-106">Este tópico mostra as etapas básicas para implementar o transporte com credenciais de mensagem usando as <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> associações e.</span><span class="sxs-lookup"><span data-stu-id="e3332-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="e3332-107">Para obter mais informações sobre como definir o modo de segurança, consulte [como: definir o modo de segurança](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="e3332-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="e3332-108">Ao definir o modo de segurança como `TransportWithMessageCredential` , o transporte determina o mecanismo real que fornece a segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="e3332-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="e3332-109">Para HTTP, o mecanismo é protocolo SSL (SSL) via HTTP (HTTPS); para TCP, é SSL sobre TCP ou Windows.</span><span class="sxs-lookup"><span data-stu-id="e3332-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="e3332-110">Se o transporte for HTTP (usando o <xref:System.ServiceModel.WSHttpBinding> ), o SSL sobre http fornecerá a segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="e3332-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="e3332-111">Nesse caso, você deve configurar o computador que hospeda o serviço com um certificado SSL associado a uma porta, conforme mostrado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3332-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="e3332-112">Se o transporte for TCP (usando o <xref:System.ServiceModel.NetTcpBinding> ), por padrão, a segurança no nível de transporte fornecida é a segurança do Windows ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="e3332-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="e3332-113">Ao usar SSL sobre TCP, você deve especificar o certificado usando o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método, conforme mostrado posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="e3332-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="e3332-114">Para usar o WSHttpBinding com um certificado para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e3332-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e3332-115">Use a ferramenta HttpCfg.exe para associar um certificado SSL a uma porta no computador.</span><span class="sxs-lookup"><span data-stu-id="e3332-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="e3332-116">Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="e3332-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="e3332-117">Crie uma instância da <xref:System.ServiceModel.WSHttpBinding> classe e defina a <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e3332-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="e3332-118">Defina a propriedade <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="e3332-119">(Para obter mais informações, consulte [selecionando um tipo de credencial](selecting-a-credential-type.md).) O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e3332-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="e3332-120">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e3332-121">Observe que o endereço deve usar o esquema "HTTPS" e deve conter o nome real do computador e o número da porta ao qual o certificado SSL está associado.</span><span class="sxs-lookup"><span data-stu-id="e3332-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="e3332-122">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e3332-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="e3332-123">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e3332-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="e3332-124">Crie a instância do <xref:System.ServiceModel.ServiceHost> e chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3332-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="e3332-125">Para usar o NetTcpbinding com um certificado para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e3332-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e3332-126">Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e3332-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="e3332-127">Defina <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="e3332-128">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e3332-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="e3332-129">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e3332-130">Observe que o endereço deve usar o esquema "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="e3332-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="e3332-131">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e3332-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="e3332-132">Crie a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="e3332-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="e3332-133">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X. 509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e3332-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="e3332-134">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e3332-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="e3332-135">Chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3332-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="e3332-136">Para usar o NetTcpbinding com o Windows para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="e3332-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="e3332-137">Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade como <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="e3332-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="e3332-138">Defina a segurança de transporte para usar o Windows definindo o <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> para <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="e3332-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="e3332-139">(Observe que esse é o padrão.)</span><span class="sxs-lookup"><span data-stu-id="e3332-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="e3332-140">Defina <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="e3332-141">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="e3332-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="e3332-142">Crie uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="e3332-143">Observe que o endereço deve usar o esquema "net. TCP".</span><span class="sxs-lookup"><span data-stu-id="e3332-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="e3332-144">(Como alternativa, você pode definir o endereço base na configuração.)</span><span class="sxs-lookup"><span data-stu-id="e3332-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="e3332-145">Crie a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="e3332-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="e3332-146">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X. 509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e3332-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="e3332-147">Adicione um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e3332-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="e3332-148">Chame o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3332-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="e3332-149">Usando a configuração</span><span class="sxs-lookup"><span data-stu-id="e3332-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="e3332-150">Para usar o WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e3332-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="e3332-151">Configure o computador com um certificado SSL associado a uma porta.</span><span class="sxs-lookup"><span data-stu-id="e3332-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="e3332-152">(Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="e3332-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="e3332-153">Você não precisa definir um <`transport`> valor do elemento com essa configuração.</span><span class="sxs-lookup"><span data-stu-id="e3332-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="e3332-154">Especifique o tipo de credencial do cliente para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e3332-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="e3332-155">O exemplo a seguir define o `clientCredentialType` atributo do `message` elemento <> como `UserName` .</span><span class="sxs-lookup"><span data-stu-id="e3332-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="e3332-156">Para usar o NetTcpbinding com um certificado para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e3332-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="e3332-157">Para SSL sobre TCP, você deve especificar explicitamente o certificado no `<behaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="e3332-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="e3332-158">O exemplo a seguir especifica um certificado por seu emissor no local de armazenamento padrão (computador local e repositórios pessoais).</span><span class="sxs-lookup"><span data-stu-id="e3332-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2. <span data-ttu-id="e3332-159">Adicionar um [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações</span><span class="sxs-lookup"><span data-stu-id="e3332-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="e3332-160">Adicione um elemento Binding e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="e3332-161">Adicione um <`security` elemento> e defina o `mode` atributo como `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="e3332-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="e3332-162">Adicione um `message>` elemento <e defina o `clientCredentialType` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="e3332-163">Para usar o NetTcpbinding com o Windows para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="e3332-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="e3332-164">Adicionar um [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações,</span><span class="sxs-lookup"><span data-stu-id="e3332-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="e3332-165">Adicione um `binding` elemento <> e defina o `name` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="e3332-166">Adicione um <`security` elemento> e defina o `mode` atributo como `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="e3332-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="e3332-167">Adicione um `transport` elemento <> e defina o `clientCredentialType` atributo como `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e3332-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="e3332-168">Adicione um `message` elemento <> e defina o `clientCredentialType` atributo como um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="e3332-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="e3332-169">O código a seguir define o valor para um certificado.</span><span class="sxs-lookup"><span data-stu-id="e3332-169">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3332-170">Veja também</span><span class="sxs-lookup"><span data-stu-id="e3332-170">See also</span></span>

- [<span data-ttu-id="e3332-171">Como definir o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="e3332-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="e3332-172">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="e3332-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="e3332-173">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e3332-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
