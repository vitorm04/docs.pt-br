---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 384a1cdb6d39f4d6ecd2353a15c0da7c6d2e82bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224036"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
Especifica configurações que habilitem a auditoria de eventos de segurança durante as operações de serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|auditLogLocation|Especifica o local do log de auditoria. Os valores válidos incluem o seguinte:<br /><br /> -Padrão: Eventos de segurança são gravados no log de aplicativo no Windows XP e no Log de eventos no Windows Server 2003 e Windows Vista.<br />-Aplicativo: Eventos de auditoria são gravados no Log de eventos do aplicativo.<br />-Segurança: Eventos de auditoria são gravados no Log de eventos de segurança.<br /><br /> O valor padrão é o padrão. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.<br /><br /> Aplicativos devem ser notificados para falhas de gravação no log de auditoria. Se seu aplicativo não foi projetado para lidar com falhas de auditoria, você deve usar esse atributo para suprimir falhas na gravação no log de auditoria.<br /><br /> Se esse atributo for `true`, as exceções que não seja a OutOfMemoryException, StackOverFlowException, ThreadAbortException e ArgumentException resultantes de tentativas de gravar eventos de auditoria são manipuladas pelo sistema e não são propagadas para o aplicativo. Se esse atributo for `false`, todas as exceções que resultam de tentativas de gravar eventos de auditoria serão passadas para o aplicativo.<br /><br /> O padrão é `true`.|  
|serviceAuthorizationAuditLevel|Especifica os tipos de eventos de autorização que são registrados no log de auditoria. Os valores válidos incluem o seguinte:<br /><br /> -None: Sem auditoria de eventos de autorização de serviço é executado.<br />-Êxito: Somente eventos de autorização de serviço bem-sucedida são auditados.<br />-Falha: Somente serviço autorização eventos de falha são auditados.<br />-SuccessOrFailure: Eventos de autorização do serviço de êxito e falha são auditados.<br /><br /> O valor padrão é None. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Especifica o tipo de eventos de auditoria de autenticação de mensagem registrados. Os valores válidos incluem o seguinte:<br /><br /> -None: Nenhum evento de auditoria é gerado.<br />-Êxito: Somente eventos de (incluindo a validação de token, criptografia e validação de assinatura de mensagem de validação completo) de segurança com êxito são registrados.<br />-Falha: Somente eventos de falha são registrados.<br />-SuccessOrFailure: Eventos de êxito e falha são registrados.<br /><br /> O valor padrão é None. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado para auditoria de eventos de autenticação do Windows Communication Foundation (WCF). Quando a auditoria estiver habilitada, a autenticação com êxito ou falha tentativas (ou ambos) podem ser auditados. Os eventos são gravados em um dos três logs de eventos: aplicativo, segurança ou o log padrão para a versão do sistema operacional. Os logs de eventos podem todas ser exibidos usando o Visualizador de eventos do Windows.  
  
 Para obter um exemplo detalhado de como usar este elemento de configuração, consulte [comportamento de auditoria de serviço](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Por padrão, no Windows XP dos eventos de auditoria podem ser vistos no Log do aplicativo; no Windows Server 2003 e Windows Vista, os eventos de auditoria podem ser vistos no Log de segurança. O local dos eventos de auditoria pode ser especificado definindo o `auditLogLocation` de atributo para 'Application' ou 'Segurança'. Para obter mais informações, confira [Como: Auditar eventos de segurança](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Se os eventos são gravados no Log de segurança, o LocalSecurityPolicy -> Habilitar o acesso ao objeto deve ser definido para "Êxito" e "Falha".  
  
 Ao examinar o log de eventos, a origem dos eventos de auditoria é "Auditoria de ServiceModel 3.0.0.0". Registros de auditoria de autenticação de mensagem tem uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço têm uma categoria de 'ServiceAuthorization'.  
  
 Eventos de auditoria de autenticação de mensagem abrangem se a mensagem foi violada, se a mensagem expirou e se o cliente pode se autenticar no serviço. Eles fornecem informações sobre se a autenticação com êxito ou falha, juntamente com a identidade do cliente e o ponto de extremidade a mensagem foi enviado ao junto com a ação associada à mensagem.  
  
 Eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização de serviço. Eles fornecem informações sobre se a autorização com êxito ou falha, juntamente com a identidade do cliente, o ponto de extremidade a mensagem foi enviado para a ação associada à mensagem, o identificador do contexto de autorização que foi gerado a partir de mensagem de entrada e o tipo do Gerenciador de autorização que tomou a decisão de acesso.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Auditoria](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Como: auditar eventos de segurança](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Comportamento de auditoria de serviço](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
