---
title: "&lt;rede&gt; elemento (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d3e99a10403a735383ee5e1a78c1f85ac7fd8281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="3b89f-102">&lt;rede&gt; elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3b89f-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3b89f-103">Configura as opções de rede para um servidor de transporte protocolo SMTP (Simple Mail) externo.</span><span class="sxs-lookup"><span data-stu-id="3b89f-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="3b89f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3b89f-104">\<configuration></span></span>  
<span data-ttu-id="3b89f-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="3b89f-105">\<system.net></span></span>  
<span data-ttu-id="3b89f-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="3b89f-106">\<mailSettings></span></span>  
<span data-ttu-id="3b89f-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="3b89f-107">\<smtp></span></span>  
<span data-ttu-id="3b89f-108">\<rede ></span><span class="sxs-lookup"><span data-stu-id="3b89f-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b89f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b89f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b89f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3b89f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b89f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3b89f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b89f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3b89f-112">Attributes</span></span>  
  
|<span data-ttu-id="3b89f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3b89f-113">Attribute</span></span>|<span data-ttu-id="3b89f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b89f-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="3b89f-115">Especifica o nome de domínio do cliente a ser usado na solicitação do protocolo SMTP inicial para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="3b89f-116">O valor padrão é o nome do host local do computador local, enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3b89f-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="3b89f-117">Especifica se as credenciais de usuário padrão devem ser usadas para acessar o servidor de email SMTP para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="3b89f-118">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3b89f-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="3b89f-119">Especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3b89f-120">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="3b89f-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="3b89f-121">Especifica o nome do host do servidor de email SMTP a ser usado para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="3b89f-122">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="3b89f-123">Especifica a senha a ser usado para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3b89f-124">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="3b89f-125">Especifica o número da porta a ser usado para se conectar ao servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="3b89f-126">O valor padrão é 25.</span><span class="sxs-lookup"><span data-stu-id="3b89f-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="3b89f-127">Especifica o serviço de provedor SPN (nome) a ser usada para autenticação com proteção estendida para transações SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="3b89f-128">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="3b89f-129">Especifica o nome de usuário a ser usado para autenticação no servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="3b89f-130">Esse atributo não tem valor padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b89f-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3b89f-131">Child Elements</span></span>  
 <span data-ttu-id="3b89f-132">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3b89f-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b89f-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3b89f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="3b89f-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="3b89f-134">Element</span></span>|<span data-ttu-id="3b89f-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b89f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b89f-136">\<SMTP > elemento (configurações de rede)</span><span class="sxs-lookup"><span data-stu-id="3b89f-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="3b89f-137">Configura as opções de envio de mensagens de transporte protocolo SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="3b89f-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b89f-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b89f-138">Remarks</span></span>  
 <span data-ttu-id="3b89f-139">Alguns servidores SMTP requerem que você autentica para o servidor antes do uso.</span><span class="sxs-lookup"><span data-stu-id="3b89f-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="3b89f-140">Se você deseja autenticar usando as credenciais de rede padrão em seu host, defina o `defaultCredentials` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="3b89f-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="3b89f-141">O <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `defaultCredentials` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3b89f-142">Você também pode usar a autenticação básica (um nome de usuário e senha) para autenticar-se ao servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="3b89f-143">Para usar essa opção, você deve especificar um nome de usuário válido e uma senha para o servidor SMTP especificado.</span><span class="sxs-lookup"><span data-stu-id="3b89f-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b89f-144">A autenticação básica envia o `userName` e `password` valores para o servidor sem criptografia.</span><span class="sxs-lookup"><span data-stu-id="3b89f-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="3b89f-145">Qualquer pessoa monitoramento de tráfego de rede pode exibir suas credenciais e usá-los para se conectar ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3b89f-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="3b89f-146">Considere o uso de um mecanismo de autenticação mais seguro, como o Kerberos ou NT LAN Manager (NTLM). Se `defaultCredentials` é `true`, Kerberos ou NTLM será usado se o servidor oferecer suporte a esses protocolos.</span><span class="sxs-lookup"><span data-stu-id="3b89f-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="3b89f-147">As opções de credenciais de rede padrão e autenticação básicas são mutuamente exclusivas; Se você definir `defaultCredentials` para `true` e especificar um nome de usuário e senha, a credencial de rede padrão é usada e os dados de autenticação básica são ignorados.</span><span class="sxs-lookup"><span data-stu-id="3b89f-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="3b89f-148">Para a autenticação básica se você especificar um `userName`, você também deve especificar um `password` para autenticação para o servidor de email.</span><span class="sxs-lookup"><span data-stu-id="3b89f-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="3b89f-149">O <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `userName` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="3b89f-150">O <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `password` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="3b89f-151">Um `password` atributo normalmente não deve ser inserido em arquivos de configuração por motivos de segurança.</span><span class="sxs-lookup"><span data-stu-id="3b89f-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="3b89f-152">O `clientDomain` atributo altera o nome de domínio de cliente usado na solicitação inicial de protocolo SMTP para um servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="3b89f-153">O `clientDomain` atributo pode ser definido como o nome de domínio totalmente qualificado do computador local, em vez do nome de host local que é usado por padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="3b89f-154">Isso fornece maior conformidade com os padrões de protocolo SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="3b89f-155">O valor padrão é o nome do host local do computador local, enviando a solicitação.</span><span class="sxs-lookup"><span data-stu-id="3b89f-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="3b89f-156">O <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `clientDomain` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3b89f-157">O `targetName` atributo é usado para autenticação ao usar a proteção estendida.</span><span class="sxs-lookup"><span data-stu-id="3b89f-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="3b89f-158">O valor padrão é o formato "SMTPSVC /\<host >" onde \<host > é o nome do host do servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="3b89f-159">O <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `targetName` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="3b89f-160">O `enableSsl` atributo especifica se o SSL é usado para acessar um servidor de email SMTP.</span><span class="sxs-lookup"><span data-stu-id="3b89f-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="3b89f-161">O <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe só dá suporte à extensão do serviço SMTP para SMTP seguro em Transport Layer Security conforme definido na RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="3b89f-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="3b89f-162">Nesse modo, a sessão SMTP começa em um canal não criptografado, em seguida, um comando STARTTLS é emitido pelo cliente para o servidor para alternar para comunicações seguras usando SSL.</span><span class="sxs-lookup"><span data-stu-id="3b89f-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="3b89f-163">Consulte RFC 3207 publicado pelo Engineering Task Force IETF (Internet) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3b89f-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="3b89f-164">Um método alternativo de conexão é em que uma sessão SSL é estabelecida com antecedência antes de qualquer protocolo de comandos são enviados.</span><span class="sxs-lookup"><span data-stu-id="3b89f-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="3b89f-165">Esse método de conexão às vezes é chamado SMTPS e por padrão usa a porta 465.</span><span class="sxs-lookup"><span data-stu-id="3b89f-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="3b89f-166">Atualmente, não há suporte para esse método alternativo de conexão usando SSL.</span><span class="sxs-lookup"><span data-stu-id="3b89f-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="3b89f-167">O <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriedade pode ser usada para obter o valor atual do `enableSsl` atributo dos arquivos de configuração aplicável.</span><span class="sxs-lookup"><span data-stu-id="3b89f-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b89f-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b89f-168">Example</span></span>  
 <span data-ttu-id="3b89f-169">O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.</span><span class="sxs-lookup"><span data-stu-id="3b89f-169">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a><span data-ttu-id="3b89f-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b89f-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="3b89f-171">Esquema de configurações de rede</span><span class="sxs-lookup"><span data-stu-id="3b89f-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
