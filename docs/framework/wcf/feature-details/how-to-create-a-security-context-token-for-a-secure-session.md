---
title: Como criar um token de contexto de segurança para uma sessão segura
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
ms.openlocfilehash: 4e91580035d4de23ae90cd0d59a08f321ae70a1c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464143"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Como criar um token de contexto de segurança para uma sessão segura
Ao usar um token de contexto de segurança de estado (SCT) em uma sessão segura, a sessão pode suportar que o serviço seja reciclado. Por exemplo, quando um SCT apátrida é usado em uma sessão segura e o IIS (Internet Information Services, serviços de informações da Internet) é redefinido, então os dados de sessão associados ao serviço são perdidos. Esses dados da sessão incluem um cache de token SCT. Assim, da próxima vez que um cliente envia ao serviço um SCT apátrida, um erro é devolvido, porque a chave associada ao SCT não pode ser recuperada. Se, no entanto, um SCT imponente for usado, então a chave associada ao SCT está contida no SCT. Como a chave está contida no SCT e, portanto, contida na mensagem, a sessão segura não é afetada pelo serviço ser reciclado. Por padrão, o Windows Communication Foundation (WCF) usa SCTs apátridas em uma sessão segura. Este tópico detalha como usar SCTs estaduais em uma sessão segura.  
  
> [!NOTE]
> Os SCTs estaduais não podem ser usados em <xref:System.ServiceModel.Channels.IDuplexChannel>uma sessão segura que envolva um contrato derivado de .  
  
> [!NOTE]
> Para aplicativos que usam SCTs estaduais em uma sessão segura, a identidade do thread para o serviço deve ser uma conta de usuário que tenha um perfil de usuário associado. Quando o serviço é executado em uma conta que `Local Service`não tem um perfil de usuário, como , uma exceção pode ser lançada.  
  
> [!NOTE]
> Quando a representação for necessária no Windows XP, use uma sessão segura sem um SCT imponente. Quando SCTs estaduais são usados <xref:System.InvalidOperationException> com personificação, um é jogado. Para obter mais informações, consulte [Cenários Não Suportados](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Para usar SCTs estaduais em uma sessão segura  
  
- Crie uma vinculação personalizada que especifica que as mensagens SOAP são protegidas por uma sessão segura que usa um SCT imponente.  
  
    1. Defina uma vinculação personalizada, adicionando um [ \<>de vinculação personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ao arquivo de configuração do serviço.  
  
        ```xml  
        <customBinding>  
        </customBinding>
        ```  
  
    2. Adicione [ \<](../../configure-apps/file-schema/wcf/bindings.md) um elemento de>criança de vinculação ao [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Especifique um `name` nome de vinculação definindo o atributo para um nome único dentro do arquivo de configuração.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        </binding>
        ```  
  
    3. Especifique o modo de autenticação para mensagens enviadas para e a partir deste serviço adicionando um [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento de segurança>filho ao [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Especifique que uma sessão `authenticationMode` segura `SecureConversation`é usada definindo o atributo para . Especifique que os SCTs `requireSecurityContextCancellation` estaduais são usados definindo o atributo para `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">
        </security>
        ```  
  
    4. Especifique como o cliente é autenticado enquanto a sessão segura é [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)estabelecida adicionando um [ \<elemento de>filho seguroConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) à>de segurança .  
  
         Especifique como o cliente `authenticationMode` é autenticado definindo o atributo.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5. Especifique a codificação da mensagem adicionando um elemento de codificação, como [ \<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6. Especifique o transporte adicionando um elemento de transporte, como o [ \<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     O exemplo de código a seguir usa a configuração para especificar uma vinculação personalizada que as mensagens podem usar com SCTs estaduais em uma sessão segura.  
  
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
 O exemplo de código a seguir <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> cria uma vinculação personalizada que usa o modo de autenticação para bootstrap de uma sessão segura.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Quando a autenticação do Windows é usada em combinação com <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> um SCT imponente, o WCF não preenche a propriedade com a identidade do chamador real, mas define a propriedade como anônima. Como a segurança do WCF deve recriar o conteúdo do contexto de segurança do serviço para cada solicitação do SCT de entrada, o servidor não acompanha a sessão de segurança na memória. Como é impossível serializar <xref:System.Security.Principal.WindowsIdentity> a instância no <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> SCT, a propriedade retorna uma identidade anônima.  
  
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
  
## <a name="see-also"></a>Confira também

- [\<>de vinculação personalizada](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
