---
title: "Como criar uma sessão segura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f2393209352f18eb25b9837ca1ad8ca2746b91d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-secure-session"></a>Como criar uma sessão segura
Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) associação, as associações fornecidas pelo sistema em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automaticamente use sessões seguras quando a segurança de mensagens está habilitada.  
  
 Por padrão, sessões seguras não sobrevivem a um servidor Web que é reciclado. Quando uma sessão segura é estabelecida, o cliente e o serviço de cache a chave que está associada com a sessão segura. Como as mensagens são trocadas, apenas um identificador para a chave armazenada em cache é trocado. Se o servidor Web for reciclado, o cache é reciclado, também, de modo que o servidor Web não é possível recuperar a chave armazenada em cache para o identificador. Se isso acontecer, uma exceção será devolvida ao cliente. Sessões seguras que usam um token de contexto de segurança com monitoração de estado (SCT) podem sobreviver a um servidor Web que estão sendo reciclado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando um SCT com monitoração de estado em uma sessão segura, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Para especificar que um serviço usa sessões seguras usando uma das associações fornecidas pelo sistema  
  
-   Configure um serviço para usar uma associação fornecida pelo sistema que dá suporte à segurança de mensagem.  
  
     Com exceção do [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) associação, quando as associações fornecidas pelo sistema são configuradas para usar a segurança de mensagem, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticamente usa sessões seguras. A tabela a seguir lista as associações fornecidas pelo sistema que oferecem suporte à segurança de mensagem e se a segurança de mensagem é o mecanismo de segurança padrão.  
  
    |Associação fornecida pelo sistema|Elemento de configuração|Segurança de mensagem em por padrão|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Não|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Sim|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Não|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Não|  
  
     O exemplo de código a seguir usa a configuração para especificar uma associação denominada `wsHttpBinding_Calculator` que usa o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança e proteger sessões.  
  
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
  
     O exemplo de código a seguir especifica que o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), segurança e proteger as sessões são usadas para proteger o `secureCalculator` service.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Sessões seguras podem ser desativadas para o [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) definindo o `establishSecurityContext` atributo `false`. Para outros fornecido pelo sistema associações, sessões seguras podem apenas ser desativadas, criando uma associação personalizada.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Para especificar que um serviço usa sessões seguras usando uma associação personalizada  
  
-   Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]criar uma associação personalizada, consulte [como: personalizar uma associação System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
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
 [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md) (Visão geral de associações do WCF)
