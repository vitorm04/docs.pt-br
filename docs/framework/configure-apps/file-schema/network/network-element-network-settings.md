---
title: Elemento <network> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154810"
---
# <a name="network-element-network-settings"></a>\<Elemento> de rede (Configurações de rede)
Configura as opções de rede para um servidor SMTP (Simple Mail Transport Protocol, protocolo de transporte de correio simples) externo.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configurações de e-mail**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de rede**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`clientDomain`|Especifica o nome de domínio do cliente a ser usado na solicitação inicial de protocolo SMTP para se conectar ao servidor de e-mail SMTP. O valor padrão é o nome localhost do computador local que envia a solicitação.|  
|`defaultCredentials`|Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de e-mail SMTP para transações SMTP. O valor padrão é `false`.|  
|`enableSsl`|Especifica se o SSL é usado para acessar um servidor de e-mail SMTP. O valor padrão é `false`.|  
|`host`|Especifica o nome de host do servidor de e-mail SMTP para usar para transações SMTP. Esse atributo não tem valor padrão.|  
|`password`|Especifica a senha a ser usada para autenticação no servidor de e-mail SMTP. Esse atributo não tem valor padrão.|  
|`port`|Especifica o número de porta a ser usado para se conectar ao servidor de e-mail SMTP. O valor padrão é 25.|  
|`targetName`|Especifica o Nome do Provedor de Serviços (SPN) para usar para autenticação ao usar proteção estendida para transações SMTP. Esse atributo não tem valor padrão.|  
|`userName`|Especifica o nome de usuário a ser usado para autenticação no servidor de e-mail SMTP. Esse atributo não tem valor padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<smtp elemento> (configurações de rede)](smtp-element-network-settings.md)|Configura opções de envio de e-mails do Simple Mail Transport Protocol (SMTP).|  
  
## <a name="remarks"></a>Comentários  
 Alguns servidores SMTP exigem que você se autentique no servidor antes de usar. Se você quiser autenticar-se usando as credenciais de `defaultCredentials` rede `true`padrão em seu host, defina o atributo para . A <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para `defaultCredentials` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.  
  
 Você também pode usar autenticação básica (nome de usuário e senha) para autenticar-se no servidor SMTP. Para usar essa opção, você deve especificar um nome de usuário e senha válidos para o servidor SMTP especificado.  
  
> [!NOTE]
> A autenticação `userName` básica `password` envia os valores para o servidor descriptografados. Qualquer pessoa que monitore o tráfego da rede pode visualizar suas credenciais e usá-las para se conectar ao servidor. Você deve considerar o uso de um mecanismo de autenticação mais seguro, como Kerberos ou NT LAN Manager (NTLM.) Se `defaultCredentials` `true`for , Kerberos ou NTLM será usado se o servidor suportar esses protocolos.  
  
 As opções básicas de autenticação e credenciais de rede padrão são mutuamente exclusivas; se você `defaultCredentials` `true` definir e especificar um nome de usuário e senha, a credencial de rede padrão será usada e os dados básicos de autenticação são ignorados.  
  
 Para autenticação básica, `userName`se você especificar `password` um, você também deve especificar uma autenticação para autenticação no servidor de e-mail.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para `userName` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis. A <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para `password` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis. Um `password` atributo normalmente não seria inserido em arquivos de configuração por razões de segurança.  
  
 O `clientDomain` atributo altera o nome de domínio do cliente usado na solicitação inicial de protocolo SMTP para um servidor SMTP. O `clientDomain` atributo pode ser definido para o nome de domínio totalmente qualificado da máquina local, em vez do nome localhost que é usado por padrão. Isso proporciona maior conformidade com as normas de protocolo SMTP. O valor padrão é o nome localhost do computador local que envia a solicitação. A <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para `clientDomain` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.  
  
 O `targetName` atributo é usado para autenticação ao usar proteção estendida. O valor padrão é do formulário "SMTPSVC/\<host>" onde \<o host> é o nome de host do servidor de e-mail SMTP. A <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para `targetName` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.  
  
 O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de e-mail SMTP. A <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe só suporta a extensão de serviço SMTP para Segurança segura de SMTP sobre segurança de camada de transporte, conforme definido no RFC 3207. Neste modo, a sessão SMTP começa em um canal não criptografado, em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para uma comunicação segura usando SSL. Consulte o RFC 3207 publicado pela Internet Engineering Task Force (IETF) para obter mais informações.  
  
 Um método de conexão alternativo é onde uma sessão SSL é estabelecida antes de qualquer comando de protocolo ser enviado. Este método de conexão às vezes é chamado de SMTPS e, por padrão, usa a porta 465. Este método de conexão alternativa usando SSL não é suportado no momento.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para `enableSsl` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica os parâmetros SMTP apropriados para enviar e-mails usando as credenciais de rede padrão.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
