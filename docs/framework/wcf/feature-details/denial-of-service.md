---
title: Negação de Serviço
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: f67a8b2977e84e24654b4b65c0cdd03bcbcb1b20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968829"
---
# <a name="denial-of-service"></a>Negação de Serviço
A negação de serviço ocorre quando um sistema está sobrecarregado de forma que as mensagens não possam ser processadas ou processadas extremamente lentamente.  
  
## <a name="excess-memory-consumption"></a>Consumo de memória em excesso  
 Um problema pode ocorrer ao ler um documento XML com um grande número de nomes locais, namespaces ou prefixos exclusivos. Se você estiver usando uma classe <xref:System.Xml.XmlReader>derivada de e chamar <xref:System.Xml.XmlReader.Prefix%2A> a <xref:System.Xml.XmlReader.LocalName%2A>propriedade ou <xref:System.Xml.XmlReader.NamespaceURI%2A> para cada item, a cadeia de caracteres retornada será adicionada a um <xref:System.Xml.NameTable>. A coleção mantida pelo <xref:System.Xml.NameTable> nunca diminui em tamanho, criando uma "perda de memória" virtual dos identificadores de cadeia de caracteres.  
  
 As atenuações incluem:  
  
- Derive da <xref:System.Xml.NameTable> classe e aplique uma cota de tamanho máximo. (Não é possível impedir o uso de <xref:System.Xml.NameTable> um ou mudar <xref:System.Xml.NameTable> o quando estiver cheio.)  
  
- Evite usar as propriedades mencionadas e, em <xref:System.Xml.XmlReader.MoveToAttribute%2A> vez disso, <xref:System.Xml.XmlReader.IsStartElement%2A> use o método com o método onde for possível; esses métodos não retornam cadeias de caracteres e <xref:System.Xml.NameTable> , portanto, evitam o problema de preenchimento da coleção.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Cliente mal-intencionado envia solicitações de licença excessivas para o serviço  
 Se um cliente mal-intencionado bombards um serviço com solicitações de licença excessivas, ele pode fazer com que o servidor use memória excessiva.  
  
 Mitigação: Use as seguintes propriedades da <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> classe:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: controla o número máximo de tempos limitados `SecurityContextToken`que o servidor armazena em cache após `SPNego` ou `SSL` a negociação.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: controla o tempo de vida `SecurityContextTokens` do que o servidor emite `SPNego` após `SSL` ou negociação. O servidor armazena em cache `SecurityContextToken`os s por esse período de tempo.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: controla o número máximo de conversas seguras que são estabelecidas no servidor, mas para as quais nenhuma mensagem de aplicativo foi processada. Essa cota impede que os clientes estabeleçam conversas seguras no serviço, fazendo com que o serviço Mantenha o estado por cliente, mas nunca usá-los.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: controla o tempo máximo que o serviço mantém uma conversa segura sem receber uma mensagem de aplicativo do cliente para a conversa. Essa cota impede que os clientes estabeleçam conversas seguras no serviço, fazendo com que o serviço Mantenha o estado por cliente, mas nunca usá-los.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>Associações personalizadas WSDualHttpBinding ou duplas exigem autenticação de cliente  
 Por padrão, o <xref:System.ServiceModel.WSDualHttpBinding> tem a segurança habilitada. No entanto, é possível que, se a autenticação do cliente esteja desabilitada <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> definindo a <xref:System.ServiceModel.MessageCredentialType.None>Propriedade como, um usuário mal-intencionado pode causar um ataque de negação de serviço em um terceiro serviço. Isso pode ocorrer porque um cliente mal-intencionado pode direcionar o serviço para enviar um fluxo de mensagens para um terceiro serviço.  
  
 Para atenuar isso, não defina a propriedade como `None`. Além disso, lembre-se dessa possibilidade ao criar uma associação personalizada que tenha um padrão de mensagem dupla.  
  
## <a name="auditing-event-log-can-be-filled"></a>O log de eventos de auditoria pode ser preenchido  
 Se um usuário mal-intencionado entender que a auditoria está habilitada, esse invasor poderá enviar mensagens inválidas que fazem com que as entradas de auditoria sejam gravadas. Se o log de auditoria for preenchido dessa maneira, o sistema de auditoria falhará.  
  
 Para atenuar isso, defina a <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> Propriedade como `true` e use as propriedades do Visualizador de eventos para controlar o comportamento de auditoria. Para obter mais informações sobre como usar o Visualizador de Eventos para exibir e gerenciar logs de eventos, consulte [Visualizador de eventos](https://go.microsoft.com/fwlink/?LinkId=186123). Para obter mais informações, consulte [auditoria](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-to-become-unresponsive"></a>Implementações inválidas de IAuthorizationPolicy podem fazer com que o serviço fique sem resposta  
 Chamar o <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> método em uma implementação com falha <xref:System.IdentityModel.Policy.IAuthorizationPolicy> da interface pode fazer com que o serviço fique sem resposta.  
  
 Mitigação: Use apenas código confiável. Ou seja, use apenas o código que você escreveu e testou, ou que venha de um provedor confiável. Não permita que extensões não confiáveis do <xref:System.IdentityModel.Policy.IAuthorizationPolicy> sejam conectadas ao seu código sem a devida consideração. Isso se aplica a todas as extensões usadas em uma implementação de serviço. O WCF não faz nenhuma distinção entre o código do aplicativo e o código estrangeiro que está conectado usando pontos de extensibilidade.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>O tamanho máximo do token do Kerberos pode precisar de redimensionamento  
 Se um cliente pertencer a um grande número de grupos (aproximadamente 900, embora o número real varie de acordo com os grupos), poderá ocorrer um problema quando o bloco de um cabeçalho de mensagem exceder 64 quilobytes. Nesse caso, você pode aumentar o tamanho máximo do token Kerberos, conforme descrito no artigo Suporte da Microsoft "a[autenticação Kerberos do Internet Explorer não funciona devido a um buffer insuficiente em conexão com o IIS](https://go.microsoft.com/fwlink/?LinkId=89176)". Talvez você também precise aumentar o tamanho máximo da mensagem WCF para acomodar o token Kerberos maior.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>O registro automático resulta em vários certificados com o mesmo nome de assunto para o computador  
 O *registro automático* é a capacidade do [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] de registrar automaticamente usuários e computadores para certificados. Quando um computador está em um domínio com o recurso habilitado, um certificado X. 509 com a finalidade pretendida da autenticação do cliente é criado automaticamente e inserido no armazenamento de certificados pessoais do computador local sempre que um novo computador é ingressado no rede. No entanto, o registro automático usa o mesmo nome de entidade para todos os certificados que ele cria no cache.  
  
 O impacto é que os serviços WCF podem falhar ao abrir em domínios com o registro automático. Isso ocorre porque os critérios de pesquisa de credencial do serviço X. 509 padrão podem ser ambíguos porque existem vários certificados com o nome DNS (sistema de nomes de domínio) totalmente qualificado do computador. Um certificado é originado do registro automático; o outro pode ser um certificado emitido por conta própria.  
  
 Para atenuar isso, faça referência ao certificado exato a ser usado usando um critério de pesquisa mais preciso no [ \<> ServiceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Por exemplo, use a <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> opção e especifique o certificado por sua impressão digital exclusiva (hash).  
  
 Para obter mais informações sobre o recurso de registro automático, consulte [registro automático de certificado no Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Último dos vários nomes de entidade alternativos usados para autorização  
 No caso raro, quando um certificado X. 509 contiver vários nomes de entidade alternativos, e você autorizar usando o nome alternativo da entidade, a autorização poderá falhar.  
  
## <a name="protect-configuration-files-with-acls"></a>Proteger arquivos de configuração com ACLs  
 Você pode especificar declarações obrigatórias e opcionais em arquivos de código e de configuração para tokens emitidos do CardSpace. Isso resulta na emissão de elementos correspondentes em `RequestSecurityToken` mensagens enviadas para o serviço de token de segurança. Um invasor pode modificar o código ou a configuração para remover declarações obrigatórias ou opcionais, potencialmente obtendo o serviço de token de segurança para emitir um token que não permite o acesso ao serviço de destino.  
  
 Para atenuar: Exigir acesso ao computador para modificar o arquivo de configuração. Use listas de controle de acesso (ACLs) de arquivo para proteger arquivos de configuração. O WCF requer que o código esteja no diretório do aplicativo ou no cache de assembly global antes de permitir que tal código seja carregado da configuração. Use ACLs de diretório para proteger diretórios.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>O número máximo de sessões seguras para um serviço foi atingido  
 Quando um cliente é autenticado com êxito por um serviço e uma sessão segura é estabelecida com o serviço, o serviço mantém o controle da sessão até que o cliente o cancele ou a sessão expire. Cada sessão estabelecida conta com relação ao limite para o número máximo de sessões simultâneas ativas com um serviço. Quando esse limite é atingido, os clientes que tentam criar uma nova sessão com esse serviço são rejeitados até que uma ou mais sessões ativas expirem ou sejam canceladas por um cliente. Um cliente pode ter várias sessões com um serviço e cada uma dessas sessões conta com relação ao limite.  
  
> [!NOTE]
> Quando você usa sessões com estado, o parágrafo anterior não se aplica. Para obter mais informações sobre sessões com estado [, consulte Como: Crie um token de contexto de segurança para uma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)sessão segura.  
  
 Para atenuar isso, defina o limite para o número máximo de sessões ativas e o tempo de vida máximo de uma sessão <xref:System.ServiceModel.Channels.SecurityBindingElement> definindo a propriedade <xref:System.ServiceModel.Channels.SecurityBindingElement> da classe.  
  
## <a name="see-also"></a>Consulte também

- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Divulgação de informações](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
