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
# <a name="network-element-network-settings"></a><span data-ttu-id="3eda6-102">\<Elemento> de rede (Configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3eda6-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="3eda6-103">Configura as opções de rede para um servidor SMTP (Simple Mail Transport Protocol, protocolo de transporte de correio simples) externo.</span><span class="sxs-lookup"><span data-stu-id="3eda6-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="3eda6-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eda6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3eda6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3eda6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3eda6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configurações de e-mail**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3eda6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="3eda6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3eda6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="3eda6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>de rede**</span><span class="sxs-lookup"><span data-stu-id="3eda6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3eda6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3eda6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eda6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3eda6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3eda6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3eda6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eda6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3eda6-112">Attributes</span></span>  
  
|<span data-ttu-id="3eda6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3eda6-113">Attribute</span></span>|<span data-ttu-id="3eda6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eda6-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="3eda6-115">Especifica o nome de domínio do cliente a ser usado na solicitação inicial de protocolo SMTP para se conectar ao servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="3eda6-116">O valor padrão é o nome localhost do computador local que envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3eda6-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="3eda6-117">Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de e-mail SMTP para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="3eda6-118">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3eda6-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="3eda6-119">Especifica se o SSL é usado para acessar um servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3eda6-120">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3eda6-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="3eda6-121">Especifica o nome de host do servidor de e-mail SMTP para usar para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="3eda6-122">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="3eda6-123">Especifica a senha a ser usada para autenticação no servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3eda6-124">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="3eda6-125">Especifica o número de porta a ser usado para se conectar ao servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="3eda6-126">O valor padrão é 25.</span><span class="sxs-lookup"><span data-stu-id="3eda6-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="3eda6-127">Especifica o Nome do Provedor de Serviços (SPN) para usar para autenticação ao usar proteção estendida para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="3eda6-128">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="3eda6-129">Especifica o nome de usuário a ser usado para autenticação no servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3eda6-130">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eda6-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3eda6-131">Child Elements</span></span>  
 <span data-ttu-id="3eda6-132">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3eda6-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eda6-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3eda6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3eda6-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="3eda6-134">Element</span></span>|<span data-ttu-id="3eda6-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eda6-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eda6-136">\<smtp elemento> (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3eda6-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="3eda6-137">Configura opções de envio de e-mails do Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="3eda6-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eda6-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="3eda6-138">Remarks</span></span>  
 <span data-ttu-id="3eda6-139">Alguns servidores SMTP exigem que você se autentique no servidor antes de usar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="3eda6-140">Se você quiser autenticar-se usando as credenciais de `defaultCredentials` rede `true`padrão em seu host, defina o atributo para .</span><span class="sxs-lookup"><span data-stu-id="3eda6-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="3eda6-141">A <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para `defaultCredentials` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3eda6-142">Você também pode usar autenticação básica (nome de usuário e senha) para autenticar-se no servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="3eda6-143">Para usar essa opção, você deve especificar um nome de usuário e senha válidos para o servidor SMTP especificado.</span><span class="sxs-lookup"><span data-stu-id="3eda6-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3eda6-144">A autenticação `userName` básica `password` envia os valores para o servidor descriptografados.</span><span class="sxs-lookup"><span data-stu-id="3eda6-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="3eda6-145">Qualquer pessoa que monitore o tráfego da rede pode visualizar suas credenciais e usá-las para se conectar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3eda6-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="3eda6-146">Você deve considerar o uso de um mecanismo de autenticação mais seguro, como Kerberos ou NT LAN Manager (NTLM.) Se `defaultCredentials` `true`for , Kerberos ou NTLM será usado se o servidor suportar esses protocolos.</span><span class="sxs-lookup"><span data-stu-id="3eda6-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="3eda6-147">As opções básicas de autenticação e credenciais de rede padrão são mutuamente exclusivas; se você `defaultCredentials` `true` definir e especificar um nome de usuário e senha, a credencial de rede padrão será usada e os dados básicos de autenticação são ignorados.</span><span class="sxs-lookup"><span data-stu-id="3eda6-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="3eda6-148">Para autenticação básica, `userName`se você especificar `password` um, você também deve especificar uma autenticação para autenticação no servidor de e-mail.</span><span class="sxs-lookup"><span data-stu-id="3eda6-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="3eda6-149">A <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para `userName` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="3eda6-150">A <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para `password` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="3eda6-151">Um `password` atributo normalmente não seria inserido em arquivos de configuração por razões de segurança.</span><span class="sxs-lookup"><span data-stu-id="3eda6-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="3eda6-152">O `clientDomain` atributo altera o nome de domínio do cliente usado na solicitação inicial de protocolo SMTP para um servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="3eda6-153">O `clientDomain` atributo pode ser definido para o nome de domínio totalmente qualificado da máquina local, em vez do nome localhost que é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="3eda6-154">Isso proporciona maior conformidade com as normas de protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="3eda6-155">O valor padrão é o nome localhost do computador local que envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3eda6-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="3eda6-156">A <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para `clientDomain` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3eda6-157">O `targetName` atributo é usado para autenticação ao usar proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="3eda6-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="3eda6-158">O valor padrão é do formulário "SMTPSVC/\<host>" onde \<o host> é o nome de host do servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="3eda6-159">A <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para `targetName` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3eda6-160">O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de e-mail SMTP.</span><span class="sxs-lookup"><span data-stu-id="3eda6-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3eda6-161">A <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe só suporta a extensão de serviço SMTP para Segurança segura de SMTP sobre segurança de camada de transporte, conforme definido no RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="3eda6-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="3eda6-162">Neste modo, a sessão SMTP começa em um canal não criptografado, em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para uma comunicação segura usando SSL.</span><span class="sxs-lookup"><span data-stu-id="3eda6-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="3eda6-163">Consulte o RFC 3207 publicado pela Internet Engineering Task Force (IETF) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3eda6-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="3eda6-164">Um método de conexão alternativo é onde uma sessão SSL é estabelecida antes de qualquer comando de protocolo ser enviado.</span><span class="sxs-lookup"><span data-stu-id="3eda6-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="3eda6-165">Este método de conexão às vezes é chamado de SMTPS e, por padrão, usa a porta 465.</span><span class="sxs-lookup"><span data-stu-id="3eda6-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="3eda6-166">Este método de conexão alternativa usando SSL não é suportado no momento.</span><span class="sxs-lookup"><span data-stu-id="3eda6-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="3eda6-167">A <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para `enableSsl` obter o valor atual do atributo a partir de arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="3eda6-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eda6-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3eda6-168">Example</span></span>  
 <span data-ttu-id="3eda6-169">O exemplo a seguir especifica os parâmetros SMTP apropriados para enviar e-mails usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="3eda6-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3eda6-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="3eda6-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="3eda6-171">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="3eda6-171">Network Settings Schema</span></span>](index.md)
