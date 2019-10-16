---
title: Como definir o modo de segurança
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320905"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="90b13-102">Como definir o modo de segurança</span><span class="sxs-lookup"><span data-stu-id="90b13-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="90b13-103">A segurança do Windows Communication Foundation (WCF) tem três modos de segurança comuns encontrados na maioria das associações predefinidas: transporte, mensagem e "transporte com credencial de mensagem".</span><span class="sxs-lookup"><span data-stu-id="90b13-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="90b13-104">Dois modos adicionais são específicos de duas associações: o modo "somente transporte-credencial" encontrado no <xref:System.ServiceModel.BasicHttpBinding>, e o modo "ambos", encontrado no <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="90b13-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="90b13-105">No entanto, este tópico se concentra nos três modos de segurança comuns: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> e <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="90b13-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="90b13-106">Observe que nem toda Associação predefinida dá suporte a todos esses modos.</span><span class="sxs-lookup"><span data-stu-id="90b13-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="90b13-107">Este tópico define o modo com as classes <xref:System.ServiceModel.WSHttpBinding> e <xref:System.ServiceModel.NetTcpBinding> e demonstra como definir o modo de forma programática e por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="90b13-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="90b13-108">Para obter mais informações, consulte segurança do WCF, consulte [visão geral de segurança](./feature-details/security-overview.md), [protegendo serviços](securing-services.md)e [protegendo serviços e clientes](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="90b13-108">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="90b13-109">Para obter mais informações sobre o modo de transporte e a mensagem, consulte [segurança de transporte](./feature-details/transport-security.md) e [segurança de mensagem](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="90b13-109">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="90b13-110">Para definir o modo de segurança no código</span><span class="sxs-lookup"><span data-stu-id="90b13-110">To set the security mode in code</span></span>

1. <span data-ttu-id="90b13-111">Crie uma instância da classe de associação que você está usando.</span><span class="sxs-lookup"><span data-stu-id="90b13-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="90b13-112">Para obter uma lista de associações predefinidas, consulte [associações fornecidas pelo sistema](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="90b13-112">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="90b13-113">Este exemplo cria uma instância da classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="90b13-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="90b13-114">Defina a propriedade `Mode` do objeto retornado pela propriedade `Security`.</span><span class="sxs-lookup"><span data-stu-id="90b13-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="90b13-115">Como alternativa, defina o modo como mensagem, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90b13-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="90b13-116">Ou defina o modo como transporte com credenciais de mensagem, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90b13-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="90b13-117">Você também pode definir o modo no construtor da associação, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="90b13-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="90b13-118">Definindo a propriedade ClientCredentialtype</span><span class="sxs-lookup"><span data-stu-id="90b13-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="90b13-119">Definir o modo como um dos três valores determina como você define a propriedade `ClientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="90b13-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="90b13-120">Por exemplo, usando a classe <xref:System.ServiceModel.WSHttpBinding>, definir o modo como `Transport` significa que você deve definir a propriedade <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> da classe <xref:System.ServiceModel.HttpTransportSecurity> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="90b13-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="90b13-121">Para definir a propriedade ClientCredentialtype para o modo de transporte</span><span class="sxs-lookup"><span data-stu-id="90b13-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="90b13-122">Crie uma instância da associação.</span><span class="sxs-lookup"><span data-stu-id="90b13-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="90b13-123">Defina a propriedade `Mode` como `Transport`.</span><span class="sxs-lookup"><span data-stu-id="90b13-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="90b13-124">Defina a propriedade `ClientCredential` com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="90b13-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="90b13-125">O código a seguir define a propriedade como `Windows`.</span><span class="sxs-lookup"><span data-stu-id="90b13-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="90b13-126">Para definir a propriedade ClientCredentialtype para o modo de mensagem</span><span class="sxs-lookup"><span data-stu-id="90b13-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="90b13-127">Crie uma instância da associação.</span><span class="sxs-lookup"><span data-stu-id="90b13-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="90b13-128">Defina a propriedade `Mode` como `Message`.</span><span class="sxs-lookup"><span data-stu-id="90b13-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="90b13-129">Defina a propriedade `ClientCredential` com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="90b13-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="90b13-130">O código a seguir define a propriedade como `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="90b13-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="90b13-131">Para definir o modo e a propriedade ClientCredentialtype na configuração</span><span class="sxs-lookup"><span data-stu-id="90b13-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="90b13-132">Adicione um elemento de associação apropriado ao elemento [\<bindings >](../configure-apps/file-schema/wcf/bindings.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="90b13-132">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="90b13-133">O exemplo a seguir adiciona um elemento de [> \<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="90b13-133">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="90b13-134">Adicione um elemento `<binding>` e defina seu atributo `name` para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="90b13-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="90b13-135">Adicione um elemento `<security>` e defina o atributo `mode` como `Message`, `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="90b13-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="90b13-136">Se o modo for definido como `Transport`, adicione um elemento `<transport>` e defina o atributo `clientCredential` com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="90b13-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="90b13-137">O exemplo a seguir define o modo como "`Transport"`" e, em seguida, define o atributo `clientCredentialType` do elemento `<transport>` como "`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="90b13-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="90b13-138">Como alternativa, defina o `security mode` como "`Message"`, seguido por um elemento `<"message">`.</span><span class="sxs-lookup"><span data-stu-id="90b13-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="90b13-139">Este exemplo define o `clientCredentialType` como "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="90b13-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="90b13-140">Usar o valor <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> é um caso especial e é explicado abaixo.</span><span class="sxs-lookup"><span data-stu-id="90b13-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="90b13-141">Usando TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="90b13-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="90b13-142">Ao definir o modo de segurança como `TransportWithMessageCredential`, o transporte determina o mecanismo real que fornece a segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="90b13-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="90b13-143">Por exemplo, o protocolo HTTP usa protocolo SSL (SSL) via HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="90b13-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="90b13-144">Portanto, a definição da propriedade `ClientCredentialType` de qualquer objeto de segurança de transporte (como <xref:System.ServiceModel.HttpTransportSecurity>) é ignorada.</span><span class="sxs-lookup"><span data-stu-id="90b13-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="90b13-145">Em outras palavras, você só pode definir o `ClientCredentialType` do objeto de segurança da mensagem (para a associação `WSHttpBinding`, o objeto <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).</span><span class="sxs-lookup"><span data-stu-id="90b13-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="90b13-146">Para obter mais informações, consulte [como: usar segurança de transporte e credenciais de mensagem](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="90b13-146">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90b13-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90b13-147">See also</span></span>

- [<span data-ttu-id="90b13-148">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="90b13-148">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="90b13-149">Como usar a segurança do transporte e as credenciais de mensagem</span><span class="sxs-lookup"><span data-stu-id="90b13-149">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="90b13-150">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="90b13-150">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="90b13-151">Segurança de mensagem</span><span class="sxs-lookup"><span data-stu-id="90b13-151">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="90b13-152">Visão geral de segurança</span><span class="sxs-lookup"><span data-stu-id="90b13-152">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="90b13-153">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="90b13-153">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="90b13-154">\<Security ></span><span class="sxs-lookup"><span data-stu-id="90b13-154">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="90b13-155">\<Security ></span><span class="sxs-lookup"><span data-stu-id="90b13-155">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="90b13-156">\<Security ></span><span class="sxs-lookup"><span data-stu-id="90b13-156">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
