---
title: Negação de serviço
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb9f542d931f5febc2c04d1b0e093cc20f487c57
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="denial-of-service"></a>Negação de serviço
Negação de serviço ocorre quando um sistema está sobrecarregado de forma que as mensagens não podem ser processadas ou eles são processados muito lentamente.  
  
## <a name="excess-memory-consumption"></a>Consumo de memória em excesso  
 Pode ocorrer um problema ao ler um documento XML com um grande número de prefixos, namespaces ou nomes exclusivos de locais. Se você estiver usando uma classe que deriva de <xref:System.Xml.XmlReader>, e você chama o <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> ou <xref:System.Xml.XmlReader.NamespaceURI%2A> propriedade para cada item, a cadeia de caracteres retornada é adicionada a uma <xref:System.Xml.NameTable>. A coleção mantida pelo <xref:System.Xml.NameTable> nunca diminui de tamanho, criando uma máquina virtual "vazamento de memória" das alças de cadeia de caracteres.  
  
 Atenuantes incluem:  
  
-   Derivam de <xref:System.Xml.NameTable> classe e impor uma cota de tamanho máximo. (Você não pode impedir o uso de um <xref:System.Xml.NameTable> ou alternar o <xref:System.Xml.NameTable> quando ele estiver cheio.)  
  
-   Evite usar as propriedades mencionadas e em vez disso, use o <xref:System.Xml.XmlReader.MoveToAttribute%2A> método com o <xref:System.Xml.XmlReader.IsStartElement%2A> método sempre que possível; esses métodos não retornar cadeias de caracteres e, portanto, evitar o problema de sobrecarga do <xref:System.Xml.NameTable> coleção.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Cliente mal-intencionado envia solicitações de licença excessivas ao serviço  
 Se um cliente mal-intencionado bombardeiam um serviço com solicitações de licença excessiva, isso poderá causar para uso excessivo de memória do servidor.  
  
 Mitigação: Use as seguintes propriedades da <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: controla o número máximo de limitada de tempo `SecurityContextToken`que o servidor armazena em cache após `SPNego` ou `SSL` negociação.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: controla o tempo de vida de `SecurityContextTokens` que os problemas de servidor a seguir `SPNego` ou `SSL` negociação. Os caches de servidor a `SecurityContextToken`s para esse período de tempo.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: controla o número máximo de conversas seguras que são estabelecidas no servidor, mas para que nenhum aplicativo de mensagens foram processado. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando o serviço manter o estado por cliente, mas nunca usá-los.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: controla o tempo máximo que o serviço mantém uma conversa segura ativo sem receber uma mensagem de aplicativo do cliente para a conversa. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando o serviço manter o estado por cliente, mas nunca usá-los.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding ou associações personalizadas duplas exigem autenticação de cliente  
 Por padrão, o <xref:System.ServiceModel.WSDualHttpBinding> tem segurança habilitada. É possível, no entanto, se a autenticação do cliente é desabilitada por definir o <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> propriedade <xref:System.ServiceModel.MessageCredentialType.None>, um usuário mal-intencionado pode causar um ataque de negação de serviço em um serviço de terceiro. Isso pode ocorrer porque um cliente mal-intencionado pode direcionar o serviço para enviar um fluxo de mensagens para atender a um terceiro.  
  
 Para atenuar isso, não defina a propriedade como `None`. Estar ciente dessa possibilidade ao criar uma associação personalizada que tem um padrão de mensagem dupla.  
  
## <a name="auditing-event-log-can-be-filled"></a>Log de eventos de auditoria pode ser preenchido  
 Se um usuário mal-intencionado entenda que a auditoria está habilitada, essa invasor pode enviar mensagens inválidas que fazer com que as entradas de auditoria a serem gravados. Se o log de auditoria é preenchido dessa maneira, o sistema de auditoria falha.  
  
 Para atenuar isso, defina o <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade `true` e use as propriedades do Visualizador de eventos para controlar o comportamento de auditoria. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] usando o Visualizador de eventos para exibir e gerenciar logs de eventos, consulte [Visualizador de eventos](http://go.microsoft.com/fwlink/?LinkId=186123). Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Implementações inválidas de IAuthorizationPolicy pode causa serviço trava  
 Chamando o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método em uma implementação falha do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> interface pode fazer com que o serviço desligar.  
  
 Mitigação: Use somente o código confiável. Ou seja, use somente o código que você tiver gravado e testado ou que vêm de um fornecedor confiável. Não permitir extensões não confiáveis do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> devem ser inseridos em seu código sem a devida consideração. Isso se aplica a todas as extensões usadas em uma implementação de serviço. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não faz qualquer diferença entre o código do aplicativo e o código externo que é conectado usando pontos de extensibilidade.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Tamanho de Token Kerberos máximo pode ser necessário redimensionar  
 Se um cliente pertence a um grande número de grupos (aproximadamente 900, embora o número real varia dependendo dos grupos), um problema pode ocorrer quando o bloco do cabeçalho da mensagem excede 64 kilobytes. Nesse caso, você pode aumentar o tamanho de token Kerberos máximo, conforme descrito no artigo do Microsoft Support "[a autenticação Kerberos do Internet Explorer não funciona devido a um buffer insuficiente se conectam ao IIS](http://go.microsoft.com/fwlink/?LinkId=89176)." Você também pode precisar aumentar o máximo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para acomodar o maior token Kerberos da mensagem.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>O registro automático resultados em vários certificados com o mesmo nome de assunto para a máquina  
 *O registro automático* é a capacidade de [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] para registrar automaticamente os usuários e computadores para certificados. Quando um computador estiver em um domínio com o recurso habilitado, um certificado x. 509 com a finalidade de autenticação de cliente é criado e inserido no repositório de certificados pessoais do computador local sempre que uma nova máquina é unida à automaticamente a rede. No entanto, o registro automático usa o mesmo nome de assunto para todos os certificados que ele cria no cache.  
  
 O impacto é que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem falhar ao abrir em domínios com o registro automático. Isso ocorre porque os critérios de pesquisa padrão serviço x. 509 credencial podem ser ambíguos porque existem vários certificados com o nome de sistema de nome de domínio (DNS) totalmente qualificado do computador. Um certificado se origina de registro automático; a outra pode ser um certificado emitido por conta própria.  
  
 Para atenuar isso, referenciar o certificado exato para usar usando um critério de pesquisa mais preciso sobre o [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Por exemplo, use o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> opção e especifique o certificado por sua impressão digital exclusiva (hash).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] o recurso de registro automático, consulte [registro automático de certificados no Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Última de vários nomes de entidade alternativo usado para autorização  
 No caso raro quando um certificado x. 509 contém vários nomes de entidade alternativo e você autorizar usando o nome alternativo da entidade, autorização pode falhar.  
  
## <a name="protect-configuration-files-with-acls"></a>Proteger os arquivos de configuração com ACLs  
 Você pode especificar declarações obrigatórias e opcionais em arquivos de código e configuração para [!INCLUDE[infocard](../../../../includes/infocard-md.md)] tokens emitidos. Isso resulta em elementos correspondentes que está sendo emitidos em `RequestSecurityToken` serviço de token de mensagens que são enviadas para a segurança. Um invasor pode modificar código ou configuração para remover as declarações necessárias ou opcionais, potencialmente obter o serviço de token de segurança para emitir um token que não permite o acesso ao serviço de destino.  
  
 Para atenuar: exigem acesso ao computador para modificar o arquivo de configuração. Controle de acesso de arquivo de uso de ACLs para proteger os arquivos de configuração. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requer que o código seja no cache de assembly global ou de diretório do aplicativo antes de permitir esse tipo de código a ser carregado de configuração. Use as ACLs do diretório para proteger diretórios.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Número máximo de sessões seguras para um serviço é atingido  
 Quando um cliente é autenticado com êxito por um serviço e uma sessão segura é estabelecida com o serviço, o serviço mantém o controle de sessão até que o cliente cancele ou a sessão expira. Cada sessão estabelecida conta em relação ao limite para o número máximo de sessões simultâneas ativas com um serviço. Quando esse limite for atingido, clientes que tentam criar uma nova sessão com esse serviço serão rejeitados até que um ou mais ativas sessões expirarem ou são canceladas por um cliente. Um cliente pode ter várias sessões com um serviço, e cada um dessas sessões contado o limite.  
  
> [!NOTE]
>  Quando você usa sessões com monitoração de estado, o parágrafo anterior não se aplica. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] sessões com monitoração de estado, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Para atenuar isso, defina o limite para o número máximo de sessões ativas e o tempo de vida máximo para uma sessão definindo o <xref:System.ServiceModel.Channels.SecurityBindingElement> propriedade o <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
