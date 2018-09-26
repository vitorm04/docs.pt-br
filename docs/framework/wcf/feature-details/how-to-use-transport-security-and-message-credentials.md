---
title: Como utilizar credenciais de mensagem e segurança de transporte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
author: BrucePerlerMS
ms.openlocfilehash: 40fe7b1fa6a61b56d5dfdde75a92834f096a8be4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200401"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="2963b-102">Como utilizar credenciais de mensagem e segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="2963b-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="2963b-103">Proteger um serviço com credenciais de transporte e de mensagem usa o melhor dos modos de segurança de transporte e de mensagem no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2963b-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="2963b-104">Em suma, segurança de camada de transporte fornece integridade e confidencialidade, enquanto a segurança da camada de mensagem fornece uma variedade de credenciais que não são possíveis com os mecanismos de segurança de transporte estrito.</span><span class="sxs-lookup"><span data-stu-id="2963b-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="2963b-105">Este tópico mostra as etapas básicas para a implementação de transporte com credenciais de mensagem usando o <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.NetTcpBinding> associações.</span><span class="sxs-lookup"><span data-stu-id="2963b-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="2963b-106">Para obter mais informações sobre como definir o modo de segurança, consulte [como: definir o modo de segurança](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="2963b-106">For more information about setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="2963b-107">Ao definir o modo de segurança para `TransportWithMessageCredential`, o transporte determina o mecanismo real que fornece a segurança de nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="2963b-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="2963b-108">Para HTTP, o mecanismo é Secure Sockets Layer (SSL) sobre HTTP (HTTPS); para TCP, é SSL sobre TCP ou Windows.</span><span class="sxs-lookup"><span data-stu-id="2963b-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="2963b-109">Se o transporte é HTTP (usando o <xref:System.ServiceModel.WSHttpBinding>), SSL sobre HTTP fornece a segurança de nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="2963b-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="2963b-110">Nesse caso, você deve configurar o computador que hospeda o serviço com um certificado SSL associado a uma porta, conforme mostrado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2963b-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="2963b-111">Se o transporte é TCP (usando o <xref:System.ServiceModel.NetTcpBinding>), por padrão a segurança de nível de transporte fornecida é de segurança do Windows ou SSL sobre TCP.</span><span class="sxs-lookup"><span data-stu-id="2963b-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="2963b-112">Ao usar SSL sobre TCP, você deve especificar o certificado usando o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método, conforme mostrado neste tópico.</span><span class="sxs-lookup"><span data-stu-id="2963b-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="2963b-113">Para usar o WSHttpBinding com um certificado de segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="2963b-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="2963b-114">Use a ferramenta de HttpCfg.exe para associar um certificado SSL para uma porta no computador.</span><span class="sxs-lookup"><span data-stu-id="2963b-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="2963b-115">Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="2963b-115">For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="2963b-116">Criar uma instância do <xref:System.ServiceModel.WSHttpBinding> de classe e defina a <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="2963b-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="2963b-117">Defina o <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> propriedade para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="2963b-118">(Para obter mais informações, consulte [selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="2963b-118">(For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="2963b-119">Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="2963b-120">Observe que o endereço deve usar o esquema "HTTPS" e deve conter o nome real da máquina e o número da porta associado ao certificado SSL.</span><span class="sxs-lookup"><span data-stu-id="2963b-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="2963b-121">(Como alternativa, você pode definir o endereço base na configuração).</span><span class="sxs-lookup"><span data-stu-id="2963b-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="2963b-122">Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2963b-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="2963b-123">Criar a instância das <xref:System.ServiceModel.ServiceHost> e chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2963b-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="2963b-124">Para usar a NetTcpBinding com um certificado de segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="2963b-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="2963b-125">Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="2963b-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="2963b-126">Defina o <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="2963b-127">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="2963b-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="2963b-128">Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="2963b-129">Observe que o endereço deve usar o esquema de "NET. TCP".</span><span class="sxs-lookup"><span data-stu-id="2963b-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="2963b-130">(Como alternativa, você pode definir o endereço base na configuração).</span><span class="sxs-lookup"><span data-stu-id="2963b-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="2963b-131">Criar a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="2963b-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="2963b-132">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X.509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2963b-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="2963b-133">Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2963b-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="2963b-134">Chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2963b-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="2963b-135">Para usar a NetTcpBinding com Windows para segurança de transporte (no código)</span><span class="sxs-lookup"><span data-stu-id="2963b-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="2963b-136">Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="2963b-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="2963b-137">Definir a segurança de transporte para usar o Windows, definindo o <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> para <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="2963b-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="2963b-138">(Observe que esse é o padrão).</span><span class="sxs-lookup"><span data-stu-id="2963b-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="2963b-139">Defina o <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="2963b-140">O código a seguir usa o <xref:System.ServiceModel.MessageCredentialType.Certificate> valor.</span><span class="sxs-lookup"><span data-stu-id="2963b-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="2963b-141">Criar uma instância da <xref:System.Uri> classe com um endereço base apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="2963b-142">Observe que o endereço deve usar o esquema de "NET. TCP".</span><span class="sxs-lookup"><span data-stu-id="2963b-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="2963b-143">(Como alternativa, você pode definir o endereço base na configuração).</span><span class="sxs-lookup"><span data-stu-id="2963b-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="2963b-144">Criar a instância da <xref:System.ServiceModel.ServiceHost> classe.</span><span class="sxs-lookup"><span data-stu-id="2963b-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="2963b-145">Use o <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe para definir explicitamente o certificado X.509 para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2963b-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="2963b-146">Adicionar um ponto de extremidade de serviço usando o <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="2963b-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="2963b-147">Chamar o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2963b-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="2963b-148">Usando a configuração</span><span class="sxs-lookup"><span data-stu-id="2963b-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="2963b-149">Para usar o WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2963b-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="2963b-150">Configure o computador com um certificado SSL associado a uma porta.</span><span class="sxs-lookup"><span data-stu-id="2963b-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="2963b-151">(Para obter mais informações, consulte [como: configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="2963b-151">(For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="2963b-152">Não é necessário definir um <`transport`> valor do elemento com essa configuração.</span><span class="sxs-lookup"><span data-stu-id="2963b-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="2963b-153">Especifique o tipo de credencial de cliente para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2963b-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="2963b-154">O exemplo a seguir define o `clientCredentialType` atributo da <`message`> elemento `UserName`.</span><span class="sxs-lookup"><span data-stu-id="2963b-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="2963b-155">Para usar a NetTcpBinding com um certificado para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="2963b-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="2963b-156">Para SSL sobre TCP, você deve especificar explicitamente o certificado no `<behaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="2963b-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="2963b-157">O exemplo a seguir especifica um certificado por seu emissor no local de armazenamento padrão (computador local e armazenamentos pessoais).</span><span class="sxs-lookup"><span data-stu-id="2963b-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2.  <span data-ttu-id="2963b-158">Adicionar um [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações</span><span class="sxs-lookup"><span data-stu-id="2963b-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="2963b-159">Adicione um elemento de associação e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="2963b-160">Adicionar um <`security`> elemento e defina o `mode` atributo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="2963b-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="2963b-161">Adicione um <`message>` elemento e defina o `clientCredentialType` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="2963b-162">Para usar a NetTcpBinding com Windows para segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="2963b-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="2963b-163">Adicionar um [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) à seção de associações,</span><span class="sxs-lookup"><span data-stu-id="2963b-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="2963b-164">Adicione um <`binding`> elemento e defina o `name` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="2963b-165">Adicionar um <`security`> elemento e defina o `mode` atributo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="2963b-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="2963b-166">Adicionar um <`transport`> elemento e defina o `clientCredentialType` atributo `Windows`.</span><span class="sxs-lookup"><span data-stu-id="2963b-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="2963b-167">Adicione um <`message`> elemento e defina o `clientCredentialType` de atributo para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="2963b-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="2963b-168">O código a seguir define o valor para um certificado.</span><span class="sxs-lookup"><span data-stu-id="2963b-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2963b-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2963b-169">See Also</span></span>  
 [<span data-ttu-id="2963b-170">Como definir o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="2963b-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="2963b-171">Protegendo serviços</span><span class="sxs-lookup"><span data-stu-id="2963b-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="2963b-172">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2963b-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
