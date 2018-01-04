---
title: Protocolos de mensagens
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 600a1bd57015c6a64a51bf99f3ded35a375e62fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="messaging-protocols"></a>Protocolos de mensagens
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pilha de canais emprega canais de codificação e transporte para transformar a representação interna de mensagem em seu formato de transmissão e enviá-lo usando um transporte particular. O transporte mais comuns usado para interoperabilidade de serviços da Web é HTTP e as codificações mais comuns usadas pelos serviços da Web são baseadas em XML SOAP 1.1, SOAP 1.2 e mecanismo de otimização de transmissão mensagem (MTOM).  
  
 Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos usados pelo <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/RFC/rfc2616.txt|  
|Ligação de SOAP 1.1 HTTP|http://www.w3.org/TR/2000/Note-SOAP-20000508/, seção 7|  
|SOAP 1.2 associação de HTTP|http://www.w3.org/TR/soap12-part2/, seção 7|  
  
 Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos que <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> empregar.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/REC-XML|  
|SOAP 1.1|http://www.w3.org/TR/2000/Note-SOAP-20000508/|  
|SOAP 1.2 Core|http://www.w3.org/TR/soap12-part1/|  
|2004 do WS-Addressing/08|http://www.w3.org/Submission/2004/SUBM-WS-Addressing-20040810/|  
|Endereçamento 1.0 - Core de serviços Web do W3C|http://www.w3.org/TR/2006/rec-WS-addr-Core-20060509|  
|Endereçamento associação SOAP 1.0 - de serviços Web do W3C|http://www.w3.org/TR/2006/rec-WS-addr-SOAP-20060509|  
|Endereçamento associação WSDL 1.0 - de serviços Web do W3C|http://www.w3.org/TR/2006/CR-WS-addr-WSDL-20060529/|  
Endereçamento 1.0 - metadados de serviços Web do W3C|http://www.w3.org/TR/WS-addr-Metadata/|  
|Associação de SOAP1.1 WSDL|http://www.w3.org/TR/WSDL/|  
|Associação de SOAP1.2 WSDL|http://www.w3.org/Submission/wsdl11soap12/|  
  
 Este tópico aborda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para os seguintes protocolos que <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> utiliza.  
  
|Documento de especificação /|Link|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM + SOAP 1.2 associação|http://www.w3.org/TR/soap12-MTOM/|  
|MTOM ligação de SOAP 1.1|http://www.w3.org/Submission/soap11mtom10/|  
|Asserção do WS-Policy MTOM|http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.|  
  
 Os seguintes namespaces XML e prefixos associados são usados ao longo deste tópico.  
  
|Prefixo|Namespace Uniform Resource Identifier (URI)|  
|------------|---------------------------------------------------|  
|S11|http://schemas.xmlsoap.org/SOAP/envelope|  
|/s12|http://www.w3.org/2003/05/SOAP-envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wsam|http://www.w3.org/2007/05/Addressing/Metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|wsaw10|http://www.w3.org/2006/05/Addressing/WSDL|  
|XOP|http://www.w3.org/2004/08/XOP/Include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
ponto de distribuição|http://schemas.microsoft.com/NET/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 e SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>Envelope e processamento de modelo  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa o processamento do envelope SOAP 1.1 Basic Profile 1.1 (BP11) e Basic Profile 1.0 (SSBP10) a seguir. SOAP 1.2 Envelope processamento é implementado Parte1 SOAP12 a seguir.  
  
 Esta seção explica certas opções de implementação realizadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relativas à BP11 e SOAP12 Parte1.  
  
#### <a name="mandatory-header-processing"></a>Processamento de cabeçalho obrigatório  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]segue as regras para processar cabeçalhos marcados `mustUnderstand` descrito nas especificações SOAP 1.1 e SOAP 1.2, com as seguintes variações.  
  
 Uma mensagem que entra o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais é processada pelo canais individuais configurados pelos elementos de associação associada, por exemplo, codificação de mensagem de texto, segurança, mensagens confiáveis e transações. Cada canal reconhece os cabeçalhos do namespace associado e marca-os conforme entendido. Depois que uma mensagem insere o distribuidor, o formatador de operação lê cabeçalhos esperados pelo contrato de mensagem/operação e marcas-los compreendidos correspondente. Em seguida, o distribuidor verifica se todos os cabeçalhos restantes não são compreendidos mas marcados como `mustUnderstand` e lançará uma exceção. As mensagens que contêm `mustUnderstand` cabeçalhos que são destinados ao destinatário não são processados pelo código do aplicativo de destino.  
  
 Como em camadas processamento permite a separação entre camadas de infraestrutura e de aplicativo do nó de SOAP:  
  
-   B1111: Cabeçalhos que não são compreendidos são detectados depois que a mensagem é processada pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais de infraestrutura, mas antes de ser processada por aplicativo  
  
     O `mustUnderstand` difere do valor do cabeçalho entre SOAP 1.1 e SOAP 1.2. Basic Profile 1.1 requer que o `mustUnderstand` valor ser 0 ou 1 para mensagens SOAP 1.1. SOAP 1.2 permite 0, 1, `false`, e `true` como valores, mas recomenda emitindo uma representação canônica `xs:boolean` valores (`false`, `true`).  
  
-   B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emite `mustUnderstand` valores 0 e 1 para versões de SOAP 1.1 e SOAP 1.2 do envelope SOAP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aceita o espaço de valor inteiro de `xs:boolean` para o `mustUnderstand` cabeçalho (0, 1, `false`, `true`)  
  
#### <a name="soap-faults"></a>Falhas de SOAP  
 A seguir está uma lista de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-implementações específicas de falhas SOAP.  
  
-   B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retorna os seguintes códigos de falha de SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, e `s11:Server`.  
  
-   B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retorna os seguintes códigos de falha de SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, e `s12:Receiver`.  
  
### <a name="http-binding"></a>Associação HTTP  
  
#### <a name="soap-11-http-binding"></a>Ligação de SOAP 1.1 HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa a associação HTTP SOAP1.1 após a especificação de Basic Profile 1.1 seção 3.4 com os seguintes esclarecimentos:  
  
-   B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço não implementa o redirecionamento de solicitações HTTP POST.  
  
-   B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] os clientes oferecem suporte a Cookies HTTP conforme 3.4.8.  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 associação de HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa associação SOAP 1.2 HTTP conforme descrito na SOAP 1.2-parte 2 (SOAP12Part2) especificação com as seguintes esclarecimentos.  
  
 SOAP 1.2 introduziu um parâmetro de ação opcional para o `application/soap+xml` tipo de mídia. Esse parâmetro é útil para otimizar a expedição de mensagem sem a necessidade de que o corpo da mensagem SOAP servirá quando WS-Addressing não é usado.  
  
-   R2221: O `application/soap+xml` parâmetro action, quando presente em uma solicitação de SOAP 1.2, deve corresponder a `soapAction` atributo no `wsoap12:operation` elemento de associação WSDL correspondente.  
  
-   R2222: O `application/soap+xml` parâmetro action, quando presente em uma mensagem SOAP 1.2, deve corresponder `wsa:Action` quando 08/2004 do WS-Addressing ou WS-Addressing 1.0 são usados.  
  
 Quando o WS-Addressing é desabilitado e uma solicitação de entrada não contém um parâmetro de ação, uma mensagem `Action` é considerado não especificado.  
  
## <a name="ws-addressing"></a>WS-Addressing.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa 3 versões do WS-Addressing:  
  
-   2004 do WS-Addressing/08  
  
-   Serviços Web do W3C endereçamento SOAP Binding (ADDR10 SOAP) e 1.0 Core (ADDR10 NÚCLEOS)  
  
-   WS-Addressing 1.0 - metadados  
  
### <a name="endpoint-references"></a>Referências de ponto de extremidade  
 Todas as versões do WS-Addressing que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa usa referências de ponto de extremidade para descrever os pontos de extremidade.  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>Referências de ponto de extremidade e WS-Addressing versões  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa vários dos protocolos de infraestrutura que usam o WS-Addressing e, em particular a `EndpointReference` elemento e `W3C.WsAddressing.EndpointReferenceType` classe (por exemplo, WS-ReliableMessaging, WS-SecureConversation e WS-Trust). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte ao uso de qualquer versão do WS-Addressing com outros protocolos de infraestrutura. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]suportam a pontos de extremidade de uma versão do WS-Addressing por ponto de extremidade.  
  
 Para R3111, o namespace para o `EndpointReference` elemento ou tipo usado em mensagens trocadas com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade deve corresponder à versão do WS-Addressing implementada por este ponto de extremidade.  
  
 Por exemplo, se um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade implementa o WS-ReliableMessaging a `AcksTo` retornado por tal um ponto de extremidade dentro do cabeçalho `CreateSequenceResponse` usa a versão do WS-Addressing que o `EncodingBinding` elemento especifica para esse ponto de extremidade.  
  
#### <a name="endpoint-references-and-metadata"></a>Metadados e referências de ponto de extremidade  
 Vários cenários exigem a comunicação de metadados ou uma referência aos metadados para um determinado ponto de extremidade.  
  
 B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emprega mecanismos descritos na especificação do WS-MetadataExchange (MEX), seção 6 para incluir metadados para referências de ponto de extremidade por valor ou por referência.  
  
 Considere um cenário onde um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço requer autenticação usando um token de segurança asserções Markup Language (SAML) emitido pelo emissor de token em http://sts.fabrikam123.com. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade descreve esse requisito de autenticação usando `sp:IssuedToken` asserção com uma instrução `sp:Issuer` asserção apontando para o emissor do token. Aplicativos cliente que acessam o `sp:Issuer` asserção precisam saber como se comunicar com o ponto de extremidade do emissor do token. O cliente precisa saber metadados sobre o emissor do token. Usando as extensões de metadados de referência do ponto de extremidade definidas no MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma referência aos metadados do emissor do token.  
  
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
  
### <a name="message-addressing-headers"></a>Cabeçalhos de endereçamento de mensagem  
  
#### <a name="message-headers"></a>Cabeçalhos de mensagem  
 Para ambas as versões do WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa os seguintes cabeçalhos de mensagem, conforme descrito pelas especificações `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, e `wsa:RelatesTo`.  
  
 B3211: para todas as versões de WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honra, mas não produzir pronta, cabeçalhos de mensagem do WS-Addressing `wsa:FaultTo` e `wsa:From`.  
  
 Aplicativos que interagem com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos podem adicionar esses cabeçalhos de mensagem e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processará adequadamente.  
  
#### <a name="reference-parameters-and-properties"></a>Propriedades e parâmetros de referência  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa o processamento dos parâmetros de referência de ponto de extremidade e referência p  
  
 Propriedades de acordo com as especificações do respectivas.  
  
 B3221: Quando estiver configurado para usar 08/2004 do WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade não fazem distinção entre propriedades de referência e parâmetros de referência de processamento.  
  
### <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 A sequência de mensagens envolvidas na invocação de operação de serviço da Web é conhecida como o *padrão de troca de mensagem*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]padrões de troca unidirecional dá suporte à solicitação-resposta e mensagens duplex. Esta seção explica WS-Addressing requisitos na mensagem de processamento dependendo do padrão de troca de mensagem que está sendo usado.  
  
 Ao longo desta seção, o solicitante envia a primeira mensagem e o respondedor recebe a primeira mensagem.  
  
#### <a name="one-way-message"></a>Mensagem unidirecional  
 Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade é configurado para oferecer suporte a mensagens com um determinado `Action` para seguir o padrão unidirecional, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade segue os requisitos e os comportamentos a seguir. A menos que especificado o contrário, comportamentos e regras se aplicam para ambas as versões do WS-Addressing tem suporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3311: O solicitante deve incluir `wsa:To`, `wsa:Action`e os cabeçalhos para todos os parâmetros de referência especificados pela referência de ponto de extremidade. Quando 08/2004 do WS-Addressing é usado e [Propriedades da referência] são especificados pela referência de ponto de extremidade, os cabeçalhos correspondentes devem ser adicionados à mensagem muito.  
  
-   B3312: O solicitante pode incluir `MessageID`, `ReplyTo`, e `FaultTo` cabeçalhos. A infraestrutura de destinatário irá ignorá-las e eles serão passados para o aplicativo.  
  
-   R3313: Quando HTTP é usado e nenhuma mensagem está sendo enviada no trecho de resposta HTTP, o Respondente deve enviar uma resposta HTTP com um corpo vazio e um código de status HTTP 202.  
  
     Quando o transporte HTTP está em uso e o contrato da operação declara uma mensagem unidirecional, a resposta HTTP ainda pode ser usada para enviar mensagens de infraestrutura — por exemplo, o sistema de mensagens confiável pode enviar um `SequenceAcknowledgement` mensagem em uma resposta HTTP.  
  
-   B3314: O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondente não envia uma mensagem de falha em resposta a uma mensagem unidirecional.  
  
#### <a name="request-reply"></a>Solicitação-resposta  
 Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade é configurado para uma mensagem com um determinado `Action` seguir o padrão de solicitação-resposta, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade segue os comportamentos e os requisitos abaixo. A menos que especificado o contrário, comportamentos e regras se aplicam para ambas as versões do WS-Addressing tem suporte em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3321: O solicitante deve incluir na solicitação `wsa:To`, `wsa:Action`, `wsa:MessageID`e os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pela referência de ponto de extremidade.  
  
-   R3322: Quando 08/2004 do WS-Addressing é usado, `ReplyTo` também deve ser incluído na solicitação.  
  
-   R3323: Quando WS-Addressing 1.0 é usada e `ReplyTo` é não está presente na solicitação, uma referência de ponto de extremidade padrão com a propriedade [address] igual a "http://www.w3.org/2005/08/addressing/anonymous" é usada.  
  
-   R3324: O solicitante deve incluir `wsa:To`, `wsa:Action`, e `wsa:RelatesTo` cabeçalhos na mensagem de resposta, bem como os cabeçalhos para todos os parâmetros de referência ou referência propriedades (ou ambos) especificado pelo `ReplyTo` referência de ponto de extremidade do solicitação.  
  
### <a name="web-services-addressing-faults"></a>Falhas de endereçamento de serviços Web  
 R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produz as seguintes falhas definidas pelo 2004 do WS-Addressing/08.  
  
|Código|Causa|  
|----------|-----------|  
|wsa:DestinationUnreachable|A mensagem chegou com um `ReplyTo` , que é diferente do endereço de resposta estabelecido para este canal; não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho de para.|  
|wsa:ActionNotSupported|os canais de infraestrutura ou distribuidor associado com o ponto de extremidade não reconhecem a ação especificada no `Action` cabeçalho.|  
  
 R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produz as seguintes falhas definidas por WS-Addressing 1.0.  
  
|Código|Causa|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|Duplicar `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`. Duplicar `wsa:RelatesTo` com o mesmo `RelationshipType`.|  
|wsa10:MessageAddressingHeaderRequired|O cabeçalho de endereçamento necessário está ausente.|  
|wsa10:DestinationUnreachable|A mensagem chegou com um `ReplyTo` , que é diferente do endereço de resposta estabelecido para este canal. Não há nenhum ponto de extremidade escutando no endereço especificado no cabeçalho de para.|  
|wsa10:ActionNotSupported|Uma ação especificada no `Action` cabeçalho não é reconhecido pelo canais de infraestrutura ou distribuidor associado com o ponto de extremidade.|  
|wsa10:EndpointUnavailable|O canal de RM envia essa falha, que indica o ponto de extremidade não processará a sequência com base na análise do `CreateSequence` cabeçalhos de endereçamento da mensagem.|  
  
 Mapas de código nas tabelas anteriores para `FaultCode` em SOAP 1.1 e `SubCode` (com o código = remetente) em SOAP 1.2.  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 asserções de WS-Policy e associação  
  
#### <a name="indicating-use-of-ws-addressing"></a>Indicam o uso de WS-Addressing.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa declarações de política para indicar o suporte de ponto de extremidade para uma versão específica do WS-Addressing.  
  
 A declaração de política a seguir tem assunto de política do ponto de extremidade [WS-PA] e indica as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 do WS-Addressing.  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 Esta declaração de política de aumenta a especificação de 2004 do WS-Addressing/08.  
  
 A seguinte declaração de política indica que as mensagens enviadas/recebidas deve usar WS-Addressing 1.0.  
  
```xml
<wsam:Addressing/>   
```  
  
 A seguinte declaração de política tem um assunto de política do ponto de extremidade [WS-PA] e indica se as mensagens enviadas e recebidas do ponto de extremidade devem usar 08/2004 do WS-Addressing.  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 O `wsaw10:UsingAddressing` elemento é obtido do [WS-Addressing-WSDL] e é usado no contexto do WS-Policy em conformidade com essa especificação, seção 3.1.2.  
  
 Uso de endereçamento não altera a semântica da WSDL 1.1, SOAP 1.1 e SOAP 1.2 HTTP associações. Por exemplo, se uma resposta é esperada para uma solicitação que é enviada para um ponto de extremidade que usa a associação HTTP de 1. x endereçamento e WSDL SOAP, a resposta deve ser enviada usando-se a resposta HTTP.  
  
 Para respostas enviadas pela resposta http, a declaração de WS-AM é:  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 A declaração de política concluída pode ter esta aparência:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 No entanto, há padrões de troca de mensagem se beneficiar de duas conexões de HTTP inverso independentes estabelecidas entre o solicitante e o respondedor, por exemplo, unidirecionais mensagens enviadas pelo respondente.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece um recurso pelo qual dois canais de transporte subjacente podem formar um canal Duplex compostos, onde um canal é usado para mensagens de entrada e a outra é usada para mensagens de saída. No caso de transporte HTTP, Duplex compostos fornece duas conexões de HTTP inverso. O solicitante usa uma conexão para enviar mensagens para o respondente e o respondedor usa o outro para enviar mensagens de volta para o solicitante.  
  
 Para respostas enviadas por solicitações de http separados, a declaração de ws-am é  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 A declaração de política concluída pode ter esta aparência:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 Use o seguinte declaração que tem o ponto de extremidade de política de entidade [WS-PA] nos pontos de extremidade usam associações de HTTP do WSDL 1.1 SOAP 1. x requer duas conexões de HTTP inverso separado a ser usado para mensagens que fluem do solicitante Respondente e Respondente ao solicitante, respectivamente.  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 A instrução anterior gera os seguintes requisitos `wsa:ReplyTo` cabeçalho para mensagens de solicitação:  
  
-   R3514: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com o `[address]` propriedade não é igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de 1. x HTTP WSDL 1.1 SOAP e tem uma alternativa de política com um `wsap10:UsingAddressing` ou `wsap:UsingAddressing` associado a asserção `cdp:CompositeDuplex` anexado.  
  
-   R3515: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com o `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous" ou não tem um `ReplyTo` cabeçalho todos, se o ponto de extremidade usa um WSDL 1.1 SOAP HTTP de 1. x associação e tem uma alternativa de política com `wsap10:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.  
  
-   R3516: Solicitar mensagens enviadas para um ponto de extremidade devem ter um `ReplyTo` cabeçalho com um `[address]` propriedade igual a "http://www.w3.org/2005/08/addressing/anonymous" se o ponto de extremidade usa uma associação de 1. x HTTP WSDL 1.1 SOAP e tem uma alternativa de política com `wsap:UsingAddressing` asserção e nenhum `cdp:CompositeDuplex` asserção anexada.  
  
 A especificação WS-addressing WSDL tenta descrever associações de protocolo semelhante com a introdução de um elemento `<wsaw:Anonymous/>` com três valores textuais (obrigatórios, opcionais e proibidos) para indicar requisitos sobre o `wsa:ReplyTo` cabeçalho (seção 3.2). Infelizmente, essa definição de elemento não é particularmente útil como uma declaração no contexto do WS-Policy, porque ele requer extensões específicas de domínio para dar suporte a interseção de alternativas usando esse elemento como uma declaração. Essa definição de elemento também indica o valor da `ReplyTo` cabeçalho em vez do comportamento de ponto de extremidade na conexão, que é específico para o transporte HTTP.  
  
#### <a name="action-definition"></a>Definição da ação  
 08/2004 do WS-Addressing define uma `wsa:Action` de atributo para o `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos. WS-Addressing 1.0 WSDL associação (WS-ADDR10-WSDL) define um atributo semelhante, `wsaw10:Action`.  
  
 A única diferença entre os dois é a semântica de padrão de ação padrão descrita na seção 3.3.2 do WS-ADDR e 4.4.4 do WS-ADDR10-WSDL, respectivamente.  
  
 É razoável ter dois pontos de extremidade que compartilham o mesmo `portType` (ou um contrato, na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologia), mas com diferentes versões do WS-Addressing. Mas, considerando que a ação é definida pelo `portType` e não devem alterar entre os pontos de extremidade que implementam o `portType`, torna impossível dar suporte a ambos os padrões de ação padrão.  
  
 Para resolver esse controvérsia incrível, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte a uma única versão do `Action` atributo.  
  
 B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa o `wsaw10:Action` atributo no `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementos conforme definido em WS-ADDR10-WSDL para determinar o `Action` URI para as mensagens correspondentes independentemente da versão do WS-Addressing usado pelo ponto de extremidade.  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Use ponto de extremidade de referência interna WSDL porta  
 WS-ADDR10-WSDL seção 4.1 estende o `wsdl:port` elemento para incluir o `<wsa10:EndpointReference…/>` elemento filho para descrever o ponto de extremidade em termos de WS-Addressing. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]expande esse utilitário em 08/2004 do WS-Addressing, permitindo que `<wsa:EndpointReference…/>` apareça como um elemento filho do `wsdl:port`.  
  
-   R3531: Se um ponto de extremidade tem uma alternativa de política anexada com um `<wsaw10:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa10:EndpointReference …/>`.  
  
-   R3532: Se um `wsdl:port` contém um elemento filho `<wsa10:EndpointReference …/>`, o `wsa10:EndpointReference/wsa10:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.  
  
-   R3533: Se um ponto de extremidade tem uma alternativa de política anexada com `<wsap:UsingAddressing/>` declaração de política correspondente `wsdl:port` elemento pode conter um elemento filho `<wsa:EndpointReference …/>`.  
  
-   R3534: Se um `wsdl:port` contém um elemento filho `<wsa:EndpointReference …/>`, o `wsa:EndpointReference/wsa:Address` valor do elemento filho deve corresponder ao valor da `@address` atributo do irmão `wsdl:port` / `wsdl:location` elemento.  
  
### <a name="composition-with-ws-security"></a>Composição com WS-Security  
 De acordo com a seções de consideração de segurança em WS-ADDR e WS-ADDR10, todos os cabeçalhos de mensagem de endereçamento são recomendados sejam assinados com o corpo da mensagem para associá-los juntos.  
  
 Quando WS-Security é usado para proteção de integridade de mensagem, a mensagem WS-Addressing cabeçalhos, bem como cabeçalhos resultaram de parâmetros de referência ou propriedades (ou ambos) deve ser assinada junto com o corpo da mensagem.  
  
### <a name="examples"></a>Exemplos  
  
#### <a name="one-way-message"></a>Mensagem unidirecional  
 Nesse cenário, o remetente envia uma mensagem unidirecional para o receptor. 1.0 W3C WS-Addressing, HTTP 1.1 e SOAP 1.2 são usados.  
  
 A estrutura de mensagens de solicitação: Os cabeçalhos de mensagem incluem `wsa10:To` e `wsa10:Action` elementos. O corpo da mensagem inclui um determinado `<app:Ping>` elemento do namespace do aplicativo.  
  
 Cabeçalhos HTTP: O destino na POSTAGEM coincide com o URI no `wsa10:To` elemento.  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a>Mecanismo de otimização de transmissão de mensagem SOAP  
 Esta seção descreve o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] detalhes de implementação para o HTTP SOAP MTOM. Tecnologia MTOM é o mecanismo de codificação de mensagem SOAP da mesma classe como codificação tradicional de texto/XML ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] codificação binária. MTOM inclui o seguinte:  
  
-   Um mecanismo de empacotamento descrito pelo [XOP] e a codificação XML que otimiza os itens de informações XML que contém dados binários codificados na base64 em partes separadas de binários.  
  
-   Um encapsulamento MIME do pacote XOP que serializa o Infoset XML e cada parte binária do pacote XOP em uma parte MIME separada.  
  
-   Uma codificação de MIME XOP aplicada ao SOAP Envelope de 1. x.  
  
-   Um HTTP associação de transporte.  
  
 É possível usar MTOM com transportes não HTTP com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. No entanto, neste tópico nos concentraremos no HTTP.  
  
 O formato MTOM aproveita um grande conjunto de especificações que abrangem MTOM em si, XOP e MIME. Modularidade desse conjunto de especificação dificulta um pouco reconstruir os requisitos exatos na semântica de formato e o processamento. Esta seção descreve os requisitos de processamento e o formato para a associação HTTP MTOM.  
  
### <a name="mtom-message-encoding"></a>Codificação de mensagem MTOM  
  
#### <a name="generating-mtom-messages"></a>Gerando mensagens MTOM  
 A seção 3.1 [XOP] descreve o processo de codificação XML com itens de informações de elemento que contêm valores de base64 em um pacote XOP abstrata definido.  
  
 A sequência de etapas a seguir descreve o processo de codificação de MTOM específico:  
  
1.  Certifique-se de que o Envelope SOAP a ser decodificado não contém nenhum item de informação do elemento com um `[namespace name]` de "http://www.w3.org/2004/08/xop/include" e um `[local name]` de `Include`.  
  
2.  Crie um pacote vazio do MIME.  
  
3.  Identifica os itens de informações do elemento a ser otimizado em Infoset XML Original. Para os itens deve ser otimizada, os caracteres que compõem o `[children]` as informações do elemento item deve ser na forma canônica de `xs:base64Binary` (consulte XSD-2, 3.2.16 base64Binary) e não deve conter nenhum caractere de espaço em branco anterior, embutido, ou Após o conteúdo não seja espaço em branco.  
  
4.  Criar um Envelope SOAP XOP que é uma cópia do Envelope SOAP Original, mas com os filhos de cada informação do elemento item identificado na etapa anterior é substituída por um `xop:Include` item de informação do elemento construída da seguinte maneira:  
  
    1.  Transforme os caracteres substituídos em dados binários processando-os como dados codificados na base64.  
  
    2.  Gere um valor de cabeçalho de Content-ID exclusivo que satisfaz os requisitos de R3133 e R3134.  
  
    3.  Gere um cabeçalho de codificação de transferência de conteúdo MIME com o valor binário.  
  
    4.  Se o item de informação do elemento que está sendo otimizado ([pai] recentemente inserido `xop:Include` item de informação do elemento) tem um `xmime:contentType` item de informação de atributo, gerar um cabeçalho de tipo de conteúdo MIME com o valor da `xmime:contentType` atributo.  
  
    5.  Gere uma nova parte MIME binária com conteúdo formado por dados binários decodificados dos caracteres substituídos processados como base64, o cabeçalho Content-ID do 4b, o cabeçalho de codificação de transferência de conteúdo de 4 núcleos, o cabeçalho Content-Type se gerado na etapa 4d.  
  
    6.  Adicionar uma `href` de atributo para o `xop:Include` elemento com o valor de cid: uri derivado do valor do cabeçalho Content-ID gerado na etapa 4b. Remover o delimitador "\<" e ">" caracteres, o restante da cadeia de caracteres e adicione o prefixo de URL-escape `cid:`. O conjunto mínimo de caracteres a seguir é necessário para ser substituídas por RFC1738 e RFC2396. Outros caracteres podem ser substituídos.  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  Crie uma parte MIME raiz com o Envelope de SOAP XOP da etapa 4.  
  
6.  Grave os cabeçalhos HTTP, incluindo o cabeçalho de tipo de conteúdo HTTP.  
  
7.  Grave o pacote MIME.  
  
#### <a name="processing-mtom-messages"></a>Processando mensagens MTOM  
 O processamento de um MTOM mensagem é o contrário exato do processo descrito na anterior "gerando MTOM mensagens" seção:  
  
1.  Certifique-se de que a parte MIME raiz tem o tipo de conteúdo `application/xop+xml`.  
  
2.  Construa um Envelope SOAP ao analisar a parte MIME do pacote como um documento XML raiz. Codificação de caracteres é determinado pelo `charset` parâmetro do tipo de conteúdo da parte MIME raiz.  
  
3.  Para cada item de informação do elemento no Envelope SOAP construído, que tem, como o único membro de sua propriedade [filhos], um `xop:Include` item de informação do elemento:  
  
    1.  Remover o `cid:` prefixo e unescape todas as sequências de escape de URI (RFC 2396) no valor da `@href` atributo do `xop:Include` elemento. Coloque a cadeia de caracteres de resultado em "\<", ">".  
  
    2.  Localize a parte MIME com o valor do cabeçalho Content-ID que corresponde à cadeia derivada na etapa 3a.  
  
    3.  Substitua o `xop:Include` item de informação do elemento que aparece no `children` propriedade de cada item com os itens de informações de caracteres que representam a codificação base64 canônico (consulte XSD-2, 3.2.16 base64Binary) do corpo da entidade da parte MIME identificado na etapa 3b (substitua efetivamente o `xop:Include` item de informação do elemento com os dados reconstruídos com a parte do pacote).  
  
#### <a name="http-content-type-header"></a>Cabeçalho de tipo de conteúdo HTTP  
 A seguir está uma lista de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] esclarecimentos para o formato do cabeçalho HTTP conteúdo-tipo de uma mensagem MTOM codificado do SOAP 1. x derivado de requisitos indicados na especificação MTOM e derivados de MTOM e RFC 2387.  
  
-   R4131: Um cabeçalho HTTP conteúdo-tipo deve ter o valor de diversas partes/relacionado (diferencia maiusculas de minúsculas) e seus parâmetros. Nomes de parâmetros diferenciam maiusculas de minúsculas. Ordem do parâmetro não é significativa.  
  
-   A forma de Backus-Naur completo (BNF) do cabeçalho Content-Type para mensagens MIME é listado na RFC 2045, seção 5.1.  
  
-   R4132: Um cabeçalho HTTP conteúdo-tipo deve ter um parâmetro de tipo com o valor `application/xop+xml` entre aspas duplas.  
  
 Embora o requisito para usar aspas duplas não seja explícito no RFC 2387, o texto observa que todo o tipo de mídia com diversas partes/relacionado que contêm parâmetros provavelmente reservada caracteres, como "@" or "/" e, portanto, precisam de aspas duplas.  
  
-   R4133: Um cabeçalho HTTP conteúdo-tipo deve ter um parâmetro de inicialização com o valor do cabeçalho Content-ID da parte MIME que contém o SOAP 1. x Envelope, entre aspas duplas. Se o parâmetro start for omitido, a primeira parte MIME deve conter o SOAP Envelope de 1. x.  
  
-   R4134: Um cabeçalho de tipo de conteúdo HTTP para uma mensagem SOAP 1.1 MTOM codificado deve incluir o parâmetro de informações de início com o valor de texto/xml, entre aspas duplas.  
  
-   R4135: Um cabeçalho de tipo de conteúdo HTTP para uma mensagem SOAP 1.2 MTOM codificado deve incluir o parâmetro de informações de início com o valor de `application/soap+xml`, entre aspas duplas.  
  
-   R4136: O cabeçalho de tipo de conteúdo HTTP para uma mensagem MTOM codificado do SOAP 1. x deve ter o parâmetro de limite com o valor (entre aspas duplas) que corresponde a limites MIME que BNF definido em RFC 2046, seção 5.1.1  
  
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
  
#### <a name="infoset-mime-part"></a>Parte MIME de infoset  
 O SOAP 1. x Envelope é encapsulado como parte do pacote XOP MIME raiz e é geralmente chamado de `infoset` parte.  
  
-   R4141: O SOAP 1. x Envelope deve ser encapsulado como parte do pacote XOP MIME, chamado raiz a `infoset` parte e referenciado de tipo de conteúdo HTTP.  
  
-   R4142: O SOAP `Infoset` parte deve incluir os seguintes cabeçalhos MIME: `Content-ID`, `Content-Transfer-Encoding`, e `Content-Type`.  
  
 O formato do cabeçalho Content-ID é definido por RFC 2045 como  
  
```  
"Content-ID" ":" msg-id  
```  
  
 onde `msg-id` é definido na RFC 2822 (que substitui o RFC 822, referenciada na RFC 2045) como:  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 e é efetivamente um endereço de email incluído dentro de "\<" e ">". O `[CFWS]` prefixo e sufixo foram adicionadas no RFC 2822 para transportar comentários e não deve ser usados para preservar a interoperabilidade.  
  
 R4143: O valor do cabeçalho Content-ID para a parte MIME Infoset deve seguir `msg-id` produção da RFC 2822 com o `[CFWS]` partes de prefixo e sufixo omitidos.  
  
 Um número de implementações de MIME relaxada requisitos para o valor entre "\<" e ">" para ser um endereço de email e usado `absoluteURI` entre "\<", ">" Além do endereço de email. Esta versão do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa valores de cabeçalho MIME Content-ID do formulário:  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144: Processadores MTOM devem aceitar valores de cabeçalho de Content-ID que correspondem reduzidas a seguir `msg-id`.  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC 2045) fornece o cabeçalho de codificação de transferência de conteúdo para comunicar-se a codificação do conteúdo da parte MIME. O padrão definido para codificação de transferência de conteúdo é 7-bits, que não é adequado para a maioria das mensagens SOAP, portanto, o cabeçalho de codificação de transferência de conteúdo é necessária para obter melhor interoperabilidade:  
  
-   R4145: A parte de SOAP Infoset deve conter o cabeçalho de codificação de transferência de conteúdo.  
  
-   R4146: Se a codificação de caracteres de Envelope SOAP é UTF-8, o valor do cabeçalho de codificação de transferência de conteúdo deve ser 8 bits.  
  
-   R4147: Se a codificação de caracteres de Envelope SOAP é UTF-16, o valor do cabeçalho de codificação de transferência de conteúdo deve ser binário.  
  
-   [XOP] seção 5, de acordo com  
  
-   R4148: SOAP1.1 Infoset parte deve conter o cabeçalho Content-Type com o tipo de mídia application/xop + xml e parâmetros de tipo = "text/xml" e o conjunto de caracteres  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: A parte de SOAP 1.2 Infoset deve conter o cabeçalho Content-Type com o tipo de mídia `application/xop+xml` e parâmetros de tipo = "`application/soap+xml`" e `charset`.  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     Enquanto XOP define o `charset` parâmetro `application/xop+xml` para ser opcional, é necessário para interoperabilidade semelhante para o requisito de BP 1.1 o `charset` parâmetro para o `text/xml` tipo de mídia.  
  
-   R41410: O `type` e `charset` parâmetros devem estar presentes no cabeçalho de Content-Type da parte de Infoset de SOAP 1. x.  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>Suporte de ponto de extremidade do WCF para MTOM  
 A finalidade de MTOM é codificar uma mensagem SOAP para otimizar o dados codificados na base64. A seguir está uma lista de restrições:  
  
-   R4151: Qualquer item de informação do elemento que contém dados codificados em base64 pode ser otimizado.  
  
-   B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] otimiza os itens de informações do elemento que contêm dados codificados em base64 e excederem 1024 bytes de comprimento.  
  
 Um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade configurado para usar MTOM sempre enviará mensagens codificadas MTOM. Mesmo que nenhuma parte de atender aos critérios necessários, a mensagem é codificado ainda MTOM (serializado como um pacote MIME com uma única parte MIME que contém o envelope SOAP).  
  
### <a name="ws-policy-assertion-for-mtom"></a>Asserção do WS-Policy para MTOM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa a seguinte declaração de política para indicar o uso MTOM pelo ponto de extremidade:  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211: A declaração de política anterior tem um assunto de política do ponto de extremidade e especifica que todas as mensagens enviadas e recebidas do ponto de extremidade devem ser otimizadas usando MTOM.  
  
-   B4212: Quando estiver configurado para usar a otimização MTOM, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ponto de extremidade adiciona uma declaração de política de MTOM para a diretiva anexada ao correspondente `wsdl:binding`.  
  
### <a name="composition-with-ws-security"></a>Composição com WS-Security  
 MTOM é um mecanismo de codificação é semelhante a `text/xml` e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML binário. MTOM oferece composição natural com WS-Security e outros WS-* protocolos: uma mensagem protegida usando o WS-Security pode ser otimizada MTOM.  
  
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
 Neste exemplo, uma mensagem é codificada usando MTOM e SOAP 1.2 são protegidos usando o WS-Security. As partes binárias identificadas para codificação é o conteúdo do `BinarySecurityToken`, `CipherValue` do `EncryptedData` correspondente para a assinatura criptografada e o corpo criptografado. Observe que o `CipherValue` do `EncryptedKey` não foi identificado para a otimização, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pois seu tamanho é menor, em seguida, 1024 bytes.  
  
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
