---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b1542406caf9bb3684ccf2d97ed441f1dc3d0db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe HttpTransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe HttpTransportBindingElement tem as seguintes propriedades:  
  
### <a name="allowcookies"></a>allowCookies  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se o cliente aceita cookies e os propaga em solicitações futuras.  
  
### <a name="authenticationscheme"></a>authenticationScheme  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O esquema de autenticação usado para autenticar solicitações de cliente processadas por um ouvinte HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se os proxies são ignorados para endereços locais.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.  
  
### <a name="keepaliveenabled"></a>keepAliveEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Quando habilitada, as conexões HTTP são mantidas ativas independentemente do nível de atividade.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho máximo do pool de buffers.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um URI que contém o endereço do proxy a ser usado para solicitações HTTP.  
  
### <a name="proxyauthenticationscheme"></a>proxyAuthenticationScheme  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O esquema de autenticação usado para autenticar solicitações de cliente processadas por um proxy HTTP.  
  
### <a name="realm"></a>território  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O realm de autenticação.  
  
### <a name="transfermode"></a>transferMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor que especifica se as mensagens são armazenados em buffer ou transmitidas ou uma solicitação ou resposta.  
  
### <a name="unsafeconnectionntlmauthentication"></a>unsafeConnectionNtlmAuthentication  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se o compartilhamento de Conexão não segura está habilitada no servidor.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
