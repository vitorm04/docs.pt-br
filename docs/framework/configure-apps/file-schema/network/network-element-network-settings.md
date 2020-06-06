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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154810"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="9f807-102">Elemento \<network> (Configurações de Rede)</span><span class="sxs-lookup"><span data-stu-id="9f807-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="9f807-103">Configura as opções de rede para um servidor de protocolo SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="9f807-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="9f807-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f807-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f807-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f807-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9f807-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f807-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f807-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f807-107">Attributes</span></span>  
  
|<span data-ttu-id="9f807-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f807-108">Attribute</span></span>|<span data-ttu-id="9f807-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f807-109">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="9f807-110">Especifica o nome de domínio do cliente a ser usado na solicitação inicial do protocolo SMTP para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-110">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="9f807-111">O valor padrão é o nome de localhost do computador local que está enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="9f807-111">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="9f807-112">Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de email SMTP para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-112">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="9f807-113">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9f807-113">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="9f807-114">Especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-114">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9f807-115">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="9f807-115">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="9f807-116">Especifica o nome do host do servidor de email SMTP a ser usado para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-116">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="9f807-117">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-117">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="9f807-118">Especifica a senha a ser usada para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-118">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9f807-119">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-119">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="9f807-120">Especifica o número da porta a ser usada para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-120">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="9f807-121">O valor padrão é 25.</span><span class="sxs-lookup"><span data-stu-id="9f807-121">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="9f807-122">Especifica o nome do provedor de serviços (SPN) a ser usado para autenticação ao usar a proteção estendida para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-122">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="9f807-123">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-123">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="9f807-124">Especifica o nome de usuário a ser usado para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-124">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9f807-125">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-125">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f807-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f807-126">Child Elements</span></span>  
 <span data-ttu-id="9f807-127">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9f807-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f807-128">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f807-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9f807-129">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f807-129">Element</span></span>|<span data-ttu-id="9f807-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f807-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f807-131">\<smtp>Elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="9f807-131">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="9f807-132">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-132">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f807-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f807-133">Remarks</span></span>  
 <span data-ttu-id="9f807-134">Alguns servidores SMTP exigem que você se autentique no servidor antes de usar o.</span><span class="sxs-lookup"><span data-stu-id="9f807-134">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="9f807-135">Se você quiser se autenticar usando as credenciais de rede padrão em seu host, defina o `defaultCredentials` atributo como `true` .</span><span class="sxs-lookup"><span data-stu-id="9f807-135">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="9f807-136">A <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `defaultCredentials` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-136">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9f807-137">Você também pode usar a autenticação básica (um nome de usuário e senha) para se autenticar no servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-137">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="9f807-138">Para usar essa opção, você deve especificar um nome de usuário e uma senha válidos para o servidor SMTP especificado.</span><span class="sxs-lookup"><span data-stu-id="9f807-138">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f807-139">A autenticação básica envia `userName` os `password` valores e ao servidor sem criptografia.</span><span class="sxs-lookup"><span data-stu-id="9f807-139">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="9f807-140">Qualquer pessoa que monitorar o tráfego de rede pode exibir suas credenciais e usá-las para se conectar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="9f807-140">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="9f807-141">Você deve considerar o uso de um mecanismo de autenticação mais seguro, como o Kerberos ou o NT LAN Manager (NTLM). Se `defaultCredentials` for `true` , o Kerberos ou NTLM será usado se o servidor oferecer suporte a esses protocolos.</span><span class="sxs-lookup"><span data-stu-id="9f807-141">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="9f807-142">As opções de autenticação básica e credenciais de rede padrão são mutuamente exclusivas; Se você definir `defaultCredentials` como `true` e especificar um nome de usuário e uma senha, a credencial de rede padrão será usada e os dados de autenticação básica serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="9f807-142">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="9f807-143">Para a autenticação básica, se você especificar um `userName` , também deverá especificar um `password` para autenticação por conta própria no servidor de email.</span><span class="sxs-lookup"><span data-stu-id="9f807-143">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="9f807-144">A <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `userName` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-144">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="9f807-145">A <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `password` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-145">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="9f807-146">Um `password` atributo normalmente não seria inserido em arquivos de configuração por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="9f807-146">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="9f807-147">O `clientDomain` atributo altera o nome de domínio do cliente usado na solicitação inicial do protocolo SMTP para um servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-147">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="9f807-148">O `clientDomain` atributo pode ser definido como o nome de domínio totalmente qualificado do computador local, em vez do nome do localhost usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-148">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="9f807-149">Isso fornece maior conformidade com os padrões de protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-149">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="9f807-150">O valor padrão é o nome de localhost do computador local que está enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="9f807-150">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="9f807-151">A <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `clientDomain` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-151">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9f807-152">O `targetName` atributo é usado para autenticação ao usar a proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="9f807-152">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="9f807-153">O valor padrão é no formato "SMTPSVC/ \<host> ", em que \<host> é o nome do host do servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-153">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="9f807-154">A <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `targetName` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-154">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9f807-155">O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="9f807-155">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9f807-156">A <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe dá suporte apenas à extensão de serviço SMTP para segurança SMTP pela camada de transporte, conforme definido no RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="9f807-156">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="9f807-157">Nesse modo, a sessão SMTP começa em um canal não criptografado. em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para a comunicação segura usando SSL.</span><span class="sxs-lookup"><span data-stu-id="9f807-157">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="9f807-158">Consulte RFC 3207 publicado pela Internet Engineering Task Force (IETF) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9f807-158">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="9f807-159">Um método de conexão alternativo é onde uma sessão SSL é estabelecida antecipadamente antes que qualquer comando de protocolo seja enviado.</span><span class="sxs-lookup"><span data-stu-id="9f807-159">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="9f807-160">Esse método de conexão às vezes é chamado de SMTPs e, por padrão, usa a porta 465.</span><span class="sxs-lookup"><span data-stu-id="9f807-160">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="9f807-161">No momento, não há suporte para esse método de conexão alternativo usando SSL.</span><span class="sxs-lookup"><span data-stu-id="9f807-161">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="9f807-162">A <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `enableSsl` atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="9f807-162">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f807-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f807-163">Example</span></span>  
 <span data-ttu-id="9f807-164">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="9f807-164">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f807-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f807-165">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="9f807-166">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="9f807-166">Network Settings Schema</span></span>](index.md)
