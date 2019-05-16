---
title: Protocolos de mensagens
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 70972f6a211d60d9fd330277040428ef783e9668
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631531"
---
# <a name="messaging-protocols"></a>Protocolos de mensagens

A pilha de canais do Windows Communication Foundation (WCF) emprega canais de transporte e de codificação para transformar a representação interna de mensagem em seu formato de transmissão e enviá-lo por meio de um transporte particular. O transporte mais comuns usado para a interoperabilidade de serviços da Web é HTTP, e as codificações mais comuns usadas pelos serviços da Web são baseados em XML SOAP 1.1, SOAP 1.2 e MTOM Message Transmission Optimization Mechanism ().

Este tópico abrange detalhes de implementação de WCF para os seguintes protocolos utilizados por <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.

Especificação/documento:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [Ligação de SOAP 1.1 HTTP](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), seção 7
- [SOAP 1.2 associação de HTTP](https://www.w3.org/TR/soap12-part2) seção 7

Este tópico abrange detalhes de implementação de WCF para os seguintes protocolos <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> empregar.

Especificação/documento:

- [XML](https://www.w3.org/TR/REC-xml)
- [SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1.2 Core](https://www.w3.org/TR/soap12-part1/)
- [2004 de WS-Addressing/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [1.0 - Core endereçamento de serviços Web do W3C](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [Endereçamento 1.0 - associação de SOAP de serviços de Web do W3C](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [Endereçamento 1.0 - associação de WSDL de serviços de Web do W3C](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [1.0 - metadados endereçamento de serviços Web do W3C](https://www.w3.org/TR/ws-addr-metadata/)
- [Associação de SOAP1.1 WSDL](https://www.w3.org/TR/wsdl/)
- [Associação de SOAP1.2 WSDL](https://www.w3.org/Submission/wsdl11soap12/)

Este tópico abrange detalhes de implementação de WCF para protocolos a seguir <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> emprega.

Especificação/documento:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SOAP 1.2 de associação](https://www.w3.org/TR/soap12-mtom/)
- [MTOM ligação de SOAP 1.1](https://www.w3.org/Submission/soap11mtom10/)
- [Asserção do WS-Policy MTOM](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico:

| Prefixo | Namespace Uniform Resource Identifier (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SOAP 1.1 e SOAP 1.2

### <a name="envelope-and-processing-model"></a>Envelope e processamento de modelo
O WCF implementa o processamento do envelope SOAP 1.1 Basic Profile 1.1 (BP11) e o Basic Profile 1.0 (SSBP10) a seguir. SOAP 1.2 Envelope processamento é implementado Parte1 SOAP12 a seguir.

Esta seção explica a certas opções de implementação tomadas pelo WCF em relação a BP11 e SOAP12 Parte1.

#### <a name="mandatory-header-processing"></a>Processamento de cabeçalho obrigatórios
WCF segue as regras para processar cabeçalhos marcado `mustUnderstand` descrito nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.

Uma mensagem que entra a pilha de canais do WCF é processada por canais individuais configurados por elementos de ligação associada, por exemplo, codificação de mensagem de texto, segurança, mensagens confiáveis e transações. Cada canal reconhece os cabeçalhos do namespace associado e os marca como compreendido. Depois que uma mensagem insere o dispatcher, o formatador de operação lê cabeçalhos esperados pelo contrato de mensagem/operação correspondente e marcas-los compreendidos. Em seguida, o dispatcher verifica se todos os cabeçalhos restantes não são compreendidos mas marcados como `mustUnderstand` e gera uma exceção. Mensagens que contêm `mustUnderstand` cabeçalhos que são destinados ao destinatário não são processados pelo código do aplicativo de destino.

Como em camadas de processamento permite a separação entre as camadas de infraestrutura e aplicativo do nó SOAP:

- B1111: Cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pela pilha de canal de infraestrutura do WCF, mas antes de ser processada pelo aplicativo

     O `mustUnderstand` difere do valor de cabeçalho entre SOAP 1.1 e SOAP 1.2. Basic Profile 1.1 requer que o `mustUnderstand` valor ser 0 ou 1 para mensagens SOAP 1.1. SOAP 1.2 permite 0, 1, `false`, e `true` como valores, mas recomenda emitindo uma representação canônica do `xs:boolean` valores (`false`, `true`).

- B1112: WCF emite `mustUnderstand` valores 0 e 1 para versões de SOAP 1.1 e SOAP 1.2 do envelope SOAP. WCF aceita o espaço de todo o valor de `xs:boolean` para o `mustUnderstand` cabeçalho (0, 1, `false`, `true`)

#### <a name="soap-faults"></a>Falhas de SOAP
A seguir está uma lista das implementações de falhas SOAP específicas do WCF.

- B2121: WCF retorna os seguintes códigos de falha de SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, e `s11:Server`.

- B2122: WCF retorna os seguintes códigos de falha de SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, e `s12:Receiver`.

### <a name="http-binding"></a>Associação de HTTP

#### <a name="soap-11-http-binding"></a>Ligação de SOAP 1.1 HTTP
O WCF implementa a associação HTTP SOAP1.1 seguindo a seção 3.4 com os seguintes esclarecimentos de especificação do Basic Profile 1.1:

- B2211: Serviço do WCF não implementa o redirecionamento de solicitações HTTP POST.

- B2212: Clientes do WCF dão suporte a Cookies HTTP de acordo com 3.4.8.

#### <a name="soap-12-http-binding"></a>SOAP 1.2 associação de HTTP
O WCF implementa associação SOAP 1.2 HTTP, conforme descrito na SOAP 1.2-parte 2 (SOAP12Part2) especificação com os seguintes esclarecimentos.

SOAP 1.2 introduziu um parâmetro de ação opcional para o `application/soap+xml` tipo de mídia. Esse parâmetro é útil para otimizar a expedição de mensagens sem a necessidade de que o corpo da mensagem SOAP ser analisado ao WS-Addressing não é usado.

- R2221: O `application/soap+xml` parâmetro de ação, quando presente em uma solicitação de SOAP 1.2, deve corresponder a `soapAction` o atributo no `wsoap12:operation` elemento dentro de associação WSDL correspondente.

- R2222: O `application/soap+xml` parâmetro de ação, quando presentes em uma mensagem SOAP 1.2, deve corresponder ao `wsa:Action` quando 2004 de WS-Addressing/08 ou WS-Addressing 1.0 são usadas.

Quando o WS-Addressing é desabilitado e uma solicitação de entrada não contém um parâmetro de ação, uma mensagem `Action` é considerada como não especificado.

## <a name="ws-addressing"></a>WS-Addressing
O WCF implementa as 3 versões do WS-Addressing:

- 2004 de WS-Addressing/08

- Serviços Web do W3C endereçamento 1.0 Core (ADDR10-núcleo) e SOAP associação (ADDR10 SOAP)

- WS-Addressing 1.0 - metadados

### <a name="endpoint-references"></a>Referências de ponto de extremidade
Todas as versões do WS-Addressing que o WCF implementa usam referências de ponto de extremidade para descrever os pontos de extremidade.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Referências de ponto de extremidade e WS-Addressing versões
O WCF implementa um número dos protocolos de infraestrutura que usam o WS-Addressing e, em particular a `EndpointReference` elemento e `W3C.WsAddressing.EndpointReferenceType` classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust). O WCF oferece suporte ao uso de qualquer versão do WS-Addressing com outros protocolos de infraestrutura. Pontos de extremidade do WCF dão suporte a uma versão do WS-Addressing por ponto de extremidade.

Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um ponto de extremidade do WCF deve corresponder à versão do WS-Addressing implementada por esse ponto de extremidade.

Por exemplo, se um ponto de extremidade do WCF implementa WS-ReliableMessaging, o `AcksTo` retornado por tal um ponto de extremidade dentro do cabeçalho `CreateSequenceResponse` usa a versão de WS-Addressing que o `EncodingBinding` elemento especifica para esse ponto de extremidade.

#### <a name="endpoint-references-and-metadata"></a>Metadados e referências de ponto de extremidade
Um número de cenários exige comunicação de metadados ou uma referência aos metadados para um determinado ponto de extremidade.

B3121: WCF emprega mecanismos descritos na seção 6 para incluir metadados para referências de ponto de extremidade por valor ou referência de especificação de WS-MetadataExchange (MEX).

Considere um cenário em que um serviço WCF requer autenticação usando um token de declarações marcação linguagem SAML (Security) emitido pelo emissor de token em `http://sts.fabrikam123.com`. O ponto de extremidade do WCF descreve esse requisito de autenticação por meio `sp:IssuedToken` asserção com aninhado `sp:Issuer` asserção que aponta para o emissor do token. Aplicativos cliente que acessam o `sp:Issuer` asserção precisa saber como se comunicar com o ponto de extremidade do emissor do token. O cliente precisa saber os metadados sobre o emissor do token. Usando as extensões de metadados de referência de ponto de extremidade definidas no MEX, o WCF fornece uma referência aos metadados do emissor do token.

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>Cabeçalhos de endereçamento de mensagens

#### <a name="message-headers"></a>Cabeçalhos de mensagem
Para ambas as versões do WS-Addressing, o WCF usa os seguintes cabeçalhos de mensagem conforme prescrito pelas especificações `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, e `wsa:RelatesTo`.

B3211: Para todas as versões de WS-Addressing, WCF respeita, mas não produz imediato, cabeçalhos de mensagem do WS-Addressing `wsa:FaultTo` e `wsa:From`.

Aplicativos que interagem com aplicativos do WCF podem adicionar que esses cabeçalhos de mensagem e o WCF irá processá-las adequadamente.

#### <a name="reference-parameters-and-properties"></a>Propriedades e parâmetros de referência

O WCF implementa o processamento de parâmetros de referência do ponto de extremidade e propriedades de referência de acordo com as respectivas especificações.

B3221: Quando configurado para usar 08/2004 de WS-Addressing, pontos de extremidade do WCF não fazem distinção entre as propriedades de referência e parâmetros de referência de processamento.

### <a name="message-exchange-patterns"></a>Padrões de troca de mensagem
A sequência das mensagens envolvidas na invocação de operação do serviço Web é conhecida como o *padrão de troca de mensagem*. Padrões de troca de mensagem duplex, solicitação-resposta e dá suporte a WCF unidirecional. Esta seção explica os requisitos, dependendo do padrão de troca de mensagem que está sendo usado de processamento de mensagens WS-Addressing.

Ao longo desta seção, o solicitante envia a primeira mensagem e o Respondente recebe a primeira mensagem.

#### <a name="one-way-message"></a>Mensagem unidirecional
Quando um ponto de extremidade do WCF está configurado para dar suporte a mensagens com um determinado `Action` para seguir o padrão unidirecional, o ponto de extremidade do WCF segue os requisitos e os comportamentos a seguir. A menos que especificado de outra forma, regras e comportamentos se aplicam a ambas as versões do WS-Addressing tem suportada no WCF:

- R3311: O solicitante deve incluir `wsa:To`, `wsa:Action`e os cabeçalhos para todos os parâmetros de referência especificados pela referência de ponto de extremidade. Quando 08/2004 de WS-Addressing é usado e [Propriedades de referência] são especificados pela referência de ponto de extremidade, os cabeçalhos correspondentes devem ser adicionados à mensagem muito.

- B3312: O solicitante pode incluir `MessageID`, `ReplyTo`, e `FaultTo` cabeçalhos. A infraestrutura de receptor irá ignorá-los e eles serão passados para o aplicativo.

- R3313: Quando HTTP é usado e nenhuma mensagem está sendo enviada sobre o segmento de resposta HTTP, o Respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.

     Quando o transporte HTTP está em uso e o contrato de operação declara uma mensagem unidirecional, a resposta HTTP ainda pode ser usada para enviar mensagens de infraestrutura — por exemplo, o sistema de mensagens confiável pode enviar um `SequenceAcknowledgement` mensagem em uma resposta HTTP.

- B3314: O respondente do WCF não envia uma mensagem de falha em resposta a uma mensagem unidirecional.

#### <a name="request-reply"></a>Solicitação-resposta
Quando um ponto de extremidade do WCF é configurado para uma mensagem com um determinado `Action` para seguir o padrão de solicitação-resposta, o ponto de extremidade do WCF segue os comportamentos e os requisitos abaixo. A menos que especificado o contrário, comportamentos e as regras se aplicam a ambas as versões do WS-Addressing tem suportada no WCF:

- R3321: O solicitante deve incluir na solicitação `wsa:To`, `wsa:Action`, `wsa:MessageID`e os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pela referência de ponto de extremidade.

- R3322: Quando 08/2004 de WS-Addressing é usado, `ReplyTo` também deve ser incluído na solicitação.

- R3323: Quando é usado o WS-Addressing 1.0 e `ReplyTo` não está presente na solicitação, uma referência de ponto de extremidade padrão com a propriedade [endereço] igual a `http://www.w3.org/2005/08/addressing/anonymous` é usado.

- R3324: O solicitante deve incluir `wsa:To`, `wsa:Action`, e `wsa:RelatesTo` cabeçalhos na mensagem de resposta, bem como os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pelo `ReplyTo` referência de ponto de extremidade na solicitação.

### <a name="web-services-addressing-faults"></a>Falhas de endereçamento de serviços da Web
R3411: O WCF gera as seguintes falhas definidas pelo 08/2004 de WS-Addressing.

| Código | Causa |
|----------|-----------|
| `wsa:DestinationUnreachable` | A mensagem chegou com um `ReplyTo` que é diferente do endereço de resposta estabelecido para este canal; não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho To. |
| `wsa:ActionNotSupported` | canais de infraestrutura ou dispatcher associado com o ponto de extremidade não reconhecem a ação especificada no `Action` cabeçalho. |

R3412: O WCF gera as seguintes falhas definidas pelo WS-Addressing 1.0.

| Código | Causa |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Duplicar `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`. Duplicar `wsa:RelatesTo` com o mesmo `RelationshipType`. |
| `wsa10:MessageAddressingHeaderRequired` | O cabeçalho de endereçamento necessário está ausente. |
| `wsa10:DestinationUnreachable` | A mensagem chegou com um `ReplyTo` que é diferente do endereço de resposta estabelecido para este canal. Não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho To. |
| `wsa10:ActionNotSupported` | Uma ação especificada no `Action` cabeçalho não é reconhecido pelo dispatcher associado com o ponto de extremidade ou canais de infraestrutura. |
| `wsa10:EndpointUnavailable` | O canal do RM envia essa falha, que indica o ponto de extremidade não processará a sequência com base no exame do `CreateSequence` cabeçalhos de endereçamento da mensagem. |

Mapas de código nas tabelas anteriores ao `FaultCode` em SOAP 1.1 e `SubCode` (com o código = remetente) em SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 associação e asserções WS-Policy

#### <a name="indicating-use-of-ws-addressing"></a>Que indica o uso do WS-Addressing.
O WCF usa as declarações de política para indicar o suporte de ponto de extremidade para uma versão específica do WS-Addressing.

A seguinte declaração de política tem o assunto da diretriz de ponto de extremidade [WS-PA] e indica as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 de WS-Addressing.

```xml
<wsap:UsingAddressing />
```

Esta declaração de política aumenta a especificação de 2004 de WS-Addressing/08.

A seguinte declaração de política, que isso indica que as mensagens enviadas/recebidas deve usar WS-Addressing 1.0.

```xml
<wsam:Addressing/>
```

A seguinte declaração de política tem um assunto de política de ponto de extremidade [WS-PA] e indica se as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 de WS-Addressing.

```xml
<wsaw10:UsingAddressing />
```

O `wsaw10:UsingAddressing` elemento é obtido do [WS-Addressing-WSDL] e é usado no contexto do WS-Policy em conformidade com essa especificação, seção 3.1.2.

Uso de endereçamento não altera a semântica de WSDL 1.1, SOAP 1.1 e associações de HTTP SOAP 1.2. Por exemplo, se uma resposta é esperada para uma solicitação enviada para um ponto de extremidade que usa a associação de HTTP 1.x Addressing e SOAP WSDL, a resposta deve ser enviada usando a resposta HTTP.

Para respostas enviadas pela resposta http, a declaração de WS-AM é:

```xml
<wsam:AnonymousResponses/>
```

A declaração de política completo pode ter esta aparência:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

No entanto, há padrões de troca de mensagem se beneficiar de duas conexões de HTTP inverso independentes estabelecidas entre o solicitante e o Respondente, por exemplo, não solicitadas unidirecionais mensagens enviadas pelo respondente.

O WCF oferece um recurso pelo qual dois canais de transporte subjacente podem formar um canal dúplex de composição, onde um canal é usado para mensagens de entrada e a outra é usada para mensagens de saída. No caso do transporte de HTTP dúplex de composição fornece duas conexões de HTTP do inverso. O solicitante usa uma conexão para enviar mensagens para o respondente e o Respondente usa o outro para enviar mensagens de volta ao solicitante.

Para respostas enviadas por solicitações http separado, a declaração de ws-am é

```xml
<wsam:NonAnonymousResponses/>
```

A declaração de política completo pode ter esta aparência:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Uso a seguinte asserção que tem o assunto de política de ponto de extremidade [WS-PA] em pontos de extremidade que usam associações de HTTP do WSDL 1.1 SOAP 1.x requer duas conexões de HTTP inverso separado a ser usado para mensagens que fluem do solicitante para Respondente e o Respondente ao solicitante, respectivamente.

```xml
<cdp:CompositeDuplex/>
```

A instrução anterior leva aos requisitos a seguir o `wsa:ReplyTo` cabeçalho para mensagens de solicitação:

- R3514: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com o `[address]` propriedade não é igual a `http://www.w3.org/2005/08/addressing/anonymous` se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com um `wsap10:UsingAddressing` ou `wsap:UsingAddressing` asserção juntamente com `cdp:CompositeDuplex` anexado.

- R3515: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com o `[address]` propriedade igual a `http://www.w3.org/2005/08/addressing/anonymous`, ou não tem um `ReplyTo` cabeçalho no lugar, se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com `wsap10:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.

- R3516: Solicitar que as mensagens enviadas para um ponto de extremidade devem ter uma `ReplyTo` cabeçalho com um `[address]` propriedade igual a `http://www.w3.org/2005/08/addressing/anonymous` se o ponto de extremidade usa uma associação de HTTP do 1.x WSDL 1.1 SOAP e tem uma alternativa de política com `wsap:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.

A especificação de WS-addressing WSDL tenta descrever as associações do protocolo semelhante com a introdução de um elemento `<wsaw:Anonymous/>` com três valores textuais (obrigatórios, opcionais e proibidos) para indicar requisitos sobre o `wsa:ReplyTo` cabeçalho (seção 3.2). Infelizmente, essa definição de elemento não é particularmente útil como uma asserção no contexto do WS-Policy, porque ele requer extensões específicas de domínio para dar suporte a interseção de alternativas usando esse elemento como uma asserção. Essa definição de elemento também indica o valor da `ReplyTo` cabeçalho em vez do comportamento de ponto de extremidade durante a transmissão, o que torna específico ao transporte HTTP.

#### <a name="action-definition"></a>Definição de ação
08/2004 de WS-Addressing define uma `wsa:Action` de atributo para o `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos. WS-Addressing 1.0 WSDL associação (WS-ADDR10 WSDL) define um atributo semelhante, `wsaw10:Action`.

A única diferença entre os dois é a semântica de padrão de ação padrão descrita na seção 3.3.2 do WS-ADDR e 4.4.4 do WS-ADDR10-WSDL, respectivamente.

É razoável ter dois pontos de extremidade que compartilham o mesmo `portType` (ou um contrato, na terminologia do WCF), mas usando diferentes versões do WS-Addressing. Mas considerando que a ação é definida pela `portType` e não devem alterar entre os pontos de extremidade que implementam o `portType`, ele se torna impossível dar suporte a ambos os padrões de ação padrão.

Para resolver esta controvérsia incrível, o WCF oferece suporte a uma única versão do `Action` atributo.

B3521: O WCF usa o `wsaw10:Action` atributo `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos conforme definido em WS-ADDR10 WSDL para determinar o `Action` URI para as mensagens correspondentes independentemente da versão do WS-Addressing usadas pelo ponto de extremidade.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Porta de WSDL de dentro do uso ponto de extremidade de referência
WS-ADDR10-WSDL seção 4.1 estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto de extremidade em termos de WS-Addressing. WCF expande esse utilitário em 2004 de WS-Addressing/08, permitindo `<wsa:EndpointReference…/>` apareça como um elemento filho de `wsdl:port`.

- R3531: Se um ponto de extremidade tem uma alternativa de política anexada com um `<wsaw10:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa10:EndpointReference …/>`.

- R3532: Se um `wsdl:port` contém um elemento filho `<wsa10:EndpointReference …/>`, o `wsa10:EndpointReference/wsa10:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.

- R3533: Se um ponto de extremidade tem uma alternativa de política anexada com `<wsap:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa:EndpointReference …/>`.

- R3534: Se um `wsdl:port` contém um elemento filho `<wsa:EndpointReference …/>`, o `wsa:EndpointReference/wsa:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.

### <a name="composition-with-ws-security"></a>Composição com o WS-Security
De acordo com a seções de consideração de segurança no WS-ADDR e WS-ADDR10, todos os cabeçalhos de mensagem de endereçamento são recomendados sejam assinadas junto com o corpo da mensagem para ligá-los juntos.

Quando o WS-Security é usado para proteção de integridade da mensagem, WS-Addressing mensagem resultaram de cabeçalhos, bem como cabeçalhos de parâmetros de referência ou propriedades (ou ambos) deve ser assinada juntamente com o corpo da mensagem.

### <a name="examples"></a>Exemplos

#### <a name="one-way-message"></a>Mensagem unidirecional
Nesse cenário, o remetente envia uma mensagem unidirecional para o receptor. W3C WS-Addressing 1.0, HTTP 1.1 e SOAP 1.2 são usados.

A estrutura de mensagens de solicitação: Incluem os cabeçalhos da mensagem `wsa10:To` e `wsa10:Action` elementos. O corpo da mensagem inclui um determinado `<app:Ping>` elemento do namespace do aplicativo.

Cabeçalhos HTTP: O destino na POSTAGEM corresponde ao URI no `wsa10:To` elemento.

O cabeçalho Content-Type tem o valor de `application/soap+xml` conforme solicitado pelo SOAP 1.2. Parâmetros `charset` e `action` são incluídos. O `action` parâmetro do cabeçalho Content-Type corresponde ao valor do `wsa10:Action` cabeçalho da mensagem.

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay 
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

O receptor responde com uma resposta HTTP vazia e o status de 202. Um exemplo de resposta HTTP:

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>Mecanismo de otimização da transmissão de mensagens SOAP
Esta seção descreve os detalhes de implementação de WCF para o HTTP SOAP MTOM. A tecnologia MTOM é o mecanismo de codificação de mensagem SOAP da mesma classe, como codificação tradicional de texto/XML ou binário do WCF. MTOM inclui o seguinte:

- Uma codificação XML e o mecanismo de empacotamento descrito pelo [XOP] que otimiza a itens de informações de XML que contém dados binários codificados em base64 em partes separadas de binários.

- Um encapsulamento MIME do pacote XOP que serializa o XML Infoset e cada parte binária do pacote XOP em uma parte MIME separada.

- Uma codificação de MIME XOP aplicada ao SOAP 1.x Envelope.

- Um HTTP ligação de transporte.

É possível usar o MTOM com transportes não-HTTP com WCF. No entanto, neste tópico nos concentraremos em HTTP.

O formato MTOM aproveita um grande conjunto de especificações que abrangem o MTOM em si, XOP e MIME. A modularidade desse conjunto da especificação torna um pouco difícil de reconstruir os requisitos exatos em que a semântica de formato e o processamento. Esta seção descreve os requisitos de formato e o processamento para a associação HTTP MTOM.

### <a name="mtom-message-encoding"></a>Codificação de mensagem MTOM

#### <a name="generating-mtom-messages"></a>Gerando mensagens MTOM
A seção 3.1 [XOP] descreve o processo de codificação de XML com itens de informações do elemento que contêm valores de base64 em um pacote XOP definido de forma abstrata.

A sequência de etapas a seguir descreve o processo de codificação de MTOM específicas:

1. Certifique-se de que o Envelope SOAP a ser decodificado não contém nenhum item de informação do elemento com um `[namespace name]` dos `http://www.w3.org/2004/08/xop/include` e uma `[local name]` de `Include`.

2. Crie um pacote vazio do MIME.

3. Identifique os itens de informações do elemento a ser otimizado dentro o XML Infoset Original. Para os itens que serão otimizados, os caracteres que compõem o `[children]` as informações do elemento de item deve ser no formato canônico de `xs:base64Binary` (consulte XSD-2, 3.2.16 base64Binary) e não deve conter quaisquer caracteres de espaço em branco anteriores embutidos com, ou Após o conteúdo diferente de espaço em branco.

4. Criar um Envelope SOAP XOP que é uma cópia do Envelope SOAP Original, mas com os filhos de cada informações sobre o elemento item identificado na etapa anterior é substituída por um `xop:Include` item de informação do elemento construída da seguinte maneira:

    1. Transforme os caracteres substituídos em dados binários processando-os como dados codificados em base64.

    2. Gere um valor de cabeçalho Content-ID exclusivo que satisfaz os requisitos de R3133 e R3134.

    3. Gere um cabeçalho Content-Transfer-Encoding MIME com o valor binário.

    4. Se o item de informação do elemento que está sendo otimizado ([pai] de recém-inserido `xop:Include` item de informação do elemento) tem um `xmime:contentType` atributo de item de informação, gerar um cabeçalho de tipo de conteúdo MIME com o valor da `xmime:contentType` atributo.

    5. Gere uma nova parte MIME binária com conteúdo formado por dados binários decodificados dos caracteres substituídos processados como base64, o cabeçalho Content-ID do 4b, o cabeçalho Content-Transfer-Encoding de 4 núcleos, o cabeçalho Content-Type se gerado na etapa 4d.

    6. Adicionar um `href` de atributo para o `xop:Include` elemento com o valor de cid: uri derivado do valor de cabeçalho de Content-ID gerado na etapa 4b. Remover o delimitador "\<" e ">" caracteres, o restante da cadeia de caracteres e adicione o prefixo de URL-escape `cid:`. O conjunto mínimo de caracteres a seguir é necessário ser substituídas por RFC1738 e RFC2396. Outros caracteres podem ser substituídos.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Crie uma parte MIME raiz com o Envelope SOAP de XOP da etapa 4.

6. Gravar os cabeçalhos HTTP, incluindo o cabeçalho HTTP Content-Type.

7. O pacote MIME é gravado.

#### <a name="processing-mtom-messages"></a>Processamento de mensagens MTOM
O processamento de um MTOM mensagem é o inverso exato do processo descrito anteriormente na "gerando MTOM mensagens" seção:

1. Verifique se a parte MIME raiz tem o tipo de conteúdo `application/xop+xml`.

2. Construa um Envelope SOAP ao analisar a parte MIME do pacote como um documento XML raiz. Codificação de caracteres é determinada pelo `charset` parâmetro o tipo de conteúdo da parte MIME raiz.

3. Para cada item de informações do elemento no Envelope SOAP construído, que tem, como os únicos membros de sua propriedade [filhos], um `xop:Include` item de informação do elemento:

    1. Remover o `cid:` de prefixo e unescape todas as sequências de escape do URI (RFC 2396) no valor da `@href` atributo do `xop:Include` elemento. Coloque a cadeia de caracteres de resultado no "\<", ">".

    2. Localize a parte do MIME com o valor do cabeçalho Content-ID que corresponde à cadeia de caracteres derivada na etapa 3a.

    3. Substitua os `xop:Include` item de informação do elemento que aparece no `children` propriedade de cada item com os itens de informações de caracteres que representam a codificação base64 canônico (consulte XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificado na etapa 3b (substituir com eficiência o `xop:Include` item de informação do elemento com os dados reconstruídos com a parte do pacote).

#### <a name="http-content-type-header"></a>Cabeçalho HTTP Content-Type
A seguir está uma lista de esclarecimentos de WCF para o formato do cabeçalho HTTP Content-Type 1.x codificada por MTOM mensagens SOAP derivado de requisitos mencionados na especificação do MTOM propriamente dito e é derivado do MTOM e RFC 2387.

- R4131: Um cabeçalho HTTP Content-Type deve ter o valor de diversas partes/relacionado (diferencia maiusculas de minúsculas) e seus parâmetros. Nomes de parâmetros diferenciam maiusculas de minúsculas. Ordem do parâmetro não é significativa.

- A forma de Backus-Naur completo (BNF) do cabeçalho Content-Type para mensagens MIME é listado na RFC 2045, seção 5.1.

- R4132: Um cabeçalho HTTP Content-Type deve ter um parâmetro de tipo com o valor `application/xop+xml` entre aspas duplas.

Embora o requisito para usar as aspas duplas não seja explícito na RFC 2387, o texto observa que todos os parâmetros de tipo de mídia com diversas partes/relacionado provavelmente contêm caracteres reservados como "\@" ou "/" e, portanto, precisam de aspas duplas marca.

- R4133: Um cabeçalho HTTP Content-Type deve ter um parâmetro de inicialização com o valor do cabeçalho Content-ID da parte MIME que contém o SOAP 1.x Envelope, entre aspas duplas. Se o parâmetro start for omitido, a primeira parte MIME deve conter o SOAP 1.x Envelope.

- R4134: Um cabeçalho HTTP Content-Type para uma mensagem SOAP 1.1 MTOM codificado deve incluir o parâmetro de informações de início com o valor de texto/xml, entre aspas duplas.

- R4135: Um cabeçalho HTTP Content-Type para uma mensagem codificada em SOAP 1.2 MTOM deve incluir o parâmetro de informações de início com o valor de `application/soap+xml`, colocado entre aspas duplas.

- R4136: Cabeçalho HTTP Content-Type para uma mensagem codificada por MTOM do SOAP 1. x deve ter o parâmetro de limite com o valor de (delimitado por aspas duplas) que corresponde ao limite MIME que BNF definido no RFC 2046, seção 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace 
    bchars := bcharsnospace / " " 
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+" 
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Exemplos:

     CORRIGIR

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     CORRIGIR

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     INCORRETO

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1" 
    ```

#### <a name="infoset-mime-part"></a>Parte do MIME Infoset
O SOAP 1.x Envelope é encapsulado como parte do pacote XOP MIME raiz e geralmente é chamado de `infoset` parte.

- R4141: O SOAP 1.x Envelope deve ser encapsulado como parte da raiz do pacote XOP MIME, chamado de `infoset` parte e referenciado de tipo de conteúdo HTTP.

- R4142: O SOAP `Infoset` parte deve incluir os seguintes cabeçalhos MIME: `Content-ID`, `Content-Transfer-Encoding`, e `Content-Type`.

O formato do cabeçalho Content-ID é definido por RFC 2045 como

```
"Content-ID" ":" msg-id
```

onde `msg-id` é definido no RFC 2822 (que substitui o RFC 822, referenciada na RFC 2045) como:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

e é efetivamente um endereço de email incluído dentro de "\<" e ">". O `[CFWS]` prefixo e sufixo foram adicionadas no RFC 2822 para transportar os comentários e não deve ser usados para preservar a interoperabilidade.

R4143: O valor do cabeçalho Content-ID para a parte de Infoset MIME deve seguir `msg-id` produção da RFC 2822 com o `[CFWS]` partes de prefixo e sufixo omitidas.

Um número de implementações de MIME relaxada requisitos para o valor incluído dentro de "\<" e ">" para ser um endereço de email e usado `absoluteURI` entre "\<", ">", além do endereço de email. Esta versão do WCF usa os valores do cabeçalho MIME Content-ID do formulário:

```
Content-ID: <http://tempuri.org/0> 
```

R4144: Processadores MTOM devem aceitar valores de cabeçalho Content-ID que correspondem aos reduzida a seguir `msg-id`.

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) fornece o cabeçalho Content-Transfer-Encoding para comunicar a codificação do conteúdo da parte MIME. O padrão definido para o Content-Transfer-Encoding é de 7 bits, que não é adequado para a maioria das mensagens SOAP, portanto, o cabeçalho Content-Transfer-Encoding é necessária para uma interoperabilidade maior:

- R4145: A parte de Infoset de SOAP deve conter o cabeçalho Content-Transfer-Encoding.

- R4146: Se a codificação de caracteres do Envelope SOAP é UTF-8, o valor do cabeçalho Content-Transfer-Encoding deve ser 8 bits.

- R4147: Se a codificação de caracteres do Envelope SOAP é UTF-16, o valor do cabeçalho Content-Transfer-Encoding deve ser binário.

- [XOP] seção 5, de acordo com

- R4148: Parte de Infoset SOAP1.1 deve conter o cabeçalho Content-Type com o tipo de mídia application/xop + xml e parâmetros de tipo = "text/xml" e o conjunto de caracteres

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: A parte de SOAP 1.2 Infoset deve conter o cabeçalho Content-Type com o tipo de mídia `application/xop+xml` e digite parâmetros = "`application/soap+xml`" e `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Enquanto XOP define o `charset` parâmetro para `application/xop+xml` para que sejam opcionais, ela é necessária para interoperabilidade semelhante para o requisito de BP 1.1 a `charset` parâmetro para o `text/xml` tipo de mídia.

- R41410: O `type` e `charset` parâmetros devem estar presentes no cabeçalho Content-Type da parte de Infoset de 1.x de SOAP.

#### <a name="wcf-endpoint-support-for-mtom"></a>Suporte de ponto de extremidade do WCF para MTOM
A finalidade do MTOM é codificar uma mensagem SOAP para otimizar o dados codificados em base64. A seguir está uma lista de restrições:

- R4151: Qualquer item de informações do elemento que contém dados codificados em base64 que pode ser otimizada.

- B4152: WCF otimiza os itens de informações do elemento que contêm dados codificados em base64 e excederem 1.024 bytes de comprimento.

Um ponto de extremidade do WCF configurado para usar MTOM sempre enviarão mensagens codificadas por MTOM. Mesmo que nenhuma parte atendem aos critérios necessários, a mensagem é ainda codificada por MTOM (serializado como um pacote MIME com uma única parte MIME que contém o envelope SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Asserção do WS-Policy para MTOM
Para indicar o uso MTOM pelo ponto de extremidade, o WCF usa a seguinte declaração de política:

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- R4211: A declaração de política anterior tem um assunto de política de ponto de extremidade e especifica que todas as mensagens enviadas e recebidas do ponto de extremidade devem ser otimizadas usando MTOM.

- B4212: Quando configurado para usar a otimização MTOM, um ponto de extremidade do WCF adiciona uma declaração de política de MTOM à política de anexado ao correspondente `wsdl:binding`.

### <a name="composition-with-ws-security"></a>Composição com o WS-Security
MTOM é um mecanismo de codificação que é semelhante ao `text/xml` e XML binário do WCF. MTOM oferece composição natural com o WS-Security e outros WS-* protocolos: uma mensagem protegida usando o WS-Security pode ser otimizada usando MTOM.

### <a name="examples"></a>Exemplos

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 mensagem codificada usando MTOM

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>WCF seguro SOAP 1.2 a mensagem codificada usando MTOM
Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 é protegida usando o WS-Security. As partes binárias identificadas para codificação é o conteúdo do `BinarySecurityToken`, `CipherValue` da `EncryptedData` correspondente à assinatura criptografada e criptografado do corpo. Observe que o `CipherValue` do `EncryptedKey` não foi identificada para otimização pelo WCF, porque seu tamanho é menor, em seguida, 1.024 bytes.

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml"; 
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```
