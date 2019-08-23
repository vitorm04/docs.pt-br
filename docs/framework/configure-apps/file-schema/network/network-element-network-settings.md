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
ms.openlocfilehash: ee60b990bc749dbb9c5d0e7426c57e9392ddf9d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920967"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="15343-102">\<Elemento de > de rede (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="15343-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="15343-103">Configura as opções de rede para um servidor de protocolo SMTP externo.</span><span class="sxs-lookup"><span data-stu-id="15343-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="15343-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="15343-104">\<configuration></span></span>  
<span data-ttu-id="15343-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="15343-105">\<system.net></span></span>  
<span data-ttu-id="15343-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="15343-106">\<mailSettings></span></span>  
<span data-ttu-id="15343-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="15343-107">\<smtp></span></span>  
<span data-ttu-id="15343-108">\<network></span><span class="sxs-lookup"><span data-stu-id="15343-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15343-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15343-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15343-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15343-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15343-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15343-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15343-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="15343-112">Attributes</span></span>  
  
|<span data-ttu-id="15343-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="15343-113">Attribute</span></span>|<span data-ttu-id="15343-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="15343-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="15343-115">Especifica o nome de domínio do cliente a ser usado na solicitação inicial do protocolo SMTP para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="15343-116">O valor padrão é o nome de localhost do computador local que está enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="15343-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="15343-117">Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de email SMTP para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="15343-118">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="15343-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="15343-119">Especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="15343-120">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="15343-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="15343-121">Especifica o nome do host do servidor de email SMTP a ser usado para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="15343-122">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="15343-123">Especifica a senha a ser usada para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="15343-124">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="15343-125">Especifica o número da porta a ser usada para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="15343-126">O valor padrão é 25.</span><span class="sxs-lookup"><span data-stu-id="15343-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="15343-127">Especifica o nome do provedor de serviços (SPN) a ser usado para autenticação ao usar a proteção estendida para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="15343-128">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="15343-129">Especifica o nome de usuário a ser usado para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="15343-130">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15343-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15343-131">Child Elements</span></span>  
 <span data-ttu-id="15343-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="15343-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15343-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15343-133">Parent Elements</span></span>  
  
|<span data-ttu-id="15343-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="15343-134">Element</span></span>|<span data-ttu-id="15343-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="15343-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15343-136">\<Elemento de > SMTP (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="15343-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="15343-137">Configura as opções de envio de email do protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15343-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="15343-138">Remarks</span></span>  
 <span data-ttu-id="15343-139">Alguns servidores SMTP exigem que você se autentique no servidor antes de usar o.</span><span class="sxs-lookup"><span data-stu-id="15343-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="15343-140">Se você quiser se autenticar usando as credenciais de rede padrão em seu host, defina `defaultCredentials` o atributo `true`como.</span><span class="sxs-lookup"><span data-stu-id="15343-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="15343-141">A <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `defaultCredentials` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="15343-142">Você também pode usar a autenticação básica (um nome de usuário e senha) para se autenticar no servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="15343-143">Para usar essa opção, você deve especificar um nome de usuário e uma senha válidos para o servidor SMTP especificado.</span><span class="sxs-lookup"><span data-stu-id="15343-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15343-144">A autenticação básica envia `userName` os `password` valores e ao servidor sem criptografia.</span><span class="sxs-lookup"><span data-stu-id="15343-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="15343-145">Qualquer pessoa que monitorar o tráfego de rede pode exibir suas credenciais e usá-las para se conectar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="15343-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="15343-146">Você deve considerar o uso de um mecanismo de autenticação mais seguro, como o Kerberos ou o NT LAN Manager (NTLM). Se `defaultCredentials` for`true`, o Kerberos ou NTLM será usado se o servidor oferecer suporte a esses protocolos.</span><span class="sxs-lookup"><span data-stu-id="15343-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="15343-147">As opções de autenticação básica e credenciais de rede padrão são mutuamente exclusivas; Se você definir `defaultCredentials` como `true` e especificar um nome de usuário e uma senha, a credencial de rede padrão será usada e os dados de autenticação básica serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="15343-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="15343-148">Para a autenticação básica, se você `userName`especificar um, também deverá especificar `password` um para autenticação por conta própria no servidor de email.</span><span class="sxs-lookup"><span data-stu-id="15343-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="15343-149">A <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `userName` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="15343-150">A <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `password` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="15343-151">Um `password` atributo normalmente não seria inserido em arquivos de configuração por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="15343-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="15343-152">O `clientDomain` atributo altera o nome de domínio do cliente usado na solicitação inicial do protocolo SMTP para um servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="15343-153">O `clientDomain` atributo pode ser definido como o nome de domínio totalmente qualificado do computador local, em vez do nome do localhost usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="15343-154">Isso fornece maior conformidade com os padrões de protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="15343-155">O valor padrão é o nome de localhost do computador local que está enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="15343-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="15343-156">A <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `clientDomain` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="15343-157">O `targetName` atributo é usado para autenticação ao usar a proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="15343-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="15343-158">O valor padrão é no formato "SmtpSvc/\<host >", em que \<host > é o nome do host do servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="15343-159">A <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `targetName` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="15343-160">O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="15343-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="15343-161">A <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe dá suporte apenas à extensão de serviço SMTP para segurança SMTP pela camada de transporte, conforme definido no RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="15343-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="15343-162">Nesse modo, a sessão SMTP começa em um canal não criptografado. em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para a comunicação segura usando SSL.</span><span class="sxs-lookup"><span data-stu-id="15343-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="15343-163">Consulte RFC 3207 publicado pela Internet Engineering Task Force (IETF) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="15343-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="15343-164">Um método de conexão alternativo é onde uma sessão SSL é estabelecida antecipadamente antes que qualquer comando de protocolo seja enviado.</span><span class="sxs-lookup"><span data-stu-id="15343-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="15343-165">Esse método de conexão às vezes é chamado de SMTPs e, por padrão, usa a porta 465.</span><span class="sxs-lookup"><span data-stu-id="15343-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="15343-166">No momento, não há suporte para esse método de conexão alternativo usando SSL.</span><span class="sxs-lookup"><span data-stu-id="15343-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="15343-167">A <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual `enableSsl` do atributo dos arquivos de configuração aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="15343-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15343-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="15343-168">Example</span></span>  
 <span data-ttu-id="15343-169">O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="15343-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15343-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15343-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="15343-171">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="15343-171">Network Settings Schema</span></span>](index.md)
