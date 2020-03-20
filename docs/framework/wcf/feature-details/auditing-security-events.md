---
title: Auditoria de eventos de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 535f19741ff26e9472ce56ff06b670f7d0523be8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185461"
---
# <a name="auditing-security-events"></a>Auditoria de eventos de segurança
Os aplicativos criados com o Windows Communication Foundation (WCF) podem registrar eventos de segurança (sucesso, falha ou ambos) com o recurso de auditoria. Os eventos são gravados no registro de eventos do sistema Windows e podem ser examinados usando o Visualizador de Eventos.  
  
 A auditoria fornece uma maneira de um administrador detectar um ataque que já ocorreu ou está em andamento. Além disso, a auditoria pode ajudar um desenvolvedor a depurar problemas relacionados à segurança. Por exemplo, se um erro na configuração da política de autorização ou verificação acidentalmente negar acesso a um usuário autorizado, um desenvolvedor pode descobrir e isolar rapidamente a causa desse erro examinando o registro de eventos.  
  
 Para obter mais informações sobre a segurança do WCF, consulte [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). Para obter mais informações sobre a programação do WCF, consulte [Programação Básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Nível e Comportamento de Auditoria  
 Existem dois níveis de auditorias de segurança:  
  
- Nível de autorização de serviço, no qual um chamador é autorizado.  
  
- Nível de mensagem, no qual o WCF verifica a validade da mensagem e autentica o chamador.  
  
 Você pode verificar os níveis de auditoria para obter sucesso ou falha, que é conhecido como o comportamento da *auditoria*.  
  
## <a name="audit-log-location"></a>Localização do registro de auditoria  
 Depois de determinar um nível de auditoria e comportamento, você (ou um administrador) pode especificar um local para o registro de auditoria. As três opções incluem: Padrão, Aplicativo e Segurança. Quando você especifica padrão, o registro real depende de qual sistema você está usando e se o sistema suporta a escrita no registro de segurança. Para obter mais informações, consulte a seção "Sistema Operacional" mais tarde neste tópico.  
  
 Para escrever no registro `SeAuditPrivilege`de segurança requer o . Por padrão, apenas as contas do Sistema Local e do Serviço de Rede têm esse privilégio. Para gerenciar as `read` funções `delete` de `SeSecurityPrivilege`registro de segurança e requer o . Por padrão, apenas os administradores têm esse privilégio.  
  
 Em contraste, os usuários autenticados podem ler e gravar no registro do aplicativo. O Windows XP grava eventos de auditoria no registro de aplicativos por padrão. O registro também pode conter informações pessoais que são visíveis para todos os usuários autenticados.  
  
## <a name="suppressing-audit-failures"></a>Suprimindo falhas de auditoria  
 Outra opção durante a auditoria é suprimir qualquer falha de auditoria. Por padrão, uma falha de auditoria não afeta um aplicativo. Se necessário, no entanto, `false`você pode definir a opção para , o que faz com que uma exceção seja lançada.  
  
## <a name="programming-auditing"></a>Auditoria de Programação  
 Você pode especificar o comportamento de auditoria programática ou através da configuração.  
  
### <a name="auditing-classes"></a>Aulas de Auditoria  
 A tabela a seguir descreve as classes e propriedades usadas para programar o comportamento de auditoria.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Permite definir opções de auditoria como um comportamento de serviço.|  
|<xref:System.ServiceModel.AuditLogLocation>|Enumeração para especificar para qual log escrever. Os valores possíveis são Padrão, Aplicativo e Segurança. Quando você seleciona Padrão, o sistema operacional determina a localização real do registro. Consulte a seção "Escolha do registro de eventos de aplicativos ou seguranças" mais tarde neste tópico.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Especifica quais tipos de eventos de autenticação de mensagens são auditados no nível da mensagem. As escolhas `Failure` `Success`são, `SuccessOrFailure` `None`e .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Especifica quais tipos de eventos de autorização de serviço são auditados no nível de serviço. As escolhas `Failure` `Success`são, `SuccessOrFailure` `None`e .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Especifica o que acontece com a solicitação do cliente quando a auditoria falha. Por exemplo, quando o serviço tenta escrever no registro `SeAuditPrivilege`de segurança, mas não tem . O valor `true` padrão de indica que as falhas são ignoradas e a solicitação do cliente é processada normalmente.|  
  
 Para um exemplo de configuração de um aplicativo para registrar eventos de auditoria, consulte [Como: Auditar Eventos de Segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Configuração  
 Você também pode usar a configuração para especificar o [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)comportamento de auditoria adicionando um [ \<serviçoSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) sob os comportamentos>. Você deve adicionar o [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elemento um comportamento>como mostrado no código a seguir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
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
  
 Se a auditoria estiver `auditLogLocation` ativada e não for especificada, o nome de registro padrão será "Segurança" do registro da plataforma que suporta a gravação no registro de segurança; caso contrário, é o registro "Application". Apenas os sistemas operacionais Windows Server 2003 e Windows Vista suportam a escrita no registro de segurança. Para obter mais informações, consulte a seção "Sistema Operacional" mais tarde neste tópico.  
  
## <a name="security-considerations"></a>Considerações de segurança  
 Se um usuário mal-intencionado souber que a auditoria está ativada, esse invasor pode enviar mensagens inválidas que fazem com que as entradas de auditoria sejam escritas. Se o registro de auditoria for preenchido dessa forma, o sistema de auditoria falhará. Para mitigar isso, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> defina a `true` propriedade e use as propriedades do Visualizador de Eventos para controlar o comportamento de auditoria.  
  
 Os eventos de auditoria que são gravados no Registro de Aplicativos no Windows XP são visíveis para qualquer usuário autenticado.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Escolhendo entre registros de eventos de aplicativos e segurança  
 As tabelas a seguir fornecem informações para ajudá-lo a escolher se deve fazer login no Aplicativo ou no registro de eventos de Segurança.  
  
#### <a name="operating-system"></a>Sistema operacional  
  
|Sistema|Log do aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|Windows XP SP2 ou posterior|Com suporte|Sem suporte|  
|Windows Server 2003 SP1 e Windows Vista|Com suporte|O contexto do segmento deve possuir`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Outros fatores  
 Além do sistema operacional, a tabela a seguir descreve outras configurações que controlam a habilitação do registro.  
  
|Fator|Log do aplicativo|Log de segurança|  
|------------|---------------------|------------------|  
|Gerenciamento de políticas de auditoria|Não aplicável.|Junto com a configuração, o registro de segurança também é controlado pela política da Autoridade de Segurança Local (LSA). A categoria "Audit object access" também deve ser habilitada.|  
|Experiência padrão do usuário|Todos os usuários autenticados podem gravar no registro do aplicativo, portanto, nenhuma etapa adicional de permissão é necessária para os processos de aplicativos.|O processo de aplicação `SeAuditPrivilege`(contexto) deve ter .|  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Como fazer auditoria de eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<comportamentos>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
