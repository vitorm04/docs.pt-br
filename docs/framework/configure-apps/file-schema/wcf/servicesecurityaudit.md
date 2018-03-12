---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 25355acfd7bc82ccff33f68a690f3f02d1235438
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Especifica configurações que habilitem a auditoria de eventos de segurança durante operações de serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<behavior>  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessOrFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|auditLogLocation|Especifica o local do log de auditoria. Os valores válidos incluem o seguinte:<br /><br /> -Padrão: Eventos de segurança são gravados no log de aplicativo no Windows XP e ao Log de eventos no Windows Server 2003 e Windows Vista.<br />-Aplicativo: Eventos de auditoria são gravados no Log de eventos do aplicativo.<br />-Segurança: Eventos de auditoria são gravados no Log de eventos de segurança.<br /><br /> O valor padrão é o padrão. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Um valor booleano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.<br /><br /> Aplicativos devem ser notificados para falhas de gravação no log de auditoria. Se seu aplicativo não foi projetado para lidar com falhas de auditoria, você deve usar esse atributo para suprimir falhas na gravação no log de auditoria.<br /><br /> Se esse atributo for `true`, exceções que não sejam OutOfMemoryException, StackOverFlowException, ThreadAbortException e ArgumentException resultantes das tentativas para gravar eventos de auditoria são manipuladas pelo sistema e não são propagadas para o aplicativo. Se esse atributo for `false`, todas as exceções resultantes das tentativas para gravar eventos de auditoria serão passadas para o aplicativo.<br /><br /> O padrão é `true`.|  
|serviceAuthorizationAuditLevel|Especifica os tipos de eventos de autorização que são registrados no log de auditoria. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Nenhum auditoria de eventos de autorização de serviço é executado.<br />-Êxito: Apenas eventos de autorização de serviço bem-sucedida são auditados.<br />-Falha: Somente serviço autorização eventos de falha são auditados.<br />-SuccessOrFailure: Os dois eventos de autorização do serviço de êxito e falha são auditados.<br /><br /> O valor padrão é None. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Especifica o tipo de eventos de auditoria de autenticação de mensagem registrados. Os valores válidos incluem o seguinte:<br /><br /> -Nenhum: Nenhum evento de auditoria é gerado.<br />-Êxito: Apenas eventos de (incluindo a validação de assinatura de mensagem, criptografia e validação de token de validação completa) de segurança com êxito são registrados.<br />-Falha: Somente os eventos de falha são registrados.<br />-SuccessOrFailure: Ambos os eventos de êxito e falha são registrados.<br /><br /> O valor padrão é None. Para obter mais informações, consulte <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado para auditoria [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] eventos de autenticação. Quando a auditoria estiver habilitada, a autenticação com êxito ou falha tentativas (ou ambos) podem ser auditados. Os eventos são gravados em um dos três logs de eventos: o log padrão para a versão do sistema operacional, aplicativo ou segurança. Os logs de eventos podem ser exibidos usando o Visualizador de eventos do Windows.  
  
 Para obter um exemplo detalhado de como usar este elemento de configuração, consulte [o comportamento de auditoria de serviço](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Por padrão, no Windows XP os eventos de auditoria podem ser vistos no Log do aplicativo; no Windows Server 2003 e Windows Vista, os eventos de auditoria podem ser vistos no Log de segurança. O local dos eventos de auditoria pode ser especificado definindo a `auditLogLocation` 'Aplicativo' ou 'Security' do atributo. Para obter mais informações, consulte [como: eventos de auditoria de segurança](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Se os eventos são gravados no Log de segurança, o LocalSecurityPolicy -> Habilitar acesso do objeto deve ser definido como "Êxito" e "Falha".  
  
 Ao examinar o log de eventos, a origem dos eventos de auditoria é "ServiceModel auditoria 3.0.0.0". Registros de auditoria de autenticação de mensagem tem uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço tem uma categoria de 'ServiceAuthorization'.  
  
 Eventos de auditoria de autenticação de mensagem abrangem se a mensagem foi violada, se a mensagem expirou e se o cliente pode autenticar para o serviço. Eles fornecem informações sobre se a autenticação foi bem-sucedida ou falhou com a identidade do cliente e o ponto de extremidade a mensagem foi enviado ao junto com a ação associada à mensagem.  
  
 Eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização do serviço. Eles fornecem informações sobre se a autorização teve êxito ou falha com a identidade do cliente, o ponto de extremidade a mensagem foi enviado para a ação associada à mensagem, o identificador do contexto de autorização que foi gerado a partir de mensagem de entrada e o tipo do Gerenciador de autorização que fez a decisão de acesso.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [Comportamentos de segurança](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Auditoria](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Como auditar de eventos de segurança](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Comportamento de auditoria de serviço](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
