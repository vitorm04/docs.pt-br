---
title: Como habilitar a detecção de repetição de mensagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964657"
---
# <a name="how-to-enable-message-replay-detection"></a>Como habilitar a detecção de repetição de mensagem
Um ataque de reprodução ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo para uma ou mais das partes. A menos que seja atenuado, os computadores sujeitos ao ataque processarão o fluxo como mensagens legítimas, resultando em uma variedade de consequências inadequadas, como ordens redundantes de um item.  
  
 Para obter mais informações sobre a detecção de reprodução de mensagem, consulte [detecção de reprodução de mensagem](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 O procedimento a seguir demonstra várias propriedades que você pode usar para controlar a detecção de reprodução usando o Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Para controlar a detecção de reprodução no cliente usando código  
  
1. Crie um <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em uma <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, consulte [como: criar uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). O exemplo a seguir usa um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> criado com o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> da classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Use a propriedade <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> para retornar uma referência à classe <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> e defina qualquer uma das propriedades a seguir, conforme apropriado:  
  
    1. `DetectReplay`. Um valor booliano. Isso rege se o cliente deve detectar repetições do servidor. O padrão é `true`.  
  
    2. `MaxClockSkew`. Um valor <xref:System.TimeSpan>. Controla quanto tempo a distorção do mecanismo de reprodução pode tolerar entre o cliente e o servidor. O mecanismo de segurança examina o carimbo de data/hora enviado e determina se ele foi enviado muito longe no passado. O padrão é 5 minutos.  
  
    3. `ReplayWindow`. Um valor `TimeSpan`. Isso rege quanto tempo uma mensagem pode residir na rede depois que o servidor a envia (por meio de intermediários) antes de acessar o cliente. O cliente rastreia as assinaturas das mensagens enviadas na `ReplayWindow` mais recente para fins de detecção de repetição.  
  
    4. `ReplayCacheSize`. Um valor inteiro. O cliente armazena as assinaturas da mensagem em um cache. Essa configuração especifica quantas assinaturas o cache pode armazenar. Se o número de mensagens enviadas na última janela de reprodução atingir o limite de cache, novas mensagens serão rejeitadas até que as assinaturas armazenadas em cache mais antigas atinjam o limite de tempo. O padrão é 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Para controlar a detecção de reprodução no serviço usando código  
  
1. Crie um <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em uma <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2. Use a propriedade <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> para retornar uma referência à classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> e defina as propriedades conforme descrito anteriormente.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Para controlar a detecção de reprodução na configuração do cliente ou serviço  
  
1. Crie um [\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Crie um elemento `<security>`.  
  
3. Crie um [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) ou [\<> de localServiceSettings](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Defina os seguintes valores de atributo, conforme apropriado: `detectReplays`, `maxClockSkew`, `replayWindow`e `replayCacheSize`. O exemplo a seguir define os atributos de um `<localServiceSettings>` e um elemento `<localClientSettings>`:  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> usando o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> e define as propriedades de reprodução da associação.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Escopo da reprodução: somente segurança da mensagem  
 Observe que os procedimentos a seguir se aplicam somente ao modo de segurança da mensagem. Para transporte e transporte com modos de credenciais de mensagem, os mecanismos de transporte detectam repetições.  
  
## <a name="secure-conversation-notes"></a>Proteger anotações de conversa  
 Para associações que habilitam conversas seguras, você pode ajustar essas configurações para o canal de aplicativo, bem como para a associação de inicialização de conversa segura. Por exemplo, você pode desativar as repetições para o canal de aplicativo, mas habilitá-las para o canal de bootstrap que estabelece a conversa segura.  
  
 Se você não usar sessões de conversa seguras, a detecção de repetição não garantirá a detecção de repetições em cenários de farm de servidores e quando o processo for reciclado. Isso se aplica às seguintes associações fornecidas pelo sistema:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding> com a propriedade <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> definida como `false`.  
  
## <a name="compiling-the-code"></a>Compilando o Código  
  
- Os namespaces a seguir são necessários para compilar o código:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Veja também

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Sessões e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
