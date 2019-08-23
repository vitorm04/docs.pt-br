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
# <a name="how-to-create-a-secure-session"></a>Como: criar uma sessão segura
Com exceção da Associação de [ \<> BasicHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , as associações fornecidas pelo sistema no Windows Communication Foundation (WCF) automaticamente usam sessões seguras quando a segurança da mensagem está habilitada.  
  
 Por padrão, as sessões seguras não sobrevivem a um servidor Web que é reciclado. Quando uma sessão segura é estabelecida, o cliente e o serviço armazenam em cache a chave que está associada à sessão segura. À medida que as mensagens são trocadas, apenas um identificador para a chave armazenada em cache é trocado. Se o servidor Web for reciclado, o cache também será reciclado, de modo que o servidor Web não possa recuperar a chave armazenada em cache para o identificador. Se isso acontecer, uma exceção será gerada de volta para o cliente. As sessões seguras que usam um identificador de contexto de segurança com estado (SCT) podem sobreviver a um servidor Web sendo reciclado. Para obter mais informações sobre como usar um SCT com estado em uma sessão [segura, consulte Como: Crie um token de contexto de segurança para uma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)sessão segura.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Para especificar que um serviço usa sessões seguras usando uma das associações fornecidas pelo sistema  
  
- Configure um serviço para usar uma associação fornecida pelo sistema que dê suporte à segurança de mensagens.  
  
     Com exceção da Associação de [ \<> BasicHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , quando as associações fornecidas pelo sistema são configuradas para usar a segurança de mensagem, o WCF usa automaticamente as sessões seguras. A tabela a seguir lista as associações fornecidas pelo sistema que dão suporte à segurança da mensagem e se a segurança da mensagem é o mecanismo de segurança padrão.  
  
    |Associação fornecida pelo sistema|Elemento de configuração|Segurança de mensagem ativada por padrão|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Não|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Não|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Não|  
  
     O exemplo de código a seguir usa a configuração para especificar `wsHttpBinding_Calculator` uma associação denominada que usa a [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança de mensagem e sessões seguras.  
  
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
  
     O exemplo de código a seguir especifica que os [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança de mensagem e sessões seguras são usados `secureCalculator` para proteger o serviço.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > As sessões seguras podem ser desativadas para o [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) definindo `establishSecurityContext` o atributo `false`como. Para as outras associações fornecidas pelo sistema, as sessões seguras só podem ser desativadas com a criação de uma associação personalizada.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Para especificar que um serviço usa sessões seguras usando uma associação personalizada  
  
- Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura.  
  
     Para obter mais informações sobre como criar uma associação personalizada [, consulte Como: Personalize uma associação](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)fornecida pelo sistema.  
  
     O exemplo de código a seguir usa a configuração para especificar uma ligação personalizada que mensagens usando uma sessão segura.  
  
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
  
     O exemplo de código a seguir cria uma associação personalizada que <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> usa o modo de autenticação para inicializar uma sessão segura.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md)
