---
title: 'Como: Criar uma sessão segura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: c0e5281d227d343d8734809b27b57d8a2bead627
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147587"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="778a7-102">Como: Criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="778a7-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="778a7-103">Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) de associação, as associações fornecidas pelo sistema no Windows Communication Foundation (WCF) automaticamente usam sessões seguras quando a segurança de mensagens está habilitada.</span><span class="sxs-lookup"><span data-stu-id="778a7-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="778a7-104">Por padrão, sessões seguras não sobrevivem a um servidor Web que é reciclado.</span><span class="sxs-lookup"><span data-stu-id="778a7-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="778a7-105">Quando uma sessão segura é estabelecida, o cliente e o serviço de cache a chave que está associada com a sessão segura.</span><span class="sxs-lookup"><span data-stu-id="778a7-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="778a7-106">Como as mensagens são trocadas, apenas um identificador para a chave armazenada em cache é trocado.</span><span class="sxs-lookup"><span data-stu-id="778a7-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="778a7-107">Se o servidor Web for reciclado, o cache é reciclado, também, de modo que o servidor Web não é possível recuperar a chave armazenada em cache para o identificador.</span><span class="sxs-lookup"><span data-stu-id="778a7-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="778a7-108">Se isso acontecer, uma exceção será devolvida ao cliente.</span><span class="sxs-lookup"><span data-stu-id="778a7-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="778a7-109">Sessões seguras que usam um token de contexto de segurança com monitoração de estado (SCT) possam sobreviver a um servidor Web que está sendo reciclado.</span><span class="sxs-lookup"><span data-stu-id="778a7-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="778a7-110">Para obter mais informações sobre como usar um SCT com monitoração de estado em uma sessão segura, consulte [como: Criar um contexto de segurança para uma sessão segura Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="778a7-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="778a7-111">Para especificar que um serviço usa sessões seguras usando uma das associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="778a7-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="778a7-112">Configure um serviço para usar uma associação fornecida pelo sistema que dá suporte à segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="778a7-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="778a7-113">Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) de associação, quando as associações fornecidas pelo sistema estão configuradas para usar automaticamente a segurança de mensagem, WCF usa sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="778a7-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="778a7-114">A tabela a seguir lista as associações fornecidas pelo sistema que dão suporte à segurança de mensagem e se a segurança de mensagem é o mecanismo de segurança padrão.</span><span class="sxs-lookup"><span data-stu-id="778a7-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="778a7-115">Associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="778a7-115">System-provided binding</span></span>|<span data-ttu-id="778a7-116">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="778a7-116">Configuration element</span></span>|<span data-ttu-id="778a7-117">Segurança de mensagem em por padrão</span><span class="sxs-lookup"><span data-stu-id="778a7-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="778a7-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="778a7-119">Não</span><span class="sxs-lookup"><span data-stu-id="778a7-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="778a7-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="778a7-121">Sim</span><span class="sxs-lookup"><span data-stu-id="778a7-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="778a7-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="778a7-123">Sim</span><span class="sxs-lookup"><span data-stu-id="778a7-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="778a7-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="778a7-125">Sim</span><span class="sxs-lookup"><span data-stu-id="778a7-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="778a7-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="778a7-127">Não</span><span class="sxs-lookup"><span data-stu-id="778a7-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="778a7-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="778a7-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="778a7-129">Não</span><span class="sxs-lookup"><span data-stu-id="778a7-129">No</span></span>|  
  
     <span data-ttu-id="778a7-130">O exemplo de código a seguir usa a configuração para especificar uma associação denominada `wsHttpBinding_Calculator` que usa o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança da mensagem e proteger sessões.</span><span class="sxs-lookup"><span data-stu-id="778a7-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="778a7-131">O exemplo de código a seguir especifica que o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), a segurança da mensagem e proteger as sessões são usadas para proteger o `secureCalculator` serviço.</span><span class="sxs-lookup"><span data-stu-id="778a7-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="778a7-132">Sessões seguras podem ser desativadas para o [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) definindo a `establishSecurityContext` atributo `false`.</span><span class="sxs-lookup"><span data-stu-id="778a7-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="778a7-133">Para as outras associações fornecidas pelo sistema, sessões seguras podem apenas ser desativadas, criando uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="778a7-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="778a7-134">Para especificar que um serviço usa sessões seguras usando uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="778a7-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="778a7-135">Crie uma ligação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="778a7-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="778a7-136">Para obter mais informações sobre como criar uma ligação personalizada, consulte [como: Personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="778a7-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="778a7-137">O exemplo de código a seguir usa a configuração para especificar uma associação que as mensagens usando uma sessão segura personalizada.</span><span class="sxs-lookup"><span data-stu-id="778a7-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="778a7-138">O exemplo de código a seguir cria uma associação personalizada que usa o <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> modo de autenticação para inicializar uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="778a7-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="778a7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="778a7-139">See Also</span></span>  
 [<span data-ttu-id="778a7-140">Visão geral de associações do WCF</span><span class="sxs-lookup"><span data-stu-id="778a7-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
