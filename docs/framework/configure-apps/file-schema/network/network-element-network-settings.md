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
ms.openlocfilehash: f7b73a725cd406df9ce41e2c4522850ce974022f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089214"
---
# <a name="network-element-network-settings"></a>Elemento de > de rede \<(configurações de rede)
Configura as opções de rede para um servidor de protocolo SMTP externo.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<smtp >** ](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**rede** >

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
|`clientDomain`|Especifica o nome de domínio do cliente a ser usado na solicitação inicial do protocolo SMTP para se conectar ao servidor de email SMTP. O valor padrão é o nome de localhost do computador local que está enviando a solicitação.|  
|`defaultCredentials`|Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de email SMTP para transações SMTP. O valor padrão é `false`.|  
|`enableSsl`|Especifica se o SSL é usado para acessar um servidor de email SMTP. O valor padrão é `false`.|  
|`host`|Especifica o nome do host do servidor de email SMTP a ser usado para transações SMTP. Esse atributo não tem valor padrão.|  
|`password`|Especifica a senha a ser usada para autenticação no servidor de email SMTP. Esse atributo não tem valor padrão.|  
|`port`|Especifica o número da porta a ser usada para se conectar ao servidor de email SMTP. O valor padrão é 25.|  
|`targetName`|Especifica o nome do provedor de serviços (SPN) a ser usado para autenticação ao usar a proteção estendida para transações SMTP. Esse atributo não tem valor padrão.|  
|`userName`|Especifica o nome de usuário a ser usado para autenticação no servidor de email SMTP. Esse atributo não tem valor padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<elemento > SMTP (configurações de rede)](smtp-element-network-settings.md)|Configura as opções de envio de email do protocolo SMTP.|  
  
## <a name="remarks"></a>Comentários  
 Alguns servidores SMTP exigem que você se autentique no servidor antes de usar o. Se você quiser se autenticar usando as credenciais de rede padrão no seu host, defina o atributo `defaultCredentials` como `true`. A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `defaultCredentials` dos arquivos de configuração aplicáveis.  
  
 Você também pode usar a autenticação básica (um nome de usuário e senha) para se autenticar no servidor SMTP. Para usar essa opção, você deve especificar um nome de usuário e uma senha válidos para o servidor SMTP especificado.  
  
> [!NOTE]
> A autenticação básica envia os valores de `userName` e `password` ao servidor sem criptografia. Qualquer pessoa que monitorar o tráfego de rede pode exibir suas credenciais e usá-las para se conectar ao servidor. Você deve considerar o uso de um mecanismo de autenticação mais seguro, como o Kerberos ou o NT LAN Manager (NTLM). Se `defaultCredentials` for `true`, o Kerberos ou NTLM será usado se o servidor oferecer suporte a esses protocolos.  
  
 As opções de autenticação básica e credenciais de rede padrão são mutuamente exclusivas; Se você definir `defaultCredentials` como `true` e especificar um nome de usuário e uma senha, a credencial de rede padrão será usada e os dados de autenticação básica serão ignorados.  
  
 Para a autenticação básica, se você especificar um `userName`, também deverá especificar um `password` para autenticar-se no servidor de email.  
  
 A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `userName` dos arquivos de configuração aplicáveis. A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `password` dos arquivos de configuração aplicáveis. Um atributo `password` normalmente não seria inserido em arquivos de configuração por motivos de segurança.  
  
 O atributo `clientDomain` altera o nome de domínio do cliente usado na solicitação inicial do protocolo SMTP para um servidor SMTP. O atributo `clientDomain` pode ser definido como o nome de domínio totalmente qualificado do computador local, em vez do nome do localhost que é usado por padrão. Isso fornece maior conformidade com os padrões de protocolo SMTP. O valor padrão é o nome de localhost do computador local que está enviando a solicitação. A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `clientDomain` dos arquivos de configuração aplicáveis.  
  
 O atributo `targetName` é usado para autenticação ao usar a proteção estendida. O valor padrão é o formato "SMTPSVC/\<host >" em que \<host > é o nome do host do servidor de email SMTP. A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `targetName` dos arquivos de configuração aplicáveis.  
  
 O atributo `enableSsl` especifica se o SSL é usado para acessar um servidor de email SMTP. A classe <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> só dá suporte à extensão de serviço SMTP para segurança SMTP sobre a camada de transporte, conforme definido no RFC 3207. Nesse modo, a sessão SMTP começa em um canal não criptografado. em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para a comunicação segura usando SSL. Consulte RFC 3207 publicado pela Internet Engineering Task Force (IETF) para obter mais informações.  
  
 Um método de conexão alternativo é onde uma sessão SSL é estabelecida antecipadamente antes que qualquer comando de protocolo seja enviado. Esse método de conexão às vezes é chamado de SMTPs e, por padrão, usa a porta 465. No momento, não há suporte para esse método de conexão alternativo usando SSL.  
  
 A propriedade <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> pode ser usada para obter o valor atual do atributo `enableSsl` dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [Esquema de configurações de rede](index.md)
