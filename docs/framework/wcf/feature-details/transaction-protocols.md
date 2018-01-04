---
title: "Protocolos de transação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13784a3a5062705abba1b3bbb33a04e66bd22072
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols"></a>Protocolos de transação
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]implementa os protocolos WS-AT e coordenação WS.  
  
|Documento de especificação /|Versão|Link|  
|-----------------------------|-------------|----------|  
|Coordenação WS|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96104](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|WS-AtomicTransaction|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> http://go.microsoft.com/fwlink/?LinkId=96081|  
  
 Interoperabilidade nessas especificações de protocolo é necessária em dois níveis: entre aplicativos e gerenciadores de transações (consulte a figura a seguir). Especificações descrevem detalhadamente os formatos de mensagem e a mensagem do exchange para ambos os níveis de interoperabilidade. Determinados segurança, confiabilidade e codificações para o aplicativo para exchange se aplicam para troca de aplicativo comum. No entanto, interoperabilidade com êxito entre gerenciadores de transações exige contrato na associação de determinado, porque geralmente não está configurado pelo usuário.  
  
 Este tópico descreve uma composição da especificação de transação WS-Atomic (WS-AT) com segurança e descreve a associação de segurança usada para comunicação entre os gerenciadores de transações. A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS incluindo IBM, IONA, Sun Microsystems e outros.  
  
 A figura a seguir ilustra a interoperabilidade entre dois gerenciadores de transações, gerente de transação 1 e 2 do Gerenciador de transações e dois aplicativos, o aplicativo 1 e 2 do aplicativo.  
  
 ![Protocolos de transação](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")  
  
 Considere um cenário típico de WS-coordenação/WS-AT com um iniciador (I) e um participante (P). O iniciador e o participante tem gerenciadores de transações (ITM e PTM, respectivamente). Confirmação de duas fases é conhecida como 2PC neste tópico.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Resposta de mensagem do aplicativo|  
|2. CreateCoordinationContextResponse|13. Confirmação (preenchimento)|  
|3. Registro (preenchimento)|14. Preparar (2PC)|  
|4. RegisterResponse|15. Preparar (2PC)|  
|5. Mensagem de aplicativo|16. Preparada (2PC)|  
|6. CreateCoordinationContext com contexto|17. Preparada (2PC)|  
|7. Registro (durável)|18. Confirmada (preenchimento)|  
|8. RegisterResponse|19. 2PC (confirmação)|  
|9. CreateCoordinationContextResponse|20. 2PC (confirmação)|  
|10. Registro (durável)|21. Confirmada (2PC)|  
|11. RegisterResponse|22. Confirmada (2PC)|  
  
 Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e a associação de segurança usada para comunicação entre os gerenciadores de transações. A abordagem descrita neste documento foram testada com êxito com outras implementações do WS-AT e coordenação WS.  
  
 A figura e a tabela ilustram quatro classes de mensagens a partir do ponto de vista de segurança:  
  
-   Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).  
  
-   Mensagens de registro (o registro e RegisterResponse)  
  
-   Mensagens de protocolo (preparar, Rollback, confirmação, Aborted e assim por diante).  
  
-   Mensagens de aplicativo.  
  
 Classes de três mensagem primeiro são consideradas mensagens do Gerenciador de transações e sua configuração de associação é descrita em "Aplicativo de troca de mensagens" neste tópico. A quarta classe da mensagem é mensagens de aplicativo e é descrita na seção "Exemplos de mensagem" neste tópico. Esta seção descreve as associações de protocolo usadas para cada uma dessas classes por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Os seguintes Namespaces de XML e prefixos associados são usados em todo este documento.  
  
|Prefixo|Versão|URI de Namespace|  
|------------|-------------|-------------------|  
|S11||[http://go.microsoft.com/fwlink/?LinkId=96014](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|wsa|Pré-1.0<br /><br /> 1.0|http://www.w3.org/2004/08/Addressing<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96022](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|wscoor|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96078](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|WSAT|1.0<br /><br /> 1.1|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96081](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|t|Pré-1.3<br /><br /> 1.3|[http://go.microsoft.com/fwlink/?LinkId=96082](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96100](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|o||[http://go.microsoft.com/fwlink/?LinkId=96101](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|XSD||[http://go.microsoft.com/fwlink/?LinkId=96102](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a>Associações do Gerenciador de transações  
 R1001: Gerenciadores de transações que participam de uma transação WS-AT 1.0 devem usar os SOAP 1.1 e 08/2004 do WS-Addressing para transações de WS-Atomic e trocas de mensagens de coordenação WS.  
  
 R1002: Gerenciadores de transações que participam de uma transação WS-AT 1.1 devem usar os SOAP 1.1 e WS-Addressing 2005/08 para transações de WS-Atomic e trocas de mensagens de coordenação WS.  
  
 As mensagens de aplicativo não são restritos a essas associações e são descritas posteriormente.  
  
### <a name="transaction-manager-https-binding"></a>Associação de HTTPS de Gerenciador de transações  
 A associação de HTTPS de Gerenciador de transação depende exclusivamente de segurança de transporte para obter segurança e estabelecer relação de confiança entre cada par de remetente e o receptor na árvore de transação.  
  
#### <a name="https-transport-configuration"></a>Configuração de transporte HTTPS  
 Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações. Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação:  
  
-   R1111: Certificados x. 509 apresentados pela conexão devem ter um nome de assunto que corresponda o nome de domínio totalmente qualificado (FQDN) do computador de origem.  
  
-   B1112: O DNS deve ser funcional entre cada par de remetente e o receptor do sistema para verificações de nome de assunto de x. 509 seja bem-sucedida.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Ativação e registro de configuração de associação  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]requer a associação de solicitação/resposta duplex com correlação via HTTPS. (Para obter mais informações sobre a correlação e descrições dos padrões de troca de mensagem de solicitação/resposta, consulte transação WS-Atomic, 8 de seção).  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuração de associação de protocolo 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS. Correlação entre as mensagens será deixada como um detalhe de implementação.  
  
 B1131: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Gerenciador de transações misto associação de segurança  
 Esta é uma alternativa (misto) que usa a segurança de transporte combinada com o modelo de Token emitido de coordenação WS para fins de estabelecimento de identidade de associação. Ativação e registro são os únicos elementos que diferem entre as duas associações.  
  
#### <a name="https-transport-configuration"></a>Configuração de transporte HTTPS  
 Certificados x. 509 são usados para estabelecer a identidade do Gerenciador de transações. Autenticação de cliente/servidor é necessária e autorização do cliente/servidor é mantida como um detalhe de implementação.  
  
#### <a name="activation-message-binding-configuration"></a>Configuração de associação de mensagem de ativação  
 Mensagens de ativação geralmente não participar de interoperabilidade porque eles ocorrem normalmente entre um aplicativo e seu gerente de transação local.  
  
 B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para mensagens de ativação. Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing para WS-AT 1.0 e WS-Addressing 2005/08 1.1 WS-AT.  
  
 Especificação WS-AT, 8 de seção, descreve mais detalhes sobre a correlação e os padrões de troca de mensagem.  
  
-   R1222: após receber uma `CreateCoordinationContext`, o coordenador deve emitir uma `SecurityContextToken` com segredo associado `STx`. Esse token é retornado em uma `t:IssuedTokens` cabeçalho após a especificação WS-Trust.  
  
-   R1223: Se a ativação ocorrer dentro de um contexto de coordenação existente, o `t:IssuedTokens` cabeçalho com o `SecurityContextToken` associado existente contexto deve fluir no `CreateCoordinationContext` mensagem.  
  
 Um novo `t:IssuedTokens` cabeçalho deve ser gerado para anexar para a saída `wscoor:CreateCoordinationContextResponse` mensagem.  
  
#### <a name="registration-message-binding-configuration"></a>Configuração de associação de mensagem de registro  
 B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa associação de HTTPS duplex (descrito na [protocolos de mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Mensagens de resposta e solicitação são correlacionadas usando 08/2004 do WS-Addressing para WS-AT 1.0 e WS-Addressing 2005/08 1.1 WS-AT.  
  
 WS-AtomicTransaction, 8 de seção descreve mais detalhes sobre a correlação e descrições dos padrões de troca de mensagem.  
  
 R1232: Saída `wscoor:Register` mensagens devem usar o `IssuedTokenOverTransport` o modo de autenticação descrito [protocolos de segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 O `wsse:Timestamp` elemento deve ser assinado usando o `SecurityContextToken``STx` emitido. Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante inscrição na transação. A mensagem RegistrationResponse é enviada novamente por HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuração de associação de protocolo 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oferece suporte a mensagens unidirecionais (datagrama) sobre HTTPS. Correlação entre as mensagens será deixada como um detalhe de implementação.  
  
 B1241: Implementações devem suportar `wsa:ReferenceParameters` conforme descrito em WS-Addressing para alcançar a correlação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do 2PC mensagens.  
  
## <a name="application-message-exchange"></a>Troca de mensagens de aplicativo  
 Aplicativos estão livres para usar qualquer associação específica para mensagens de aplicativo, desde que a associação atende aos seguintes requisitos de segurança:  
  
-   R2001: Mensagens de aplicativo para o aplicativo devem fluir de `t:IssuedTokens` cabeçalho junto com o `CoordinationContext` no cabeçalho da mensagem.  
  
-   R2002: Integridade e confidencialidade de `t:IssuedToken` deve ser fornecido.  
  
 O `CoordinationContext` cabeçalho contém `wscoor:Identifier`. Enquanto a definição de `xsd:AnyURI` permite o uso de absolute e relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oferece suporte apenas para `wscoor:Identifiers`, que são URIs absolutos.  
  
 B2003: Se o `wscoor:Identifier` do `wscoor:CoordinationContext` é um URI relativo, falhas serão retornadas de transacional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.  
  
## <a name="message-examples"></a>Exemplos de mensagem  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Mensagens de solicitação/resposta CreateCoordinationContext  
 As seguintes mensagens sigam um padrão de solicitação/resposta.  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a>CreateCoordinationContext com WSCoor 1.0  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a>CreateCoordinationContext com WSCoor 1.1  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>   
<Address>https://...</a:Address>   
</a:ReplyTo>   
<a:To>https://...</a:To>   
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
</u:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
<wscoor:CreateCoordinationContext>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
</wscoor:CreateCoordinationContext>  
 </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a>CreateCoordinationContextResponse com confiança Pre-1.3 e WSCoor 1.0  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a>CreateCoordinationContextResponse com confiança 1.3 e WSCoor 1.1  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>   
<wsse:SecurityTokenReference >   
<wsse:Reference  
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedUnattachedReference>   
<wst:RequestedProofToken>   
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
  <!-- base64 encoded value -->   
</wst:BinarySecret>   
</wst:RequestedProofToken>   
<wst:Lifetime>   
<wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
<wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
</wst:Lifetime>   
<wst:KeySize>256</wst:KeySize>   
</wst:RequestSecurityTokenResponse>   
</t:IssuedTokens>   
<o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">   
<u:Timestamp u:Id="_0">   
<u:Created>2005-12-15T23:36:12.015Z</u:Created>   
<u:Expires>2005-12-15T23:41:12.015Z</u:Expires>   
</u:Timestamp>   
</o:Security>   
</s:Header>   
<s:Body>   
<wscoor:CreateCoordinationContextResponse>   
<wscoor:CoordinationContext>   
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Mensagens de registro  
 As seguintes mensagens são mensagens de registro.  
  
#### <a name="register-with-wscoor-10"></a>Registrar com WSCoor 1.0  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-with-wscoor-11"></a>Registrar com WSCoor 1.1  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
<a:ReplyTo>   
<a:Address>https://...</a:Address>   
</a:ReplyTo>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wssu:Timestamp wssu:Id="_0" >   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
<!-- supporting signature over the timestamp -->  
<wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
<ds:SignedInfo>   
<ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>   
<ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>   
<ds:Reference URI="#_0">   
<ds:Transforms>   
<ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>   
</ds:Transforms>   
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</ds:KeyInfo>   
</wsse:Signature>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wscoor:Register>   
<wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
<wscoor:ParticipantProtocolService>   
<a:Address>https://... </a:Address>  
</wscoor:ParticipantProtocolService>   
</wscoor:Register>   
</s:Body>   
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-10"></a>Registrar a resposta com WSCoor 1.0  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-11"></a>Registrar a resposta com WSCoor 1.1  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">   
<wssu:Timestamp>   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wscoor:RegisterResponse>   
<wscoor:CoordinatorProtocolService>  
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>Duas mensagens de protocolo de confirmação de fase  
 A seguinte mensagem de erro se relaciona com o protocolo de confirmação de duas fases (2PC).  
  
#### <a name="commit-with-wsat-10"></a>Confirmar com WSAT 1.0  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="commit-with-wsat-11"></a>Confirmar com WSAT 1.1  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
<a:To>https://...</a:To>   
<wsse:Security   
s:mustUnderstand="1"   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">   
<wssu:Timestamp wssu:Id="_0" >   
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>   
</wsse:Security>   
</s:Header>   
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">   
<wsat:Commit />   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="application-messages"></a>Mensagens de aplicativo  
 As seguintes mensagens são mensagens do aplicativo.  
  
#### <a name="application-message-request"></a>Solicitação de mensagem do aplicativo  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
