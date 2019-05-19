---
title: Informações de privacidade do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 6da9e2a91fe8156c0631aa77594e3ed47d32cb8b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882181"
---
# <a name="windows-communication-foundation-privacy-information"></a>Informações de privacidade do Windows Communication Foundation
A Microsoft está comprometida em proteger a privacidade dos usuários finais. Quando você compila um aplicativo usando o Windows Communication Foundation (WCF), versão 3.0, seu aplicativo pode afetar a privacidade de seus usuários finais. Por exemplo, seu aplicativo explicitamente poderá coletar informações de contato do usuário, ou ele pode solicitar ou enviar informações pela Internet para seu site da Web. Se você incorporar tecnologia da Microsoft em seu aplicativo, o que a tecnologia pode ter seu próprio comportamento que pode afetar a privacidade. WCF não enviar todas as informações à Microsoft do seu aplicativo, a menos que você ou o usuário final optar por enviá-los para nós.  
  
## <a name="wcf-in-brief"></a>WCF no resumo  
 O WCF é uma estrutura de mensagens distribuída usando o Microsoft .NET Framework que permite aos desenvolvedores criar aplicativos distribuídos. Mensagens de comunicado entre dois aplicativos contêm informações de cabeçalho e corpo.  
  
 Cabeçalhos podem conter o roteamento de mensagens, informações de segurança, transações e muito mais, dependendo dos serviços usados pelo aplicativo. Normalmente, as mensagens são criptografadas por padrão. A única exceção é ao usar o `BasicHttpBinding`, que foi projetado para uso com os serviços da Web herdados, não é seguro. Como criador do aplicativo, você é responsável pelo design final. Mensagens no corpo SOAP contêm dados específicos do aplicativo; No entanto, esses dados, como definido pelo aplicativo informações pessoais podem ser protegidos usando recursos de criptografia ou a confidencialidade do WCF. As seções a seguir descrevem os recursos que potencialmente afetam a privacidade.  
  
## <a name="messaging"></a>Mensagens  
 Cada mensagem do WCF tem um cabeçalho de endereço que especifica o destino da mensagem e, em que a resposta deve ir.  
  
 O componente de endereço de um endereço de ponto de extremidade é um identificador de URI (Uniform Resource) que identifica o ponto de extremidade. O endereço pode ser um endereço de rede ou um endereço lógico. O endereço pode incluir o nome do computador (nome de host, nome de domínio totalmente qualificado) e um endereço IP. O endereço do ponto de extremidade também pode conter um identificador global exclusivo (GUID) ou uma coleção de GUIDs para endereçamento temporário usado para distinguir cada endereço. Cada mensagem contém uma ID de mensagem que é um GUID. Esse recurso segue o padrão de referência do WS-Addressing.  
  
 A camada de mensagens do WCF não grava nenhuma informação pessoal para o computador local. No entanto, ele poderá propagar as informações pessoais no nível da rede se um desenvolvedor de serviços criou um serviço que expõe essas informações (por exemplo, por usando o nome de uma pessoa em um nome de ponto de extremidade, ou incluir informações pessoais na Web do ponto de extremidade Serviços de linguagem de descrição, mas não exigir que os clientes usar https para acessar o WSDL). Além disso, se um desenvolvedor executa o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta em relação a um ponto de extremidade que expõe informações pessoais, a saída da ferramenta poderia conter essas informações e o arquivo de saída é gravado para o disco rígido local.  
  
## <a name="hosting"></a>Hospedagem  
 O recurso de hospedagem do WCF permite que os aplicativos para iniciar por demanda ou para habilitar o compartilhamento de porta entre vários aplicativos. Um aplicativo WCF pode ser hospedado no Internet Information Services (IIS), semelhante ao ASP.NET.  
  
 Hospedagem não expõem quaisquer informações específicas sobre a rede e não mantém dados na máquina.  
  
## <a name="message-security"></a>Segurança de mensagem  
 Segurança do WCF fornece os recursos de segurança para aplicativos de mensagens. As funções de segurança fornecidas incluem autenticação e autorização.  
  
 Autenticação é realizada pela transmissão de credenciais entre os clientes e serviços. A autenticação pode ser por meio da segurança de nível de transporte ou por meio de SOAP mensagem de nível de segurança, da seguinte maneira:  
  
- Na segurança de mensagem SOAP, a autenticação é realizada por meio de credenciais, como nome de usuário/senhas, certificados x. 509, tíquetes Kerberos e os tokens SAML, que podem conter informações pessoais, dependendo do emissor.  
  
- Usando a segurança de transporte, a autenticação é feita por meio de mecanismos de autenticação do transporte tradicionais, como esquemas de autenticação HTTP (básica, Digest, Negotiate, NTLM, None, a autorização integrada do Windows e anônima) e a autenticação de formulário.  
  
 A autenticação pode resultar em uma sessão segura estabelecida entre os pontos de extremidade de comunicação. A sessão é identificada por um GUID que dura o tempo de vida da sessão de segurança. A tabela a seguir mostra o que é mantido e onde.  
  
|Dados|Armazenamento|  
|----------|-------------|  
|Credenciais de apresentação, como nome de usuário, certificados X.509, tokens Kerberos e as referências às credenciais.|Mecanismos de gerenciamento, como o repositório de certificados do Windows de credenciais do Windows padrão.|  
|Informações de associação de usuário, como nomes de usuário e senhas.|Provedores de associação do ASP.NET.|  
|Informações de identidade sobre o serviço usado para autenticar o serviço aos clientes.|Endereço do ponto de extremidade do serviço.|  
|Informações do chamador.|Os logs de auditoria.|  
  
## <a name="auditing"></a>Auditoria  
 A auditoria registra o êxito ou falha de eventos de autenticação e autorização. Registros de auditoria contêm os seguintes dados: identificação do chamador, o URI da ação e o URI de serviço.  
  
 A auditoria também registra quando o administrador modifica a configuração de log de mensagens (ativando ou desativando), porque o log de mensagens pode registrar dados específicos do aplicativo em cabeçalhos e corpos. Para [!INCLUDE[wxp](../../../includes/wxp-md.md)], um registro é registrado no log de eventos do aplicativo. Para [!INCLUDE[wv](../../../includes/wv-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], um registro é registrado no log de eventos de segurança.  
  
## <a name="transactions"></a>Transações  
 O recurso de transações fornece serviços transacionais para um aplicativo WCF.  
  
 Cabeçalhos de transação usados na propagação de transações podem conter IDs de transação ou IDs de inscrição, que são GUIDs.  
  
 A funcionalidade de transações usa o Gerenciador de transações (um componente do Windows) do Microsoft Distributed Transaction coordenador (MSDTC) para gerenciar o estado da transação. Por padrão, as comunicações entre os gerenciadores de transações são criptografadas. Gerenciadores de transações podem registrar IDs de inscrição, IDs de transação e referências de ponto de extremidade como parte de seu estado durável. O tempo de vida esse estado é determinado pelo tempo de vida do arquivo de log do Gerenciador de transações. O serviço MSDTC possui e mantém esse log.  
  
 O recurso de transações implementa os padrões WS-Coordination e transações de WS-Atomic.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis no WCF fornecem a transferência de mensagens quando ocorrem falhas intermediárias ou transporte. Eles fornecem um exatamente-uma vez de transferência de mensagens, mesmo quando o transporte subjacente se desconecta (por exemplo, uma conexão TCP em uma rede sem fio) ou perde uma mensagem (um proxy HTTP descartando uma mensagem de entrada ou de saída). Sessões confiáveis também recuperar a mensagem reordenação (como pode acontecer no caso de roteamento de vários caminhos), preservando a ordem na qual as mensagens foram enviadas.  
  
 Sessões confiáveis são implementadas usando o protocolo WS-ReliableMessaging (WS-RM). Eles adicionam cabeçalhos WS-RM que contêm informações de sessão, que são usadas para identificar todas as mensagens associadas a uma determinada sessão confiável. Cada sessão WS-RM tem um identificador, que é um GUID.  
  
 Nenhuma informação pessoal é mantida no computador do usuário final.  
  
## <a name="queued-channels"></a>Canais na fila  
 As filas armazenam mensagens de um aplicativo de envio em nome de um aplicativo de recebimento e posteriormente, encaminham essas mensagens para o aplicativo de recebimento. Eles ajudam a garantir a transferência de mensagens dos aplicativos de envio para aplicativos de recebimento, quando, por exemplo, o aplicativo de recebimento é transitório. O WCF oferece suporte para enfileiramento de mensagens usando o Microsoft Message Queuing (MSMQ) como um transporte.  
  
 O recurso de canais na fila não adiciona cabeçalhos de uma mensagem. Em vez disso, ele cria uma mensagem de enfileiramento de mensagens com o conjunto de propriedades de mensagem de enfileiramento de mensagens apropriado e invoca métodos de enfileiramento de mensagens para colocar a mensagem na fila de enfileiramento de mensagens. O enfileiramento é um componente opcional que acompanha o Windows.  
  
 Nenhuma informação é mantida no computador do usuário final pelo recurso de canais na fila, pois ela usa o enfileiramento de mensagens como a infraestrutura de enfileiramento de mensagens.  
  
## <a name="com-integration"></a>Integração de COM+  
 Esse recurso encapsula a funcionalidade e COM+ existente para criar serviços que são compatíveis com os serviços WCF. Esse recurso não usa cabeçalhos específicos e ela não retém os dados na máquina do usuário final.  
  
## <a name="com-service-moniker"></a>Moniker de serviço COM  
 Isso fornece um invólucro não gerenciado para um cliente WCF padrão. Esse recurso não tem cabeçalhos específicos durante a transmissão nem manter a dados no computador.  
  
## <a name="peer-channel"></a>Canal par  
 Um canal par permite o desenvolvimento de aplicativos com vários participantes usando o WCF. Mensagens entre vários participantes ocorre no contexto de uma malha. Malhas são identificadas por um nome que podem juntar a nós. Cada nó no canal par cria um ouvinte TCP em uma porta especificada pelo usuário e estabelece conexões com outros nós na malha para garantir a resiliência. Para se conectar a outros nós na malha, nós também trocam alguns dados, incluindo o endereço de escuta e endereços IP da máquina, com outros nós na malha. As mensagens enviadas em torno da malha podem conter informações de segurança que pertencem ao remetente para evitar falsificação de mensagens e a violação.  
  
 Nenhuma informação pessoal é armazenada no computador do usuário final.  
  
## <a name="it-professional-experience"></a>Experiência do profissional de TI  
  
### <a name="tracing"></a>Rastreamento  
 O recurso de diagnóstico da infraestrutura do WCF registra em log as mensagens que passam por meio de transporte e camadas do modelo de serviço e as atividades e eventos associados a essas mensagens. Esse recurso é desativado por padrão. Ele é habilitado usando o arquivo de configuração do aplicativo e o comportamento de rastreamento pode ser modificado usando o provedor de WMI do WCF em tempo de execução. Quando habilitada, a infra-estrutura de rastreamento emite um rastreamento de diagnóstico que contém as mensagens, atividades e eventos de processamento para ouvintes configurados. O formato e o local de saída são determinados por opções de configuração de ouvinte do administrador, mas normalmente é um arquivo XML formatado. O administrador é responsável por definir a lista de controle de acesso (ACL) nos arquivos de rastreamento. Em particular, quando hospedado pelo sistema de ativação do Windows (WAS), o administrador deve se certificar que de arquivos não são servidos do diretório raiz virtual pública se não for desejado.  
  
 Há dois tipos de rastreamento: Diagnóstico do modelo de serviço e de log de mensagens de rastreamento, descrito na seção a seguir. Cada tipo é configurado por meio de sua própria origem de rastreamento: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> e <xref:System.ServiceModel>. Ambas essas fontes de rastreamento de registro em log capturam dados que são locais para o aplicativo.  
  
### <a name="message-logging"></a>Registro em log de mensagens  
 A mensagem de log de origem de rastreamento (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permite que um administrador registrar em log as mensagens desse fluxo por meio do sistema. Por meio da configuração, o usuário pode decidir registrar mensagens inteiras ou somente os cabeçalhos de mensagem, se é preciso registrar nas camadas de modelo de transporte e/ou serviço e se é necessário incluir mensagens malformadas. Além disso, o usuário pode configurar a filtragem para restringir quais mensagens são registradas.  
  
 Por padrão, o log de mensagens está desabilitado. O administrador do computador local pode impedir que o administrador de nível de aplicativo transformar a mensagem de logon.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Registro de mensagem criptografada e descriptografada  
 Mensagens são registradas, criptografadas ou descriptografadas, conforme descrito nos seguintes termos.  
  
 Registro de transporte  
 Registra mensagens recebidas e enviadas no nível do transporte. Essas mensagens contêm todos os cabeçalhos e podem ser criptografadas antes de serem enviados durante a transmissão e ao que está sendo recebido.  
  
 Se as mensagens são criptografadas antes de serem enviados durante a transmissão e quando elas são recebidas, elas são registradas criptografados também. Uma exceção é quando um protocolo de segurança é usado (https): estiverem conectados, em seguida, descriptografados antes de serem enviados e depois que está sendo recebido mesmo se eles são criptografados durante a transmissão.  
  
 Log de serviço  
 Registra mensagens recebidas ou enviadas no nível do modelo de serviço, após a realização processamento do cabeçalho de canal, pouco antes e depois de inserir o código do usuário.  
  
 As mensagens registradas nesse nível são descriptografadas, mesmo se elas foram protegidas e criptografadas durante a transmissão.  
  
 Registro em log de mensagem malformada  
 Registra mensagens que a infraestrutura do WCF não é possível entender ou processar.  
  
 As mensagens são registradas como-está, ou seja, criptografado ou não  
  
 Quando mensagens são registradas no formulário não criptografado ou descriptografado, por padrão, o WCF remove as chaves de segurança e potencialmente informações pessoais das mensagens de antes de registrá-los. As seções a seguir descrevem quais informações são removidas e quando. O administrador do computador e ambos implantador de aplicativo deve tomar determinadas ações de configuração para alterar o comportamento padrão para registrar em log as chaves e informações potencialmente particulares.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informações removidas dos cabeçalhos de mensagem quando o registro em log mensagens/não criptografado descriptografado  
 Quando mensagens são registradas na forma descriptografada/sem criptografia, chaves de segurança e informações potencialmente particulares são removidos por padrão com base em cabeçalhos de mensagens e corpos de mensagens antes que elas são registradas. A lista a seguir mostra o que o WCF considera as chaves e informações potencialmente particulares.  
  
 Chaves são removidas:  
  
 \- Para xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 wst:Entropy  
  
 \- Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:password  
  
 wsse:Nonce  
  
 Informações potencialmente particulares que são removidas:  
  
 \- Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- Para xmlns:saml = "urn: oasis: nomes: tc: SAML:1.0:assertion" os itens em negrito (abaixo) serão removidos:  
  
 \<Asserção  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId="[ID]"  
  
 Issuer="[string]"  
  
 IssueInstant="[dateTime]"  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition>  
  
 \<Público-alvo > [uri]\</Audience > +  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition />*  
  
 <\!– o tipo base abstrato  
  
 \<Condição / > *  
  
 -->  
  
 \</ Condições >?  
  
 \<Conselhos >  
  
 \<AssertionIDReference>[ID]\</AssertionIDReference>*  
  
 \<Assertion>[assertion]\</Assertion>*  
  
 [qualquer] *  
  
 \</Advice>?  
  
 <\!– Tipos de base abstratos  
  
 \<Instrução / > *  
  
 \<SubjectStatement>  
  
 \<Assunto >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 \<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+  
  
 \<SubjectConfirmationData > [qualquer]\</SubjectConfirmationData >?  
  
 \<ds:KeyInfo>...\</ds:KeyInfo>?  
  
 \</SubjectConfirmation>?  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod="[uri]"  
  
 AuthenticationInstant="[dateTime]"  
  
 >  
  
 [Assunto]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 AuthorityKind="[QName]"  
  
 Location="[uri]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 [Assunto]  
  
 \<Atributo  
  
 AttributeName="[string]"  
  
 AttributeNamespace="[uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</ Atributo > +  
  
 \</AttributeStatement>*  
  
 \<AuthorizationDecisionStatement  
  
 Resource="[uri]"  
  
 Decision="[Permit&#124;Deny&#124;Indeterminate]"  
  
 >  
  
 [Assunto]  
  
 \<Action Namespace="[uri]">[string]\</Action>+  
  
 \<Evidência >  
  
 \<AssertionIDReference>[ID]\</AssertionIDReference>+  
  
 \<Assertion>[assertion]\</Assertion>+  
  
 \</ Evidência >?  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Removido do corpos de mensagem quando o registro em log mensagens/não criptografado descriptografado de informações  
 Conforme descrito anteriormente, WCF remove chaves e conhecidas informações potencialmente pessoais de cabeçalhos de mensagem para mensagens registradas/não criptografado descriptografado. Além disso, o WCF remove chaves e informações potencialmente particulares conhecidas de corpos de mensagem para os elementos do corpo e ações na lista a seguir, que descrevem as mensagens de segurança envolvidas na troca de chaves.  
  
 Para os seguintes namespaces:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (por exemplo, se nenhuma ação disponível)  
  
 Informações são removidas para esses elementos de corpo, que envolvem a troca de chaves:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Informações também são removidas para cada uma das seguintes ações:  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Nenhuma informação é removida do cabeçalhos específicos de aplicativo e o corpo de dados  
 O WCF não rastreia informações pessoais em cabeçalhos específicos do aplicativo (por exemplo, cadeias de consulta) ou o corpo de dados (por exemplo, o número de cartão de crédito).  
  
 Quando o log de mensagens estiver ativada, informações pessoais em cabeçalhos específicos de aplicativo e informações do corpo podem ser visíveis nos logs. Novamente, o implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e de log. Ele também pode desativar registro em log se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de log depois que ele é registrado.  
  
### <a name="service-model-tracing"></a>Rastreamento de modelo de serviço  
 A origem de rastreamento do modelo de serviço (<xref:System.ServiceModel>) habilita o rastreamento de atividades e eventos relacionados ao processamento de mensagem. Esse recurso usa a funcionalidade de diagnóstico do .NET Framework do <xref:System.Diagnostics>. Assim como acontece com o <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> propriedade, o local e sua ACL são configuráveis pelo usuário usando arquivos de configuração de aplicativo do .NET Framework. Assim como acontece com o log de mensagens, o local do arquivo é sempre configurado quando o administrador habilita o rastreamento; Portanto, o administrador controla a ACL.  
  
 Quando uma mensagem está no escopo os rastreamentos contêm cabeçalhos de mensagem. Aplicam as mesmas regras para ocultar informações potencialmente pessoais nos cabeçalhos de mensagem na seção anterior: as informações pessoais identificadas anteriormente foram removidas por padrão, dos cabeçalhos em rastreamentos. O administrador da máquina e o implantador de aplicativo deverá modificar a configuração para registrar informações potencialmente particulares. No entanto, as informações pessoais contidas em cabeçalhos específicos de aplicativo são registradas em rastreamentos. O implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e o rastreamento. Ele também pode desativar o rastreamento se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de rastreamento depois que ele é registrado.  
  
 Como parte do rastreamento de ServiceModel, IDs exclusivas (chamado de IDs de atividade e, geralmente um GUID) vincular atividades diferentes juntos como uma mensagem flui por meio de diferentes partes da infraestrutura.  
  
#### <a name="custom-trace-listeners"></a>Ouvintes de rastreamento personalizado  
 Para ambas as mensagens de log e rastreamento, um ouvinte de rastreamento personalizado pode ser configurado, o que pode enviar mensagens e rastreamentos durante a transmissão (por exemplo, para um banco de dados remoto). O implantador de aplicativo é responsável por configurar ouvintes personalizados ou permitindo que os usuários fazer isso. Ele também é responsável por quaisquer informações pessoais exposto no local remoto e corretamente aplicando as ACLs para este local.  
  
### <a name="other-features-for-it-professionals"></a>Outros recursos para profissionais de TI  
 O WCF possui um provedor WMI que expõe as informações de configuração de infraestrutura do WCF por meio do WMI (fornecido com o Windows). Por padrão, a interface WMI está disponível para administradores.  
  
 Configuração do WCF usa o mecanismo de configuração do .NET Framework. Os arquivos de configuração são armazenados no computador. O desenvolvedor do aplicativo e o administrador criam os arquivos de configuração e a ACL para cada um dos requisitos do aplicativo. Um arquivo de configuração pode conter endereços de ponto de extremidade e links para os certificados no repositório de certificados. Os certificados podem ser usados para fornecer dados de aplicativo para configurar várias propriedades dos recursos usados pelo aplicativo.  
  
 O WCF também usa a funcionalidade de despejo de processo do .NET Framework ao chamar o <xref:System.Environment.FailFast%2A> método.  
  
### <a name="it-pro-tools"></a>IT Pro ferramentas  
 O WCF também fornece as seguintes IT professional ferramentas, fornecidos no SDK do Windows.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 O visualizador exibe os arquivos de rastreamento do WCF. O visualizador mostra o texto que está contido nos rastreamentos.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 O editor permite que o usuário criar e editar arquivos de configuração do WCF. O editor mostra o texto que está contido nos arquivos de configuração. A mesma tarefa pode ser feita com um editor de texto.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Essa ferramenta permite que o usuário gerencie ServiceModel instala em um computador. A ferramenta exibe mensagens de status na janela do console quando ele é executado e, no processo, poderá exibir informações sobre a configuração da instalação do WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe e WSATUI.dll  
 Essas ferramentas permitem que os profissionais de TI configurar o suporte de rede de WS-AtomicTransaction interoperável no WCF. As ferramentas de exibam e permitir que o usuário altere os valores das configurações de WS-AtomicTransaction mais comumente usadas, armazenadas no registro.  
  
## <a name="cross-cutting-features"></a>Recursos abrangentes  
 Os seguintes recursos são abrangentes. Ou seja, eles podem ser compostos com qualquer um dos recursos anteriores.  
  
### <a name="service-framework"></a>Estrutura de serviço  
 Cabeçalhos podem conter uma ID de instância, que é um GUID que associa uma mensagem uma instância de uma classe CLR.  
  
 A descrição de linguagem WSDL (Web Services) contém uma definição da porta. Cada porta tem um endereço de ponto de extremidade e uma associação que representa os serviços usados pelo aplicativo. Expondo a WSDL pode ser desativado usando a configuração. Nenhuma informação é mantida no computador.  
  
## <a name="see-also"></a>Consulte também

- [Windows Communication Foundation](index.md)
- [Segurança](../../../docs/framework/wcf/feature-details/security.md)
