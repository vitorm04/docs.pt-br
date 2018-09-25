---
title: Negação de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: d4f7ebf784ab02ecdd0203423157da5bef968a87
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090299"
---
# <a name="denial-of-service"></a>Negação de serviço
Negação de serviço ocorre quando um sistema está sobrecarregado de tal forma que as mensagens não podem ser processadas, ou eles são processados extremamente lenta.  
  
## <a name="excess-memory-consumption"></a>Consumo de memória em excesso  
 Um problema pode ocorrer ao ler um documento XML com um grande número de nomes locais exclusivos, namespaces ou prefixos. Se você estiver usando uma classe que deriva de <xref:System.Xml.XmlReader>, e você chamar o <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> ou <xref:System.Xml.XmlReader.NamespaceURI%2A> propriedade para cada item, a cadeia de caracteres retornada é adicionada a um <xref:System.Xml.NameTable>. A coleção mantida pelo <xref:System.Xml.NameTable> nunca diminui de tamanho, criar uma máquina virtual "vazamento de memória" das alças de cadeia de caracteres.  
  
 Atenuantes incluem:  
  
-   Derivar o <xref:System.Xml.NameTable> de classe e impor uma cota de tamanho máximo. (Você não pode impedir o uso de um <xref:System.Xml.NameTable> ou alternar o <xref:System.Xml.NameTable> quando estiver cheio.)  
  
-   Evite usar as propriedades mencionadas e em vez disso, use o <xref:System.Xml.XmlReader.MoveToAttribute%2A> método com o <xref:System.Xml.XmlReader.IsStartElement%2A> método sempre que possível; esses métodos não retornar cadeias de caracteres e, portanto, evitar o problema de sobrecarga do <xref:System.Xml.NameTable> coleção.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Cliente mal-intencionado envia solicitações de licença excessivas ao serviço  
 Se um cliente mal-intencionado bombardeiam um serviço com solicitações de licença excessiva, isso poderá causar para uso excessivo de memória do servidor.  
  
 Mitigação: Use as seguintes propriedades do <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe:  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: controla o número máximo de tempo limitado `SecurityContextToken`s que o servidor armazena em cache após `SPNego` ou `SSL` negociação.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: controla o tempo de vida do `SecurityContextTokens` que os problemas de servidor a seguir `SPNego` ou `SSL` negociação. Os caches de servidor a `SecurityContextToken`s para esse período de tempo.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: controla o número máximo de conversas seguras que são estabelecidas no servidor, mas para que nenhuma mensagem de aplicativo tenha sido processadas. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando assim o serviço manter o estado por cliente, mas nunca usá-los.  
  
-   <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: controla o tempo máximo que o serviço mantém uma conversa segura ativo sem receber uma mensagem de aplicativo do cliente para a conversa. Essa cota impede que os clientes estabelecendo conversas seguras no serviço, causando assim o serviço manter o estado por cliente, mas nunca usá-los.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding ou Dual ligações personalizadas exigem a autenticação de cliente  
 Por padrão, o <xref:System.ServiceModel.WSDualHttpBinding> tem segurança habilitada. É possível, no entanto, que, se a autenticação do cliente é desabilitada por configuração de <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> propriedade para <xref:System.ServiceModel.MessageCredentialType.None>, um usuário mal-intencionado pode causar um ataque de negação de serviço em um serviço de terceiro. Isso pode ocorrer porque um cliente mal-intencionado pode direcionar o serviço para enviar uma transmissão de mensagens para atender a um terceiro.  
  
 Para atenuar isso, não defina a propriedade como `None`. Também estar ciente dessa possibilidade ao criar uma associação personalizada que tem um padrão de mensagem dupla.  
  
## <a name="auditing-event-log-can-be-filled"></a>Log de eventos de auditoria pode ser preenchido  
 Se um usuário mal-intencionado compreende que a auditoria está habilitada, esse invasor pode enviar mensagens inválidas que fazem com que as entradas de auditoria a serem gravados. Se o log de auditoria é preenchido dessa maneira, o sistema de auditoria falha.  
  
 Para atenuar isso, defina as <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> propriedade para `true` e usar as propriedades de Visualizador de eventos para controlar o comportamento de auditoria. Para obter mais informações sobre como usar o Visualizador de eventos para exibir e gerenciar logs de eventos, consulte [Visualizador de eventos](https://go.microsoft.com/fwlink/?LinkId=186123). Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Implementações inválidas de IAuthorizationPolicy Can causa serviço trava  
 Chamar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método em uma implementação com falha do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> interface pode fazer com que o serviço parar de responder.  
  
 Mitigação: Use somente o código confiável. Ou seja, use somente o código que você tenha escrito e testado, ou que vem de um provedor confiável. Não permita que as extensões não confiáveis de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> sejam conectados ao seu código sem a devida consideração. Isso se aplica a todas as extensões usadas em uma implementação de serviço. O WCF não fará qualquer distinção entre o código do aplicativo e o código externo que está conectado usando pontos de extensibilidade.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Tamanho máximo de Kerberos do Token, talvez seja necessário redimensionar  
 Se um cliente pertence a um grande número de grupos (aproximadamente 900, embora o número real varia, dependendo dos grupos), um problema pode ocorrer quando o bloco do cabeçalho da mensagem excede 64 quilobytes. Nesse caso, você pode aumentar o tamanho de token Kerberos máximo, conforme descrito no artigo da Microsoft Support "[a autenticação Kerberos do Internet Explorer não funciona devido a um buffer insuficiente se conectam ao IIS](https://go.microsoft.com/fwlink/?LinkId=89176)." Também convém aumentar o tamanho máximo da mensagem do WCF para acomodar o maior token do Kerberos.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Resultados de registro automático em vários certificados com o mesmo nome de assunto para a máquina  
 *O registro automático* é a capacidade de [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] registrar automaticamente os usuários e computadores para certificados. Quando um computador estiver em um domínio com o recurso habilitado, um certificado X.509 com a finalidade de autenticação de cliente é automaticamente criado e inserido no repositório de certificados pessoais do computador local sempre que uma nova máquina é unida à rede. No entanto, o registro automático usa o mesmo nome de assunto para todos os certificados que ele cria no cache.  
  
 O impacto é que os serviços WCF podem falhar abrir em domínios com o registro automático. Isso ocorre porque os critérios de pesquisa padrão serviço x. 509 credencial podem ser ambíguos porque existem vários certificados com o nome de sistema de nome de domínio (DNS) totalmente qualificado do computador. O registro automático; é proveniente de um certificado a outra pode ser um certificado emitido por conta própria.  
  
 Para atenuar isso, o certificado exato a ser usado por meio de um critério de pesquisa mais preciso de referência a [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Por exemplo, use o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> opção e especifique o certificado por sua impressão digital exclusiva (hash).  
  
 Para obter mais informações sobre o recurso de registro automático, consulte [registro automático de certificados no Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Último dos vários nomes alternativo da entidade usado para autorização  
 Em casos raros quando um certificado X.509 contém vários nomes alternativo da entidade e você autorizar usando o nome alternativo da entidade, a autorização pode falhar.  
  
## <a name="protect-configuration-files-with-acls"></a>Proteger arquivos de configuração com as ACLs  
 Você pode especificar as declarações obrigatórias e opcionais em arquivos de código e a configuração para [!INCLUDE[infocard](../../../../includes/infocard-md.md)] tokens emitidos. Isso resulta em elementos correspondentes que está sendo emitidos em `RequestSecurityToken` mensagens que são enviadas para a segurança de serviço de token. Um invasor pode modificar código ou a configuração para remover declarações obrigatórias ou opcionais, potencialmente, obtendo o serviço de token de segurança para emitir um token que não permite o acesso ao serviço de destino.  
  
 Para atenuar: exigem acesso ao computador para modificar o arquivo de configuração. Controle de acesso de arquivo de uso de ACLs para proteger arquivos de configuração. WCF requer que o código ser no cache de assembly global ou de diretório do aplicativo antes que ele permita que esse código ser carregado da configuração. Use as ACLs do diretório para proteger os diretórios.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Número máximo de sessões seguras para um serviço é atingido  
 Quando um cliente é autenticado com êxito por um serviço e uma sessão segura é estabelecida com o serviço, o serviço mantém controle de sessão até que o cliente cancela a ele ou a sessão expirar. Contagens de cada sessão estabelecida para o limite para o número máximo de sessões simultâneas do Active Directory com um serviço. Quando esse limite for atingido, os clientes que tentam criar uma nova sessão com o serviço serão rejeitados até que uma ou sessões ativas mais expiram ou são canceladas por um cliente. Um cliente pode ter várias sessões com um serviço, e cada uma dessas sessões de contagens em relação ao limite.  
  
> [!NOTE]
>  Quando você usa sessões com monitoração de estado, o parágrafo anterior não se aplica. Para obter mais informações sobre as sessões com monitoração de estado, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Para atenuar isso, defina o limite para o número máximo de sessões ativas e o tempo de vida máximo para uma sessão, definindo o <xref:System.ServiceModel.Channels.SecurityBindingElement> propriedade do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe.  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
