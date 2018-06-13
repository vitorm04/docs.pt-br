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
ms.openlocfilehash: 5c761a23d2560f40a0121d684dcb411a716de5a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497133"
---
# <a name="how-to-enable-message-replay-detection"></a>Como habilitar a detecção de repetição de mensagem
Um ataque de repetição ocorre quando um invasor copia um fluxo de mensagens entre duas partes e repete o fluxo para um ou mais das partes. A menos que atenuado, os computadores sujeitos a ataque processará o fluxo como mensagens legítimas, resultando em um intervalo de consequências incorretas, como pedidos de redundância de um item.  
  
 Para obter mais informações sobre a detecção de repetição de mensagem, consulte [a detecção de repetição de mensagem](http://go.microsoft.com/fwlink/?LinkId=88536).  
  
 O procedimento a seguir demonstra várias propriedades que você pode usar para controlar a detecção de repetição usando o Windows Communication Foundation (WCF).  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a>Para controlar a detecção de reprodução no cliente usando código  
  
1.  Criar um <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md). O exemplo a seguir usa uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> criado com o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
2.  Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> de classe e defina uma das propriedades a seguir, conforme apropriado:  
  
    1.  `DetectReplay`. Um valor booliano. Isso determina se o cliente deve detectar reproduções do servidor. O padrão é `true`.  
  
    2.  `MaxClockSkew`. Um valor <xref:System.TimeSpan>. Controla a quantidade distorção de tempo que o mecanismo de repetição pode tolerar entre o cliente e o servidor. O mecanismo de segurança examina o tempo carimbo enviados e determina se ele foi enviado muito distante no passado. O padrão é 5 minutos.  
  
    3.  `ReplayWindow`. Um valor `TimeSpan`. Isso determina quanto tempo uma mensagem pode permanecer na rede depois que o servidor envia (através de intermediários) antes de alcançar o cliente. O cliente controla as assinaturas das mensagens enviadas dentro a versão mais recente `ReplayWindow` para fins de detecção de reprodução.  
  
    4.  `ReplayCacheSize`. Um valor inteiro. O cliente armazena as assinaturas da mensagem em um cache. Essa configuração especifica quantas assinaturas pode armazenar o cache. Se o número de mensagens enviadas dentro da janela de reprodução última atingir o limite de cache, novas mensagens serão rejeitadas até que as assinaturas em cache mais antigas atingem o limite de tempo. O padrão é 500000.  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a>Para controlar a detecção de reprodução no serviço usando código  
  
1.  Criar um <xref:System.ServiceModel.Channels.SecurityBindingElement> para usar em um <xref:System.ServiceModel.Channels.CustomBinding>.  
  
2.  Use o <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> propriedade para retornar uma referência para o <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> de classe e defina as propriedades conforme descrito anteriormente.  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a>Para controlar a detecção de repetição na configuração do cliente ou serviço  
  
1.  Criar um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Criar um `<security>` elemento.  
  
3.  Criar um [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) ou [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).  
  
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
 O exemplo a seguir cria um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> usando o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> método e define as propriedades de reprodução da associação.  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a>Escopo da reprodução: segurança de mensagem somente  
 Observe que os procedimentos a seguir se aplicam somente ao modo de segurança de mensagem. Para o transporte com modos de credencial de mensagem e transporte, os mecanismos de transporte detectam reproduções.  
  
## <a name="secure-conversation-notes"></a>Proteger notas da conversa  
 Para associações que permitem conversas seguras, você pode ajustar essas configurações tanto para o canal de aplicativo, bem como para a associação de inicialização de conversa segura. Por exemplo, você pode desativar reproduções para o canal de aplicativo, mas habilitá-las para o canal de inicialização que estabelece a conversa segura.  
  
 Se você não usar sessões de conversa segura, detecção de reprodução não garante a detectar reproduções em cenários de farm de servidor e quando o processo ser reciclado. Isso se aplica às seguintes associações fornecidas pelo sistema:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>.  
  
-   <xref:System.ServiceModel.WSHttpBinding> com o <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> propriedade definida como `false`.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Os namespaces a seguir são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Sessões e conversas seguras](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
