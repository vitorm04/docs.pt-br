---
title: Auditoria de eventos de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e4219553f97f272577e8efdeb106b43e5f76ee59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496019"
---
# <a name="auditing-security-events"></a>Auditoria de eventos de segurança
Os aplicativos criados com o Windows Communication Foundation (WCF) podem registrar eventos de segurança (êxito, falha ou ambos) com o recurso de auditoria. Os eventos são gravados no log de eventos do sistema e podem ser examinados usando o Visualizador de eventos.  
  
 A auditoria fornece uma maneira de um administrador para detectar um ataque que já ocorreu ou está em andamento. Além disso, a auditoria pode ajudar um desenvolvedor para depurar os problemas relacionados à segurança. Por exemplo, se um erro na configuração da política de verificação ou autorização acidentalmente nega acesso a um usuário autorizado, um desenvolvedor rapidamente pode descobrir e isolar a causa desse erro examinando o log de eventos.  
  
 Para obter mais informações sobre a segurança do WCF, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). Para obter mais informações sobre programação de WCF, consulte [básicas de programação WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Nível de auditoria e comportamento  
 Existem dois níveis de auditorias de segurança:  
  
-   Nível de autorização de serviço, em que o chamador está autorizado.  
  
-   Nível de mensagem, em que o WCF verifica a validade da mensagem e autentica o chamador.  
  
 Você pode verificar os dois níveis de sucesso ou falha, que é conhecida como de auditoria a *auditoria comportamento*.  
  
## <a name="audit-log-location"></a>Local do Log de auditoria  
 Depois de determinar um nível de auditoria e o comportamento, você (ou um administrador) pode especificar um local para o log de auditoria. Incluem as três opções: padrão, aplicativo e segurança. Quando você especificar o padrão, o log real depende do sistema no qual você está usando e se o sistema oferece suporte à gravação no log de segurança. Para obter mais informações, consulte a seção "Sistema operacional", mais adiante neste tópico.  
  
 Para gravar no log de segurança requer a `SeAuditPrivilege`. Por padrão, apenas as contas Sistema Local e serviço de rede têm esse privilégio. Para gerenciar as funções de log de segurança `read` e `delete` requer o `SeSecurityPrivilege`. Por padrão, somente os administradores têm esse privilégio.  
  
 Por outro lado, os usuários autenticados podem ler e gravar no log de aplicativo. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] gravações de auditoria de eventos no log de aplicativo por padrão. O log também pode conter informações pessoais que são visíveis para todos os usuários autenticados.  
  
## <a name="suppressing-audit-failures"></a>Suprimir falhas de auditoria  
 Outra opção durante a auditoria é suprimir qualquer falha de auditoria. Por padrão, uma falha de auditoria não afeta a um aplicativo. Se necessário, no entanto, você pode definir a opção `false`, que faz com que uma exceção seja lançada.  
  
## <a name="programming-auditing"></a>Auditoria de programação  
 Você pode especificar o comportamento de auditoria programaticamente ou por meio da configuração.  
  
### <a name="auditing-classes"></a>Classes de auditoria  
 A tabela a seguir descreve as classes e propriedades usadas para auditoria de comportamento do programa.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Permite definir opções para a auditoria como comportamento de serviço.|  
|<xref:System.ServiceModel.AuditLogLocation>|Enumeração para especificar que o log para gravar. Os valores possíveis são padrão, aplicativo e segurança. Quando você seleciona o padrão, o sistema operacional determina o local de log real. Consulte a seção "Opções de Log de eventos de segurança ou aplicativo", mais adiante neste tópico.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Especifica quais tipos de eventos de autenticação de mensagem são auditados no nível da mensagem. As opções são `None`, `Failure`, `Success`, e `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Especifica quais tipos de eventos de serviço de autorização são auditados no nível de serviço. As opções são `None`, `Failure`, `Success`, e `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Especifica o que acontece com a solicitação do cliente durante a auditoria de falha. Por exemplo, quando o serviço tenta gravar no log de segurança, mas não tem `SeAuditPrivilege`. O valor padrão de `true` indica que falhas são ignoradas e a solicitação do cliente é processada normalmente.|  
  
 Para obter um exemplo da configuração de um aplicativo para registrar eventos de auditoria, consulte [como: eventos de auditoria de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Configuração  
 Você também pode usar a configuração para especificar o comportamento de auditoria, adicionando um [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) sob o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Você deve adicionar o elemento em um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) conforme mostrado no código a seguir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!— auditLogLocation="Application" or "Security" -—>  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Se a auditoria está habilitada e uma `auditLogLocation` não for especificado, o nome do log padrão é o log de "Segurança" para a plataforma com suporte de gravação no log de segurança; caso contrário, ele é o log de "Aplicativo". Somente o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas operacionais oferecem suporte a gravação no log de segurança. Para obter mais informações, consulte a seção "Sistema operacional", mais adiante neste tópico.  
  
## <a name="security-considerations"></a>Considerações sobre segurança  
 Se um usuário mal-intencionado sabe que a auditoria está habilitada, essa invasor pode enviar mensagens inválidas que fazer com que as entradas de auditoria a serem gravados. Se o log de auditoria é preenchido dessa maneira, o sistema de auditoria falha. Para atenuar isso, defina o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade `true` e use as propriedades do Visualizador de eventos para controlar o comportamento de auditoria. Para obter mais informações, consulte o artigo do Microsoft Support em Exibir e gerenciar logs de eventos usando o Visualizador de eventos no Windows XP, disponível em [como exibir e gerenciar logs de eventos no Visualizador de eventos no Windows XP](http://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Auditoria de eventos que são gravados no log de aplicativo [!INCLUDE[wxp](../../../../includes/wxp-md.md)] são visíveis a qualquer usuário autenticado.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Escolhendo entre aplicativos e Logs de eventos de segurança  
 As tabelas a seguir fornecem informações para ajudá-lo a escolher se deve fazer logon no aplicativo ou o log de eventos de segurança.  
  
#### <a name="operating-system"></a>Sistema operacional  
  
|Sistema|Log de aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] ou posterior|Com suporte|Sem suporte|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)]|Com suporte|Deve ter o contexto de thread `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Outros fatores  
 Além do sistema operacional, a tabela a seguir descreve outras configurações que controlam a habilitação de registro em log.  
  
|Fator|Log de aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|Gerenciamento de política de auditoria|Não aplicável.|Junto com a configuração, o log de segurança também é controlado pela política de autoridade (LSA) de segurança local. A categoria "Auditar acesso ao objeto" também deve ser habilitada.|  
|Experiência de usuário padrão|Todos os usuários autenticados podem gravar no log de aplicativo, portanto, nenhuma etapa de permissão adicional é necessária para processos de aplicativos.|O processo de aplicativo (contexto) deve ter `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Como auditar de eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
