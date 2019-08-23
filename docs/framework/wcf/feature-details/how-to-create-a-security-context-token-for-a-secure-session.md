---
title: 'Como: criar um token de contexto de segurança para uma sessão segura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: e6c41ed32d63932bc1fac72bc6e727eb82806617
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966077"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Como: criar um token de contexto de segurança para uma sessão segura
Usando um símbolo de contexto de segurança com estado (SCT) em uma sessão segura, a sessão pode resistir ao serviço que está sendo reciclado. Por exemplo, quando um SCT sem estado é usado em uma sessão segura e Serviços de Informações da Internet (IIS) é redefinido, os dados de sessão associados ao serviço são perdidos. Esses dados de sessão incluem um cache de token SCT. Assim, na próxima vez que um cliente envia o serviço a um SCT sem estado, um erro é retornado, pois a chave associada ao SCT não pode ser recuperada. Se, no entanto, um SCT com estado for usado, a chave que está associada ao SCT está contida no SCT. Como a chave está contida no SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço que está sendo reciclado. Por padrão, Windows Communication Foundation (WCF) usa SCTs sem estado em uma sessão segura. Este tópico fornece detalhes sobre como usar SCTs com estado em uma sessão segura.  
  
> [!NOTE]
> O estado SCTs não pode ser usado em uma sessão segura que envolve um contrato derivado de <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
> Para aplicativos que usam SCTs com estado em uma sessão segura, a identidade do thread para o serviço deve ser uma conta de usuário que tenha um perfil de usuário associado. Quando o serviço é executado em uma conta que não tem um perfil de usuário, `Local Service`como, uma exceção pode ser lançada.  
  
> [!NOTE]
> Quando a representação é necessária no Windows XP, use uma sessão segura sem um SCT com estado. Quando SCTs com estado são usados com representação, <xref:System.InvalidOperationException> um é gerado. Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Para usar SCTs com estado em uma sessão segura  
  
- Crie uma associação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT com estado.  
  
    1. Defina uma associação personalizada, adicionando um [ \<> personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) para o arquivo de configuração do serviço.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2. Adicione uma [ \<Associação >](../../../../docs/framework/misc/binding.md) elemento [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)filho ao > CustomBinding.  
  
         Especifique um nome de associação definindo o `name` atributo como um nome exclusivo dentro do arquivo de configuração.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3. Especifique o modo de autenticação para as mensagens enviadas de e para esse serviço adicionando um [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento filho de segurança para a [ \<> personalizadabinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Especifique que uma sessão segura é usada definindo o `authenticationMode` atributo como. `SecureConversation` Especifique que SCTs com estado são usados definindo o `requireSecurityContextCancellation` atributo como `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4. Especifique como o cliente é autenticado enquanto a sessão segura é estabelecida adicionando um [ \<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento filho ao > de [ \<segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Especifique como o cliente é autenticado definindo o `authenticationMode` atributo.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Especifique a codificação de mensagem adicionando um elemento de codificação, [ \<como textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Especifique o transporte adicionando um elemento de transporte, como o [ \<> httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     O exemplo de código a seguir usa a configuração para especificar uma associação personalizada que as mensagens podem usar com estado SCTs em uma sessão segura.  
  
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
 O exemplo de código a seguir cria uma associação personalizada que <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> usa o modo de autenticação para inicializar uma sessão segura.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Quando a autenticação do Windows é usada em combinação com um SCT com estado, o WCF <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> não preenche a propriedade com a identidade do chamador real, mas, em vez disso, define a propriedade como anônima. Como a segurança do WCF deve recriar o conteúdo do contexto de segurança do serviço para cada solicitação da SCT de entrada, o servidor não mantém o controle da sessão de segurança na memória. Como é impossível serializar a <xref:System.Security.Principal.WindowsIdentity> instância no SCT, a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade retorna uma identidade anônima.  
  
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

- [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
