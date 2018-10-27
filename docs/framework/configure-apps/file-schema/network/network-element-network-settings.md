---
title: '&lt;rede&gt; (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: 242ee42ded339b349cb9e4eb93750b9f5db29b51
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50135226"
---
# <a name="ltnetworkgt-element-network-settings"></a>&lt;rede&gt; (configurações de rede)
Configura as opções de rede para um servidor de transporte protocolo SMTP (Simple Mail) externo.  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
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
|`clientDomain`|Especifica o nome de domínio do cliente para usar na solicitação de protocolo SMTP inicial para se conectar ao servidor de email SMTP. O valor padrão é o nome do host local do computador local enviar a solicitação.|  
|`defaultCredentials`|Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de email SMTP para transações de SMTP. O valor padrão é `false`.|  
|`enableSsl`|Especifica se o SSL é usado para acessar um servidor de email SMTP. O valor padrão é `false`.|  
|`host`|Especifica o nome do host do servidor de email SMTP a ser usado para transações de SMTP. Esse atributo não tem valor padrão.|  
|`password`|Especifica a senha a ser usado para autenticação no servidor de email SMTP. Esse atributo não tem valor padrão.|  
|`port`|Especifica o número de porta a ser usado para se conectar ao servidor de email SMTP. O valor padrão é 25.|  
|`targetName`|Especifica o serviço de provedor de SPN (nome) a ser usado para autenticação ao usar a proteção estendida para transações de SMTP. Esse atributo não tem valor padrão.|  
|`userName`|Especifica o nome de usuário a ser usado para autenticação no servidor de email SMTP. Esse atributo não tem valor padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<SMTP > (configurações de rede)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).|  
  
## <a name="remarks"></a>Comentários  
 Alguns servidores SMTP requerem que você autentique-se ao servidor antes do uso. Se você quiser autenticar-se usando as credenciais de rede padrão em seu host, defina as `defaultCredentials` atributo `true`. O <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `defaultCredentials` atributo dos arquivos de configuração aplicáveis.  
  
 Você também pode usar a autenticação básica (um nome de usuário e senha) para autenticar-se ao servidor SMTP. Para usar essa opção, você deve especificar um nome de usuário válido e uma senha para o servidor SMTP especificado.  
  
> [!NOTE]
>  A autenticação básica envia o `userName` e `password` valores para o servidor não criptografado. Qualquer pessoa de monitoramento de tráfego de rede pode exibir suas credenciais e usá-los para se conectar ao servidor. Você deve considerar usar um mecanismo de autenticação mais seguro, como o Kerberos ou NT LAN Manager (NTLM). Se `defaultCredentials` é `true`, Kerberos ou NTLM será usado se o servidor dá suporte a esses protocolos.  
  
 As opções de credenciais de rede padrão e a autenticação básicas são mutuamente excludentes; Se você definir `defaultCredentials` para `true` e especifique um nome de usuário e senha, a credencial de rede padrão é usada e os dados de autenticação básica são ignorados.  
  
 Para a autenticação básica, se você especificar uma `userName`, você também deve especificar um `password` para autenticação por conta própria no servidor de email.  
  
 O <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `userName` atributo dos arquivos de configuração aplicáveis. O <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `password` atributo dos arquivos de configuração aplicáveis. Um `password` atributo normalmente não deve ser inserido nos arquivos de configuração por motivos de segurança.  
  
 O `clientDomain` atributo altera o nome de domínio do cliente usado na solicitação de protocolo SMTP inicial para um servidor SMTP. O `clientDomain` atributo pode ser definido como o nome de domínio totalmente qualificado do computador local, em vez do nome de host local que é usado por padrão. Isso fornece maior conformidade com os padrões de protocolo SMTP. O valor padrão é o nome do host local do computador local enviar a solicitação. O <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `clientDomain` atributo dos arquivos de configuração aplicáveis.  
  
 O `targetName` atributo é usado para autenticação ao usar a proteção estendida. O valor padrão é o formato "SMTPSVC /\<host >" onde \<host > é o nome do host do servidor de email SMTP. O <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `targetName` atributo dos arquivos de configuração aplicáveis.  
  
 O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de email SMTP. O <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe só dá suporte a extensão de serviço SMTP para SMTP seguro em Transport Layer Security conforme definido na RFC 3207. Nesse modo, a sessão SMTP é iniciada em um canal não criptografado e, em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para comunicações seguras usando SSL. Consulte 3207 RFC publicado pelo Engineering Task Force IETF (Internet) para obter mais informações.  
  
 Um método de conexão alternativo é onde uma sessão SSL é estabelecida com antecedência antes de qualquer protocolo que os comandos são enviados. Esse método de conexão às vezes é chamado SMTPS e por padrão usa a porta 465. Atualmente, não há suporte para esse método alternativo de conexão usando SSL.  
  
 O <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `enableSsl` atributo dos arquivos de configuração aplicáveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.  
  
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
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
