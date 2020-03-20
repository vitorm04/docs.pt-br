---
title: Como criar um token de contexto de segurança para uma sessão segura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 02e0403f9ae5bb437145fa3a015edc69b884c4d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185011"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="e266a-102">Como criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="e266a-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="e266a-103">Ao usar um token de contexto de segurança de estado (SCT) em uma sessão segura, a sessão pode suportar que o serviço seja reciclado.</span><span class="sxs-lookup"><span data-stu-id="e266a-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="e266a-104">Por exemplo, quando um SCT apátrida é usado em uma sessão segura e o IIS (Internet Information Services, serviços de informações da Internet) é redefinido, então os dados de sessão associados ao serviço são perdidos.</span><span class="sxs-lookup"><span data-stu-id="e266a-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="e266a-105">Esses dados da sessão incluem um cache de token SCT.</span><span class="sxs-lookup"><span data-stu-id="e266a-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="e266a-106">Assim, da próxima vez que um cliente envia ao serviço um SCT apátrida, um erro é devolvido, porque a chave associada ao SCT não pode ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="e266a-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="e266a-107">Se, no entanto, um SCT imponente for usado, então a chave associada ao SCT está contida no SCT.</span><span class="sxs-lookup"><span data-stu-id="e266a-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="e266a-108">Como a chave está contida no SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço ser reciclado.</span><span class="sxs-lookup"><span data-stu-id="e266a-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="e266a-109">Por padrão, o Windows Communication Foundation (WCF) usa SCTs apátridas em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="e266a-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="e266a-110">Este tópico detalha como usar SCTs estaduais em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="e266a-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e266a-111">Os SCTs estaduais não podem ser usados em <xref:System.ServiceModel.Channels.IDuplexChannel>uma sessão segura que envolva um contrato derivado de .</span><span class="sxs-lookup"><span data-stu-id="e266a-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e266a-112">Para aplicativos que usam SCTs estaduais em uma sessão segura, a identidade do thread para o serviço deve ser uma conta de usuário que tenha um perfil de usuário associado.</span><span class="sxs-lookup"><span data-stu-id="e266a-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="e266a-113">Quando o serviço é executado em uma conta que `Local Service`não tem um perfil de usuário, como , uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="e266a-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e266a-114">Quando a representação for necessária no Windows XP, use uma sessão segura sem um SCT imponente.</span><span class="sxs-lookup"><span data-stu-id="e266a-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="e266a-115">Quando SCTs estaduais são usados <xref:System.InvalidOperationException> com personificação, um é jogado.</span><span class="sxs-lookup"><span data-stu-id="e266a-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="e266a-116">Para obter mais informações, consulte [Cenários Não Suportados](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="e266a-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="e266a-117">Para usar SCTs estaduais em uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="e266a-117">To use stateful SCTs in a secure session</span></span>  
  
- <span data-ttu-id="e266a-118">Crie uma vinculação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT imponente.</span><span class="sxs-lookup"><span data-stu-id="e266a-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1. <span data-ttu-id="e266a-119">Defina uma vinculação personalizada, adicionando um [ \<>de vinculação personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ao arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="e266a-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. <span data-ttu-id="e266a-120">Adicione [ \<](../../configure-apps/file-schema/wcf/bindings.md) um elemento de>criança de vinculação ao [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e266a-120">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="e266a-121">Especifique um `name` nome de vinculação definindo o atributo para um nome único dentro do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e266a-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. <span data-ttu-id="e266a-122">Especifique o modo de autenticação para mensagens enviadas para e a partir deste serviço adicionando um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de segurança>filho ao [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e266a-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="e266a-123">Especifique que uma sessão `authenticationMode` segura `SecureConversation`é usada definindo o atributo para .</span><span class="sxs-lookup"><span data-stu-id="e266a-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="e266a-124">Especifique que os SCTs `requireSecurityContextCancellation` estaduais são usados definindo o atributo para `false`.</span><span class="sxs-lookup"><span data-stu-id="e266a-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. <span data-ttu-id="e266a-125">Especifique como o cliente é autenticado enquanto a sessão segura é [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)estabelecida adicionando um [ \<elemento de>filho seguroConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) à>de segurança .</span><span class="sxs-lookup"><span data-stu-id="e266a-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="e266a-126">Especifique como o cliente `authenticationMode` é autenticado definindo o atributo.</span><span class="sxs-lookup"><span data-stu-id="e266a-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. <span data-ttu-id="e266a-127">Especifique a codificação da mensagem adicionando um elemento de codificação, como [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="e266a-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. <span data-ttu-id="e266a-128">Especifique o transporte adicionando um elemento de transporte, como o [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="e266a-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="e266a-129">O exemplo de código a seguir usa a configuração para especificar uma vinculação personalizada que as mensagens podem usar com SCTs estaduais em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="e266a-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="e266a-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e266a-130">Example</span></span>  
 <span data-ttu-id="e266a-131">O exemplo de código a seguir <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> cria uma vinculação personalizada que usa o modo de autenticação para bootstrap de uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="e266a-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="e266a-132">Quando a autenticação do Windows é usada em combinação com <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> um SCT imponente, o WCF não preenche a propriedade com a identidade do chamador real, mas define a propriedade como anônima.</span><span class="sxs-lookup"><span data-stu-id="e266a-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="e266a-133">Como a segurança do WCF deve recriar o conteúdo do contexto de segurança do serviço para cada solicitação do SCT de entrada, o servidor não acompanha a sessão de segurança na memória.</span><span class="sxs-lookup"><span data-stu-id="e266a-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="e266a-134">Como é impossível serializar <xref:System.Security.Principal.WindowsIdentity> a instância no <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> SCT, a propriedade retorna uma identidade anônima.</span><span class="sxs-lookup"><span data-stu-id="e266a-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="e266a-135">A configuração a seguir exibe esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="e266a-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e266a-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="e266a-136">See also</span></span>

- [<span data-ttu-id="e266a-137">\<>de vinculação personalizada</span><span class="sxs-lookup"><span data-stu-id="e266a-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
