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
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184946"
---
# <a name="how-to-enable-message-replay-detection"></a>Como habilitar a detecção de repetição de mensagem
Um ataque de repetição ocorre quando um invasor copia um fluxo de mensagens entre duas partes e reproduz o fluxo para uma ou mais das partes. A menos que mitigado, os computadores sujeitos ao ataque processarão o fluxo como mensagens legítimas, resultando em uma série de consequências ruins, como ordens redundantes de um item.  
  
 Para obter mais informações sobre a detecção de repetição de mensagens, consulte [Detecção de reprodução de mensagens](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).  
  
 O procedimento a seguir demonstra várias propriedades que você pode usar para controlar a detecção de repetição usando o Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Para controlar a detecção de repetição no cliente usando código  
  
1. Crie <xref:System.ServiceModel.Channels.SecurityBindingElement> um para <xref:System.ServiceModel.Channels.CustomBinding>usar em um . Para obter mais informações, [consulte Como: Criar uma vinculação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). O exemplo a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> seguir usa <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> um <xref:System.ServiceModel.Channels.SecurityBindingElement> criado com o da classe.  
  
2. Use <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> a propriedade para retornar <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> uma referência à classe e definir qualquer uma das seguintes propriedades, conforme apropriado:  
  
    1. `DetectReplay`. Um valor booliano. Isso rege se o cliente deve detectar replays do servidor. O padrão é `true`.  
  
    2. `MaxClockSkew`. Um valor <xref:System.TimeSpan>. Ele governa quanto tempo o mecanismo de repetição pode tolerar entre o cliente e o servidor. O mecanismo de segurança examina o carimbo de hora enviado e determina se foi enviado muito para trás no passado. O padrão é 5 minutos.  
  
    3. `ReplayWindow`. Um valor `TimeSpan`. Isso rege o tempo que uma mensagem pode viver na rede depois que o servidor a envia (através de intermediários) antes de chegar ao cliente. O cliente rastreia as assinaturas das mensagens enviadas no mais recente `ReplayWindow` para fins de detecção de repetição.  
  
    4. `ReplayCacheSize`. Um valor inteiro. O cliente armazena as assinaturas da mensagem em um cache. Esta configuração especifica quantas assinaturas o cache pode armazenar. Se o número de mensagens enviadas na última janela de replay atingir o limite de cache, novas mensagens serão rejeitadas até que as assinaturas armazenadas em cache mais antigas atinjam o limite de tempo. O padrão é 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Para controlar a detecção de repetição no serviço usando código  
  
1. Crie <xref:System.ServiceModel.Channels.SecurityBindingElement> um para <xref:System.ServiceModel.Channels.CustomBinding>usar em um .  
  
2. Use <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> a propriedade para retornar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> uma referência à classe e defina as propriedades como descrito anteriormente.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Para controlar a detecção de repetição na configuração para o cliente ou serviço  
  
1. Crie um [ \<>de vinculação personalizado ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Crie `<security>` um elemento.  
  
3. Crie um [ \<>de configurações de cliente sumido](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) local ou [ \<>de serviços locais ](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4. Defina os seguintes valores `maxClockSkew` `replayWindow`de `replayCacheSize`atributo, conforme apropriado: `detectReplays`, e . O exemplo a seguir define `<localServiceSettings>` os `<localClientSettings>` atributos de a e de um elemento:  
  
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
 O exemplo a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> seguir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> cria um uso do método e define as propriedades de repetição da vinculação.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Escopo de replay: somente segurança de mensagens  
 Observe que os procedimentos a seguir se aplicam apenas ao modo de segurança de mensagem. Para os modos Transport and Transport with Message Credential, os mecanismos de transporte detectam repetições.  
  
## <a name="secure-conversation-notes"></a>Notas de conversação seguras  
 Para vinculações que permitem conversas seguras, você pode ajustar essas configurações tanto para o canal do aplicativo quanto para a vinculação de bootstrap de conversação segura. Por exemplo, você pode desativar replays para o canal do aplicativo, mas habilitá-los para o canal bootstrap que estabelece a conversa segura.  
  
 Se você não usar sessões de conversação seguras, a detecção de repetição não garante a detecção de replays em cenários de fazendas de servidores e quando o processo é reciclado. Isso se aplica às seguintes vinculações fornecidas pelo sistema:  
  
- <xref:System.ServiceModel.BasicHttpBinding>.  
  
- <xref:System.ServiceModel.WSHttpBinding>com <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> a propriedade `false`definida para .  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
- Os seguintes namespaces são necessários para compilar o código:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Sessões seguras e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
