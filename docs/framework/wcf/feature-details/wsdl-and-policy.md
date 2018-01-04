---
title: "WSDL e política"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd52e36199fc2412abb003d530dd5614cda8049b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="wsdl-and-policy"></a>WSDL e política
Este tópico aborda [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL 1.1, detalhes de implementação de WS-Policy e mecanismo WS-PolicyAttachment, bem como declarações adicionais do WS-Policy e extensões WSDL 1.1 introduzidas por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa o WS-Policy e mecanismo WS-PolicyAttachment especificações enviadas ao W3C com restrições e esclarecimentos descritos neste documento.  
  
 Este documento usa os prefixos e os namespaces mostrado na tabela a seguir.  
  
|Prefixo|Namespace|  
|------------|---------------|  
|wsp (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/Policy|  
|wsp (WS-Policy 1.5)|http://www.w3.org/NS/WS-Policy|  
|HTTP|http://schemas.microsoft.com/WS/06/2004/Policy/http|  
|MSMQ|http://schemas.microsoft.com/WS/06/2004/mspolicy/MSMQ|  
|MSF|http://schemas.microsoft.com/WS/2006/05/Framing/Policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/SecurityPolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/WSDL/Contract|  
|CDP|http://schemas.microsoft.com/NET/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>Extensões WSDL1.1 do WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa as seguintes extensões WSDL1.1 para descrever os requisitos de sessão do contrato.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs: Boolean, indica que essa operação inicia um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessão; o padrão é de valor `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs: Boolean, indica que esta operação encerra um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessão; o padrão é de valor `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs: Boolean, indica que este contrato requer session seja estabelecida.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>URIs de transporte de associação de 1. x HTTP SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usa os seguintes URIs para indicar os transportes para ser usado para elementos de extensão de associação WSDL 1.1, SOAP 1.1 e SOAP 1.2.  
  
|Transporte|URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/SOAP/TCP|  
|MSMQ|http://schemas.microsoft.com/SOAP/MSMQ|  
|Pipes nomeados|http://schemas.microsoft.com/SOAP/Named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Declarações de política implementadas pelo WCF  
 Além das declarações de política introduzidas nas especificações de serviços da Web (WS-*) e mencionado em outras seções deste documento, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementa as seguintes declarações de política.  
  
|Declaração de política|Entidade de política|Descrição|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação básica HTTP.|  
|http:HttpDigestAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação Digest HTTP.|  
|http:HttpNegotiateAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação de negociação de HTTP.|  
|http:HttpNtlmAuthentication|Ponto de extremidade|Ponto de extremidade usa a autenticação NTLM HTTP.|  
|MSF: Streaming|Ponto de extremidade|Ponto de extremidade usa quadros mensagem transmitida. Essa declaração é usada com o protocolo Message Framing fornecido para os transportes, como TCP e pipes nomeados.|  
|MSF:SslTransportSecurity|Ponto de extremidade|Ponto de extremidade usa a segurança de camada de transporte (TLS) com os quadros de mensagem.|  
|MSF:WindowsTransportSecurity|Ponto de extremidade|Ponto de extremidade usa a negociação de provedor de segurança (SPNEGO) com os quadros de mensagem.|  
|MSMQ:MsmqBestEffort|Ponto de extremidade|MSMQ com garantia de melhor esforço.|  
|MSMQ:MsmqSession|Ponto de extremidade|Garante de MSMQ com a sessão.|  
|MSMQ:MsmqVolatile|Ponto de extremidade|MSMQ volátil.|  
|MSMQ: autenticado|Ponto de extremidade|A autenticação é usada com o transporte MSMQ.|  
|MSMQ:WindowsDomain|Ponto de extremidade|MSMQ usa a autenticação de domínio do Windows.|  
|CDP:CompositeDuplex|Ponto de extremidade|Ponto de extremidade usa duas conexões de transporte inversa separado para do in e out de mensagens.|  
|mssp:RsaToken|Aninhados|Declaração de token de chave RSA. Normalmente, esse requisito é atendido por uma chave RSA serializada diretamente como parte das informações de chave em uma assinatura de endosso.|  
|mssp:SslContextToken|Aninhados|Requer que um SecurityContextToken obtida por meio de handshake TLS binário usando o WS-Trust. Asserções aninhadas incluem: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Aninhados|Especifique um requisito de que um token de segurança de solicitação (primeira) solicitar mensagens [WS-Trust] usando a associação de cancelar [WS-Trust, WS-SC] não ser enviadas para o emissor de um determinado SecurityContextToken. Se essa asserção estiver presente, essas mensagens de solicitação não devem ser enviadas para o emissor. Se essa asserção não estiver presente, essas mensagens de solicitação podem ser enviadas para o emissor.|  
|mssp:RequireClientCertificate|Aninhados|Este elemento opcional especifica um requisito para um certificado de cliente a ser fornecido como parte do protocolo TLSNEGO. Se essa asserção estiver presente, um certificado de cliente deve ser fornecido. Se essa asserção não estiver presente, um certificado de cliente não deve ser fornecido. Essa declaração não deve ser usada fora mssp:SslContextToken.|  
  
## <a name="see-also"></a>Consulte também  
 [Publicação de WSDL personalizada](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Como exportar o WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Como importar WSDL personalizado](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
