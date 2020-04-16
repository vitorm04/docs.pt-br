---
title: Protocolos de mensagens
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463826"
---
# <a name="messaging-protocols"></a>Protocolos de mensagens

A pilha de canais da Windows Communication Foundation (WCF) emprega canais de codificação e transporte para transformar a representação de mensagens internas em seu formato de fio e enviá-la usando um transporte específico. O transporte mais comum usado para interoperabilidade de serviços Web é http, e as codificações mais comuns usadas pelos serviços da Web são SOAP 1.1, SOAP 1.2 e Message Transmission Optimization Mechanism (MTOM).

Este tópico abrange detalhes de implementação do <xref:System.ServiceModel.Channels.HttpTransportBindingElement>WCF para os seguintes protocolos empregados por .

Especificação/documento:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Seção 7
- [ENCASABÃO 1.2 HTTP Vinculação](https://www.w3.org/TR/soap12-part2) Seção 7

Este tópico abrange detalhes de implementação <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do WCF para os seguintes protocolos que e empregam.

Especificação/Documento:

- [XML](https://www.w3.org/TR/REC-xml)
- [SABÃO 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SABÃO 1.2 Núcleo](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Services Endereçando 1.0 - Núcleo](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Services Endereçando 1.0 - Encadernamento soap](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Web Services Endereçando 1.0 - WSDL Binding](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Services Endereçando 1.0 - Metadados](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP1.1 Vinculação](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP1.2 Vinculação](https://www.w3.org/Submission/wsdl11soap12/)

Este tópico abrange detalhes de implementação <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do WCF para os seguintes protocolos que empregam.

Especificação/documento:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SABÃO 1.2 Ligação](https://www.w3.org/TR/soap12-mtom/)
- [SABÃO MTOM 1.1 Ligação](https://www.w3.org/Submission/soap11mtom10/)
- [Afirmação da política do MTOM WS](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico:

| Prefixo | Identificador de recursos uniforme sinuoso (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| Wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| Dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SABÃO 1.1 e SABÃO 1.2

### <a name="envelope-and-processing-model"></a>Modelo de Envelope e Processamento
O WCF implementa o processamento de envelopes SOAP 1.1 seguindo o Perfil Básico 1.1 (BP11) e o Perfil Básico 1.0 (SSBP10). O processamento do envelope SOAP 1.2 é implementado após o SOAP12-Part1.

Esta seção explica certas escolhas de implementação tomadas pelo WCF em relação ao BP11 e AO SOAP12-Part1.

#### <a name="mandatory-header-processing"></a>Processamento obrigatório do cabeçalho
O WCF segue as regras `mustUnderstand` para o processamento de cabeçalhos marcados nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.

Uma mensagem que entra na pilha de canais WCF é processada por canais individuais configurados por elementos de vinculação associados, por exemplo, Codificação de Mensagens de Texto, Segurança, Mensagens Confiáveis e Transações. Cada canal reconhece cabeçalhos do namespace associado e os marca como entendidos. Uma vez que uma mensagem entra no despachante, a matéria-chave de operação lê cabeçalhos esperados pelo contrato de mensagem/operação correspondente e os marca compreendidos. Em seguida, o despachante verifica se quaisquer `mustUnderstand` cabeçalhos restantes não são compreendidos, mas marcados como e lança uma exceção. As mensagens `mustUnderstand` que contêm cabeçalhos direcionados ao destinatário não são processadas pelo código do aplicativo destinatário.

Esse processamento em camadas permite a separação entre camadas de infra-estrutura e camadas de aplicação do nó SOAP:

- B1111: Cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pela pilha de canais de infra-estrutura WCF, mas antes de ser processada por aplicativo

     O `mustUnderstand` valor do cabeçalho difere entre SOAP 1.1 e SOAP 1.2. O Perfil Básico 1.1 exige que o `mustUnderstand` valor seja 0 ou 1 para mensagens SOAP 1.1. Soap 1.2 permite 0, `false` `true` 1, e como valores, mas recomenda `xs:boolean` emitir`false` `true`uma representação canônica de valores (, ).

- B1112: O WCF emite `mustUnderstand` valores 0 e 1 para as versões SOAP 1.1 e SOAP 1.2 do envelope SOAP. O WCF aceita todo `xs:boolean` o `mustUnderstand` espaço de valor `false`do `true`cabeçalho (0, 1, )

#### <a name="soap-faults"></a>Falhas de sabÃO
A seguir está uma lista de implementações de falha SOAP específicas do WCF.

- B2121: O WCF retorna os seguintes `s11:mustUnderstand`códigos de falha SOAP 1.1: , `s11:Client`e `s11:Server`.

- B2122: O WCF retorna os seguintes `s12:MustUnderstand`códigos de falha SOAP 1.2: , `s12:Sender`e `s12:Receiver`.

### <a name="http-binding"></a>Vinculação HTTP

#### <a name="soap-11-http-binding"></a>ENCASABÃO 1.1 HTTP Vinculação
O WCF implementa a vinculação SOAP1.1 HTTP seguindo a seção de especificação perfil básico 3.4 com os seguintes esclarecimentos:

- B2211: O serviço WCF não implementa o redirecionamento das solicitações HTTP POST.

- B2212: Os clientes WCF suportam cookies HTTP de acordo com 3.4.8.

#### <a name="soap-12-http-binding"></a>ENCASABÃO 1.2 HTTP Vinculação
O WCF implementa a vinculação SOAP 1.2 HTTP conforme descrito na especificação SOAP 1.2-part 2 (SOAP12Part2) com os seguintes esclarecimentos.

O SOAP 1.2 introduziu um `application/soap+xml` parâmetro de ação opcional para o tipo de mídia. Este parâmetro é útil para otimizar o envio de mensagens sem exigir que o corpo da mensagem SOAP seja analisado quando o WS-Addressing não for usado.

- R2221: `application/soap+xml` O parâmetro de ação, quando presente em uma `soapAction` solicitação SOAP `wsoap12:operation` 1.2, deve corresponder ao atributo no elemento dentro da ligação WSDL correspondente.

- R2222: `application/soap+xml` O parâmetro de ação, quando presente em uma `wsa:Action` mensagem SOAP 1.2, deve corresponder quando ws-endereçamento 2004/08 ou WS-Endereçamento 1.0 são usados.

Quando o WS-Endereçamento é desativado e uma solicitação `Action` recebida não contém um parâmetro de ação, a mensagem é considerada não especificada.

## <a name="ws-addressing"></a>WS-Addressing
O WCF implementa 3 versões do WS-Addressing:

- WS-Addressing 2004/08

- Serviços web W3C endereçando núcleo 1.0 (ADDR10-CORE) e encadernamento de sabão (ADDR10-SOAP)

- WS-Addressing 1.0 - Metadados

### <a name="endpoint-references"></a>Referências de ponto final
Todas as versões do WS-Addressing que o WCF implementa usam referências de ponto final para descrever pontos finais.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Referências de ponto final e versões endereçadas ao WS
O WCF implementa vários protocolos de infra-estrutura que usam `EndpointReference` o `W3C.WsAddressing.EndpointReferenceType` WS-Addressing e, em particular, o elemento e a classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust). O WCF suporta o uso de qualquer versão do WS-Addressing com outros protocolos de infra-estrutura. Os pontos finais do WCF suportam uma versão do WS-Addressing por ponto final.

Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um ponto final WCF deve corresponder à versão do WS-Addressing implementada por este ponto final.

Por exemplo, se um ponto final do WCF implementar `AcksTo` o WS-ReliableMessaging, o cabeçalho retornado por um ponto final dentro `CreateSequenceResponse` usará a versão WS-Endereçamento que o `EncodingBinding` elemento especifica para este ponto final.

#### <a name="endpoint-references-and-metadata"></a>Referências e metadados de ponto final
Uma série de cenários requerem a comunicação de metadados ou uma referência a metadados para um determinado ponto final.

B3121: O WCF emprega mecanismos descritos na seção 6 de especificação WS-MetadataExchange (MEX) para incluir metadados para referências de ponto final por valor ou por referência.

Considere um cenário em que um serviço WCF requer autenticação usando um token SAML (Security `http://sts.fabrikam123.com`Assertions Markup Language, linguagem de marcação de afirmações de segurança) emitido pelo emissor de token em . O ponto final do WCF descreve `sp:IssuedToken` esse requisito de `sp:Issuer` autenticação usando a afirmação com uma afirmação aninhada apontando para o emissor de token. Os aplicativos clientes `sp:Issuer` que acessam a afirmação precisam saber como se comunicar com o ponto final do emissor do token. O cliente precisa saber metadados sobre o emissor de tokens. Usando as extensões de metadados de referência de ponto final definidas no MEX, o WCF fornece uma referência aos metadados do emissor de token.

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

### <a name="message-addressing-headers"></a>Endereçamento de mensagens cabeçalhos

#### <a name="message-headers"></a>Cabeçalhos da mensagem
Para ambas as versões WS-Addressing, o WCF usa `wsa:To` `wsa:ReplyTo`os `wsa:Action` `wsa:MessageID`seguintes cabeçalhos de mensagem conforme prescrito pelas especificações, e `wsa:RelatesTo`.

B3211: Para todas as versões ws-addressing, wcf honras, mas não produz `wsa:FaultTo` fora `wsa:From`da caixa, ws-addressing cabeçalhos de mensagem e .

Os aplicativos que interagem com aplicativos WCF podem adicionar esses cabeçalhos de mensagem e o WCF irá processá-los de acordo.

#### <a name="reference-parameters-and-properties"></a>Parâmetros e propriedades de referência

O WCF implementa o processamento de parâmetros de referência de ponto final e propriedades de referência de acordo com as respectivas especificações.

B3221: Quando configurados para usar o WS-Endereçamento 2004/08, os pontos finais do WCF não diferenciam entre o processamento de propriedades de referência e parâmetros de referência.

### <a name="message-exchange-patterns"></a>Padrões de troca de mensagens
A seqüência de mensagens envolvidas na invocação da operação de serviço web é referida como o padrão de *troca de mensagens*. O WCF suporta padrões de troca de mensagens unidirecionais, de solicitação e de troca de mensagens duplex. Esta seção esclarece os requisitos de Endereçamento do WS no processamento de mensagens, dependendo do padrão de troca de mensagens que está sendo usado.

Ao longo desta seção, o solicitante envia a primeira mensagem e o respondente recebe a primeira mensagem.

#### <a name="one-way-message"></a>Mensagem unidirecional
Quando um ponto final do WCF é configurado para suportar mensagens com um dado `Action` para seguir um padrão unidirecional, o ponto final do WCF segue os seguintes comportamentos e requisitos. A menos que especificado de outra forma, comportamentos e regras se aplicam a ambas as versões do WS-Addressing suportado no WCF:

- R3311: O solicitante `wsa:To`deve `wsa:Action`incluir , e cabeçalhos para todos os parâmetros de referência especificados pela referência do ponto final. Quando o WS-Addressing 2004/08 for usado e [propriedades de referência] forem especificadas pela referência do ponto final, os cabeçalhos correspondentes também devem ser adicionados à mensagem.

- B3312: O solicitante `MessageID`pode `ReplyTo`incluir `FaultTo` , e cabeçalhos. A infra-estrutura do receptor irá ignorá-los, e eles serão passados para o aplicativo.

- R3313: Quando http é usado e nenhuma mensagem está sendo enviada na perna de resposta HTTP, o respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.

     Quando o transporte HTTP estiver em uso e o contrato de operação declarar uma mensagem unidirecional, a resposta HTTP `SequenceAcknowledgement` ainda pode ser usada para enviar mensagens de infra-estrutura — por exemplo, mensagens confiáveis podem enviar uma mensagem em uma resposta HTTP.

- B3314: O respondente do WCF não envia uma mensagem de falha em resposta a uma mensagem unidirecional.

#### <a name="request-reply"></a>Solicitação-resposta
Quando um ponto final do WCF é `Action` configurado para uma mensagem com um dado para seguir o padrão de solicitação-resposta, o ponto final do WCF segue os comportamentos e requisitos abaixo. A menos que especificado em contrário, comportamentos e regras se aplicam a ambas as versões do WS-Addressing suportado no WCF:

- R3321: O solicitante deve incluir `wsa:To` `wsa:Action`na `wsa:MessageID`solicitação , e cabeçalhos para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela referência do ponto final.

- R3322: Quando o WS-Endereçamento 2004/08 for usado, `ReplyTo` também deve ser incluído na solicitação.

- R3323: Quando o WS-Endereçamento `ReplyTo` 1.0 é usado e não está presente na solicitação, uma referência de ponto final padrão com a propriedade [endereço] igual a `http://www.w3.org/2005/08/addressing/anonymous` é usada.

- R3324: O solicitante `wsa:To`deve `wsa:Action`incluir `wsa:RelatesTo` , e cabeçalhos na mensagem de resposta, bem como cabeçalhos para todos os parâmetros de referência ou propriedades de referência (ou ambos) especificados pela referência de `ReplyTo` ponto final na solicitação.

### <a name="web-services-addressing-faults"></a>Serviços web abordando falhas
R3411: O WCF produz as seguintes falhas definidas pelo WS-Addressing 2004/08.

| Código | Causa |
|----------|-----------|
| `wsa:DestinationUnreachable` | A mensagem `ReplyTo` chegou com um que é diferente do endereço de resposta estabelecido para este canal; não há ponto final ouvindo o endereço especificado no cabeçalho Para. |
| `wsa:ActionNotSupported` | os canais de infra-estrutura ou despachante associados ao `Action` ponto final não reconhecem a ação especificada no cabeçalho. |

R3412: O WCF produz as seguintes falhas definidas pelo WS-Endereçamento 1.0.

| Código | Causa |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | `wsa:To`Duplicado, `wsa:From` `wsa:ReplyTo` `wsa:MessageID`ou . Duplicata `wsa:RelatesTo` `RelationshipType`com o mesmo . |
| `wsa10:MessageAddressingHeaderRequired` | O cabeçalho de endereçamento necessário está faltando. |
| `wsa10:DestinationUnreachable` | A mensagem `ReplyTo` chegou com um que é diferente do endereço de resposta estabelecido para este canal. Não há ponto final ouvindo o endereço especificado no cabeçalho Para. |
| `wsa10:ActionNotSupported` | Uma ação especificada `Action` no cabeçalho não é reconhecida pelos canais de infra-estrutura ou pelo despachante associado ao ponto final. |
| `wsa10:EndpointUnavailable` | O canal RM envia essa falha de volta, indicando que o `CreateSequence` ponto final não processará a seqüência com base no exame dos cabeçalhos endereçados da mensagem. |

Código nas tabelas `FaultCode` anteriores mapas para `SubCode` em SOAP 1.1 e (com Code=Sender) em SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>Afirmações de política de vinculação e ws-saque a wsdl 1.1

#### <a name="indicating-use-of-ws-addressing"></a>Indicando o uso do WS-Addressing
O WCF usa as afirmações de diretiva para indicar o suporte ao ponto final para uma versão específica do WS-Addressing.

A seguinte afirmação de política tem Endpoint Policy Subject [WS-PA] e indica que as mensagens enviadas e recebidas do ponto final devem usar o WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

Esta afirmação de política aumenta a especificação WS-Addressing 2004/08.

A seguinte afirmação de diretiva indica que as mensagens enviadas/recebidas devem usar o WS-Endereçamento 1.0.

```xml
<wsam:Addressing/>
```

A seguinte afirmação de diretiva tem um Assunto de Diretiva de Ponto Final [WS-PA] e indica que as mensagens enviadas e recebidas do ponto final devem usar o WS-Addressing 2004/08.

```xml
<wsaw10:UsingAddressing />
```

O `wsaw10:UsingAddressing` elemento é emprestado de [WS-Addressing-WSDL] e é usado no contexto da WS-Policy em conformidade com essa especificação, seção 3.1.2.

O uso de Endereçamento não altera a semântica das ligações WSDL 1.1, SOAP 1.1 e SOAP 1.2 HTTP. Por exemplo, se uma resposta for esperada para uma solicitação enviada para um ponto final que usa endereçamento e vinculação WSDL SOAP 1.x HTTP, a resposta deve ser enviada usando a resposta HTTP.

Para respostas enviadas pela resposta http, a afirmação do WS-AM é:

```xml
<wsam:AnonymousResponses/>
```

A afirmação completa da política pode ser assim:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

No entanto, existem padrões de troca de mensagens que se beneficiam de ter duas conexões HTTP independentes estabelecidas entre o solicitante e o respondente, por exemplo, mensagens de mão única não solicitadas enviadas pelo respondente.

O WCF oferece um recurso pelo qual dois canais de transporte subjacentes podem formar um canal Duplex Composto, onde um canal é usado para mensagens de entrada e o outro é usado para mensagens de saída. No caso do TRANSPORTE HTTP, o Composto Duplex fornece duas conexões HTTP inversas. O solicitante usa uma conexão para enviar mensagens ao respondente, e o respondente usa a outra para enviar mensagens de volta ao solicitante.

Para respostas enviadas por solicitações http separadas, a afirmação ws-am é

```xml
<wsam:NonAnonymousResponses/>
```

A afirmação completa da política pode ser assim:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

O uso da seguinte afirmação que tem O Assunto da Política de Ponto Final [WS-PA] em pontos finais que usam as vinculações WSDL 1.1 SOAP 1.x HTTP requer duas conexões HTTP inversas separadas para serem usadas para mensagens que fluem do solicitante para responder e responder ao solicitante, respectivamente.

```xml
<cdp:CompositeDuplex/>
```

A declaração anterior leva aos `wsa:ReplyTo` seguintes requisitos no cabeçalho para mensagens de solicitação:

- R3514: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous` final devem ter um cabeçalho com a propriedade não igual a se `wsap10:UsingAddressing` o `wsap:UsingAddressing` ponto `cdp:CompositeDuplex` final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com uma ou afirmação acoplada à anexada.

- R3515: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous`final devem `ReplyTo` ter um cabeçalho com a propriedade igual ou não ter um cabeçalho, `wsap10:UsingAddressing` se o `cdp:CompositeDuplex` ponto final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com afirmação e nenhuma afirmação anexada.

- R3516: As mensagens de solicitação enviadas `ReplyTo` a `[address]` um ponto `http://www.w3.org/2005/08/addressing/anonymous` final devem ter um cabeçalho com uma propriedade igual a se `wsap:UsingAddressing` o ponto `cdp:CompositeDuplex` final usar uma vinculação WSDL 1.1 SOAP 1.x HTTP e tiver uma alternativa de política com afirmação e nenhuma afirmação anexada.

A especificação WSDL que trata do WSDL tenta descrever `<wsaw:Anonymous/>` vinculações de protocolo semelhantes introduzindo um elemento com `wsa:ReplyTo` três valores textuais (necessários, opcionais e proibidos) para indicar requisitos no cabeçalho (seção 3.2). Infelizmente, tal definição de elemento não é particularmente utilizável como uma afirmação no contexto da WS-Policy, porque requer extensões específicas de domínio para apoiar a intersecção de alternativas usando tal elemento como uma afirmação. Essa definição de elemento também `ReplyTo` indica o valor do cabeçalho em oposição ao comportamento do ponto final no fio, o que o torna específico para o transporte HTTP.

#### <a name="action-definition"></a>Definição de Ação
WS-Addressing 2004/08 define `wsa:Action` um `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` atributo para os elementos. WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) define `wsaw10:Action`um atributo semelhante, .

A única diferença entre os dois é a semântica padrão de padrão de ação descrita na seção 3.3.2 do WS-ADDR e na seção 4.4.4 do WS-ADDR10-WSDL, respectivamente.

É razoável ter dois pontos finais que `portType` compartilham o mesmo (ou contrato, na terminologia wcf), mas usando versões diferentes do WS-Addressing. Mas dado que a `portType` Ação é definida pelo e `portType`não deve mudar entre os pontos finais que implementam o , torna-se impossível suportar ambos os padrões de ação padrão.

Para resolver essa controvérsia, o WCF suporta `Action` uma única versão do atributo.

B3521: O WCF usa o atributo `wsaw10:Action` em `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos definidos no WS-ADDR10-WSDL para determinar o `Action` URI para as mensagens correspondentes, independentemente da versão WS-Endereçamento usada pelo ponto final.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Use a referência de ponto final dentro da porta WSDL
A seção 4.1 WS-ADDR10-WSDL estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto final nos termos de endereçamento de WS. O WCF expande esse utilitário no WS-Addressing 2004/08, permitindo `<wsa:EndpointReference…/>` aparecer como um elemento infantil de `wsdl:port`.

- R3531: Se um ponto final tiver uma `<wsaw10:UsingAddressing/>` alternativa de `wsdl:port` política anexada com `<wsa10:EndpointReference …/>`uma afirmação de política, o elemento correspondente pode conter um elemento filho .

- R3532: Se `wsdl:port` a contém `<wsa10:EndpointReference …/>`um `wsa10:EndpointReference/wsa10:Address` elemento filho, o valor `@address` do elemento `wsdl:port` / `wsdl:location` filho deve corresponder ao valor do atributo do elemento irmão.

- R3533: Se um ponto final tiver `<wsap:UsingAddressing/>` uma alternativa de `wsdl:port` política anexada `<wsa:EndpointReference …/>`com a afirmação da política, o elemento correspondente pode conter um elemento filho .

- R3534: Se `wsdl:port` a contém `<wsa:EndpointReference …/>`um `wsa:EndpointReference/wsa:Address` elemento filho, o valor `@address` do elemento `wsdl:port` / `wsdl:location` filho deve corresponder ao valor do atributo do elemento irmão.

### <a name="composition-with-ws-security"></a>Composição com WS-Security
De acordo com as seções de consideração de segurança no WS-ADDR e ws-ADDR10, todos os cabeçalhos de mensagem endereçados são recomendados a serem assinados juntamente com o corpo de mensagens para amarrá-los juntos.

Quando o WS-Security for usado para proteção da integridade da mensagem, os cabeçalhos de mensagem que endereçam o WS, bem como os cabeçalhos resultantes de parâmetros de referência ou propriedades (ou ambos) devem ser assinados juntamente com o corpo da mensagem.

### <a name="examples"></a>Exemplos

#### <a name="one-way-message"></a>Mensagem unidirecional
Neste cenário, o remetente envia uma mensagem de mão única para o receptor. SOAP 1.2, HTTP 1.1 e W3C WS-Addressing 1.0 são usados.

A estrutura da mensagem de `wsa10:To` `wsa10:Action` solicitação: os cabeçalhos de mensagem incluem e elementos. O corpo da mensagem inclui um elemento específico `<app:Ping>` do namespace do aplicativo.

Cabeçalhos HTTP: O destino no `wsa10:To` POST corresponde ao URI no elemento.

O cabeçalho tipo de `application/soap+xml` conteúdo tem o valor do que é exigido pelo SOAP 1.2. `charset` Parâmetros `action` e estão incluídos. O `action` parâmetro do cabeçalho tipo de `wsa10:Action` conteúdo corresponde ao valor do cabeçalho da mensagem.

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

O receptor responde com uma resposta HTTP vazia e status 202. Um exemplo da resposta HTTP:

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

## <a name="soap-message-transmission-optimization-mechanism"></a>Mecanismo de otimização de transmissão de mensagens soap
Esta seção descreve os detalhes de implementação do WCF para o HTTP SOAP MTOM. A tecnologia MTOM é o mecanismo de codificação de mensagens SOAP da mesma classe que a codificação de texto/XML tradicional ou codificação binária WCF. MTOM inclui o seguinte:

- Um mecanismo de codificação e embalagem XML descrito por [XOP] que otimiza os itens de informações XML contendo dados binários codificados base64 em partes binárias separadas.

- Um encapsulamento MIME do pacote XOP que serializa o Infoset XML e cada parte binária do pacote XOP em uma parte MIME separada.

- Uma codificação MIME XOP aplicada ao ENVELOPE SOAP 1.x.

- Uma vinculação de transporte HTTP.

É possível usar MTOM com transportes não-HTTP com WCF. No entanto, neste tópico vamos focar em HTTP.

O formato MTOM aproveita um grande conjunto de especificações que abrangem o próprio MTOM, XOP e MIME. A modularidade deste conjunto de especificações torna um pouco difícil reconstruir os requisitos exatos sobre o formato e a semântica de processamento. Esta seção descreve os requisitos de formato e processamento para a vinculação MTOM HTTP.

### <a name="mtom-message-encoding"></a>Codificação de mensagens MTOM

#### <a name="generating-mtom-messages"></a>Gerando mensagens MTOM
A seção [XOP] 3.1 descreve o processo de codificação xml com itens de informações de elementoque contêm valores base64 em um pacote XOP definido abstratamente.

A seqüência de etapas a seguir descreve o processo de codificação específico do MTOM:

1. Certifique-se de que o envelope SOAP a ser `[namespace name]` codificado não contém nenhum item de informação de elemento com um de `http://www.w3.org/2004/08/xop/include` e a `[local name]` de `Include`.

2. Crie um pacote MIME vazio.

3. Identifique dentro do Conjunto de informações XML original os itens de informações do elemento a serem otimizados. Para que os itens sejam otimizados, os `[children]` caracteres que compõem o item de `xs:base64Binary` informação do elemento devem estar na forma canônica de (ver XSD-2, 3.2.16 base64Binary) e não devem conter nenhum caractere de espaço branco anterior, em linha ou seguindo o conteúdo não-espaço branco.

4. Crie um envelope xop soap que seja uma cópia do envelope SOAP original, mas com os filhos `xop:Include` de cada item de informações de elemento identificados na etapa anterior substituído por um item de informações de elemento construído da seguinte forma:

    1. Transforme os caracteres substituídos em dados binários processando-os como dados codificados pela base64.

    2. Gerar um valor de cabeçalho exclusivo de ID de conteúdo que satisfaça os requisitos R3133 e R3134.

    3. Gerar um cabeçalho MIME de codificação de transferência de conteúdo com o binário de valor.

    4. Se o item de informações de elemento sotimizar `xop:Include` (o [pai] `xmime:contentType` do item de informações de elemento recém-inserido) `xmime:contentType` tiver um item de informações de atributo, gerare um cabeçalho MIME tipo de conteúdo com o valor do atributo.

    5. Gerar uma nova parte mime binária com conteúdo formado por dados binários decodificados a partir dos caracteres substituídos processados como base64, cabeçalho de ID de conteúdo a partir de 4b, cabeçalho de codificação de conteúdo a partir de 4c, cabeçalho tipo de conteúdo se gerado na etapa 4d.

    6. Adicione `href` um atributo ao `xop:Include` elemento com o valor cid: uri derivado do valor de cabeçalho de ID de conteúdo gerado na etapa 4b. Remova os caracteres\<"" e ">", escape da seqüência `cid:`de URL e adicione o prefixo . O seguinte conjunto mínimo de caracteres é necessário para ser escapado por RFC1738 e RFC2396. Outros personagens podem ser escapados.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Crie uma parte MIME raiz com o envelope xop soap do passo 4.

6. Escreva os cabeçalhos HTTP, incluindo o cabeçalho HTTP Tipo de conteúdo.

7. Escreva o pacote MIME.

#### <a name="processing-mtom-messages"></a>Processamento de mensagens MTOM
O processamento de uma mensagem MTOM é o inverso exato do processo descrito na seção anterior "Gerando mensagens MTOM":

1. Certifique-se de que a parte `application/xop+xml`RAIZ MIME tenha o Tipo de Conteúdo .

2. Construa um envelope SOAP analisando a parte mime raiz do pacote como um documento XML. A codificação de `charset` caracteres é determinada pelo parâmetro do Tipo de conteúdo da parte MIME raiz.

3. Para cada item de informação de elemento no envelope SOAP construído, que tem, `xop:Include` como único membro de sua propriedade [crianças], um item de informação de elemento:

    1. Remova `cid:` o prefixo e o inescapar todas as seqüências de `@href` saída `xop:Include` uri (RFC 2396) no valor do atributo do elemento. Enclose a seqüência de resultado em "\<", ">".

    2. Localize a parte MIME com o valor de cabeçalho De ID de conteúdo que corresponde à seqüência derivada na etapa 3a.

    3. Substitua `xop:Include` o item de `children` informação do elemento que aparece na propriedade de cada item pelos itens de informação de caractereque representam a codificação base64 canônica (ver XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificada na etapa 3b (substitua efetivamente o item de informações do `xop:Include` elemento pelos dados reconstruídos a partir da peça do pacote).

#### <a name="http-content-type-header"></a>Cabeçalho do tipo de conteúdo HTTP
A seguir está uma lista de esclarecimentos wcf para o formato do cabeçalho HTTP Tipo de conteúdo de uma mensagem codificada SOAP 1.x MTOM derivada de requisitos indicados na própria especificação MTOM e são derivados de MTOM e RFC 2387.

- R4131: Um cabeçalho HTTP Tipo de conteúdo deve ter o valor de multiparte/relacionado (insensível a casos) e seus parâmetros. Nomes de parâmetros são insensíveis a casos. A ordem dos parâmetros não é significativa.

- O formulário backus-naur completo (BNF) do cabeçalho tipo de conteúdo para mensagens MIME está listado no RFC 2045, seção 5.1.

- R4132: Um cabeçalho HTTP Tipo de conteúdo `application/xop+xml` deve ter um parâmetro de tipo com o valor incluído entre aspas duplas.

Embora a exigência de usar aspas duplas não esteja explícita no RFC 2387, o texto observa que todos\@os parâmetros de tipo de mídia multiparte/relacionado provavelmente contêm caracteres reservados como " " ou "/" e, portanto, precisam de aspas duplas.

- R4133: Um cabeçalho HTTP Tipo de conteúdo deve ter um parâmetro inicial com o valor do cabeçalho de Identificação de Conteúdo da parte MIME que contém o Envelope SOAP 1.x, incluído em aspas duplas. Se o parâmetro de partida for omitido, a primeira parte MIME deve conter o envelope SOAP 1.x.

- R4134: Um cabeçalho http tipo de conteúdo para uma mensagem codificada SOAP 1.1 MTOM deve incluir o parâmetro start-info com o valor de texto/xml, incluído em aspas duplas.

- R4135: Um cabeçalho http tipo de conteúdo para uma mensagem codificada em SOAP 1.2 MTOM deve incluir o parâmetro start-info com o valor de `application/soap+xml`, incluído em aspas duplas.

- R4136: O cabeçalho http tipo de conteúdo para uma mensagem codificada por SOAP 1.x MTOM deve ter o parâmetro de limite com o valor (incluído entre aspas duplas) que corresponde ao limite MIME BNF definido na RFC 2046, seção 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Exemplos:

     Correto

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     Correto

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     Incorreto

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Peça MIME infoset
O envelope SOAP 1.x é encapsulado como uma parte raiz do `infoset` pacote XOP MIME e é frequentemente chamado de peça.

- R4141: O envelope SOAP 1.x deve ser encapsulado como parte raiz `infoset` do pacote XOP MIME, chamado de peça e referenciado a partir do Tipo de Conteúdo HTTP.

- R4142: A `Infoset` parte SOAP deve incluir os `Content-ID` `Content-Transfer-Encoding`seguintes `Content-Type`cabeçalhos MIME: , e .

O formato do cabeçalho de ID de conteúdo é definido pela RFC 2045 como

```
"Content-ID" ":" msg-id
```

onde `msg-id` é definido na RFC 2822 (que substitui o RFC 822, referenciado na RFC 2045) como:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

e é efetivamente um endereço\<de e-mail incluído dentro " " e ">". O `[CFWS]` prefixo e o sufixo foram adicionados na RFC 2822 para realizar comentários e não devem ser usados para preservar a interoperabilidade.

R4143: O valor do cabeçalho de ID de `msg-id` conteúdo para a peça Infoset `[CFWS]` MIME deve seguir a produção da RFC 2822 com as peças de prefixo e sufixo omitidas.

Uma série de implementações do MIME afrouxavam os requisitos para o valor incluído dentro "\<e ">" para ser um endereço de e-mail e usado `absoluteURI` em " "\<" " " " " " " " " " " " " " " ">" além do endereço de e-mail. Esta versão do WCF usa valores do cabeçalho MIME do Formulário ID de conteúdo:

```
Content-ID: <http://tempuri.org/0>
```

R4144: Os processadores MTOM devem aceitar valores de `msg-id`cabeçalho de ID de conteúdo que correspondam aos seguintes relaxados .

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

O MIME (RFC 2045) fornece o cabeçalho codificador de transferência de conteúdo para comunicar a codificação do conteúdo da parte MIME. O padrão definido para codificação de transferência de conteúdo é de 7 bits, o que não é adequado para a maioria das mensagens SOAP, de modo que o cabeçalho de codificação de transferência de conteúdo é necessário para maior interoperabilidade:

- R4145: A parte do SOAP Infoset deve conter o cabeçalho codificador de transferência de conteúdo.

- R4146: Se a codificação do caractere SOAP Envelope for UTF-8, o valor do cabeçalho codificador de transferência de conteúdo deve ser de 8 bits.

- R4147: Se a codificação do caractere SOAP Envelope for UTF-16, o valor do cabeçalho codificador de transferência de conteúdo deve ser binário.

- De acordo com a seção 5 da [XOP],

- R4148: SOAP1.1 A parte do infoset deve conter cabeçalho tipo de conteúdo com aplicativo do tipo de mídia/xop+xml e parâmetros tipo="texto/xml" e charset

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: A parte DO INFOSET SOAP 1.2 deve `application/xop+xml` conter o cabeçalho tipo de conteúdo com tipo de mídia e tipo de parâmetros="`application/soap+xml`e `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Embora o XOP `charset` defina `application/xop+xml` o parâmetro para ser opcional, é necessário para interoperabilidade `charset` semelhante ao `text/xml` requisito BP 1.1 no parâmetro para o tipo de mídia.

- R41410: `type` Os `charset` parâmetros devem estar presentes no cabeçalho tipo de conteúdo da peça SOAP 1.x Infoset.

#### <a name="wcf-endpoint-support-for-mtom"></a>Suporte ao ponto final do WCF para MTOM
O objetivo do MTOM é codificar uma mensagem SOAP para otimizar dados codificados com base64. A seguir está uma lista de restrições:

- R4151: Qualquer item de informação de elemento que contenha dados codificados com base64 pode ser otimizado.

- B4152: O WCF otimiza itens de informação de elementos que contêm dados codificados base64 e excedem 1024 bytes de comprimento.

Um ponto final wcf configurado para usar o MTOM sempre enviará mensagens codificadas pelo MTOM. Mesmo que nenhuma peça atenda aos critérios necessários, a mensagem ainda é codificada em MTOM (serializada como um pacote MIME com uma única peça MIME contendo o envelope SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Afirmação da política WS para MTOM
O WCF usa a seguinte afirmação de diretiva para indicar o uso do MTOM por ponto final:

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211: A afirmação da diretiva anterior tem um Assunto de Política de Ponto Final e especifica que todas as mensagens enviadas e recebidas do ponto final devem ser otimizadas usando o MTOM.

- B4212: Quando configurado para usar a otimização do MTOM, um ponto final do `wsdl:binding`WCF adiciona uma afirmação de diretiva MTOM à diretiva anexada ao correspondente .

### <a name="composition-with-ws-security"></a>Composição com WS-Security
MTOM é um mecanismo de `text/xml` codificação semelhante ao WCF Binary XML. O MTOM oferece composição natural com o WS-Security e outros protocolos WS-*: uma mensagem protegida usando o WS-Security pode ser otimizada usando o MTOM.

### <a name="examples"></a>Exemplos

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 Mensagem Codificada Usando MTOM

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>WCF Secure SOAP 1.2 Mensagem Codificada Usando MTOM
Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 que é protegido usando O WS-Security. As partes binárias identificadas para `BinarySecurityToken` `CipherValue` codificação `EncryptedData` são o conteúdo do , do correspondente à assinatura criptografada e corpo criptografado. Note-se `CipherValue` que `EncryptedKey` o do não foi identificado para otimização pelo WCF, pois seu comprimento é menor que 1024 bytes.

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
