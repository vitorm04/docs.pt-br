---
title: Configurando aplicativos da Internet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
caps.latest.revision: 15
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a4a013b8a4ff60222bb88c6e9c4f14badd689b5d
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="configuring-internet-applications"></a>Configurando aplicativos da Internet
O elemento de configuração [\<system.Net> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) contém informações de configuração da rede de aplicativos. Usando o Elemento [\<system.Net> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md), você pode definir servidores proxy, definir parâmetros de gerenciamento de conexão e incluir módulos de autenticação e solicitação personalizados no aplicativo.  
  
 O Elemento [\<defaultProxy> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) define o servidor proxy retornado pela classe `GlobalProxySelection`. Qualquer <xref:System.Net.HttpWebRequest> que não tenha sua própria propriedade <xref:System.Net.HttpWebRequest.Proxy%2A> definida com um valor específico usa o proxy padrão. Além de definir o endereço proxy, é possível criar uma lista de endereços de servidor que não usará o proxy e indicar que o proxy não deverá ser usado para endereços locais.  
  
 É importante observar que as configurações do Microsoft Internet Explorer são combinadas com as configurações, com o último tendo precedência sobre o primeiro.  
  
 O exemplo a seguir define o endereço do servidor proxy padrão como http://proxyserver, indica que o proxy não deverá ser usado para endereços locais e especifica que todas as solicitações para servidores localizados no domínio contoso.com deverão ignorar o proxy.  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 Use o Elemento [\<connectionManagement> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) para configurar o número de conexões persistentes que podem ser estabelecidas com um servidor específico ou com todos os outros servidores. O exemplo a seguir configura o aplicativo para usar duas conexões persistentes com o servidor www.contoso.com, quatro conexões persistentes com o servidor com o endereço IP 192.168.1.2 e uma conexão persistente com todos os outros servidores.  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 Os módulos de autenticação personalizados são configurados com o Elemento [\<authenticationModules> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md). Os módulos de autenticação personalizados devem implementar a interface <xref:System.Net.IAuthenticationModule>.  
  
 O exemplo a seguir configura um módulo de autenticação personalizado.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 Use o Elemento [\<webRequestModules> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) para configurar o aplicativo para usar módulos personalizados específicos ao protocolo para solicitar informações de recursos da Internet. Os módulos especificados devem implementar a interface <xref:System.Net.IWebRequestCreate>. É possível substituir os módulos padrão HTTP, HTTPS e de solicitação de arquivo especificando o módulo personalizado no arquivo de configuração, como no exemplo a seguir.  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Programação de rede no .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Esquema de configurações de rede](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 Elemento [\<system.Net> (configurações de rede)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)

