---
title: 'Como: criar uma sessão segura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934377"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="ceffd-102">Como: criar uma sessão segura</span><span class="sxs-lookup"><span data-stu-id="ceffd-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="ceffd-103">Com exceção da Associação de [ \<> BasicHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , as associações fornecidas pelo sistema no Windows Communication Foundation (WCF) automaticamente usam sessões seguras quando a segurança da mensagem está habilitada.</span><span class="sxs-lookup"><span data-stu-id="ceffd-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="ceffd-104">Por padrão, as sessões seguras não sobrevivem a um servidor Web que é reciclado.</span><span class="sxs-lookup"><span data-stu-id="ceffd-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="ceffd-105">Quando uma sessão segura é estabelecida, o cliente e o serviço armazenam em cache a chave que está associada à sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ceffd-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="ceffd-106">À medida que as mensagens são trocadas, apenas um identificador para a chave armazenada em cache é trocado.</span><span class="sxs-lookup"><span data-stu-id="ceffd-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="ceffd-107">Se o servidor Web for reciclado, o cache também será reciclado, de modo que o servidor Web não possa recuperar a chave armazenada em cache para o identificador.</span><span class="sxs-lookup"><span data-stu-id="ceffd-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="ceffd-108">Se isso acontecer, uma exceção será gerada de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="ceffd-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="ceffd-109">As sessões seguras que usam um identificador de contexto de segurança com estado (SCT) podem sobreviver a um servidor Web sendo reciclado.</span><span class="sxs-lookup"><span data-stu-id="ceffd-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="ceffd-110">Para obter mais informações sobre como usar um SCT com estado em uma sessão [segura, consulte Como: Crie um token de contexto de segurança para uma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ceffd-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="ceffd-111">Para especificar que um serviço usa sessões seguras usando uma das associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ceffd-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="ceffd-112">Configure um serviço para usar uma associação fornecida pelo sistema que dê suporte à segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ceffd-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="ceffd-113">Com exceção da Associação de [ \<> BasicHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , quando as associações fornecidas pelo sistema são configuradas para usar a segurança de mensagem, o WCF usa automaticamente as sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="ceffd-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="ceffd-114">A tabela a seguir lista as associações fornecidas pelo sistema que dão suporte à segurança da mensagem e se a segurança da mensagem é o mecanismo de segurança padrão.</span><span class="sxs-lookup"><span data-stu-id="ceffd-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="ceffd-115">Associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ceffd-115">System-provided binding</span></span>|<span data-ttu-id="ceffd-116">Elemento de configuração</span><span class="sxs-lookup"><span data-stu-id="ceffd-116">Configuration element</span></span>|<span data-ttu-id="ceffd-117">Segurança de mensagem ativada por padrão</span><span class="sxs-lookup"><span data-stu-id="ceffd-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="ceffd-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="ceffd-119">Não</span><span class="sxs-lookup"><span data-stu-id="ceffd-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="ceffd-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="ceffd-121">Sim</span><span class="sxs-lookup"><span data-stu-id="ceffd-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="ceffd-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="ceffd-123">Sim</span><span class="sxs-lookup"><span data-stu-id="ceffd-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="ceffd-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="ceffd-125">Sim</span><span class="sxs-lookup"><span data-stu-id="ceffd-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="ceffd-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="ceffd-127">Não</span><span class="sxs-lookup"><span data-stu-id="ceffd-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="ceffd-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="ceffd-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="ceffd-129">Não</span><span class="sxs-lookup"><span data-stu-id="ceffd-129">No</span></span>|  
  
     <span data-ttu-id="ceffd-130">O exemplo de código a seguir usa a configuração para especificar `wsHttpBinding_Calculator` uma associação denominada que usa a [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança de mensagem e sessões seguras.</span><span class="sxs-lookup"><span data-stu-id="ceffd-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="ceffd-131">O exemplo de código a seguir especifica que os [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança de mensagem e sessões seguras são usados `secureCalculator` para proteger o serviço.</span><span class="sxs-lookup"><span data-stu-id="ceffd-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="ceffd-132">As sessões seguras podem ser desativadas para o [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) definindo `establishSecurityContext` o atributo `false`como.</span><span class="sxs-lookup"><span data-stu-id="ceffd-132">Secure sessions can be turned off for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="ceffd-133">Para as outras associações fornecidas pelo sistema, as sessões seguras só podem ser desativadas com a criação de uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="ceffd-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="ceffd-134">Para especificar que um serviço usa sessões seguras usando uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="ceffd-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="ceffd-135">Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ceffd-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="ceffd-136">Para obter mais informações sobre como criar uma associação personalizada [, consulte Como: Personalize uma associação](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ceffd-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="ceffd-137">O exemplo de código a seguir usa a configuração para especificar uma ligação personalizada que mensagens usando uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ceffd-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="ceffd-138">O exemplo de código a seguir cria uma associação personalizada que <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> usa o modo de autenticação para inicializar uma sessão segura.</span><span class="sxs-lookup"><span data-stu-id="ceffd-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ceffd-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceffd-139">See also</span></span>

- [<span data-ttu-id="ceffd-140">Visão geral de associações do WCF</span><span class="sxs-lookup"><span data-stu-id="ceffd-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
