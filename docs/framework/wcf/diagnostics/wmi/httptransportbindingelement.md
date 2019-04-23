---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977035"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
 A classe HttpTransportBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe HttpTransportBindingElement tem as seguintes propriedades:  
  
### <a name="allowcookies"></a>AllowCookies  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se o cliente aceita cookies e propaga-os em solicitações futuras.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um ouvinte HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se os proxies são ignorados para endereços locais.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Quando habilitada, as conexões HTTP são mantidas ativos, independentemente do nível de atividade.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O tamanho máximo do pool de buffers.  
  
### <a name="proxyaddress"></a>ProxyAddress  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um URI que contém o endereço do proxy a ser usado para solicitações HTTP.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O esquema de autenticação usado para autenticar solicitações de cliente sendo processadas por um proxy HTTP.  
  
### <a name="realm"></a>território  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O realm de autenticação.  
  
### <a name="transfermode"></a>TransferMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas ou uma solicitação ou resposta.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se o compartilhamento de Conexão não segura está habilitada no servidor.  
  
### <a name="usedefaultwebproxy"></a>UseDefaultWebProxy  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se as configurações de proxy de todo o computador são usadas em vez de configurações específicas do usuário.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
