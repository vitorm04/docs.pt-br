---
title: Auditoria de eventos de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bad963db8d0e3644204824645f702c7b7b84963d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864236"
---
# <a name="auditing-security-events"></a>Auditoria de eventos de segurança
Os aplicativos criados com o Windows Communication Foundation (WCF) podem registrar eventos de segurança (êxito, falha ou ambos) com o recurso de auditoria. Os eventos são gravados no log de eventos do sistema Windows e podem ser examinados usando o Visualizador de eventos.  
  
 A auditoria fornece uma maneira de um administrador detectar um ataque que já ocorreu ou está em andamento. Além disso, a auditoria pode ajudar um desenvolvedor para depurar problemas relacionados à segurança. Por exemplo, se um erro na configuração da política de verificação ou autorização acidentalmente nega acesso a um usuário autorizado, um desenvolvedor rapidamente pode descobrir e isolar a causa desse erro, examinando o log de eventos.  
  
 Para obter mais informações sobre a segurança do WCF, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). Para obter mais informações sobre programação de WCF, consulte [programação WCF básica](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Nível de auditoria e o comportamento  
 Existem dois níveis de auditorias de segurança:  
  
-   Nível de autorização de serviço, em que um chamador está autorizado.  
  
-   Nível de mensagem, em que o WCF verifica a validade da mensagem e autentica o chamador.  
  
 Você pode verificar os dois níveis para o êxito ou falha, o que é conhecida como de auditoria a *comportamento de auditoria*.  
  
## <a name="audit-log-location"></a>Local do Log de auditoria  
 Depois de determinar um nível de auditoria e o comportamento, você (ou um administrador) pode especificar um local para o log de auditoria. As três opções incluem: padrão, o aplicativo e segurança. Quando você especifica o padrão, o log real depende de sistema no qual você está usando e se o sistema oferece suporte a gravação no log de segurança. Para obter mais informações, consulte a seção "Sistema operacional", mais adiante neste tópico.  
  
 Para gravar no log de segurança, é necessário o `SeAuditPrivilege`. Por padrão, somente a contas Sistema Local e serviço de rede tem esse privilégio. Para gerenciar as funções de log de segurança `read` e `delete` requer o `SeSecurityPrivilege`. Por padrão, somente os administradores têm esse privilégio.  
  
 Em contraste, os usuários autenticados podem ler e gravar no log de aplicativo. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] gravações de auditoria de eventos no log de aplicativo por padrão. O log também pode conter informações pessoais que é visíveis para todos os usuários autenticados.  
  
## <a name="suppressing-audit-failures"></a>Suprimir falhas de auditoria  
 Outra opção durante a auditoria é se deve ser suprimida qualquer falha de auditoria. Por padrão, uma falha de auditoria não afeta um aplicativo. Se necessário, no entanto, você pode definir a opção `false`, que faz com que uma exceção seja lançada.  
  
## <a name="programming-auditing"></a>Auditoria de programação  
 Você pode especificar o comportamento de auditoria por meio de programação ou por meio da configuração.  
  
### <a name="auditing-classes"></a>Classes de auditoria  
 A tabela a seguir descreve as classes e propriedades usadas para programar o comportamento de auditoria.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Permite configurar opções para a auditoria como um comportamento de serviço.|  
|<xref:System.ServiceModel.AuditLogLocation>|Enumeração para especificar que o log para gravar. Os valores possíveis são padrão, o aplicativo e segurança. Quando você seleciona um padrão, o sistema operacional determina o local de log real. Consulte a seção "Opção de Log de eventos de segurança ou aplicativo" mais adiante neste tópico.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Especifica quais tipos de eventos de autenticação de mensagem são auditados no nível da mensagem. As opções são `None`, `Failure`, `Success`, e `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Especifica quais tipos de eventos de autorização de serviço são auditados no nível de serviço. As opções são `None`, `Failure`, `Success`, e `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Especifica o que acontece com a solicitação do cliente durante a auditoria de falha. Por exemplo, quando o serviço tenta gravar no log de segurança, mas não tem `SeAuditPrivilege`. O valor padrão de `true` indica que falhas são ignoradas e a solicitação do cliente será processada normalmente.|  
  
 Para obter um exemplo de como configurar um aplicativo para registrar eventos de auditoria, consulte [como: eventos de auditoria de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Configuração  
 Você também pode usar a configuração para especificar o comportamento de auditoria com a adição de um [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) sob o [ \<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Você deve adicionar o elemento em um [ \<comportamento >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) conforme mostrado no código a seguir.  
  
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
  
 Se a auditoria está habilitada e uma `auditLogLocation` não for especificado, o nome do log padrão é o log de "Segurança" para a plataforma que dão suporte a gravação no log de segurança; caso contrário, ele é o log de "Aplicativo". Somente o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas operacionais oferecem suporte a gravação no log de segurança. Para obter mais informações, consulte a seção "Sistema operacional", mais adiante neste tópico.  
  
## <a name="security-considerations"></a>Considerações sobre segurança  
 Se um usuário mal-intencionado sabe que a auditoria está habilitada, esse invasor pode enviar mensagens inválidas que fazem com que as entradas de auditoria a serem gravados. Se o log de auditoria é preenchido dessa maneira, o sistema de auditoria falha. Para atenuar isso, defina as <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade para `true` e usar as propriedades de Visualizador de eventos para controlar o comportamento de auditoria. Para obter mais informações, consulte o artigo do Microsoft Support sobre como exibir e gerenciar logs de eventos usando o Visualizador de eventos no Windows XP disponível em [como exibir e gerenciar logs de eventos no Visualizador de eventos no Windows XP](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Auditoria de eventos que são gravados no log de aplicativo no [!INCLUDE[wxp](../../../../includes/wxp-md.md)] são visíveis para qualquer usuário autenticado.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Escolhendo entre o aplicativo e Logs de eventos de segurança  
 As tabelas a seguir fornecem informações para ajudá-lo a escolher se deseja fazer logon no aplicativo ou o log de eventos de segurança.  
  
#### <a name="operating-system"></a>Sistema operacional  
  
|Sistema|Log de aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] ou posterior|Com suporte|Sem suporte|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] e [!INCLUDE[wv](../../../../includes/wv-md.md)]|Com suporte|Contexto do thread deve ter `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Outros fatores  
 Além do sistema operacional, a tabela a seguir descreve outras configurações que controlam a habilitação do registro em log.  
  
|fator|Log de aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|Gerenciamento de política de auditoria|Não aplicável.|Junto com a configuração, o log de segurança também é controlado pela política de autoridade (LSA) de segurança local. A categoria "Auditar acesso ao objeto" também deve ser habilitada.|  
|Experiência de usuário padrão|Todos os usuários autenticados podem gravar no log de aplicativo, portanto, nenhuma etapa adicional de permissão é necessária para processos de aplicativos.|O processo de aplicativo (contexto) deve ter `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Como auditar de eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<comportamentos >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
