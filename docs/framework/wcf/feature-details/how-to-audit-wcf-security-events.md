---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
ms.openlocfilehash: 1efd651751e0f81b5125b64f81f7d2087d002d8d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196272"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Como fazer auditoria de eventos de segurança do Windows Communication Foundation
Windows Communication Foundation (WCF) permite que você registre eventos de segurança para o log de eventos do Windows, que podem ser exibido usando o Visualizador de eventos do Windows. Este tópico explica como configurar um aplicativo para que ele registra eventos de segurança. Para obter mais informações sobre a auditoria do WCF, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Auditar eventos de segurança no código  
  
1.  Especifique o local do log de auditoria. Para fazer isso, defina as <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> propriedade do <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> classe para um do <xref:System.ServiceModel.AuditLogLocation> valores de enumeração, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     O <xref:System.ServiceModel.AuditLogLocation> enumeração possui três valores: `Application`, `Security`, ou `Default`. O valor especifica um dos logs visíveis no Visualizador de eventos, ou o log de segurança ou o log de aplicativo. Se você usar o `Default` valor, o log real dependerá o sistema operacional que o aplicativo está sendo executado. Se a auditoria está habilitada e o local do log não for especificado, o padrão é o `Security` log para plataformas que dão suporte a gravação no log de segurança; caso contrário, ele gravará o `Application` log. Somente [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)] suporte à gravação no log de segurança por padrão.  
  
2.  Configure os tipos de eventos para auditoria. Ao mesmo tempo, você pode auditar eventos de nível de serviço ou de autorização de nível de mensagem. Para fazer isso, defina as <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> propriedade ou o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> propriedade com um do <xref:System.ServiceModel.AuditLevel> valores de enumeração, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Especifique se deseja suprimir ou expor falhas para o aplicativo em relação à auditoria de eventos de log. Defina as <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade para um `true` ou `false`, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     O padrão `SuppressAuditFailure` é de propriedade `true`, de modo que a falha de auditoria não afeta o aplicativo. Caso contrário, uma exceção será gerada. Para qualquer auditoria bem-sucedida, um rastreamento detalhado é gravado. Para qualquer falha de auditoria, o rastreamento é gravado no nível de erro.  
  
4.  Exclua o existente <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> da coleção de comportamentos encontrado na descrição de um <xref:System.ServiceModel.ServiceHost>. A coleção de comportamentos é acessada pela <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> propriedade, que por sua vez é acessada a partir de <xref:System.ServiceModel.ServiceHostBase.Description%2A> propriedade. Em seguida, adicione o novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> na mesma coleção, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Para configurar a auditoria na configuração  
  
1.  Para configurar a auditoria na configuração, adicione uma [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento para o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) seção do arquivo Web. config. Em seguida, adicione uma [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elemento e defina os vários atributos, como mostrado no exemplo a seguir.  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  Você deve especificar o comportamento para o serviço, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria uma instância das <xref:System.ServiceModel.ServiceHost> de classe e adiciona um novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sua coleção de comportamentos.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Definindo o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade para `true`, suprime qualquer falha ao gerar auditorias de segurança (se definido como `false`, uma exceção é lançada). No entanto, se você habilitar o Windows a seguir **configuração de segurança Local** propriedade, uma falha ao gerar eventos de auditoria fará com que o Windows desligar imediatamente:  
  
 **Auditoria: Desligar o sistema imediatamente se não for possível registrar auditorias de segurança**  
  
 Para definir a propriedade, abra o **configurações de segurança Local** caixa de diálogo. Sob **as configurações de segurança**, clique em **políticas locais**. Em seguida, clique em **opções de segurança**.  
  
 Se o <xref:System.ServiceModel.AuditLogLocation> estiver definida como <xref:System.ServiceModel.AuditLogLocation.Security> e **acesso ao objeto de auditoria** não está definido na **política de segurança Local**, eventos de auditoria não serão gravados no log de segurança. Observe que nenhuma falha é retornada, mas as entradas de auditoria não são gravadas no log de segurança.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
