---
title: Protocolos de transação versão 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a19329b56bb569a04195b38877a42d635996ff1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184384"
---
# <a name="transaction-protocols-version-10"></a>Protocolos de transação versão 1.0
A versão 1 da Windows Communication Foundation (WCF) implementa a versão 1.0 dos protocolos WS-Atomic Transaction e WS-Coordination. Para obter mais informações sobre a versão 1.1, consulte [Protocolos de transação](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Especificação/Documento|Link|  
|-----------------------------|----------|  
|Coordenação ws|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|WS-AtomicTransaction|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 A interoperabilidade nessas especificações de protocolo é exigida em dois níveis: entre aplicativos e entre gerentes de transações (veja a figura a seguir). As especificações descrevem em grande detalhe os formatos de mensagem e a troca de mensagens para ambos os níveis de interoperabilidade. Certas seguranças, confiabilidade e codificações para troca de aplicativos para aplicativos se aplicam à troca regular de aplicativos. No entanto, a interoperabilidade bem-sucedida entre os gerentes de transação requer concordância sobre a vinculação específica, porque geralmente não é configurada pelo usuário.  
  
 Este tópico descreve uma composição da especificação WS-Atomic Transaction (WS-AT) com segurança e descreve a vinculação segura usada para comunicação entre os gerentes de transações. A abordagem descrita neste documento foi testada com sucesso com outras implementações do WS-AT e ws-coordination, incluindo IBM, IONA, Sun Microsystems, entre outras.  
  
 A figura a seguir mostra a interoperabilidade entre dois gerentes de transação, o Gerenciador de Transações 1 e o Gerenciador de Transações 2, e dois aplicativos, Aplicativo 1 e Aplicativo 2:  
  
 ![Captura de tela que mostra a interação entre os gerentes de transações.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 Considere um cenário típico de WS-Coordination/WS-Atomic Transaction com um Iniciador (I) e um Participante (P). Tanto o Iniciador quanto o Participante possuem Gerentes de Transações (ITM e PTM, respectivamente). O compromisso em duas fases é referido como 2PC neste tópico.  
  
|||  
|-|-|  
|1. Criar CoordenaçãoContexto|12. Resposta de mensagem de aplicativo|  
|2. CreateCoordinationContextResponse|13. Comprometer (Conclusão)|  
|3. Registre-se (Conclusão)|14. Prepare (2PC)|  
|4. RegisterResponse|15. Prepare (2PC)|  
|5. Mensagem de aplicativo|16. Preparado (2PC)|  
|6. CriarCoordenaçãoContexto com Contexto|17. Preparado (2PC)|  
|7. Registre-se (Durável)|18. Comprometido (Conclusão)|  
|8. RegisterResponse|19. Comprometer (2PC)|  
|9. CreateCoordinationContextResponse|20. Comprometer (2PC)|  
|10. Registro (Durável)|21. Comprometido (2PC)|  
|11. RegisterResponse|22. Comprometido (2PC)|  
  
 Este documento descreve uma composição da especificação WS-AtomicTransaction com segurança e descreve a vinculação segura usada para comunicação entre os gerentes de transações. A abordagem descrita neste documento foi testada com sucesso com outras implementações do WS-AT e ws-coordination.  
  
 A figura e a tabela ilustram quatro classes de mensagens do ponto de vista da segurança:  
  
- Mensagens de ativação (CreateCoordinationContext e CreateCoordinationContextResponse).  
  
- Mensagens de registro (Register and RegisterResponse)  
  
- Mensagens de protocolo (Prepare, Rerole, Comprometa, Aborte e assim por diante).  
  
- Mensagens de aplicativo.  
  
 As três primeiras classes de mensagens são consideradas mensagens do Gerenciador de Transações e sua configuração vinculativa é descrita na "Troca de mensagens de aplicativo" mais tarde neste tópico. A quarta classe de mensagem é aplicativo para mensagens de aplicativo e é descrita na seção "Exemplos de mensagens" mais tarde neste tópico. Esta seção descreve as vinculações de protocolo usadas para cada uma dessas classes pelo WCF.  
  
 Os seguintes Namespaces XML e prefixos associados são usados ao longo deste documento.  
  
|Prefixo|URI de namespace|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|Wsa|http://www.w3.org/2004/08/addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|wsat|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|t|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|o|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|xsd|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Vinculações do Gerenciador de Transações  
 R1001: Os gerentes de transação devem usar o SOAP 1.1 e o WS-Addressing 2004/08 para trocas de mensagens WS-Atomic Transaction e WS-Coordination.  
  
 As mensagens de aplicativo não são restritas a essas vinculações e são descritas posteriormente.  
  
### <a name="transaction-manager-https-binding"></a>Vinculação HTTPS do Gerenciador de Transações  
 A vinculação HTTPS do gerenciador de transações depende exclusivamente da segurança do transporte para obter segurança e estabelecer confiança entre cada par de remetente-receptor na árvore de transações.  
  
#### <a name="https-transport-configuration"></a>Configuração de transporte HTTPS  
 Os certificados X.509 são usados para estabelecer a identidade do gerenciador de transações. A autenticação do cliente/servidor é necessária e a autorização do cliente/servidor é deixada como um detalhe de implementação:  
  
- R1111: Os certificados X.509 apresentados sobre o fio devem ter um nome de assunto que corresponda ao nome de domínio totalmente qualificado (FQDN) da máquina de origem.  
  
- B1112: O DNS deve ser funcional entre cada par de remetente-receptor no sistema para que o nome do sujeito X.509 seja bem sucedido.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Configuração de ativação e registro  
 O WCF requer a vinculação duplex de solicitação/resposta com correlação sobre HTTPS. (Para obter mais informações sobre correlação e descrições dos padrões de troca de mensagens de solicitação/resposta, consulte Transação WS-Atomic, Seção 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuração de vinculação do protocolo 2PC  
 O WCF suporta mensagens unidirecionais (datagram) sobre HTTPS. A correlação entre as mensagens é deixada como um detalhe de implementação.  
  
 B2131: As implementações devem apoiar `wsa:ReferenceParameters` conforme descrito no WS-Addressing para alcançar a correlação das mensagens 2PC do WCF.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Vinculação de segurança mista do gerenciador de transações  
 Esta é uma vinculação alternativa (modo misto) que usa segurança de transporte combinada com o modelo De token emitido pelo WS-Coordination para fins de estabelecimento de identidade.  Ativação e Registro são os únicos elementos que diferem entre as duas ligações.  
  
#### <a name="https-transport-configuration"></a>Configuração de transporte HTTPS  
 Os certificados X.509 são usados para estabelecer a identidade do gerenciador de transações. A autenticação do cliente/servidor é necessária e a autorização do cliente/servidor é deixada como um detalhe de implementação.  
  
#### <a name="activation-message-binding-configuration"></a>Configuração de vinculação de mensagem de ativação  
 As mensagens de ativação geralmente não participam da interoperabilidade porque normalmente ocorrem entre um aplicativo e seu gerenciador de transações local.  
  
 B1221: O WCF usa a vinculação HTTPS duplex (descrita em [Protocolos de Mensagens)](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)para mensagens de ativação. As mensagens de solicitação e resposta estão correlacionadas usando o WS-Addressing 2004/08.  
  
 A especificação ws-atomic transaction, Seção 8, descreve mais detalhes sobre correlação e os padrões de troca de mensagens.  
  
- R1222: Ao `CreateCoordinationContext`receber um , `SecurityContextToken` o Coordenador `STx`deve emitir um segredo associado . Este token é devolvido `t:IssuedTokens` dentro de um cabeçalho seguindo a especificação ws-trust.  
  
- R1223: Se a ativação ocorrer dentro `t:IssuedTokens` de `SecurityContextToken` um contexto de coordenação `CreateCoordinationContext` existente, o cabeçalho com o contexto existente deve fluir na mensagem.  
  
 Um `t:IssuedTokens` novo cabeçalho deve ser gerado `wscoor:CreateCoordinationContextResponse` para anexar à mensagem de saída.  
  
#### <a name="registration-message-binding-configuration"></a>Configuração de vinculação de mensagem de registro  
 B1231: O WCF usa a vinculação HTTPS duplex (descrita em [Protocolos de Mensagens](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). As mensagens de solicitação e resposta estão correlacionadas usando o WS-Addressing 2004/08.  
  
 WS-AtomicTransaction, Seção 8, descreve mais detalhes sobre correlação e descrições dos padrões de troca de mensagens.  
  
 R1232: As `wscoor:Register` mensagens de `IssuedTokenOverTransport` saída devem usar o modo de autenticação descrito nos [Protocolos de Segurança](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 O `wsse:Timestamp` elemento deve ser `SecurityContextToken STx` assinado usando o emitido. Esta assinatura é uma prova de posse do token associado à transação específica e é usada para autenticar um participante alistando-se na transação. A mensagem RegistrationResponse é enviada de volta pelo HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuração de vinculação do protocolo 2PC  
 O WCF suporta mensagens unidirecionais (datagram) sobre HTTPS. A correlação entre as mensagens é deixada como um detalhe de implementação.  
  
 B2131: As implementações devem apoiar `wsa:ReferenceParameters` conforme descrito no WS-Addressing para alcançar a correlação das mensagens 2PC do WCF.  
  
## <a name="application-message-exchange"></a>Troca de mensagens de aplicativo  
 Os aplicativos são livres para usar qualquer vinculação específica para mensagens de aplicativo para aplicativo, desde que a vinculação atenda aos seguintes requisitos de segurança:  
  
- R2001: As mensagens de aplicativo `t:IssuedTokens` para aplicativo `CoordinationContext` devem fluir o cabeçalho juntamente com o cabeçalho da mensagem.  
  
- R2002: A integridade e `t:IssuedToken` a confidencialidade devem ser fornecidas.  
  
 O `CoordinationContext` cabeçalho contém `wscoor:Identifier`. Enquanto a `xsd:AnyURI` definição de permite o uso de URIs `wscoor:Identifiers`absolutas e relativas, o WCF suporta apenas , que são URIs absolutas.  
  
 Se `wscoor:Identifier` o `wscoor:CoordinationContext` do é um URI relativo, as falhas serão devolvidas de serviços WCF transacionais.  
  
## <a name="message-examples"></a>Exemplos de mensagens  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Criarmensageações de solicitação/resposta de contexto de coordenação  
 As mensagens a seguir seguem um padrão de solicitação/resposta.  
  
#### <a name="createcoordinationcontext"></a>CriarCoordenaçãoContexto  
  
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
  
#### <a name="createcoordinationcontextresponse"></a>CriarCoordenaçãoContextResponse  
  
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
  
### <a name="registration-messages"></a>Mensagens de registro  
 As seguintes mensagens são mensagens de registro.  
  
#### <a name="register"></a>Registrar   
  
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
  
#### <a name="register-response"></a>Registrar resposta  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a>Mensagens de protocolo de confirmação de duas fases  
 A mensagem a seguir diz respeito ao protocolo de confirmação bifásica (2PC).  
  
#### <a name="commit"></a>Commit  
  
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
  
### <a name="application-messages"></a>Mensagens de aplicativo  
 As seguintes mensagens são mensagens de aplicativo.  
  
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
