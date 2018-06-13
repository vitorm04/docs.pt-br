---
title: Como criar um token de contexto de segurança para uma sessão segura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ef2f02bb5ad6e7458ae11e7880fe403f3a6e9916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493406"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="1b40d-102">Como criar um token de contexto de segurança para uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="1b40d-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="1b40d-103">Usando um token de contexto de segurança com monitoração de estado (SCT) em uma sessão segura, a sessão pode suportar o serviço ser reciclado.</span><span class="sxs-lookup"><span data-stu-id="1b40d-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="1b40d-104">Por exemplo, quando um SCT sem monitoração de estado é usado em uma sessão segura e redefinição de serviços de informações da Internet (IIS), os dados da sessão que está associados com o serviço serão perdidos.</span><span class="sxs-lookup"><span data-stu-id="1b40d-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="1b40d-105">Esses dados de sessão incluem um cache de token SCT.</span><span class="sxs-lookup"><span data-stu-id="1b40d-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="1b40d-106">Portanto, na próxima vez que um cliente envia o serviço um SCT sem monitoração de estado, um erro será retornado, porque a chave que está associada com o SCT não pode ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="1b40d-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="1b40d-107">Se, no entanto, um SCT com monitoração de estado é usado, a chave que está associada com o SCT está contida dentro de SCT.</span><span class="sxs-lookup"><span data-stu-id="1b40d-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="1b40d-108">Porque a chave é contida o SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço de ser reciclado.</span><span class="sxs-lookup"><span data-stu-id="1b40d-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="1b40d-109">Por padrão, o Windows Communication Foundation (WCF) usa SCTs sem monitoração de estado em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1b40d-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="1b40d-110">Este tópico fornece detalhes sobre como usar SCTs com monitoração de estado em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1b40d-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b40d-111">SCTs com monitoração de estado não podem ser usados em uma sessão segura que envolve um contrato que deriva de <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="1b40d-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b40d-112">Para aplicativos que usam SCTs com monitoração de estado em uma sessão segura, a identidade do segmento para o serviço deve ser uma conta de usuário que tem um perfil de usuário associado.</span><span class="sxs-lookup"><span data-stu-id="1b40d-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="1b40d-113">Quando o serviço é executado sob uma conta que não tem um perfil de usuário, como `Local Service`, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="1b40d-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b40d-114">Quando a representação é necessário no Windows XP, use uma sessão segura sem um SCT com monitoração de estado.</span><span class="sxs-lookup"><span data-stu-id="1b40d-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="1b40d-115">Quando SCTs com monitoração de estado são usadas com representação, um <xref:System.InvalidOperationException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="1b40d-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="1b40d-116">Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="1b40d-117">Para usar SCTs com monitoração de estado em uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="1b40d-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="1b40d-118">Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT com monitoração de estado.</span><span class="sxs-lookup"><span data-stu-id="1b40d-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="1b40d-119">Definir uma associação personalizada, adicionando um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) para o arquivo de configuração para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1b40d-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="1b40d-120">Adicionar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento filho para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="1b40d-121">Especifique um nome de associação, definindo o `name` de atributo para um nome exclusivo dentro do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1b40d-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="1b40d-122">Especifique o modo de autenticação para mensagens enviadas para e a partir desse serviço, adicionando um [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento filho para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="1b40d-123">Especificar que uma sessão segura é usada, definindo o `authenticationMode` atributo `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="1b40d-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="1b40d-124">Especifique que SCTs com monitoração de estado são usadas, definindo o `requireSecurityContextCancellation` atributo `false`.</span><span class="sxs-lookup"><span data-stu-id="1b40d-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="1b40d-125">Especifique como o cliente é autenticado enquanto a sessão segura é estabelecida com a adição de um [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho para o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="1b40d-126">Especifique como o cliente é autenticado, definindo o `authenticationMode` atributo.</span><span class="sxs-lookup"><span data-stu-id="1b40d-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="1b40d-127">Especifique a codificação de mensagens adicionando um elemento de codificação, como [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="1b40d-128">Especifique o transporte adicionando um elemento de transporte, como o [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="1b40d-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="1b40d-129">O exemplo de código a seguir usa a configuração para especificar uma associação personalizada que mensagens podem usar com SCTs com monitoração de estado em uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1b40d-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1b40d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b40d-130">Example</span></span>  
 <span data-ttu-id="1b40d-131">O exemplo de código a seguir cria uma associação personalizada que usa o <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> modo de autenticação para inicializar uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="1b40d-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="1b40d-132">Quando a autenticação do Windows é usada em combinação com um SCT com monitoração de estado, o WCF não preencher a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade com o chamador real da identidade, mas em vez disso, define a propriedade como anônimo.</span><span class="sxs-lookup"><span data-stu-id="1b40d-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="1b40d-133">Porque a segurança do WCF deve recriar o conteúdo do contexto de segurança de serviço para cada solicitação de SCT a entrada, o servidor não manter o controle de sessão de segurança na memória.</span><span class="sxs-lookup"><span data-stu-id="1b40d-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="1b40d-134">Porque não é possível serializar o <xref:System.Security.Principal.WindowsIdentity> instância em SCT, o <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade retorna uma identidade anônima.</span><span class="sxs-lookup"><span data-stu-id="1b40d-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="1b40d-135">A configuração a seguir exibe esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="1b40d-135">The following configuration exhibits this behavior.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b40d-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b40d-136">See Also</span></span>  
 [<span data-ttu-id="1b40d-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1b40d-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
