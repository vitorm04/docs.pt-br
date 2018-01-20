---
title: "Informações de privacidade do Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d0172b91393e4e9e373a247c33be938a3160e14
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-communication-foundation-privacy-information"></a>Informações de privacidade do Windows Communication Foundation
A Microsoft está comprometida em proteger a privacidade dos usuários finais. Quando você cria um aplicativo usando [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], versão 3.0, seu aplicativo pode afetar a privacidade de seus usuários finais. Por exemplo, seu aplicativo explicitamente pode coletar informações de contato do usuário, ou pode solicitar ou enviar informações pela Internet para seu site da Web. Se você inserir a tecnologia da Microsoft em seu aplicativo, essa tecnologia pode ter seu próprio comportamento que pode afetar a privacidade. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]não enviar informações à Microsoft do seu aplicativo, a menos que você ou o usuário final optar por enviá-lo para nós.  
  
## <a name="wcf-in-brief"></a>WCF no resumo  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]é uma estrutura de mensagens distribuída usando o Microsoft .NET Framework que permite aos desenvolvedores criar aplicativos distribuídos. Mensagens trocadas entre os dois aplicativos contêm informações de cabeçalho e corpo.  
  
 Cabeçalhos podem conter o roteamento de mensagens, as informações de segurança, transações e muito mais dependendo dos serviços usados pelo aplicativo. Normalmente, as mensagens são criptografadas por padrão. A única exceção é quando usando o `BasicHttpBinding`, que foi projetado para uso com os serviços Web herdados, não é seguro. Como criador do aplicativo, você é responsável pelo design final. Mensagens no corpo de SOAP contêm dados específicos do aplicativo; No entanto, esses dados, como definido pelo aplicativo informações pessoais podem ser protegidos usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] recursos de criptografia ou confidencialidade. As seções a seguir descrevem os recursos que afetam a privacidade.  
  
## <a name="messaging"></a>Mensagens  
 Cada [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] mensagem tem um cabeçalho de endereço que especifica o destino da mensagem e onde a resposta deve ir.  
  
 O componente de endereço de um endereço de ponto de extremidade é um identificador de recurso uniforme (URI) que identifica o ponto de extremidade. O endereço pode ser um endereço de rede ou um endereço lógico. O endereço pode incluir o nome do computador (nome de host, o nome de domínio totalmente qualificado) e um endereço IP. O endereço do ponto de extremidade também pode conter um identificador global exclusivo (GUID) ou uma coleção de GUIDs para endereçamento temporário usado para distinguir cada endereço. Cada mensagem contém uma ID de mensagem que é um GUID. Esse recurso segue o padrão de referência do WS-Addressing.  
  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] camada de mensagens não gravar informações pessoais no computador local. No entanto, ele poderá propagar informações pessoais no nível da rede se um desenvolvedor de serviço tiver criado um serviço que expõe essas informações (por exemplo, por usando o nome de uma pessoa em um nome de ponto de extremidade ou, inclusive informações pessoais na Web do ponto de extremidade Serviços de linguagem de descrição, mas não exigir que os clientes usar https para acessar o WSDL). Além disso, se um desenvolvedor é executado o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta em relação a um ponto de extremidade que expõe informações pessoais, a saída da ferramenta pode conter essas informações e o arquivo de saída é gravado para o disco rígido local.  
  
## <a name="hosting"></a>Hospedagem  
 O recurso de hospedagem no [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] permite que os aplicativos para iniciar sob demanda ou para habilitar o compartilhamento de porta entre vários aplicativos. Um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo pode ser hospedado no Internet Information Services (IIS), semelhante ao [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Hospedagem não expõem quaisquer informações específicas da rede e não mantém dados no computador.  
  
## <a name="message-security"></a>Segurança de mensagem  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]segurança fornece os recursos de segurança para aplicativos de mensagens. As funções de segurança fornecidas incluem autenticação e autorização.  
  
 Autenticação é realizada pela transmissão de credenciais entre clientes e serviços. A autenticação pode ser por meio da segurança de nível de transporte ou por meio de SOAP mensagem de nível de segurança, da seguinte maneira:  
  
-   Na segurança de mensagem SOAP, a autenticação é realizada por meio de credenciais como nome de usuário/senha, certificados x. 509, tíquetes Kerberos e os tokens SAML que podem conter informações pessoais, dependendo do emissor.  
  
-   Usando a segurança de transporte, autenticação é feita por meio de mecanismos de autenticação de transporte tradicionais como esquemas de autenticação HTTP (Basic, Digest, Negotiate, NTLM, None, a autorização integrada do Windows e anônimo) e a autenticação de formulário.  
  
 A autenticação pode resultar em uma sessão segura estabelecida entre os pontos de extremidade de comunicação. A sessão é identificada por um GUID que dura o tempo de vida da sessão de segurança. A tabela a seguir mostra o que é mantido e onde.  
  
|Dados|Armazenamento|  
|----------|-------------|  
|Credenciais de apresentação, como nome de usuário, certificados x. 509, tokens Kerberos e as referências às credenciais.|Mecanismos de gerenciamento, como o repositório de certificados do Windows de credencial do Windows padrão.|  
|Informações de associação de usuário, como nomes de usuário e senhas.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]provedores de associação.|  
|Informações de identidade sobre o serviço usado para autenticar o serviço para clientes.|Endereço de ponto de extremidade do serviço.|  
|Informações do chamador.|Logs de auditoria.|  
  
## <a name="auditing"></a>Auditoria  
 A auditoria registra o êxito ou falha de eventos de autenticação e autorização. Registros de auditoria contêm os seguintes dados: serviço URI, URI de ação e identificação do chamador.  
  
 Auditoria também registra quando o administrador modifica a configuração de log de mensagens (ativar ou desativar), porque o log de mensagem pode registrar dados específicos do aplicativo em cabeçalhos e corpos. Para [!INCLUDE[wxp](../../../includes/wxp-md.md)], um registro é registrado no log de eventos do aplicativo. Para [!INCLUDE[wv](../../../includes/wv-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], um registro é registrado no log de eventos de segurança.  
  
## <a name="transactions"></a>Transações  
 O recurso de transações fornece serviços de transação para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo.  
  
 Cabeçalhos de transação usados na propagação de transação podem conter IDs de transação ou IDs de inscrição, que são GUIDs.  
  
 O recurso de transações usa o Gerenciador de transações Microsoft Distributed Transaction coordenador (MSDTC) (um componente do Windows) para gerenciar o estado de transação. Por padrão, as comunicações entre os gerenciadores de transações são criptografadas. Gerenciadores de transações podem fazer referências de ponto de extremidade, IDs de transação e IDs de inscrição como parte de seu estado durável. O tempo de vida deste estado é determinado pelo tempo de vida do Gerenciador de transações do arquivo de log. O serviço MSDTC possui e mantém esse log.  
  
 O recurso de transações implementa os padrões de coordenação WS e WS-AT.  
  
## <a name="reliable-sessions"></a>Sessões confiáveis  
 Sessões confiáveis em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fornecem a transferência de mensagens quando ocorrerem falhas de transporte ou intermediário. Eles fornecem um exatamente-uma vez transferência de mensagens, mesmo quando o transporte subjacente se desconecta (por exemplo, uma conexão TCP em uma rede sem fio) ou perde uma mensagem (um proxy HTTP descartando uma mensagem de entrada ou saída). Sessões confiáveis também recuperar mensagem reordenação (como pode ocorrer no caso de vários caminhos de roteamento), preservando a ordem na qual as mensagens foram enviadas.  
  
 Sessões confiáveis são implementadas usando o protocolo WS-ReliableMessaging (WS-RM). Eles adicionam cabeçalhos de WS-RM que contêm informações de sessão, que são usadas para identificar todas as mensagens associadas a uma determinada sessão confiável. Cada sessão do WS-RM tem um identificador, que é um GUID.  
  
 Nenhuma informação pessoal é mantida no computador do usuário final.  
  
## <a name="queued-channels"></a>Canais em fila  
 Filas de armazenam mensagens em um aplicativo de envio em nome de um aplicativo de recebimento e encaminhá-los posteriormente essas mensagens para o aplicativo receptor. Eles ajudam a garantir a transferência de mensagens de envio de aplicativos para aplicativos de recebimento quando, por exemplo, o aplicativo de recebimento é transitório. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]fornece suporte para enfileiramento de mensagens usando o Microsoft Message Queuing (MSMQ) como um transporte.  
  
 O recurso de canais na fila não adiciona cabeçalhos para uma mensagem. Em vez disso, ele cria uma mensagem de enfileiramento de mensagens com o conjunto de propriedades de mensagem de enfileiramento de mensagens apropriado e invoca métodos de enfileiramento de mensagens para colocar a mensagem na fila do serviço de enfileiramento de mensagens. O Message Queuing é um componente opcional que é fornecido com o Windows.  
  
 Nenhuma informação é mantida no computador do usuário final do recurso de canais em fila, pois ele usa o enfileiramento de mensagens como a infraestrutura de enfileiramento de mensagens.  
  
## <a name="com-integration"></a>Integração de COM+  
 Esse recurso encapsula a funcionalidade existente e COM COM+ para criar serviços que são compatíveis com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços. Esse recurso não usa cabeçalhos específicos e ela não retém dados no computador do usuário final.  
  
## <a name="com-service-moniker"></a>Moniker de serviço COM  
 Isso fornece um wrapper gerenciado para um padrão [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente. Este recurso não tem cabeçalhos específicos na conexão nem ele persistir dados no computador.  
  
## <a name="peer-channel"></a>Canal par  
 Um canal par permite o desenvolvimento de aplicativos com vários participantes usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Mensagens entre vários participantes ocorre no contexto de uma malha. Malhas são identificadas por um nome que podem ingressar em nós. Cada nó no canal de ponto a ponto cria um ouvinte TCP em uma porta especificada pelo usuário e estabelece conexões com outros nós da malha para garantir a resiliência. Para se conectar a outros nós da malha, nós também trocam alguns dados, incluindo o endereço de ouvinte e endereços IP da máquina, com outros nós da malha. As mensagens enviadas ao redor da malha podem conter informações de segurança que pertencem ao remetente para evitar a falsificação de mensagem e a violação.  
  
 Nenhuma informação pessoal é armazenada no computador do usuário final.  
  
## <a name="it-professional-experience"></a>Experiência de profissionais de TI  
  
### <a name="tracing"></a>Rastreamento  
 O recurso de diagnóstico do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] as mensagens que passam pelas camadas de modelo de serviço e transporte de logs de infraestrutura e as atividades e os eventos associados a essas mensagens. Esse recurso é desativado por padrão. Ele é habilitado usando o arquivo de configuração do aplicativo e o comportamento de rastreamento pode ser modificado usando o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provedor WMI em tempo de execução. Quando habilitada, a infraestrutura de rastreamento emite um rastreamento de diagnóstico que contém as mensagens, atividades e eventos de processamento para ouvintes configurados. O formato e o local de saída são determinados por opções de configuração de ouvinte do administrador, mas geralmente é um arquivo XML formatado. O administrador é responsável por definir a lista de controle de acesso (ACL) nos arquivos de rastreamento. Em particular, quando hospedados pelo sistema de ativação do Windows (WAS), o administrador deve assegurar que os arquivos não são atendidos do diretório raiz virtual público se não for desejada.  
  
 Há dois tipos de rastreamento: log de mensagens e diagnóstico do modelo de serviço de rastreamento, descrito na seção a seguir. Cada tipo é configurado por meio de sua própria fonte de rastreamento: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> e <xref:System.ServiceModel>. Ambas essas fontes de rastreamento de log capturar dados é locais para o aplicativo.  
  
### <a name="message-logging"></a>Registro em log de mensagens  
 A mensagem de log de origem de rastreamento (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) permite que um administrador as mensagens de log fluxo por meio do sistema. Por meio de configuração, o usuário pode optar por registrar mensagens inteiras ou somente os cabeçalhos de mensagem, se deseja registrar nas camadas de modelo de transporte e/ou o serviço e se deseja incluir mensagens malformadas. Além disso, o usuário pode configurar a filtragem para restringir quais mensagens são registradas em log.  
  
 Por padrão, o log de mensagens está desabilitado. O administrador do computador local pode impedir que o administrador de nível de aplicativo ativar registro em log de mensagem.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Registro de mensagem criptografados e descriptografados  
 Mensagens são registradas, criptografadas ou descriptografadas, conforme descrito nos seguintes termos.  
  
 Registro de transporte  
 Registra mensagens recebidas e enviadas no nível do transporte. Essas mensagens contêm todos os cabeçalhos e podem ser criptografadas antes de serem enviados na conexão e, quando está sendo recebida.  
  
 Se as mensagens são criptografadas antes de serem enviados na conexão e quando elas são recebidas, elas são registradas criptografados. Uma exceção ocorre quando um protocolo de segurança é usado (https): elas são registradas, em seguida, descriptografados antes de serem enviados e depois que está sendo recebida mesmo se forem criptografados durante a transmissão.  
  
 Log de serviço  
 Registra mensagens recebidos ou enviados no nível do modelo de serviço, após o processamento de cabeçalho do canal tiver ocorrido, antes e depois de inserir o código do usuário.  
  
 Mensagens registradas nesse nível são descriptografadas, mesmo se eles foram protegidos e criptografados na conexão.  
  
 Log de mensagem malformada  
 Logs de mensagens que o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infraestrutura não é possível entender ou processar.  
  
 As mensagens são registradas como-ou seja, é, criptografada ou não  
  
 Quando as mensagens são registradas no descriptografado ou sem criptografia, por padrão [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove as chaves de segurança e informações pessoais potencialmente as mensagens antes de registrá-los. As próximas seções descrevem quais informações são removidas e quando. O administrador do computador e ambos implantador do aplicativo deve executar determinadas ações de configuração para alterar o comportamento padrão para chaves e as informações pessoais potencialmente de log.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informações removidas dos cabeçalhos de mensagem ao registrar em log mensagens descriptografados/não criptografado  
 Quando mensagens são registradas na forma descriptografada/sem criptografia, chaves de segurança e informações pessoais potencialmente são removidos por padrão de cabeçalhos e corpos de mensagens antes que elas são registradas. A lista a seguir mostra o que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] considera as chaves e as informações potencialmente pessoais.  
  
 Chaves são removidas:  
  
 \-Para xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 wst:Entropy  
  
 \-Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:password  
  
 wsse:nonce  
  
 Informações potencialmente pessoais que são removidas:  
  
 \-Para xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" e xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \-Para xmlns:saml = "urn: oasis: nomes: tc: SAML:1.0:assertion" os itens em negrito (abaixo) são removidos:  
  
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
  
 \<Aviso >  
  
 \<AssertionIDReference>[ID]\</AssertionIDReference>*  
  
 \<Assertion>[assertion]\</Assertion>*  
  
 [Nenhum] *  
  
 \</ Aviso >?  
  
 <\!-Tipos de base abstratos  
  
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
  
 \<SubjectConfirmationData>[any]\</SubjectConfirmationData>?  
  
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
  
 \<Ação Namespace = "[uri]" > [string]\</Action > +  
  
 \<Evidência >  
  
 \<AssertionIDReference>[ID]\</AssertionIDReference>+  
  
 \<Assertion>[assertion]\</Assertion>+  
  
 \</ Evidência >?  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informações removidas de corpos de mensagens ao registrar em log mensagens descriptografados/não criptografado  
 Conforme descrito anteriormente, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove chaves e informações potencialmente pessoais dos cabeçalhos da mensagem para mensagens registradas descriptografados/sem criptografia. Além disso, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] remove as chaves e informações pessoais potencialmente corpos de mensagens para os elementos do corpo e as ações na lista a seguir, que descrevem as mensagens de segurança envolvidas na troca de chaves.  
  
 Para os namespaces a seguir:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" e xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (por exemplo, se nenhuma ação disponível)  
  
 Informações serão removidas para esses elementos do corpo, que envolve a troca de chaves:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Informações também são removidas para cada uma das seguintes ações:  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Nenhuma informação é removida da cabeçalhos específicos de aplicativos e dados do corpo  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]não rastreia informações pessoais em cabeçalhos específicos do aplicativo (por exemplo, cadeias de consulta) ou o corpo de dados (por exemplo, o número do cartão de crédito).  
  
 Quando o log de mensagens estiver ativada, informações pessoais em cabeçalhos específicos do aplicativo e as informações de corpo podem estar visíveis nos logs. Novamente, o implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e de log. Ele também pode desativar registro se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de log depois que ele está registrado.  
  
### <a name="service-model-tracing"></a>Rastreamento de modelo de serviço  
 A origem de rastreamento de modelo de serviço (<xref:System.ServiceModel>) habilita o rastreamento de eventos e as atividades relacionadas ao processamento de mensagem. Esse recurso usa a funcionalidade de diagnóstico do .NET Framework do <xref:System.Diagnostics>. Assim como acontece com o <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> propriedade, o local e sua ACL são configuráveis pelo usuário usando arquivos de configuração de aplicativo do .NET Framework. Como com o log de mensagem, o local do arquivo é sempre configurado quando o administrador habilita o rastreamento; Assim, o administrador controla a ACL.  
  
 Quando uma mensagem no escopo, os rastreamentos contêm cabeçalhos de mensagem. Aplicam as mesmas regras para ocultar informações potencialmente pessoais em cabeçalhos de mensagem na seção anterior: as informações pessoais identificadas anteriormente foram removidas por padrão de cabeçalhos em rastreamentos. O administrador da máquina e o implantador de aplicativo devem modificar a configuração para registrar informações potencialmente pessoais. No entanto, informações pessoais contidas nos cabeçalhos específicos do aplicativo são registradas em rastreamentos. O implantador de aplicativo é responsável por definir as ACLs nos arquivos de configuração e o rastreamento. Ele também pode desativar o rastreamento se ele não quer que essa informação fique visível, ou ele pode filtrar essas informações dos arquivos de rastreamento depois que ele está registrado.  
  
 Como parte do rastreamento de ServiceModel, IDs exclusivas (chamado de IDs de atividade e, geralmente um GUID) vincular atividades diferentes juntos como uma mensagem passa pela diferentes partes da infraestrutura.  
  
#### <a name="custom-trace-listeners"></a>Ouvintes de rastreamento personalizado  
 Para ambas as mensagens de log e rastreamento, um ouvinte de rastreamento personalizada pode ser configurado, o que pode enviar mensagens e rastreamentos na conexão (por exemplo, para um banco de dados remoto). O implantador de aplicativo é responsável por configurar ouvintes personalizados ou permitindo que os usuários fazer isso. Ele também é responsável por quaisquer informações pessoais exposto no local remoto e para aplicar as ACLs adequadamente para esse local.  
  
### <a name="other-features-for-it-professionals"></a>Outros recursos para profissionais de TI  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]tem um provedor WMI que expõe o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] informações de configuração de infraestrutura por meio do WMI (fornecido com o Windows). Por padrão, a interface WMI está disponível para administradores.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]configuração usa o mecanismo de configuração do .NET Framework. Os arquivos de configuração são armazenados no computador. O desenvolvedor do aplicativo e o administrador criam os arquivos de configuração e a ACL para cada um dos requisitos do aplicativo. Um arquivo de configuração pode conter endereços de ponto de extremidade e links para os certificados no repositório de certificados. Os certificados podem ser usados para fornecer dados de aplicativo para configurar várias propriedades dos recursos usados pelo aplicativo.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]também usa a funcionalidade de despejo de processo do .NET Framework ao chamar o <xref:System.Environment.FailFast%2A> método.  
  
### <a name="it-pro-tools"></a>IT Pro ferramentas  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]também fornece as ferramentas de profissional seguir IT, fornecidas no SDK do Windows.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 O visualizador exibe [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] arquivos de rastreamento. O visualizador mostra o texto que está contido nos rastreamentos.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 O editor permite que o usuário criar e editar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] arquivos de configuração. O editor mostra o texto que está contido nos arquivos de configuração. A mesma tarefa pode ser feita com um editor de texto.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 Essa ferramenta permite que o usuário gerencie ServiceModel instala em um computador. A ferramenta exibe mensagens de status na janela do console quando ele é executado e, no processo, pode exibir informações sobre a configuração do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] instalação.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe e WSATUI.dll  
 Essas ferramentas permitem que os profissionais de TI configurar o suporte de rede WS-AtomicTransaction interoperável em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. As ferramentas de exibem e permitir que o usuário altere os valores das configurações do WS-AtomicTransaction mais comumente usadas armazenadas no registro.  
  
## <a name="cross-cutting-features"></a>Recursos abrangentes  
 Os seguintes recursos são abrangentes. Ou seja, eles podem ser compostos com qualquer um dos recursos anteriores.  
  
### <a name="service-framework"></a>Estrutura de serviço  
 Cabeçalhos podem conter uma ID de instância, que é um GUID que associa uma mensagem uma instância de uma classe CLR.  
  
 O WSDL Web Services Description Language () contém uma definição da porta. Cada porta tem um endereço de ponto de extremidade e uma associação que representa os serviços usados pelo aplicativo. Expondo WSDL pode ser desativado usando a configuração. Nenhuma informação é mantida no computador.  
  
## <a name="see-also"></a>Consulte também  
 [Windows Communication Foundation](http://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Segurança](../../../docs/framework/wcf/feature-details/security.md)
