---
title: Como fazer auditoria de eventos de segurança do Windows Communication Foundation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: b96c68c06099db2f396d16772cfaa8aee37390fe
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838007"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Como fazer auditoria de eventos de segurança do Windows Communication Foundation
O Windows Communication Foundation (WCF) permite que você registre eventos de segurança no log de eventos do Windows, que pode ser exibido usando o Visualizador de Eventos do Windows. Este tópico explica como configurar um aplicativo para que ele registre eventos de segurança. Para obter mais informações sobre a auditoria do WCF, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Para auditar eventos de segurança no código  
  
1. Especifique o local do log de auditoria. Para fazer isso, defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> da classe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> como um dos valores de enumeração <xref:System.ServiceModel.AuditLogLocation>, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     A enumeração <xref:System.ServiceModel.AuditLogLocation> tem três valores: `Application`, `Security`ou `Default`. O valor especifica um dos logs visíveis no Visualizador de Eventos, o log de segurança ou o log do aplicativo. Se você usar o valor `Default`, o log real dependerá do sistema operacional em que o aplicativo está sendo executado. Se a auditoria estiver habilitada e o local do log não for especificado, o padrão será o log de `Security` para as plataformas que dão suporte à gravação no log de segurança; caso contrário, ele gravará no log de `Application`. Somente [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e o Windows Vista dão suporte à gravação no log de segurança por padrão.  
  
2. Configure os tipos de eventos para auditar. Você pode auditar simultaneamente eventos de nível de serviço ou eventos de autorização no nível de mensagem. Para fazer isso, defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> ou a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> como um dos valores de enumeração <xref:System.ServiceModel.AuditLevel>, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Especifique se deseja suprimir ou expor falhas ao aplicativo em relação aos eventos de auditoria de log. Defina a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> como `true` ou `false`, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     A propriedade de `SuppressAuditFailure` padrão é `true`, para que a falha na auditoria não afete o aplicativo. Caso contrário, uma exceção será gerada. Para qualquer auditoria bem-sucedida, um rastreamento detalhado é gravado. Para qualquer falha na auditoria, o rastreamento é gravado no nível de erro.  
  
4. Exclua o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existente da coleção de comportamentos encontrados na descrição de um <xref:System.ServiceModel.ServiceHost>. A coleção de comportamento é acessada pela propriedade <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, que, por sua vez, é acessada pela propriedade <xref:System.ServiceModel.ServiceHostBase.Description%2A>. Em seguida, adicione o novo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à mesma coleção, conforme mostrado no código a seguir.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Para configurar a auditoria na configuração  
  
1. Para configurar a auditoria na configuração, adicione um elemento de [comportamento de\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) à seção [\<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) do arquivo Web. config. Em seguida, adicione um elemento [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) e defina os vários atributos, conforme mostrado no exemplo a seguir.  
  
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
  
2. Você deve especificar o comportamento para o serviço, conforme mostrado no exemplo a seguir.  
  
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
 O código a seguir cria uma instância da classe <xref:System.ServiceModel.ServiceHost> e adiciona uma nova <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sua coleção de comportamentos.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Definir a propriedade <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> como `true`, suprime qualquer falha ao gerar auditorias de segurança (se definido como `false`, uma exceção é lançada). No entanto, se você habilitar a seguinte propriedade de **configuração de segurança local** do Windows, uma falha ao gerar eventos de auditoria fará com que o Windows seja desligado imediatamente:  
  
 **Auditoria: desligar o sistema imediatamente se não for possível registrar auditorias de segurança**  
  
 Para definir a propriedade, abra a caixa de diálogo **configurações de segurança local** . Em **configurações de segurança**, clique em **políticas locais**. Em seguida, clique em **Opções de segurança**.  
  
 Se a propriedade <xref:System.ServiceModel.AuditLogLocation> for definida como <xref:System.ServiceModel.AuditLogLocation.Security> e o **acesso ao objeto de auditoria** não estiver definido na política de **segurança local**, os eventos de auditoria não serão gravados no log de segurança. Observe que nenhuma falha é retornada, mas as entradas de auditoria não são gravadas no log de segurança.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
