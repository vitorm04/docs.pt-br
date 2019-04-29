---
title: 'Como: criar uma sessão segura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 4464100012fe9b3e1f0e8743707b1dc9a477c3d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787862"
---
# <a name="how-to-create-a-secure-session"></a>Como: criar uma sessão segura
Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) de associação, as associações fornecidas pelo sistema no Windows Communication Foundation (WCF) automaticamente usam sessões seguras quando a segurança de mensagens está habilitada.  
  
 Por padrão, sessões seguras não sobrevivem a um servidor Web que é reciclado. Quando uma sessão segura é estabelecida, o cliente e o serviço de cache a chave que está associada com a sessão segura. Como as mensagens são trocadas, apenas um identificador para a chave armazenada em cache é trocado. Se o servidor Web for reciclado, o cache é reciclado, também, de modo que o servidor Web não é possível recuperar a chave armazenada em cache para o identificador. Se isso acontecer, uma exceção será devolvida ao cliente. Sessões seguras que usam um token de contexto de segurança com monitoração de estado (SCT) possam sobreviver a um servidor Web que está sendo reciclado. Para obter mais informações sobre como usar um SCT com monitoração de estado em uma sessão segura, consulte [como: Criar um contexto de segurança para uma sessão segura Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Para especificar que um serviço usa sessões seguras usando uma das associações fornecidas pelo sistema  
  
- Configure um serviço para usar uma associação fornecida pelo sistema que dá suporte à segurança de mensagem.  
  
     Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) de associação, quando as associações fornecidas pelo sistema estão configuradas para usar automaticamente a segurança de mensagem, WCF usa sessões seguras. A tabela a seguir lista as associações fornecidas pelo sistema que dão suporte à segurança de mensagem e se a segurança de mensagem é o mecanismo de segurança padrão.  
  
    |Associação fornecida pelo sistema|Elemento de configuração|Segurança de mensagem em por padrão|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Não|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Não|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Não|  
  
     O exemplo de código a seguir usa a configuração para especificar uma associação denominada `wsHttpBinding_Calculator` que usa o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança da mensagem e proteger sessões.  
  
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
  
     O exemplo de código a seguir especifica que o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), a segurança da mensagem e proteger as sessões são usadas para proteger o `secureCalculator` serviço.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Sessões seguras podem ser desativadas para o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) definindo a `establishSecurityContext` atributo `false`. Para as outras associações fornecidas pelo sistema, sessões seguras podem apenas ser desativadas, criando uma associação personalizada.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Para especificar que um serviço usa sessões seguras usando uma associação personalizada  
  
- Crie uma ligação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura.  
  
     Para obter mais informações sobre como criar uma ligação personalizada, consulte [como: Personalizar uma associação fornecida pelo sistema](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     O exemplo de código a seguir usa a configuração para especificar uma associação que as mensagens usando uma sessão segura personalizada.  
  
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
  
     O exemplo de código a seguir cria uma associação personalizada que usa o <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> modo de autenticação para inicializar uma sessão segura.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de associações do WCF](../../../../docs/framework/wcf/bindings-overview.md)
