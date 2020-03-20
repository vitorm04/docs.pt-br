---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 62d26b24b5d46427c1871fccf48b063c45781beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185119"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Como fazer auditoria de eventos de segurança do Windows Communication Foundation
O Windows Communication Foundation (WCF) permite registrar eventos de segurança no registro de eventos do Windows, que podem ser visualizados usando o Visualizador de Eventos do Windows. Este tópico explica como configurar um aplicativo para que ele registre eventos de segurança. Para obter mais informações sobre auditoria wcf, consulte [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Para auditar eventos de segurança em código  
  
1. Especifique o local do registro de auditoria. Para isso, defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> a <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> propriedade da <xref:System.ServiceModel.AuditLogLocation> classe como um dos valores de enumeração, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     A <xref:System.ServiceModel.AuditLogLocation> enumeração tem `Application`três `Security`valores: , ou `Default`. O valor especifica um dos registros visíveis no Visualizador de Eventos, seja no registro de segurança ou no registro do aplicativo. Se você `Default` usar o valor, o registro real dependerá do sistema operacional em que o aplicativo está sendo executado. Se a auditoria estiver ativada e o local do `Security` log não for especificado, o padrão será o registro de plataformas que suportam a gravação no registro de segurança; caso contrário, ele vai `Application` escrever para o log. Apenas o Windows Server 2003 e o Windows Vista suportam a gravação no registro de segurança por padrão.  
  
2. Configure os tipos de eventos para auditoria. Você pode auditar simultaneamente eventos de nível de serviço ou eventos de autorização de nível de mensagem. Para isso, defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> a <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> propriedade ou <xref:System.ServiceModel.AuditLevel> a propriedade como um dos valores de enumeração, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Especifique se deve suprimir ou expor falhas ao aplicativo em relação a eventos de auditoria de log. Defina <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> a `true` propriedade `false`como ou, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     A `SuppressAuditFailure` propriedade `true`padrão é, de modo que a falha na auditoria não afete o aplicativo. Caso contrário, uma exceção será gerada. Para qualquer auditoria bem sucedida, um traço verboso é escrito. Para qualquer falha na auditoria, o rastreamento é escrito no nível de erro.  
  
4. Exclua o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existente da coleção de comportamentos encontrados <xref:System.ServiceModel.ServiceHost>na descrição de um . A coleta de comportamento <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> é acessada pelo imóvel, que por sua vez é acessado a <xref:System.ServiceModel.ServiceHostBase.Description%2A> partir do imóvel. Em seguida, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> adicione o novo à mesma coleção, como mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Para configurar a auditoria na configuração  
  
1. Para configurar a auditoria na [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) configuração, adicione um elemento de comportamento>aos [ \<comportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) seção do arquivo Web.config. Em seguida, adicione um [ \<elemento de>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) e defina os vários atributos, como mostrado no exemplo a seguir.  
  
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
  
2. Você deve especificar o comportamento para o serviço, como mostrado no exemplo a seguir.  
  
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
 O código a seguir <xref:System.ServiceModel.ServiceHost> cria uma instância <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> da classe e adiciona uma nova coleção de comportamentos.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Definir <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> a `true`propriedade para, suprimir qualquer falha na geração `false`de auditorias de segurança (se definida para , uma exceção é lançada). No entanto, se você habilitar a seguinte propriedade **configuração de configuração de segurança local** do Windows, uma falha na geração de eventos de auditoria fará com que o Windows seja desligado imediatamente:  
  
 **Auditoria: Desligar o sistema imediatamente se não for possível registrar auditorias de segurança**  
  
 Para definir a propriedade, abra a caixa de diálogo **Configurações de segurança local.** Em **Configurações de segurança,** clique **em Políticas locais**. Em seguida, clique **em Opções de segurança**.  
  
 Se <xref:System.ServiceModel.AuditLogLocation> a propriedade <xref:System.ServiceModel.AuditLogLocation.Security> estiver definida e o **Audit Object Access** não estiver definido na Política de Segurança **Local,** os eventos de auditoria não serão gravados no registro de segurança. Observe que nenhuma falha é retornada, mas as entradas de auditoria não estão escritas no registro de segurança.  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
