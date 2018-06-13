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
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Como criar um token de contexto de segurança para uma sessão segura
Usando um token de contexto de segurança com monitoração de estado (SCT) em uma sessão segura, a sessão pode suportar o serviço ser reciclado. Por exemplo, quando um SCT sem monitoração de estado é usado em uma sessão segura e redefinição de serviços de informações da Internet (IIS), os dados da sessão que está associados com o serviço serão perdidos. Esses dados de sessão incluem um cache de token SCT. Portanto, na próxima vez que um cliente envia o serviço um SCT sem monitoração de estado, um erro será retornado, porque a chave que está associada com o SCT não pode ser recuperada. Se, no entanto, um SCT com monitoração de estado é usado, a chave que está associada com o SCT está contida dentro de SCT. Porque a chave é contida o SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço de ser reciclado. Por padrão, o Windows Communication Foundation (WCF) usa SCTs sem monitoração de estado em uma sessão segura. Este tópico fornece detalhes sobre como usar SCTs com monitoração de estado em uma sessão segura.  
  
> [!NOTE]
>  SCTs com monitoração de estado não podem ser usados em uma sessão segura que envolve um contrato que deriva de <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Para aplicativos que usam SCTs com monitoração de estado em uma sessão segura, a identidade do segmento para o serviço deve ser uma conta de usuário que tem um perfil de usuário associado. Quando o serviço é executado sob uma conta que não tem um perfil de usuário, como `Local Service`, uma exceção pode ser lançada.  
  
> [!NOTE]
>  Quando a representação é necessário no Windows XP, use uma sessão segura sem um SCT com monitoração de estado. Quando SCTs com monitoração de estado são usadas com representação, um <xref:System.InvalidOperationException> é gerada. Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Para usar SCTs com monitoração de estado em uma sessão segura  
  
-   Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT com monitoração de estado.  
  
    1.  Definir uma associação personalizada, adicionando um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) para o arquivo de configuração para o serviço.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Adicionar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento filho para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Especifique um nome de associação, definindo o `name` de atributo para um nome exclusivo dentro do arquivo de configuração.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Especifique o modo de autenticação para mensagens enviadas para e a partir desse serviço, adicionando um [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento filho para o [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Especificar que uma sessão segura é usada, definindo o `authenticationMode` atributo `SecureConversation`. Especifique que SCTs com monitoração de estado são usadas, definindo o `requireSecurityContextCancellation` atributo `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Especifique como o cliente é autenticado enquanto a sessão segura é estabelecida com a adição de um [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho para o [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Especifique como o cliente é autenticado, definindo o `authenticationMode` atributo.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Especifique a codificação de mensagens adicionando um elemento de codificação, como [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Especifique o transporte adicionando um elemento de transporte, como o [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     O exemplo de código a seguir usa a configuração para especificar uma associação personalizada que mensagens podem usar com SCTs com monitoração de estado em uma sessão segura.  
  
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
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria uma associação personalizada que usa o <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> modo de autenticação para inicializar uma sessão segura.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Quando a autenticação do Windows é usada em combinação com um SCT com monitoração de estado, o WCF não preencher a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade com o chamador real da identidade, mas em vez disso, define a propriedade como anônimo. Porque a segurança do WCF deve recriar o conteúdo do contexto de segurança de serviço para cada solicitação de SCT a entrada, o servidor não manter o controle de sessão de segurança na memória. Porque não é possível serializar o <xref:System.Security.Principal.WindowsIdentity> instância em SCT, o <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade retorna uma identidade anônima.  
  
 A configuração a seguir exibe esse comportamento.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
