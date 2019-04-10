---
title: Comportamento de auditoria de serviço
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 1719db9749336d584627280aba3412557b164356
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310389"
---
# <a name="service-auditing-behavior"></a>Comportamento de auditoria de serviço
Este exemplo demonstra como usar o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> para habilitar a auditoria de eventos de segurança durante as operações de serviço. Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço e cliente foram configurados usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definido como `Message` e `clientCredentialType` foi definido como `Windows`. Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O arquivo de configuração de serviço usa o `serviceSecurityAudit` elemento para configurar a auditoria.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do console para desligar o cliente.  
  
 Os logs de auditoria resultante podem ser vistos executando o Visualizador de eventos. Por padrão, no XP do Windows dos eventos de auditoria podem ser vistos no Log do aplicativo ao mesmo tempo no Windows Server 2003 e Windows Vista, os eventos de auditoria podem ser vistos no Log de segurança. No Windows Server 2008 e Windows 7, os eventos de auditoria podem ser vistos nos logs de aplicativos e serviços. O local dos eventos de auditoria pode ser especificado definindo o `auditLogLocation` do atributo de "Aplicativo" ou "Segurança". Para obter mais informações, confira [Como: Auditar eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Se os eventos são gravados no Log de segurança a LocalSecurityPolicy -> que habilitar o acesso ao objeto deve ser definido para "Êxito" e "Falha".  
  
 Ao examinar o log de eventos, a origem dos eventos de auditoria é "Auditoria de ServiceModel 3.0.0.0". Registros de auditoria de autenticação de mensagem tem uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço têm uma categoria de "ServiceAuthorization".  
  
 Eventos de auditoria de autenticação de mensagem abrangem se a mensagem foi violada, se a mensagem expirou e se o cliente pode se autenticar no serviço. Eles fornecem informações sobre se a autenticação com êxito ou falha, juntamente com a identidade do cliente e o ponto de extremidade a mensagem foi enviado ao junto com a ação associada à mensagem.  
  
 Eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização de serviço. Eles fornecem informações sobre se a autorização com êxito ou falha, juntamente com a identidade do cliente, o ponto de extremidade a mensagem foi enviado para a ação associada à mensagem, o identificador do contexto de autorização que foi gerado a partir de mensagem de entrada e o tipo do Gerenciador de autorização que tomou a decisão de acesso.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também

- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Como: auditar eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
