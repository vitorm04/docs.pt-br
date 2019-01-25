---
title: 'Como: Habilitar a detecção de reprodução de mensagem'
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
ms.openlocfilehash: 8a5f693b98d1437ccf0c8a373fcb11aa96ee6191
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653574"
---
# <a name="how-to-enable-message-replay-detection"></a>Como: Habilitar a detecção de reprodução de mensagem
Um ataque de repetição ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo a um ou mais das partes. A menos que atenuado, os computadores sujeita a ataque processará o fluxo como mensagens legítimas, resultando em um intervalo de consequências incorretas, como com redundância de pedidos de um item.  
  
 Para obter mais informações sobre a detecção de reprodução de mensagem, consulte [detecção de reprodução de mensagem](https://go.microsoft.com/fwlink/?LinkId=88536).  
  
 O procedimento a seguir demonstra as várias propriedades que você pode usar para controlar a detecção de reprodução usando o Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Para controlar a detecção de reprodução no cliente usando código  
  
1.  Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, confira [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). O exemplo a seguir usa uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> criado com o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> da <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
2.  Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> de classe e definir qualquer uma das propriedades a seguir, conforme apropriado:  
  
    1.  `DetectReplay`. Um valor booliano. Isso determina se o cliente deve detectar repetições do servidor. O padrão é `true`.  
  
    2.  `MaxClockSkew`. Um valor <xref:System.TimeSpan>. Controla quanto distorção de tempo que o mecanismo de reprodução pode tolerar entre o cliente e o servidor. O mecanismo de segurança examina o tempo de carimbo de data / enviados e determina se ele foi enviado muito distante no passado. O padrão é 5 minutos.  
  
    3.  `ReplayWindow`. Um valor `TimeSpan`. Isso controla quanto tempo uma mensagem podem residir na rede depois que o servidor envia a ele (por meio de intermediários) antes de alcançar o cliente. O cliente controla as assinaturas das mensagens enviadas dentro a versão mais recente `ReplayWindow` para fins de detecção de reprodução.  
  
    4.  `ReplayCacheSize`. Um valor inteiro. O cliente armazena as assinaturas da mensagem em um cache. Essa configuração especifica quantas assinaturas, o cache pode armazenar. Se o número de mensagens enviadas dentro a última janela reprodução atingir o limite de cache, novas mensagens são rejeitadas até que as assinaturas em cache mais antigas alcance o limite de tempo. O padrão é 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Para controlar a detecção de reprodução no serviço usando código  
  
1.  Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> de classe e defina as propriedades conforme descrito anteriormente.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Para controlar a detecção de reprodução na configuração do cliente ou serviço  
  
1.  Criar uma [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Criar um `<security>` elemento.  
  
3.  Criar uma [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) ou [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
4.  Defina os seguintes valores de atributo, conforme apropriado: `detectReplays`, `maxClockSkew`, `replayWindow`, e `replayCacheSize`. O exemplo a seguir define os atributos de ambos um `<localServiceSettings>` e um `<localClientSettings>` elemento:  
  
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
 O exemplo a seguir cria uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> método e define as propriedades de reprodução da associação.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Escopo da reprodução: Somente segurança de mensagem  
 Observe que os procedimentos a seguir se aplicam somente ao modo de segurança de mensagem. Para o transporte com modos de credencial de mensagem e transporte, os mecanismos de transporte detectam repetições.  
  
## <a name="secure-conversation-notes"></a>Proteger as notas de conversa  
 Para associações que permitem que conversas seguras, você pode ajustar essas configurações tanto para o canal de aplicativo, bem como para a associação de inicialização de conversa segura. Por exemplo, você pode desativar repetições para o canal de aplicativo, mas habilitá-los para o canal de bootstrap que estabelece a conversa segura.  
  
 Se você não usar sessões de conversa segura, detecção de reprodução não garante a detecção de repetições em cenários de farm de servidor e quando o processo ser reciclado. Isso se aplica às seguintes associações fornecidas pelo sistema:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> com o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade definida como `false`.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Os seguintes namespaces são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [Sessões e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
