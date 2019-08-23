---
title: Comportamento de auditoria de serviço
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 6d5f254f4f94adfaeaf5632ddd696891af177e93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964553"
---
# <a name="service-auditing-behavior"></a>Comportamento de auditoria de serviço
Este exemplo demonstra como usar o para <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> habilitar a auditoria de eventos de segurança durante operações de serviço. Este exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md). O serviço e o cliente foram configurados usando o [ \<> de WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O `mode` `Message` atributo `Windows` `clientCredentialType` [ do>desegurançafoidefinidocomoe\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definido como. Neste exemplo, o cliente é um aplicativo de console (. exe) e o serviço é hospedado pelo Serviços de Informações da Internet (IIS).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 O arquivo de configuração de serviço `serviceSecurityAudit` usa o elemento para configurar a auditoria.  
  
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
  
 Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. Pressione ENTER na janela do console para desligar o cliente.  
  
 Os logs de auditoria resultantes podem ser vistos executando o Visualizador de Eventos. Por padrão, no Windows XP, os eventos de auditoria podem ser vistos no log do aplicativo enquanto estiver no Windows Server 2003 e no Windows Vista, os eventos de auditoria podem ser vistos no log de segurança. No Windows Server 2008 e no Windows 7, os eventos de auditoria podem ser vistos nos logs de aplicativos e serviços. O local dos eventos de auditoria pode ser especificado definindo o `auditLogLocation` atributo como "Application" ou "Security". Para obter mais informações, confira [Como: Auditar eventos](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)de segurança. Se os eventos forem gravados no log de segurança >, o LocalSecurityPolicy habilitar o acesso ao objeto deverá ser definido como "êxito" e "falha".  
  
 Ao examinar o log de eventos, a origem dos eventos de auditoria é "ServiceModel Audit 3.0.0.0". Os registros de auditoria de autenticação de mensagens têm uma categoria de "MessageAuthentication", enquanto os registros de auditoria de autorização de serviço têm uma categoria de "Service Authorização".  
  
 Os eventos de auditoria de autenticação de mensagens abordam se a mensagem foi violada, se a mensagem expirou e se o cliente pode se autenticar no serviço. Eles fornecem informações sobre se a autenticação foi bem-sucedida ou falhou junto com a identidade do cliente e o ponto de extremidade para o qual a mensagem foi enviada junto com a ação associada à mensagem.  
  
 Os eventos de auditoria de autorização de serviço abrangem a decisão de autorização feita por um Gerenciador de autorização de serviço. Eles fornecem informações sobre se a autorização foi bem-sucedida ou falhou junto com a identidade do cliente, o ponto de extremidade para o qual a mensagem foi enviada, a ação associada à mensagem, o identificador do contexto de autorização gerado no mensagem de entrada e o tipo de Gerenciador de autorização que fez a decisão de acesso.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também

- [Auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Como: Auditar eventos de segurança](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
